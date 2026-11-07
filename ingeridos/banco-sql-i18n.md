> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco SQL Server da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `I18N`

Extração em 2026-10-21, host `server.wecareu.app`, collation `Latin1_General_CI_AS`, edição Developer Edition (64-bit), versão do produto 16.0.4305.5 (RTM).

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O banco `I18N` tem uma tabela, `dbo.I18N`. Os nomes (`SystemId`, `Screen`, `Enterprise`, `LanguageType`, `Tag`, `TranslateText`) sugerem texto traduzido por sistema, tela, empresa e idioma, com colunas de vigência e auditoria (`IsActive`, `Created`, `DtChange`, `ChangedBy`).

## Objetos que este banco não tem

- Views: Nenhuma.
- Procedures: Nenhuma.
- Functions: Nenhuma.
- Synonyms: Nenhum.
- Triggers: Nenhum.
- Checks: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Índices além da chave primária: Nenhum.

## Tabela `dbo.I18N`

- Linhas: 0. A contagem vem de `sys.partitions` (heap ou índice clustered), sem leitura das linhas.
- Chave primária: `PK__I18N__3214EC0780D98621` nas colunas `Id`.
- Unique: Nenhuma.
- Índices além da PK: Nenhum.
- Chaves estrangeiras: Nenhuma.
- Checks e triggers: Nenhum.

| Coluna | Tipo | Nulo | Identity | Default | Collation |
| --- | --- | --- | --- | --- | --- |
| `Id` | `uniqueidentifier` | não | não | `DF__I18N__Id__36B12243` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `SystemId` | `uniqueidentifier` | não | não | nenhum | — |
| `Screen` | `uniqueidentifier` | não | não | nenhum | — |
| `Enterprise` | `uniqueidentifier` | não | não | nenhum | — |
| `LanguageType` | `varchar(5)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `Tag` | `varchar(max)` | não | não | nenhum | `Latin1_General_CI_AS` |
| `TranslateText` | `text` | não | não | nenhum | `Latin1_General_CI_AS` |
| `IsActive` | `bit` | não | não | `DF__I18N__IsActive__37A5467C` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `Created` | `date` | não | não | `DF__I18N__Created__38996AB5` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `DtChange` | `date` | não | não | `DF__I18N__DtChange__398D8EEE` — expressão não visível para o login de leitura (sem VIEW DEFINITION) | — |
| `ChangedBy` | `varchar(50)` | não | não | nenhum | `Latin1_General_CI_AS` |

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

- `dbo.I18N.SystemId` parece apontar para `SystemsData.dbo.Systems.Id`. Inferida pelo nome da coluna, não é constraint.
- `dbo.I18N.Screen` parece apontar para `SystemsData.dbo.Screens.Id`. Inferida pelo nome da coluna, não é constraint.
- `dbo.I18N.Enterprise` parece apontar para `Enterprise.dbo.Enterprise.Id`. Inferida pelo nome da coluna, não é constraint.

## Ligações

- [[banco-indice]]
- [[banco-sql-relacoes]]
- [[banco-sql-address]]
- [[banco-sql-phone]]
- [[banco-sql-email]]
- [[banco-sql-enterprise]]
