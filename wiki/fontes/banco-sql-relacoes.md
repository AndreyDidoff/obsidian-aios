---
tipo: fonte
arquivo: "ingeridos/banco-sql-relacoes.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Relações entre os bancos SQL"]
---

# Relações entre os bancos SQL

Pares inferidos pelo nome da coluna em 21/10. Nada nesta lista é constraint. Não há chave estrangeira declarada nos onze bancos. Porta: [[banco-indice]].

`Created`, `ChangedBy`, `IsActive`, `DtChange` e `Change` não são ligação. Força forte é nome no padrão `TabelaId` com os dois lados `uniqueidentifier`. Força fraca é nome parecido, sem constraint.

## Entre bancos

- `address.address.SystemId` para `SystemsData.Systems.Id`. Força forte.
- `Audition.Audit.SystemId` para `SystemsData.Systems.Id`. Força forte. `EnterpriseId` para `Enterprise.Enterprise.Id`. Força forte. `UserId` para `UserLogin.Usuario.Id`. Força fraca.
- `I18N.I18N.SystemId` para `SystemsData.Systems.Id`. Força forte. `Screen` para `SystemsData.Screens.Id`. Força fraca. `Enterprise` para `Enterprise.Enterprise.Id`. Força fraca.
- `PaymentPlans.Cupom` e `PaymentPlans.PaymentPlans`: `SystemId` para `SystemsData.Systems.Id` e `EnterpriseId` para `Enterprise.Enterprise.Id`. Força forte. `PlanDurationValue.PaymentPlanId` para `PaymentPlans.PaymentPlans.Id`. Força forte, dentro do mesmo banco.
- `Report.Report`: `SystemId` e `EnterpriseId` fortes; `UserId` e `ReportedUserId` fracos, para `Usuario.Id`. `ReportFotos` repete `SystemId` e `EnterpriseId` fortes, e `ReportId` forte para `Report.Report.Id`.
- `SystemsData`: `EnterpriseSystems`, `Groups` e `Permissions` ligam `SystemId` a `Systems.Id`. `Groups` e `Permissions` ligam `ScreenId` a `Screens.Id`. `EnterpriseSystems.EnterpriseId` e `Groups.EnterpriseId` para `Enterprise.Enterprise.Id`. `GroupsPermissions` liga `GroupId` e `PermissionId`. Tudo força forte.
- `SystemService.SystemService` e `UserService`: `SystemId` e `EnterpriseId` fortes. `CompanyUsers.CompanyId` e `Schedule.CompanyId` fortes para `Company.Id`. `CompanyUsers.UserId`, `Schedule.RequestedUserId` e `Schedule.ProviderUserId` fracos para `Usuario.Id`. `Schedule.ServiceProvideAddressId` fraco para `address.address.Id`. `ScheduleServicesProvided.ScheduleId` forte para `Schedule.Id`.
- `UserLogin.BlockUsers`: `UserId` e `BlockedUserId` fracos para `Usuario.Id`. `GrupoUsuario.FkGroup` fraco para `Groups.Id`; `FkUser` fraco para `Usuario.Id`; `System` fraco para `Systems.Id`. `Session.FkUser` fraco para `Usuario.Id`; `FkSystem` fraco para `Systems.Id`. `Usuario.FkEnterprise` fraco para `Enterprise.Id`. `forgetpassword.iduser` fraco para `Usuario.Id`.

`GrupoUsuario.idsession` e `Session.idsession` são as duas chaves primárias com o mesmo nome de coluna. Não é uma coluna solta apontando para a outra.

## Sem destino único

`address.OwnerId`, `Audit.AprovedId`, `EmailOptions.Owner`, `Emails.OwnerIndentifier`, `Enterprise.ServicePlanId`, `Enterprise.Logo`, `Telefones.OwnerId`, `Report.ReportedItemId`, `Company.Logo`, `ScheduleServicesProvided.ServiceId`, `UserService.ServiceId`, `Usuario.FkUserType`, `Usuario.FkFoto`, `Usuario.FkSignature`.

O par com o Mongo está em [[banco-mongo-relacoes]].
