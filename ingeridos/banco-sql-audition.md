> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `Audition`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O banco `Audition` tem uma tabela, `Audit`. O nome sugere trilha de alteração: quem mudou, verbo, motivo, banco, tabela e o objeto antes e depois. A tabela tem `SystemId`, `EnterpriseId`, `UserId` e `AprovedId`.

## Objetos que este banco não tem

Views: nenhuma. Procedures: nenhuma. Functions: nenhuma. Synonyms: nenhum. Triggers: nenhum. Checks: nenhum. Chaves estrangeiras: nenhuma. Índices além da chave primária: nenhum.

## Tabela `dbo.Audit`

- Linhas: 0. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__Audit__3214EC076FD42DC3` na coluna `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__Audit__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `SystemId` | `uniqueidentifier` | não | não | nenhum | — |
| `EnterpriseId` | `uniqueidentifier` | não | não | nenhum | — |
| `UserId` | `uniqueidentifier` | não | não | nenhum | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `AprovedId` | `uniqueidentifier` | sim | não | nenhum | — |
| `AprovedBy` | `varchar(50)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Verb` | `varchar(10)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `Reason` | `varchar(250)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `DBDatabase` | `varchar(20)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `DBTable` | `varchar(20)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `DtChange` | `date` | não | não | `DF__Audit__DtChange__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `LastObject` | `text` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `ChangedObject` | `text` | não | não | nenhum | `Latin1_General_CI_AS` |

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

- `dbo.Audit.SystemId` e `dbo.Systems.Id` (banco `SystemsData`). Inferida pelo nome da coluna, não é constraint.
- `dbo.Audit.EnterpriseId` e `dbo.Enterprise.Id` (banco `Enterprise`). Inferida pelo nome da coluna, não é constraint.

## Ligações

- [[banco-indice]]
- [[banco-sql-relacoes]]
- [[banco-sql-paymentplans]]
- [[banco-sql-report]]
