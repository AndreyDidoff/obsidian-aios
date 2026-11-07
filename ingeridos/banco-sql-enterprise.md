> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `Enterprise`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão do produto 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O banco `Enterprise` tem uma tabela, `dbo.Enterprise`. Os nomes (`Name`, `FantasyName`, `CNPJ`, `Representante`, `TipoNegocio`, `Segmento`, `website`, colunas de endereço, `ServicePlanId` e `Logo`) sugerem o cadastro da empresa, com colunas de vigência e auditoria (`IsActive`, `Created`, `DtChange`, `ChangedBy`).

## Objetos que este banco não tem

- Views: Nenhuma.
- Procedures: Nenhuma.
- Functions: Nenhuma.
- Synonyms: Nenhum.
- Triggers: Nenhum.
- Checks: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Índices além da chave primária: Nenhum.

## Tabela `dbo.Enterprise`

- Linhas: 3. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__Enterpri__3214EC0787192F8A` nas colunas `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__Enterprise__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Name` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `FantasyName` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `CNPJ` | `varchar(14)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Representante` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `TipoNegocio` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Segmento` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `website` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `CEP` | `varchar(8)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Cidade` | `varchar(50)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Complemento` | `varchar(max)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `Numero` | `varchar(30)` | sim | não | nenhum | `Latin1_General_CI_AS` |
| `ServicePlanId` | `uniqueidentifier` | sim | não | nenhum | — |
| `Logo` | `uniqueidentifier` | sim | não | nenhum | — |
| `IsActive` | `bit` | não | não | `DF__Enterpris__IsAct__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__Enterpris__Creat__38996AB5` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__Enterpris__DtCha__398D8EEE` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
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
- [[banco-sql-email]]
- [[banco-sql-i18n]]
