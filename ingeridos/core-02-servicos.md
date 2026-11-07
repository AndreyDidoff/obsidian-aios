> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Serviços

## Onde isso mora

1. No app: o cadastro de serviços do profissional ainda é pedido de trabalho ([[board-servicos]]), não tela em uso nos apps de 21/10.
2. No BFF: [[bff-servicos]]. O app fala com api.wecareu.app.
3. Projeto Br.User.Service.API. Host https://serviceapimicroservice.bptsoftware.com.br/
4. Banco [[banco-sql-systemservice]], SQL SystemService, tabelas SystemService e UserService.

Agenda e empresa moram neste mesmo projeto e neste mesmo banco.

## O que isso é

É o cadastro do que se oferece. São duas listas no mesmo serviço.

A lista da empresa, na tabela SystemService, é o serviço disponível naquele sistema: um nome, se ainda está em uso, quando nasceu, quando mudou e quem mudou. Cada linha carrega um sistema e uma empresa. SystemId e EnterpriseId apontam por nome, com força forte, em [[banco-sql-relacoes]]; não é constraint.

A lista da pessoa, na tabela UserService, é o serviço ligado a ela: um valor numérico, se ainda está em uso, as mesmas datas e quem mudou, mais a pessoa, o sistema e a empresa. UserId aponta por nome, com força fraca, para a pessoa, em [[banco-sql-relacoes]]; não é constraint. ServiceId está sem destino único em [[banco-sql-relacoes]]. A gravação aceita o identificador que vier e não procura esse serviço na lista da empresa.

As duas listas só devolvem o que continua ativo.

## O que já se consegue fazer

Listar os serviços ativos de uma pessoa, dentro de um sistema e de uma empresa.

Listar os serviços ativos da empresa naquele sistema. Não há consulta de um item só para quem chama. A leitura de uma linha serve para montar a trilha, antes de alterar ou apagar.

Incluir um serviço da pessoa. Empresa e sistema do pedido são trocados pelos da sessão. Sem identificador, a linha nasce. Com identificador, a mesma gravação substitui a linha. Viajam o valor, quem mudou, as datas, a pessoa e o ServiceId. Não há regra de nome, de valor mínimo nem de serviço repetido. Quem mudou precisa vir no pedido.

Editar um serviço da pessoa. O pedido manda a linha inteira e cai na mesma gravação: identificador vazio inclui, identificador preenchido substitui. Se a empresa ou o sistema do pedido diferem da sessão e o cabeçalho de gestão vem preenchido, a chamada é recusada. Sem esse cabeçalho, a diferença segue. Se a gravação devolve identificador, tenta deixar trilha. A resposta diz se a trilha foi aceita.

Incluir um serviço da empresa. A empresa do pedido é trocada pela da sessão. O sistema fica o que veio no pedido. Nome e o restante seguem o mesmo caminho: identificador vazio inclui, preenchido substitui.

Editar um serviço da empresa. Vale a mesma recusa da edição da pessoa. Nesta entrada a empresa do pedido não é reescrita pela sessão.

Apagar um serviço da pessoa e apagar um serviço da empresa. A linha permanece, fica fora de uso e some das listas. O pedido chega como leitura. Na pessoa, a busca usa o identificador da linha, a pessoa, a empresa e o sistema. Na empresa, usa o identificador da linha, a empresa e o sistema. A trilha roda depois que a linha já mudou. A resposta diz se a trilha foi aceita.

Toda entrada confere a sessão antes. Sessão aceita pelo login é recusada. Sessão recusada deixa a chamada seguir.

## Em que pé está

Listar o que está ativo, da pessoa e da empresa: feito.

Incluir serviço da pessoa e da empresa: feito no dado. Pela metade no fechamento: a trilha nasce como inclusão, nomeia banco e tabela de endereço, e a resposta é a da trilha. Se a trilha quebra, a linha já foi gravada. Identificador vazio na resposta pula a trilha e responde sucesso.

Editar os dois: feito no dado, pela mesma gravação da inclusão. Pela metade na trava de empresa e sistema: a diferença só é recusada quando o cabeçalho de gestão vem preenchido. Pela metade na trilha, igual à inclusão. A edição segue mesmo quando a releitura não acha a linha.

Apagar os dois, deixando a linha fora de uso: feito no efeito. Pela metade: chega como leitura e quebra se não houver linha ativa. A trilha da pessoa grava a tabela UserService e um banco com outro nome. A trilha do catálogo não grava a tabela SystemService.

Conferência da sessão: pela metade. Token aceito vira recusa, e token recusado deixa listar, incluir, editar e apagar.

Autenticação preparada na subida: casca. Ela não entra no caminho do pedido.

Falha ao listar, gravar ou apagar: operação interna. O ocorrido vai para a operação e a chamada devolve o erro.

## O que esta nota não cobre

O aplicativo. O cadastro de serviços do profissional segue como pedido de trabalho em [[board-servicos]].

O BFF por dentro. O elo é [[bff-servicos]].

Senha, string de conexão e identificador de empresa ou de aplicativo.

O desenho do banco além do necessário para fechar a cadeia. O detalhe fica em [[banco-sql-systemservice]] e [[banco-sql-relacoes]].

O que o valor numérico representa, duração, descrição e foto do serviço.

## Incertezas

No Windows e no Linux a subida pega a conexão de login e troca o marcador de catálogo por UserLogin. O compose deste repositório aponta Database para SystemService. Fora desses dois sistemas, o serviço pede uma conexão chamada Address, e a configuração deste projeto declara a conexão UserLogin, com catálogo SystemService, sem declarar Address. Por este repositório não dá para fechar qual banco o host publicado está usando agora.

A trilha de incluir e editar, nos dois cadastros, grava banco e tabela de endereço, com motivo de inclusão também na edição. No apagar, o antes e o depois são o mesmo objeto, já inativo, então a trilha pode nascer sem diferença. O aviso de falha ao apagar ainda fala de endereço. A trava olha a linha lida; o desligamento olha os identificadores da rota. Se a rota não bater com essa linha, a trava pode deixar passar e o desligamento quebra.

A conferência manda o cabeçalho de sessão inteiro com outro prefixo na frente. No formato usual, o login recusa e esta camada deixa passar. Quem chamar com o token cru, e o login aceitar, recebe recusa. Não há, neste serviço, um contrato único do formato da sessão.

Este repositório não declara a URL do próprio host. O host desta nota é o da extração.

O valor é um número. Não dá para fechar se é preço.

Se o pedido não traz as datas, elas nascem na hora da chamada, inclusive numa edição.
