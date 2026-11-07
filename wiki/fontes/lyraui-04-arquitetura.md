---
tipo: fonte
arquivo: ingeridos/04-arquitetura-e-estrutura-do-ds.md
origem: extração via IA (Claude), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# 04 · Arquitetura do Design System

Alvo da virada de chave. Nada disso está implementado como LyraUI.

## Pontos principais

- `@lyra-ui/*`: sub-atomic até organisms. `@wecareu/*`: templates e pages universais. O que é específico de um app nunca é portado.
- Cadeia: `tokens → theme → componentes → templates/pages → apps`.
- CLIENT só light, WORKER só dark, tema não exposto ao usuário. Sem valor hardcoded.
- Nomenclatura: componente em PascalCase, props `XProps`, booleanos `is`/`has`, textos via i18n. O rótulo "camelCase" para pacotes contradiz o exemplo `button-gradient` (kebab-case).
- Definition of Done: tema, tipagem, stories, **80% de cobertura**, acessibilidade, documentação, exports públicos.
- Storybook existe hoje; ZeroHeight é o alvo; a relação entre os dois está aberta.

Ver [[lyraui]], [[engenharia-de-software]].
