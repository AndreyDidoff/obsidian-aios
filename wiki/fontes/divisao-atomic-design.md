---
tipo: fonte
arquivo: ingeridos/gemini-code-1792527331126.md
origem: extração via IA (Gemini), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# Divisão Atomic Design e Clean Architecture

## Pontos principais

- Dois monorepos de front, não um.
- `library-design-system`: átomos e moléculas (botões, inputs, tipografia, tokens, theme). Chamado de fundação visual da LyraUI.
- `library-components`: organismos e templates (contextos, formulários, auth flow).

## Tensão

[[ssot-ecossistema-engenharia]] descreve os dois como workspaces de **um** monorepo Turborepo. [[lyraui-04-arquitetura]] põe organisms dentro de `@lyra-ui/*` e templates universais em `@wecareu/*`, não em `library-components`. Ver [[engenharia-de-software]], [[contradicoes-e-lacunas]].
