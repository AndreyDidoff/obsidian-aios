---
tipo: fonte
arquivo: ingeridos/07-figma-padroes-e-tokens.md
origem: extração via IA (Claude), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# 07 · Figma: padrões e tokens

Padrão-alvo do arquivo Figma, que está sendo refeito.

## Pontos principais

- Nome `Categoria/NomeDoComponente`, mapeado 1:1 para pacotes `@lyra-ui/*`.
- Páginas: Design System (Components, Tokens) e, por app, Screens, Flows e Archive. Archive não é fonte da verdade.
- Variáveis do Figma com os mesmos nomes dos tokens. Sem valor hardcoded; o que não existe vira decisão com o Tech Lead.
- Tela nova leva o prefixo `[NEW]` (exemplos: `SecurityCenter`, `ReviewScreen`).
- Changelog no Figma: `data | componente | tipo | descrição`.
- O `node-id` não muda com o rename e é o identificador estável.
- Divergência: exemplos usam `spacing/md` no singular; as coleções reais estão no plural (spacings, paddings, borders).

Ver [[figma-lyraui]].
