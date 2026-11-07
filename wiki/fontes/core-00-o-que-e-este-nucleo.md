---
tipo: fonte
arquivo: "ingeridos/core-00-o-que-e-este-nucleo.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["O que é este núcleo"]
---

# O que é este núcleo

Porta desta leva. Retrato de 21/10 do repositório BPT-Core, os microserviços por trás do BFF. O aplicativo fala com `api.wecareu.app`. Esse endereço é o BFF, [[beautiful-api]]. A regra de negócio mora aqui, nos projetos `Br.*.API`, nos hosts `*.bptsoftware.com.br` e nos bancos lidos em 21/10.

Foto desse repositório. Não é o aplicativo e não é o BFF. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

Onze bancos SQL e quatro Mongo, no host `server.wecareu.app`. O mapa está em [[banco-indice]]. Os pares pelo nome da coluna estão em [[banco-sql-relacoes]] e [[banco-mongo-relacoes]]. Não há chave estrangeira declarada. Ligação pelo nome da coluna não é constraint.

Quatro coleções não são SQL: fotos, modelos, assinatura e documentos de validação. Assinatura e documentos estavam vazios. A forma desses campos não foi inventada.

`Br.PaymentPlan.API` não tem host na lista dos 18 de [[beautiful-api]]. Cobrança tem host e não tem tabela nos onze bancos. Ticket não tem API, host nem tabela.

## O que cada tema fecha

Cada linha é uma página. Projeto, host e banco estão nela. Conta, bloqueio, endereço, telefone, serviços, agenda, empresa, organização, planos, e-mail, idiomas, fotos, relatos, documentos, assinatura, modelos, permissões, rastro e o que não saiu do papel são página.

- [[core-01-conta]] — `Br.Login.API`, `https://loginapimicroservice.bptsoftware.com.br/`, [[banco-sql-userlogin]]: `Usuario`, `Session`, `forgetpassword`, `GrupoUsuario`. Entrar, sair, senha e os dois papéis do cadastro.
- [[core-07-bloqueio]] — `Br.Block.API`, `https://blockapimicroservice.bptsoftware.com.br/`, a mesma base, tabela `BlockUsers`.
- [[core-08-enderecos]] — `Br.Address.API`, `https://addressapimicroservice.bptsoftware.com.br/`, [[banco-sql-address]], tabela `address`.
- [[core-09-telefones]] — `Br.Phone.API`, `https://phoneapimicroservice.bptsoftware.com.br/`, [[banco-sql-phone]], banco `Phone`, tabela `Telefones`. O compose aponta `PaymentPlan`. O wikilink é o do servidor.
- [[core-02-servicos]] — `Br.User.Service.API`, `https://serviceapimicroservice.bptsoftware.com.br/`, [[banco-sql-systemservice]], tabelas `SystemService` e `UserService`.
- [[core-03-agenda]] — o mesmo projeto, o mesmo host e o mesmo banco. Tabelas `Schedule` e `ScheduleServicesProvided`. A tela de 21/10 é casca. Isto não vira decisão de produto.
- [[core-04-empresa-e-colaboradores]] — o mesmo projeto, o mesmo host e o mesmo banco. Tabelas `Company` e `CompanyUsers`. `Company` é a empresa do profissional. `Enterprise` é a organização dona do aplicativo.
- [[core-05-a-organizacao]] — `Br.Enterprise.API`, `https://enterpriseapimicroservice.bptsoftware.com.br/`, [[banco-sql-enterprise]], tabela `Enterprise`.
- [[core-06-planos-cupons-e-cobranca]] — `Br.PaymentPlan.API`, sem host na lista dos 18, [[banco-sql-paymentplans]]: `Cupom`, `PaymentPlans`, `PlanDurationValue`. Cobrança: `Br.Billing.API`, `https://billingapimicroservice.bptsoftware.com.br/`, sem ação e sem tabela nos onze bancos.
- [[core-10-emails]] — `Br.Email.API`, `https://emailapimicroservice.bptsoftware.com.br/`, [[banco-sql-email]]: `Emails` e `EmailOptions`. É envio e caixa, não o e-mail do cadastro.
- [[core-17-idiomas]] — `Br.I18N.API`, `https://i18napimicroservice.bptsoftware.com.br/`, [[banco-sql-i18n]], banco e tabela `I18N`.
- [[core-11-fotos]] — `Br.Photos.API`, `https://photosapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-photos]], coleção `photos`.
- [[core-12-relatos]] — `Br.Report.API`, `https://reportapimicroservice.bptsoftware.com.br/`, [[banco-sql-report]]: `Report` e `ReportFotos`.
- [[core-13-documentos-para-validacao]] — `Br.Validation.API`, `https://validationapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-validation]], banco `Validation`, coleção `Documents`, 0 documentos. Não aprova e não recusa. A pergunta ao login acontece e não recusa.
- [[core-16-permissoes-grupos-e-telas]] — `Br.Systems.API`, `https://systemsapimicroservice.bptsoftware.com.br/`, [[banco-sql-systemsdata]]. Seis tabelas. `Screens` não é tela do aplicativo. Não há `SystemComplement` no servidor. A checagem não recusa ninguém.
- [[core-14-assinatura]] — `Br.Signature.API`, `https://signatureapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-signature]], coleção vazia. O cadastro recebe o serviço e não o chama. No BFF segue só preparada. A pergunta ao login acontece e não recusa.
- [[core-15-modelos-de-mensagem]] — `Br.Template.API`, `https://templateapimicroservice.bptsoftware.com.br/`, Mongo [[banco-mongo-template]], coleção `Template`. Listar e desligar recusam quando o login não aceita; esta checagem não está invertida. No BFF seguem só preparados.
- [[core-18-rastro-e-falhas]] — `Br.Audit.API`, `https://auditapimicroservice.bptsoftware.com.br/`, [[banco-sql-audition]], tabela `Audit`. A checagem do rastro está invertida. Falhas: `Br.Error.Loggin.API`, `https://slacklogginapimicroservice.bptsoftware.com.br/`, sem banco SQL. Operação interna. No BFF a auditoria segue só preparada.
- [[core-19-o-que-nao-saiu-do-papel]] — `Br.Ticket.Nuget`, classe vazia, sem host e sem tabela. Consola Vue deste repositório: não é o aplicativo e não é microserviço do BFF.

