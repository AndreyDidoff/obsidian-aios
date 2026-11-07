---
tipo: fonte
arquivo: ingeridos/01-visao-geral-lyraui.md
origem: extração via IA (Claude), snapshot de 2026-10-20; o arquivo avisa que pode divergir do repositório
criado: 2026-10-20
atualizado: 2026-10-20
---

# 01 · Visão geral da LyraUI

Primeiro de uma série de 14 temas sobre o design system. Define quem é a [[lyraui]] e quem é a [[wecareu]].

## Pontos principais

- A LyraUI está em **discovery**, sem código, construída em paralelo ao MVP. O que o documento descreve é o alvo da "virada de chave", não o que roda.
- Hoje os componentes vivem em `@wecareu/*` (legado). No alvo, design system e biblioteca vão para `@lyra-ui/*`; templates e pages universais ficam em `@wecareu/*`.
- A LyraUI cobre do sub-atomic aos organisms. Também detém voz, tom, Figma e Definition of Done.
- Plataformas-alvo: `ui-client`, `web-client`, `ui-worker`, `web-worker`, `ui-business`, `web-business`, `web-admin`, `web-wiki`. O próprio texto avisa que hoje só CLIENT e WORKER existem.
- Figma (sendo refeito) e ZeroHeight (documentação). Relação com o Storybook em aberto.
- Afirma "MVP em produção". Isso conflita com [[decisoes-2026-10-20]]. Ver [[contradicoes-e-lacunas]].
