> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Telefones

## Onde isso mora

1. No app. Os apps de 21/10 não têm uma tela de gerir telefones em uso. O telefone entra no cadastro como dado. Esta nota não reescreve essa tela.
2. No BFF. [[bff-telefones]]. O app fala com api.wecareu.app.
3. No projeto Br.Phone.API, no host https://phoneapimicroservice.bptsoftware.com.br/
4. No banco [[banco-sql-phone]]. O servidor nomeia o banco Phone e a tabela Telefones. O compose deste repositório (Br.Login.API/docker-compose.yml, serviço br.phone.api) aponta Database para PaymentPlan. O wikilink desta nota é o do servidor.

## O que isso é

É o serviço que guarda o telefone de um dono: o número, um nome para esse telefone, se é celular, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O dono vai no OwnerId. A lista do dia a dia só devolve telefone que continua ativo.

## O que já se consegue fazer

Listar os telefones ativos de um dono. O identificador desse pedido é o dono, não o código de um telefone. Número desligado não volta.

Incluir um telefone. Se o pedido chega sem identificador, o serviço cria um e grava a linha. Se o identificador já vem preenchido, esse mesmo pedido regrava a linha existente. O telefone entra ativo quando o pedido não diz o contrário. Viajam juntos o número, o nome, se é celular, quem alterou e as datas. Não há conferência de formato do número, nem regra de um telefone só por dono.

Editar um telefone. O pedido manda o telefone inteiro, e essa foto substitui a linha. Identificador vazio nesse pedido vira inclusão, não alteração. Antes de gravar, o serviço lê uma lista tratando esse identificador como dono e descarta o que encontrou. A edição não deixa trilha.

Apagar um telefone. A linha não sai da tabela: fica fora de uso e deixa de aparecer na lista. O pedido leva só o identificador. A trilha que roda antes trata esse identificador como dono e fica com o primeiro telefone ativo desse dono. O desligamento em si procura um telefone cujo código seja esse mesmo identificador. As duas leituras não apontam para a mesma coisa. Se não houver telefone ativo para aquele dono, a trilha quebra e o número permanece como estava. Quando a trilha chega a ser escrita, ela nomeia o banco Phone e a tabela Phone, e exige no pedido quem fez, o nome, a empresa e o sistema. Se a trilha só responder que não gravou, o serviço ainda tenta desligar. Se ela estourar, o desligamento não acontece. Inclusão e edição não passam por essa trilha.

## Em que pé está

As quatro operações estão escritas e respondem, com o apagar sujeito a quebrar na trilha antes de desligar o número. OwnerId está sem destino único em [[banco-sql-relacoes]]; não é constraint, e o serviço aceita o dono que vier sem conferir se esse cadastro existe. Os apps de 21/10 seguem sem tela para gerir telefones em uso. A checagem de acesso está invertida: token aceito pelo login vira recusa, e token recusado deixa listar, incluir, editar e apagar seguirem. A autenticação preparada na subida do serviço não entra no caminho do pedido; a única trava é essa checagem.

## O que esta nota não cobre

Não cobre o aplicativo nem a tela de cadastro em que o número é digitado. Não cobre o BFF por dentro; o elo é [[bff-telefones]]. Não cobre operadora, DDD, máscara, WhatsApp nem qual tipo de cadastro pode ser dono do número. Não reproduz senha, connection string nem identificador de empresa ou aplicativo.

## Incertezas

O wikilink do banco permanece [[banco-sql-phone]]: o servidor nomeia o banco Phone e a tabela Telefones. O compose deste repositório, no serviço br.phone.api, aponta Database para PaymentPlan. O código que sobe no Windows e no Linux não lê essa variável: pega a conexão de login e força o catálogo Phone. Fora desses dois sistemas, o serviço pede uma conexão chamada Address, e a configuração deste projeto declara a conexão Phone, com catálogo Phone, sem declarar Address. Por este repositório não dá para fechar qual banco o host publicado está usando agora. A trilha do apagar grava a tabela como Phone, e o modelo da linha aponta para Telefones.
