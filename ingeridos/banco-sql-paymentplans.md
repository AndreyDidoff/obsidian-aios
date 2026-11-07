> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `PaymentPlans`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O nome do banco `PaymentPlans` e o das tabelas `Cupom`, `PaymentPlans` e `PlanDurationValue` sugerem cupom, plano de pagamento e duração com valor do plano. `PlanDurationValue` tem a coluna `PaymentPlanId`. `Cupom` e `PaymentPlans` têm `SystemId` e `EnterpriseId`.

## Objetos que este banco não tem

Views: nenhuma. Procedures: nenhuma. Functions: nenhuma. Synonyms: nenhum. Triggers: nenhum. Checks: nenhum. Chaves estrangeiras: nenhuma. Índices além da chave primária: nenhum.

## Tabela `dbo.Cupom`

- Linhas: 0. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__Cupom__3214EC07D8757910` na coluna `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__Cupom__Id__4222D4EF` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `SystemId` | `uniqueidentifier` | não | não | nenhum | — |
| `EnterpriseId` | `uniqueidentifier` | não | não | nenhum | — |
| `Name` | `varchar(256)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `Duration` | `datetime` | não | não | nenhum | — |
| `Discount` | `decimal(18,0)` | sim | não | nenhum | — |
| `DiscountPercent` | `decimal(18,0)` | sim | não | nenhum | — |
| `IsActive` | `bit` | não | não | `DF__Cupom__IsActive__4316F928` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__Cupom__Created__440B1D61` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__Cupom__DtChange__44FF419A` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |

## Tabela `dbo.PaymentPlans`

- Linhas: 0. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__PaymentP__3214EC07748E1C5A` na coluna `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__PaymentPlans__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `SystemId` | `uniqueidentifier` | não | não | nenhum | — |
| `EnterpriseId` | `uniqueidentifier` | não | não | nenhum | — |
| `Name` | `varchar(256)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `Description` | `text` | não | não | nenhum | `Latin1_General_CI_AS` |
| `slug` | `varchar(max)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `Priorit` | `smallint` | não | não | nenhum | — |
| `IsActive` | `bit` | não | não | `DF__PaymentPl__IsAct__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__PaymentPl__Creat__38996AB5` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__PaymentPl__DtCha__398D8EEE` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |

## Tabela `dbo.PlanDurationValue`

- Linhas: 0. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__PlanDura__3214EC07A71AD9B3` na coluna `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__PlanDuration__Id__3C69FB99` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `PaymentPlanId` | `uniqueidentifier` | não | não | nenhum | — |
| `Duration` | `datetime` | não | não | nenhum | — |
| `Value` | `float` | não | não | nenhum | — |
| `Discount` | `decimal(18,0)` | sim | não | nenhum | — |
| `DiscountPercent` | `decimal(18,0)` | sim | não | nenhum | — |
| `Priorit` | `smallint` | não | não | nenhum | — |
| `IsActive` | `bit` | não | não | `DF__PlanDurat__IsAct__3D5E1FD2` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__PlanDurat__Creat__3E52440B` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__PlanDurat__DtCha__3F466844` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |

## Diagrama

```mermaid
flowchart LR
  Cupom -->|"SystemId"| Systems
  Cupom -->|"EnterpriseId"| Enterprise
  PaymentPlans -->|"SystemId"| Systems
  PaymentPlans -->|"EnterpriseId"| Enterprise
  PlanDurationValue -->|"PaymentPlanId"| PaymentPlans
```

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

- `dbo.Cupom.SystemId` e `dbo.Systems.Id` (banco `SystemsData`). Inferida pelo nome da coluna, não é constraint.
- `dbo.Cupom.EnterpriseId` e `dbo.Enterprise.Id` (banco `Enterprise`). Inferida pelo nome da coluna, não é constraint.
- `dbo.PaymentPlans.SystemId` e `dbo.Systems.Id` (banco `SystemsData`). Inferida pelo nome da coluna, não é constraint.
- `dbo.PaymentPlans.EnterpriseId` e `dbo.Enterprise.Id` (banco `Enterprise`). Inferida pelo nome da coluna, não é constraint.
- `dbo.PlanDurationValue.PaymentPlanId` e `dbo.PaymentPlans.Id` (banco `PaymentPlans`). Inferida pelo nome da coluna, não é constraint.

## Ligações

- [[banco-indice]]
- [[banco-sql-relacoes]]
- [[banco-sql-audition]]
- [[banco-sql-report]]
