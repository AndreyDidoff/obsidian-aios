---
tipo: fonte
arquivo: "ingeridos/core-04-empresa-e-colaboradores.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Empresa e colaboradores"]
---

# Empresa e colaboradores

Retrato de 21/10 do projeto `Br.User.Service.API`. Host `https://serviceapimicroservice.bptsoftware.com.br/`, o mesmo de serviços e de agenda. Banco [[banco-sql-systemservice]], SQL `SystemService`, tabelas `Company` e `CompanyUsers`.

`Company` é a empresa do profissional. `Enterprise`, em [[banco-sql-enterprise]], é a organização dona do aplicativo. São linhas e bancos diferentes. Ver [[core-05-a-organizacao]].

Foto desse serviço. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

1. No app. Os apps de 21/10 não têm tela de empresa do profissional e colaboradores em uso.
2. No BFF. O retrato de 21/10 não publica esta porta.
3. Neste serviço: `Br.User.Service.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

A empresa do profissional e as pessoas ligadas a ela. A empresa guarda razão social, nome fantasia, documento, representante e logo, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O colaborador é uma linha em `CompanyUsers`: qual empresa, qual pessoa, se a ligação ainda vale, as datas e quem mudou.

Abrir a empresa de uma pessoa usa a ligação ativa e, em seguida, a empresa ativa. Há uma empresa por essa leitura: se a pessoa tiver mais de uma ligação ativa, volta a primeira que o banco entregar. Não há lista das pessoas de uma empresa.

## O que já se consegue fazer

Gravar uma empresa. Viajam razão social, nome fantasia, documento, representante, logo, se está em uso, as datas e quem alterou. Empresa nova deixa o código para o banco. Gravar não confere documento repetido, não tira máscara e não exige sessão.

Alterar. O pedido manda a empresa inteira e essa foto substitui a linha. Não há releitura.

Desligar a empresa. A linha permanece em `Company` e fica fora de uso. Some da abertura da pessoa, porque essa abertura só devolve empresa ativa. As ligações em `CompanyUsers` seguem como estavam. A chamada chega como leitura. Sem empresa ativa com aquele código, a chamada quebra.

Ligar uma pessoa à empresa. Nasce uma ligação ativa, e o código da ligação fica para o banco. Quem alterou não vem de quem chamou: entra um texto fixo no código. A resposta é a empresa ativa daquele código. A ligação é gravada mesmo quando essa empresa ativa não aparece, e a mesma pessoa pode ser ligada outra vez. O serviço não procura a pessoa nem a empresa antes de gravar.

Desligar um colaborador. A ligação permanece e sai de uso. A chamada chega como leitura. Sem ligação ativa daquela pessoa com aquela empresa, a chamada quebra.

Abrir a empresa de uma pessoa. Só ligação ativa e empresa ativa. Sem ligação ativa, a chamada quebra.

Perguntar a empresa pelo documento e pela pessoa. O caminho leva a pessoa e um segundo trecho nomeado como empresa. A ação lê o documento por outro nome, então esse trecho não preenche o documento. A busca pelo documento compara a pessoa ao código da ligação, não à pessoa da ligação. Sem combinação, a chamada quebra em vez de responder vazio.

Nenhuma dessas ações confere sessão, deixa rastro ou manda a falha para a operação. Login, rastro e registro de falha estão preparados na subida e não entram no pedido.

## Em que pé está

Dá para gravar, alterar e desligar a empresa, ligar e desligar o colaborador e abrir a empresa ativa da pessoa, sem tela nos apps de 21/10 e sem esta porta no BFF. A busca pelo documento compara a pessoa ao código da ligação. O cadastro do profissional chama outro host e, ao ligar o colaborador, um caminho sem a barra que a porta espera. `Company.Logo` está sem destino único.

`CompanyUsers.CompanyId` é força forte para `Company.Id`. `CompanyUsers.UserId` é força fraca para `Usuario`, em [[banco-sql-relacoes]]. Não é constraint.

## O que esta nota não cobre

O aplicativo. O BFF por dentro. Serviços e agenda, que dividem este projeto e este host: [[core-02-servicos]] e [[core-03-agenda]]. A organização dona do aplicativo. A foto que poderia ilustrar o logo. Senha, string de conexão e identificador.

## Incertezas

Este projeto não declara o host `serviceapimicroservice`. O cliente que o login usa para falar com empresa aponta para `UrlsSystems`, configurado como `https://systemsapimicroservice.bptsoftware.com.br`, sem a barra final. Esse cliente grava a empresa no caminho certo desta porta e liga o colaborador colando o código da empresa direto em `Save/User`, sem a barra. A pergunta pelo documento manda o documento no segundo trecho; a porta nomeia esse trecho como empresa e lê o documento de outro parâmetro, que chega vazio.

No Windows e no Linux a subida lê a variável `UserLogin` e só troca o catálogo quando o texto tem o marcador, e o nome posto no lugar seria `UserLogin`. A configuração deste projeto já nomeia o catálogo `SystemService`, sem o marcador. O compose do serviço `br.user.service.api` também nomeia `Database` como `SystemService`. Fora do Windows e do Linux a subida pede a conexão `Address`, e este projeto declara `UserLogin`. Por este repositório não dá para fechar qual banco o host publicado está usando agora. O wikilink permanece [[banco-sql-systemservice]].

O modelo trata o código da empresa e o da ligação como gerados na inserção. No banco esses códigos não são identity: têm valor padrão. `Created` e a data da mudança são dia; o serviço manda data e hora, e a hora não permanece. O documento da empresa cabe em 14 caracteres. Documento com máscara não cabe, e o serviço não tira a pontuação.

No cadastro do profissional, o login grava a empresa por esse cliente e copia o código da empresa para o campo de empresa da pessoa. Essa cópia não é a linha de `CompanyUsers`. A ligação depende do passo que monta o caminho sem a barra. Na empresa criada por esse cadastro, quem alterou vai como `Mobile` e o logo vai vazio. Na ligação feita por esta porta, quem alterou é o texto fixo do código.

Ver [[bpt-core]] e [[cadastro]].
