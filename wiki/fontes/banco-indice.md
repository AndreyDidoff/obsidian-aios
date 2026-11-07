---
tipo: fonte
arquivo: "ingeridos/banco-indice.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server e MongoDB da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Índice dos bancos"]
---

# Índice dos bancos

Porta da estrutura lida em 21/10. SQL Server em `server.wecareu.app`, versão 16.0.4305.5. MongoDB no mesmo host, porta 27017. Collation dos onze bancos SQL: `Latin1_General_CI_AS`. Isto é leitura da estrutura, não decisão de produto. Não traz o conteúdo das linhas e não descreve tela.

## O que entrou

Onze bancos SQL, 29 tabelas, todas em `dbo`, todas com chave primária. Quatro bancos Mongo, quatro coleções. 173 linhas no SQL, contadas sem leitura do conteúdo. No Mongo, dois documentos no total.

- [[banco-sql-address]] — `address`, 1 tabela, 14 linhas
- [[banco-sql-audition]] — `Audition`, 1 tabela, 0 linhas
- [[banco-sql-email]] — `Email`, 2 tabelas, 2 linhas
- [[banco-sql-enterprise]] — `Enterprise`, 1 tabela, 3 linhas
- [[banco-sql-i18n]] — `I18N`, 1 tabela, 0 linhas
- [[banco-sql-paymentplans]] — `PaymentPlans`, 3 tabelas, 0 linhas
- [[banco-sql-phone]] — `Phone`, 1 tabela, 1 linha
- [[banco-sql-report]] — `Report`, 2 tabelas, 0 linhas
- [[banco-sql-systemsdata]] — `SystemsData`, 6 tabelas, 3 linhas
- [[banco-sql-systemservice]] — `SystemService`, 6 tabelas, 28 linhas
- [[banco-sql-userlogin]] — `UserLogin`, 5 tabelas, 122 linhas
- [[banco-sql-relacoes]] — pares inferidos pelo nome da coluna
- [[banco-mongo-photos]] — `Photos.photos`, 1 documento
- [[banco-mongo-signature]] — `Signature.Signature`, 0 documentos
- [[banco-mongo-template]] — `Template.Template`, 1 documento
- [[banco-mongo-validation]] — `Validation.Documents`, 0 documentos
- [[banco-mongo-relacoes]] — pares entre Mongo e SQL

O banco SQL `wiki` não foi lido de novo e não é fonte. `inventory_db` ficou de fora.

## O que a estrutura não tem

Não há view, procedure, function, synonym, trigger, check, chave estrangeira declarada nem índice além da chave primária. Não há coluna identity. Há default nomeado; a expressão não está visível para o login de leitura e não foi inventada.

`Signature` e `Validation.Documents` existem e estão vazias. A forma dos campos não foi observada.

As ligações ficam em [[banco-sql-relacoes]] e [[banco-mongo-relacoes]]. Nome de tabela e de coluna fica como no servidor.

Ver [[engenharia-de-software]] e [[beautiful-api]].