## Em que pé está

O pé fino fica na nota de cada tema. Nesta porta, o recorte é este. Várias conferências de acesso estão invertidas ou incompletas. A nota de cada um diz onde. Conta, bloqueio, endereço, telefone, serviços, agenda, empresa, organização, planos, e-mail, idiomas, fotos, relatos, documentos, assinatura, modelos, permissões e rastro já são página.

| Pé | O que esta porta recorta |
|---|---|
| Feito com ressalva | conta ([[core-01-conta]]), bloqueio ([[core-07-bloqueio]]), endereço ([[core-08-enderecos]]), telefone ([[core-09-telefones]]), foto ([[core-11-fotos]]) e o catálogo de serviços ([[core-02-servicos]]). A ação existe. A conferência de acesso, em vários pontos, está invertida ou incompleta |
| Pela metade | agenda ([[core-03-agenda]]), empresa do profissional ([[core-04-empresa-e-colaboradores]]), organização ([[core-05-a-organizacao]]), planos ([[core-06-planos-cupons-e-cobranca]]), e-mail ([[core-10-emails]]), idiomas ([[core-17-idiomas]]), relato ([[core-12-relatos]]), documento de validação ([[core-13-documentos-para-validacao]]), permissão ([[core-16-permissoes-grupos-e-telas]]) e modelo de mensagem ([[core-15-modelos-de-mensagem]]). A ação está escrita e o caminho até a pessoa, até o BFF ou até a tabela observada não fecha |
| Casca | cobrança ([[core-06-planos-cupons-e-cobranca]]), assinatura ([[core-14-assinatura]]), ticket e a consola Vue ([[core-19-o-que-nao-saiu-do-papel]]). Cobrança não oferece ação e não tem tabela nesta extração. Assinatura existe como serviço e o cadastro não a chama; a coleção está vazia. Ticket é classe vazia. A consola Vue desenha tela e não é o aplicativo |
| Operação interna | rastro e aviso de falha ([[core-18-rastro-e-falhas]]). Os aplicativos de 21/10 não pedem isso |

## O que esta nota não cobre

A tela, além do ponteiro. O miolo de cada tema. Senha, connection string e identificador de empresa ou de aplicativo. Decisão de produto: onde uma nota de aplicativo ou uma decisão da empresa conflitar, vale a fonte oficial.

## Incertezas

Em vários projetos, o código que sobe no Windows e no Linux força um catálogo diferente do que o compose declara. A nota de cada tema registra o caso. Telefone já é página ([[core-09-telefones]]): o compose aponta `PaymentPlan` e, no Windows e no Linux, o código força o catálogo `Phone`. Não dá para fechar qual banco o host publicado usa. O wikilink continua o do servidor em [[banco-indice]]. Agenda ([[core-03-agenda]]), empresa ([[core-04-empresa-e-colaboradores]]), organização ([[core-05-a-organizacao]]), planos ([[core-06-planos-cupons-e-cobranca]]), e-mail ([[core-10-emails]]), idiomas ([[core-17-idiomas]]) e relatos ([[core-12-relatos]]) já são página e registram o caso delas. Assinatura ([[core-14-assinatura]]), modelos ([[core-15-modelos-de-mensagem]]) e rastro ([[core-18-rastro-e-falhas]]) também são página e registram o caso delas. Documentos ([[core-13-documentos-para-validacao]]) são página: o arquivo escolhe Mongo e a subida no servidor lê banco e coleção do ambiente. Nenhuma nota desse caso segue sem página.

Não há chave estrangeira. Ligação pelo nome da coluna não é constraint.

Ver [[bpt-core]].
