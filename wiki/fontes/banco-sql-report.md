---
tipo: fonte
arquivo: "ingeridos/banco-sql-report.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco Report"]
---

# Banco Report

Leitura de estrutura em 21/10. Não é decisão de produto. Não há chave estrangeira declarada. Porta: [[banco-indice]].

Duas tabelas, 0 linhas: `dbo.Report` e `dbo.ReportFotos`. Não se chamam `Reports` nem `ReportsPhotos`. `ReportFotos.ReportId` aponta, por nome e com força forte, para `Report.Id`. `ReportFotos.PhotoId` aponta, com força fraca, para `Photos.photos._id`. `ReportedItemId` está sem destino único. `UserId` e `ReportedUserId` apontam, com força fraca, para `Usuario.Id`. Pares: [[banco-sql-relacoes]] e [[banco-mongo-relacoes]].
