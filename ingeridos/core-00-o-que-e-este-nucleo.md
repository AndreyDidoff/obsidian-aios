> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# O que é este núcleo

Porta desta leva. O aplicativo fala com `api.wecareu.app`. Esse endereço é o BFF. A regra de negócio mora aqui, nos projetos `Br.*.API`, nos hosts `*.bptsoftware.com.br` e nos bancos lidos em 21/10. A estrutura dos bancos está em [[banco-indice]]. Os pares pelo nome da coluna estão em [[banco-sql-relacoes]] e [[banco-mongo-relacoes]]. Não há chave estrangeira declarada.

Isto não é o aplicativo do cliente nem o do artista. Não é o BFF. Onde a mesma capacidade já tem nota de tela ou de BFF, a nota do tema aponta para ela e continua daí.

## Onde isso mora

Onze bancos SQL e quatro Mongo, no host `server.wecareu.app`. O mapa de cada um está em [[banco-indice]].

Quatro coleções não são SQL: fotos, modelos, assinatura e documentos de validação. Assinatura e documentos estavam vazios. A forma desses campos não foi inventada.

`Br.PaymentPlan.API` não tem host na lista dos 18. Cobrança tem host e não tem tabela nos onze bancos. Ticket não tem API, host nem tabela.

## O que cada tema fecha

Cada linha é uma nota. Projeto, host e banco estão nela.

- [[core-01-conta]] — `Br.Login.API`, `https://loginapimicroservice.bptsoftware.com.br/`, [[banco-sql-userlogin]]: `Usuario`, `Session`, `forgetpassword`, `GrupoUsuario`. Entrar, sair, senha e os dois papéis do cadastro.
- [[core-07-bloqueio]] — `Br.Block.API`, `https://blockapimicroservice.bptsoftware.com.br/`, a mesma base, tabela `BlockUsers`.
- [[core-08-enderecos]] — `Br.Address.API`, `https://addressapimicroservice.bptsoftware.com.br/`, [[banco-sql-address]], tabela `address`.
- [[core-09-telefones]] — `Br.Phone.API`, `https://phoneapimicroservice.bptsoftware.com.br/`, [[banco-sql-phone]], banco `Phone`, tabela `Telefones`. O compose aponta `PaymentPlan`. O wikilink é o do servidor.
- [[core-02-servicos]] — `Br.User.Service.API`, `https://serviceapimicroservice.bptsoftware.com.br/`, [[banco-sql-systemservice]], tabelas `SystemService` e `UserService`.
- [[core-03-agenda]] — o mesmo projeto, o mesmo host e o mesmo banco. Tabelas `Schedule` e `ScheduleServicesProvided`. A tela de 21/10 é casca. Isto não vira decisão de produto.
- [[core-04-empresa-e-colaboradores]] — o mesmo projeto, o mesmo host e o mesmo banco. Tabelas `Company` e `CompanyUsers`. Não é a organização dona do aplicativo.
- [[core-05-a-organizacao]] — `Br.Enterprise.API`, `https://enterpriseapimicroservice.bptsoftware.com.br/`, [[banco-sql-enterprise]], tabela `Enterprise`.
- [[core-06-planos-cupons-e-cobranca]] — `Br.PaymentPlan.API`, sem host na lista dos 18, [[banco-sql-paymentplans]]: `Cupom`, `PaymentPlans`, `PlanDurationValue`. Cobrança: `Br.Billing.API`, `https://billingapimicroservice.bptsoftware.com.br/`, sem ação e sem tabela nos onze bancos.
- [[core-10-emails]] — `Br.Email.API`, `https://emailapimicroservice.bptsoftware.com.br/`, [[banco-sql-email]]: `Emails` e `EmailOptions`. É envio e caixa, não o e-mail do cadastro.
- [[core-17-idiomas]] — `Br.I18N.API`, `https://i18napimicroservice.bptsoftware.com.br/`, [[banco-sql-i18n]], banco e tabela `I18N`.
- [[core-11-fotos]] — `Br.Photos.API`, `https://photosapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-photos]], coleção `photos`.
- [[core-12-relatos]] — `Br.Report.API`, `https://reportapimicroservice.bptsoftware.com.br/`, [[banco-sql-report]]: `Report` e `ReportFotos`.
- [[core-13-documentos-para-validacao]] — `Br.Validation.API`, `https://validationapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-validation]], coleção `Documents`, vazia.
- [[core-16-permissoes-grupos-e-telas]] — `Br.Systems.API`, `https://systemsapimicroservice.bptsoftware.com.br/`, [[banco-sql-systemsdata]]. Seis tabelas. `Screens` não é tela do aplicativo. Não há `SystemComplement` no servidor.
- [[core-14-assinatura]] — `Br.Signature.API`, `https://signatureapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-signature]], coleção vazia. O cadastro não chama o serviço.
- [[core-15-modelos-de-mensagem]] — `Br.Template.API`, `https://templateapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-template]], coleção `Template`.
- [[core-18-rastro-e-falhas]] — `Br.Audit.API`, `https://auditapimicroservice.bptsoftware.com.br/`, [[banco-sql-audition]], tabela `Audit`. Falhas: `Br.Error.Loggin.API`, `https://slacklogginapimicroservice.bptsoftware.com.br/`, sem banco SQL. Operação interna.
- [[core-19-o-que-nao-saiu-do-papel]] — `Br.Ticket.Nuget`, classe vazia, sem host e sem tabela. Consola Vue deste repositório: não é o aplicativo e não é microserviço do BFF.

## Em que pé está

O pé fino está em cada nota. Nesta porta, o recorte é este.

Feito com ressalva: conta, bloqueio, endereço, telefone, foto e o catálogo de serviços existem como ação. Várias conferências de acesso estão invertidas ou incompletas. A nota de cada um diz onde.

Pela metade: agenda, empresa do profissional, organização, planos, e-mail, idiomas, relato, documento de validação, permissão e modelo de mensagem. A ação está escrita e o caminho até a pessoa, até o BFF ou até a tabela observada não fecha.

Casca: cobrança não oferece ação e não tem tabela nesta extração. Assinatura existe como serviço e o cadastro não a chama; a coleção está vazia. Ticket é classe vazia. A consola Vue desenha tela e não é o aplicativo.

Operação interna: rastro e aviso de falha. Os aplicativos de 21/10 não pedem isso.

## O que esta nota não cobre

A tela, além do ponteiro. O miolo de cada tema. Senha, connection string e identificador de empresa ou de aplicativo. Decisão de produto: onde uma nota de aplicativo ou uma decisão da empresa conflitar, vale a fonte oficial.

## Incertezas

Em vários projetos, o código que sobe no Windows e no Linux força um catálogo diferente do que o compose declara. A nota de cada tema registra o caso. O wikilink continua o do servidor em [[banco-indice]].

Não há chave estrangeira. Ligação pelo nome da coluna não é constraint.
