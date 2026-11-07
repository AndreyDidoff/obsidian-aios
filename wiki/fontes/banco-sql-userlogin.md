---
tipo: fonte
arquivo: "ingeridos/banco-sql-userlogin.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura SQL Server da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Banco UserLogin"]
---

# Banco UserLogin

Leitura de estrutura em 21/10, host `server.wecareu.app`. Não é decisão de produto. Não há view, procedure, function, synonym, chave estrangeira, check nem trigger. Porta: [[banco-indice]]. Pares: [[banco-sql-relacoes]].

Cinco tabelas, 122 linhas no total. Não há tabela `Bilings`.

- `dbo.BlockUsers` — 2 linhas. Bloqueio entre usuários.
- `dbo.GrupoUsuario` — 1 linha. Vínculo com grupo.
- `dbo.Session` — 81 linhas. Sessão.
- `dbo.Usuario` — 6 linhas. Cadastro de quem acessa.
- `dbo.forgetpassword` — 32 linhas. Recuperação de senha.

O dicionário de colunas fica no bruto. `FkFoto`, `FkSignature` e `FkUserType` estão sem destino único em [[banco-sql-relacoes]].
