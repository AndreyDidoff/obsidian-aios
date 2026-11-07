---
tipo: fonte
arquivo: "ingeridos/banco-sql-systemsdata.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco SystemsData"]
---

# Banco SystemsData

Leitura de estrutura em 21/10, host `server.wecareu.app`. Não é decisão de produto. Não há chave estrangeira declarada. Porta: [[banco-indice]]. Pares: [[banco-sql-relacoes]] e [[banco-mongo-relacoes]].

Seis tabelas, 3 linhas no total. Não há tabela `SystemComplement`. `Screens` é tabela deste banco, não tela de aplicativo.

- `dbo.EnterpriseSystems` — 2 linhas.
- `dbo.Groups` — 0 linhas.
- `dbo.GroupsPermissions` — 0 linhas.
- `dbo.Permissions` — 0 linhas.
- `dbo.Screens` — 0 linhas.
- `dbo.Systems` — 1 linha.

`Systems.PhotoId` aponta, por nome e com força fraca, para `Photos.photos._id`.
