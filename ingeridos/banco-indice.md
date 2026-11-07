> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura dos bancos SQL Server e MongoDB da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Índice dos bancos

Extração em 2026-10-21. SQL Server em `server.wecareu.app`, versão 16.0.4305.5, Developer Edition (64-bit). MongoDB no mesmo host, porta 27017. Leitura com o login `cursor-aios`. Collation dos onze bancos SQL: `Latin1_General_CI_AS`.

Isto é leitura da estrutura, não decisão de produto.

## O que entrou

Onze bancos SQL, 29 tabelas, todas em `dbo`, todas com chave primária. Quatro bancos Mongo, quatro coleções. 173 linhas no SQL, contadas por `sys.partitions`, sem leitura do conteúdo. No Mongo, dois documentos no total.

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

## O que ficou de fora

- O banco SQL `wiki`. Pedido desta extração. Não foi lido de novo e não é fonte.
- O banco `inventory_db` e o login `inventory_reader`.
- Conteúdo de linha, valor de catálogo, base64 e dado pessoal.
- Código e tela. Outro agente cruza estes arquivos com o repositório.

O login do Mongo não devolveu banco de sistema.

## Achados da estrutura

Não há, nos onze bancos, view, procedure, function, synonym, trigger, check, chave estrangeira declarada nem índice além da chave primária. Não há coluna identity. Toda chave primária existe.

Há default nomeado em várias colunas. A expressão não está visível: o login de leitura não tem `VIEW DEFINITION`. O nome do default entra no arquivo do banco. A expressão não foi inventada.

As ligações de [[banco-sql-relacoes]] e [[banco-mongo-relacoes]] são inferidas pelo nome da coluna. Força forte é nome no padrão `TabelaId` com os dois lados `uniqueidentifier`. Força fraca é nome parecido (`FkUser`, `UserId`, `Screen`) sem constraint. Coluna sem uma tabela de destino no recorte fica em "sem destino único". `Created`, `ChangedBy`, `IsActive`, `DtChange` e `Change` não são ligação.

`Signature` e `Validation.Documents` existem e estão vazias. A forma dos campos não foi observada e não foi inventada.

## Como ler

Um arquivo por banco. O dicionário da coluna está nesse arquivo. A ligação entre bancos está só nos dois arquivos de relações. Nome de tabela e de coluna fica como no servidor (`forgetpassword`, `Telefones`, `Cupom`, `OwnerIndentifier`).
