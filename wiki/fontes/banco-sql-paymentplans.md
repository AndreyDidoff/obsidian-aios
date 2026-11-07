---
tipo: fonte
arquivo: "ingeridos/banco-sql-paymentplans.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco PaymentPlans"]
---

# Banco PaymentPlans

Leitura de estrutura em 21/10. Não é decisão de produto. Não há chave estrangeira declarada. Porta: [[banco-indice]].

O banco se chama `PaymentPlans`, no plural. Três tabelas, todas com 0 linhas: `dbo.Cupom`, `dbo.PaymentPlans`, `dbo.PlanDurationValue`. `PlanDurationValue.PaymentPlanId` aponta, por nome e com força forte, para `PaymentPlans.Id`. `SystemId` e `EnterpriseId` de `Cupom` e de `PaymentPlans` apontam, com força forte, para `Systems` e `Enterprise`. Pares: [[banco-sql-relacoes]].
