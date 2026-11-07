---
tipo: fonte
arquivo: "ingeridos/banco-sql-audition.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco Audition"]
---

# Banco Audition

Leitura de estrutura em 21/10. Não é decisão de produto. Não há chave estrangeira declarada. Porta: [[banco-indice]].

O banco se chama `Audition`. Uma tabela, `dbo.Audit`, 0 linhas. `SystemId` e `EnterpriseId` apontam, por nome e com força forte, para `Systems` e `Enterprise`. `UserId` aponta, com força fraca, para `Usuario.Id`. `AprovedId` está sem destino único. A grafia `AprovedId` fica como no servidor. Pares: [[banco-sql-relacoes]].
