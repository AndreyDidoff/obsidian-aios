> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco MongoDB da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Relações do MongoDB

Recorte de 2026-10-21. Cada item abaixo é um par do arquivo de candidatos. O nome do campo sugere o outro lado. Nada nesta lista é constraint.

## Relações declaradas

Nenhuma no recorte. Não há chave estrangeira declarada nos 11 bancos SQL. O Mongo não declara FK para o SQL.

## Ligações do Mongo para o SQL

- `Template.Template.IdEnterprise` (`uuid`) para `Enterprise.Enterprise.Id` (`uniqueidentifier`). Força fraca. [[banco-mongo-template]] · [[banco-sql-enterprise]]. Inferida pelo nome da coluna, não é constraint.
- `Template.Template.IdSystem` (`uuid`) para `SystemsData.Systems.Id` (`uniqueidentifier`). Força fraca. [[banco-mongo-template]] · [[banco-sql-systemsdata]]. Inferida pelo nome da coluna, não é constraint.

## Ligações do SQL para o Mongo

- `Report.ReportFotos.PhotoId` (`uniqueidentifier`) para `Photos.photos._id` (`uuid`). Força fraca. [[banco-sql-report]] · [[banco-mongo-photos]]. Inferida pelo nome da coluna, não é constraint.
- `SystemsData.Systems.PhotoId` (`uniqueidentifier`) para `Photos.photos._id` (`uuid`). Força fraca. [[banco-sql-systemsdata]] · [[banco-mongo-photos]]. Inferida pelo nome da coluna, não é constraint.

## Sem destino único

- `Photos.photos.OwnerId` (`uuid`). [[banco-mongo-photos]]. Sem destino único: o nome se repete em `address.address` e `Phone.Telefones`, e não há tabela `Owner`. Inferida pelo nome da coluna, não é constraint.

## Ligações

[[banco-indice]]

[[banco-sql-relacoes]]
