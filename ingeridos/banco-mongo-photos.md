> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da estrutura do banco MongoDB da WeCareU no momento da extração (2026-10-21). Descreve objetos, colunas ou campos, chaves, índices, volumes e relações. Não traz o conteúdo das linhas, não cruza com código e não descreve tela. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Banco `Photos`

Extração em 2026-10-21, host `server.wecareu.app:27017`.

## Leitura da estrutura

Isto é leitura da estrutura, não decisão de produto. O nome do banco `Photos` e da coleção `photos` sugere guarda de fotos. A forma observada traz `OwnerId`, `PhotoType`, `Created`, `Change`, `ChangedBy`, `IsActive` e o caminho `DtFotos` (string longa; o valor não foi registrado).

## Coleção `photos`

A coleção tem 1 documento. A contagem é exata (`exact_count`). Para a forma foi lido 1 documento (`scanned`). O scan não foi cortado.

Capped: não.

Não há validator.

Nível de validação: nulo. Ação de validação: nula.

Índices:

- `_id_`: campo `_id`, direção `1`; unique não; sparse não; TTL nenhum; parcial não.

Campos:

O tipo `uuid` é identificador binário (subtipo UUID). Em string longa e em binário, o valor não foi registrado.

| Caminho | Tipos | Presença (`present_in_scanned` de `scanned`) | Nota |
| --- | --- | --- | --- |
| `Change` | `date` | 1 de 1 | nenhuma |
| `ChangedBy` | `string` | 1 de 1 | nenhuma |
| `Created` | `date` | 1 de 1 | nenhuma |
| `DtFotos` | `string` | 1 de 1 | String longa. O valor não foi registrado. |
| `IsActive` | `bool` | 1 de 1 | nenhuma |
| `OwnerId` | `uuid` | 1 de 1 | Identificador binário (subtipo UUID). O valor não foi registrado. |
| `PhotoType` | `int` | 1 de 1 | nenhuma |
| `_id` | `uuid` | 1 de 1 | Identificador binário (subtipo UUID). O valor não foi registrado. |

## Relações declaradas

Nenhuma neste banco.

## Nomes que parecem ligação

- O campo `ChangedBy` (tipo `string`) coincide com a coluna `ChangedBy` (`varchar(50)`) em `address.dbo.address`, `Audition.dbo.Audit`, `Email.dbo.EmailOptions`, `Email.dbo.Emails`, `Enterprise.dbo.Enterprise`, `I18N.dbo.I18N`, `PaymentPlans.dbo.Cupom`, `PaymentPlans.dbo.PaymentPlans`, `PaymentPlans.dbo.PlanDurationValue`, `Phone.dbo.Telefones`, `Report.dbo.Report`, `Report.dbo.ReportFotos`, `SystemsData.dbo.EnterpriseSystems`, `SystemsData.dbo.Groups`, `SystemsData.dbo.GroupsPermissions`, `SystemsData.dbo.Permissions`, `SystemsData.dbo.Screens`, `SystemsData.dbo.Systems`, `SystemService.dbo.Company`, `SystemService.dbo.CompanyUsers`, `SystemService.dbo.Schedule`, `SystemService.dbo.ScheduleServicesProvided`, `SystemService.dbo.SystemService`, `SystemService.dbo.UserService`, `UserLogin.dbo.BlockUsers`, `UserLogin.dbo.GrupoUsuario`, `UserLogin.dbo.Session`, `UserLogin.dbo.Usuario`, `UserLogin.dbo.forgetpassword`. Inferida pelo nome, não é constraint.
- O campo `Created` (tipo `date`) coincide com a coluna `Created` (`date`) em `address.dbo.address`, `Email.dbo.EmailOptions`, `Email.dbo.Emails`, `Enterprise.dbo.Enterprise`, `I18N.dbo.I18N`, `PaymentPlans.dbo.Cupom`, `PaymentPlans.dbo.PaymentPlans`, `PaymentPlans.dbo.PlanDurationValue`, `Phone.dbo.Telefones`, `Report.dbo.Report`, `Report.dbo.ReportFotos`, `SystemsData.dbo.EnterpriseSystems`, `SystemsData.dbo.Groups`, `SystemsData.dbo.GroupsPermissions`, `SystemsData.dbo.Permissions`, `SystemsData.dbo.Screens`, `SystemsData.dbo.Systems`, `SystemService.dbo.Company`, `SystemService.dbo.CompanyUsers`, `SystemService.dbo.Schedule`, `SystemService.dbo.ScheduleServicesProvided`, `SystemService.dbo.SystemService`, `SystemService.dbo.UserService`, `UserLogin.dbo.BlockUsers`, `UserLogin.dbo.GrupoUsuario`, `UserLogin.dbo.Session`, `UserLogin.dbo.Usuario`, `UserLogin.dbo.forgetpassword`. Inferida pelo nome, não é constraint.
- O campo `IsActive` (tipo `bool`) coincide com a coluna `IsActive` (`bit`) em `address.dbo.address`, `Email.dbo.EmailOptions`, `Email.dbo.Emails`, `Enterprise.dbo.Enterprise`, `I18N.dbo.I18N`, `PaymentPlans.dbo.Cupom`, `PaymentPlans.dbo.PaymentPlans`, `PaymentPlans.dbo.PlanDurationValue`, `Phone.dbo.Telefones`, `Report.dbo.Report`, `Report.dbo.ReportFotos`, `SystemsData.dbo.EnterpriseSystems`, `SystemsData.dbo.Groups`, `SystemsData.dbo.GroupsPermissions`, `SystemsData.dbo.Permissions`, `SystemsData.dbo.Screens`, `SystemsData.dbo.Systems`, `SystemService.dbo.Company`, `SystemService.dbo.CompanyUsers`, `SystemService.dbo.Schedule`, `SystemService.dbo.ScheduleServicesProvided`, `SystemService.dbo.SystemService`, `SystemService.dbo.UserService`, `UserLogin.dbo.BlockUsers`, `UserLogin.dbo.GrupoUsuario`, `UserLogin.dbo.Session`, `UserLogin.dbo.Usuario`, `UserLogin.dbo.forgetpassword`. Inferida pelo nome, não é constraint.
- O campo `OwnerId` (tipo `uuid`, identificador binário, subtipo UUID) coincide com a coluna `OwnerId` (`uniqueidentifier`) em `address.dbo.address`, `Phone.dbo.Telefones`. Inferida pelo nome, não é constraint.

## Ligações

[[banco-indice]]

[[banco-mongo-relacoes]]
