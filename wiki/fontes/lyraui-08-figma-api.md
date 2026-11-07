---
tipo: fonte
arquivo: ingeridos/08-regras-tecnicas-figma-api-mcp.md
origem: extração via IA (Claude), snapshot de 2026-10-20; IDs podem mudar com a refação do arquivo
criado: 2026-10-20
atualizado: 2026-10-20
---

# 08 · Regras técnicas do Figma (API e MCP)

## Pontos principais

- File key `cgiDSTP8mJptixfc06ErRt`. Página Readme `0:1`, frame `35:2`. Mais de 30 páginas.
- Bindings: cor via `setBoundVariableForPaint`; spacing, borda e opacidade via `setBoundVariable`; tipografia via `textStyleId`.
- Listar páginas com `figma.root.children`. Carregar fonte com `loadFontAsync` antes de criar texto.
- IDs parciais: spacings, paddings e borders. Opacity não tem ID registrado. Intermediários das escalas não estão nas notas.
- Nomes com barra (`headings/desktop/font-heading-sm`) só viram objetos aninhados no código se houver regra explícita no Cursor. Essa regra ainda não está escrita.

Ver [[figma-lyraui]].
