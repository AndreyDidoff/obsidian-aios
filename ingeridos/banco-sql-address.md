> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `address`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão do produto 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O banco `address` tem uma tabela, `dbo.address`. O nome do banco e das colunas (`CEP`, `Logradouro`, `Cidade`, `Bairro`, `Latitude`, `Longitude`, `AddressType`) sugere um cadastro de endereço, com `SystemId`, `OwnerId` e colunas de vigência e auditoria (`IsActive`, `Created`, `DtChange`, `ChangedBy`).

## Objetos que este banco não tem

- Views: Nenhuma.
- Procedures: Nenhuma.
- Functions: Nenhuma.
- Synonyms: Nenhum.
- Triggers: Nenhum.
- Checks: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Índices além da chave primária: Nenhum.

## Tabela `dbo.address`

- Linhas: 14. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__address__3214EC07E6E2FDF9` nas colunas `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__address__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `SystemId` | `uniqueidentifier` | não | não | nenhum | — |
| `OwnerId` | `uniqueidentifier` | não | não | nenhum | — |
| `CEP` | `varchar(8)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Cidade` | `varchar(150)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Bairro` | `varchar(100)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Logradouro` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Complemento` | `varchar(150)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Numero` | `varchar(50)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Referencia` | `varchar(256)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Latitude` | `float` | não | não | nenhum | — |
| `Longitude` | `float` | não | não | nenhum | — |
| `IsActive` | `bit` | não | não | `DF__address__IsActiv__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__address__Created__38996AB5` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__address__DtChang__398D8EEE` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `AddressType` | `int` | sim | não | nenhum | — |
| `AddressName` | `varchar(100)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Region` | `varchar(100)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Country` | `varchar(100)` | sim | não | nenhum | `Latin1_General_CI_AS` |

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

- `dbo.address.SystemId` parece apontar para `SystemsData.dbo.Systems.Id`. Inferida pelo nome da coluna, não é constraint.

## Ligações

- [[banco-indice]]
- [[banco-sql-relacoes]]
- [[banco-sql-phone]]
- [[banco-sql-email]]
- [[banco-sql-enterprise]]
- [[banco-sql-i18n]]
