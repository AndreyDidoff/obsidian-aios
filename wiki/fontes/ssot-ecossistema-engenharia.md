---
tipo: fonte
arquivo: ingeridos/wecareu_ecossistema_e_engenharia_de_software.md
origem: extração via IA (Gemini), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# SSoT de ecossistema e engenharia

## Pontos principais

- Front: Expo, React Native, TypeScript. Back: C# .NET 8 e 10, API `service_api`.
- Monorepo único com Turborepo e pnpm. Workspaces `library-design-system` e `library-components` (ex.: `@wecareu/auth-flow`).
- Cadeia obrigatória: tokens → theme → componentes → apps. Sem hex hardcoded; `useTheme()` de `@wecareu/theme`; imports só por escopo npm; dependências compartilhadas em `peerDependencies`.
- Código e comentários em inglês; UI via i18n. Sem `import React` para JSX. Sem classes.
- Azure DevOps como fonte da verdade das tarefas. n8n dispara Aider. Bloqueio se outra tarefa em Doing mexe no mesmo escopo.
- SDD v3 antes do código. Yalc para ver o design system nos apps. Jest, depois Maestro via MCP. Dívida: Chromatic no lugar do Storybook visual.
- Git: `main` produção, `develop` integração, branches `CLIENT-XXX` / `WORKER-XXX` a partir de `develop`.

Ver [[engenharia-de-software]]. Há tensão com [[divisao-atomic-design]] sobre um ou dois monorepos.
