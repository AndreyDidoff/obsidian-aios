> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `Phone`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão do produto 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O banco `Phone` tem uma tabela, `dbo.Telefones`. O nome do banco e da tabela, junto com `Telefone`, `IsMobile` e `PhoneName`, sugere um cadastro de telefone associado a `OwnerId`, com colunas de vigência e auditoria (`IsActive`, `Created`, `DtChange`, `ChangedBy`).

## Objetos que este banco não tem

- Views: Nenhuma.
- Procedures: Nenhuma.
- Functions: Nenhuma.
- Synonyms: Nenhum.
- Triggers: Nenhum.
- Checks: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Índices além da chave primária: Nenhum.

## Tabela `dbo.Telefones`

- Linhas: 1. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__Telefone__3214EC07C2BF9A52` nas colunas `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__Telefones__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `OwnerId` | `uniqueidentifier` | não | não | nenhum | — |
| `Telefone` | `varchar(14)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `IsMobile` | `bit` | não | não | `DF__Telefones__IsMob__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `IsActive` | `bit` | não | não | `DF__Telefones__IsAct__38996AB5` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__Telefones__Creat__398D8EEE` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__Telefones__DtCha__3A81B327` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `PhoneName` | `varchar(100)` | sim | não | nenhum | `Latin1_General_CI_AS` |

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

Nenhuma neste arquivo.

## Ligações

- [[banco-indice]]
- [[banco-sql-relacoes]]
- [[banco-sql-address]]
- [[banco-sql-email]]
- [[banco-sql-enterprise]]
- [[banco-sql-i18n]]
