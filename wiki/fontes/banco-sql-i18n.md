---
tipo: fonte
arquivo: "ingeridos/banco-sql-i18n.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco I18N"]
---

# Banco I18N

Leitura de estrutura em 21/10. Não é decisão de produto. Não há chave estrangeira declarada. Porta: [[banco-indice]].

O banco e a tabela se chamam `I18N`. `dbo.I18N`, 0 linhas. `SystemId` aponta, por nome e com força forte, para `SystemsData.Systems.Id`. `Screen` aponta, com força fraca, para `SystemsData.Screens.Id`. `Enterprise` aponta, com força fraca, para `Enterprise.Enterprise.Id`. Pares: [[banco-sql-relacoes]].
