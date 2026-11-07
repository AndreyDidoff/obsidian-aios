> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `Email`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão do produto 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O banco `Email` tem duas tabelas. `dbo.EmailOptions` sugere configuração de envio (`PrimaryDomain`, `PrimaryPort`, `Email`, `UsernamePassword`, `Owner`). `dbo.Emails` sugere o cadastro do endereço (`Email`, `OwnerIndentifier`). As duas têm colunas de vigência e auditoria. Não há chave estrangeira declarada entre elas.

## Objetos que este banco não tem

- Views: Nenhuma.
- Procedures: Nenhuma.
- Functions: Nenhuma.
- Synonyms: Nenhum.
- Triggers: Nenhum.
- Checks: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Índices além da chave primária: Nenhum.

## Tabela `dbo.EmailOptions`

- Linhas: 2. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__EmailOpt__3214EC07EB2BF666` nas colunas `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__EmailOptions__Id__3C69FB99` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Owner` | `uniqueidentifier` | não | não | nenhum | — |
| `PrimaryDomain` | `varchar(100)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `PrimaryPort` | `varchar(5)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `Email` | `varchar(150)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `UsernamePassword` | `varchar(150)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `IsActive` | `bit` | não | não | `DF__EmailOpti__IsAct__3D5E1FD2` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__EmailOpti__Creat__3E52440B` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__EmailOpti__DtCha__3F466844` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |

## Tabela `dbo.Emails`

- Linhas: 0. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__Emails__3214EC07CE8D5607` nas colunas `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__Emails__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `OwnerIndentifier` | `uniqueidentifier` | não | não | nenhum | — |
| `Email` | `varchar(150)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `IsActive` | `bit` | não | não | `DF__Emails__IsActive__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__Emails__Created__38996AB5` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__Emails__DtChange__398D8EEE` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

Nenhuma neste arquivo.

## Ligações

- [[banco-indice]]
- [[banco-sql-relacoes]]
- [[banco-sql-address]]
- [[banco-sql-phone]]
- [[banco-sql-enterprise]]
- [[banco-sql-i18n]]
