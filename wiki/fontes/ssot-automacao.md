---
tipo: fonte
arquivo: ingeridos/wecareu_automa_o_e_orquestra_o.md
origem: extração via IA (Gemini), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# SSoT de automação e orquestração

Detalha o fluxo que [[ssot-ecossistema-engenharia]] resume.

## Pontos principais

- Kanban: Backlog → ToDo → Doing → Blocked → Ready for QA → Fix → Ready for Deploy → Done.
- SDD v3 na tarefa: escopo (`pkg:button-close`, `screen:login`), contratos TypeScript, lista de arquivos.
- Antes de Doing, análise com `madge`. Se o escopo cruza uma tarefa em Doing, vai para Blocked. Comparar só nome de arquivo é proibido.
- Merge na `develop` em Ready for Deploy; produção é `develop` → `main`.
- Yalc: publicar o pacote e `yalc add` no app antes de testar.
- Jest nunca é substituído pelo Maestro. Maestro só depois do Jest, via MCP. Dívida: Chromatic.

Ver [[engenharia-de-software]].
