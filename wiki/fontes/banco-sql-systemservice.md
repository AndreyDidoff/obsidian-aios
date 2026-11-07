---
tipo: fonte
arquivo: "ingeridos/banco-sql-systemservice.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco SystemService"]
---

# Banco SystemService

Leitura de estrutura em 21/10, host `server.wecareu.app`. Não é decisão de produto. Não há chave estrangeira declarada. Porta: [[banco-indice]]. Pares: [[banco-sql-relacoes]].

Seis tabelas, 28 linhas no total.

- `dbo.Company` — 0 linhas.
- `dbo.CompanyUsers` — 0 linhas.
- `dbo.Schedule` — 0 linhas.
- `dbo.ScheduleServicesProvided` — 0 linhas.
- `dbo.SystemService` — 28 linhas.
- `dbo.UserService` — 0 linhas.

`UserService.ServiceId`, `ScheduleServicesProvided.ServiceId` e `Company.Logo` estão sem destino único. `Schedule.ServiceProvideAddressId` aponta, por nome e com força fraca, para `address.address.Id`.
