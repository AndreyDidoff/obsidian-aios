---
tipo: fonte
arquivo: "ingeridos/banco-mongo-template.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura MongoDB da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco Template"]
---

# Banco Template

Leitura de estrutura em 21/10. Não é SQL. Não é decisão de produto. Porta: [[banco-indice]].

Banco `Template`, coleção `Template`, 1 documento. Campos observados: `Change`, `ChangedBy`, `Created`, `DataTemplate`, `IdEnterprise`, `IdSystem`, `IsActive`, `NameTemplate`, `TemplateType`, `_id`. O valor de `DataTemplate` e dos identificadores não foi registrado. `IdEnterprise` aponta, por nome e com força fraca, para `Enterprise.Enterprise.Id`. `IdSystem` aponta, com força fraca, para `SystemsData.Systems.Id`. Pares: [[banco-mongo-relacoes]].
