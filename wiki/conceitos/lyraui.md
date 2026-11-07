---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-21
fontes: ["[[lyraui-01-visao-geral]]", "[[lyraui-04-arquitetura]]", "[[lyraui-06-catalogo-legado]]", "[[lyraui-12-principios]]", "[[lyraui-14-ferramentas]]", "[[ssot-design-system]]", "[[panorama-do-design-system]]", "[[library-components-o-que-entrega]]", "[[library-components-em-que-pe-esta]]", "[[board-estrutura-dos-apps]]", "[[board-design-no-figma]]"]
---

# LyraUI

Design system oficial da [[wecareu]] e também a persona que fala nos apps. Não é um produto para o cliente. ([[lyraui-01-visao-geral]], [[ssot-design-system]])

## Estado

Em **discovery**. Nenhuma linha de código usa o nome LyraUI. O que roda nos apps é o legado `@wecareu/*` (13 pacotes e `@wecareu/auth-flow`). A construção corre em paralelo ao [[mvp]]. ([[lyraui-01-visao-geral]], [[lyraui-06-catalogo-legado]], [[ssot-design-system]])

## Retrato do legado em 21/10

O legado `@wecareu/*` deixou de ser só menção. [[panorama-do-design-system]] lista 12 pacotes versionados no repositório `library-design-system`, sob o nome WeCareU Design System. O mapa do que a biblioteca entrega está em [[kit-visual]]. Esse retrato é da biblioteca, não um inventário dos apps.

A LyraUI segue em discovery. Nenhuma linha deste retrato usa o nome LyraUI nem o escopo `@lyra-ui/*`. O catálogo de 20/10 continua com 13 pacotes, incluindo `image-upload`. O mesmo catálogo põe `@wecareu/auth-flow` junto das telas dos apps. O retrato do pacote em 21/10 não evidencia instalação. Ver [[fluxo-de-entrada]] e [[contradicoes-e-lacunas]]. ([[library-components-o-que-entrega]], [[library-components-em-que-pe-esta]])

## Virada de chave

Três mudanças juntas: rebrand de escopo, Atomic Design novo e repositórios novos.

| Escopo | O que guarda |
|---|---|
| `@lyra-ui/*` | sub-atomic até organisms |
| `@wecareu/*` | templates e pages universais, e o que não é design system |
| dentro do app | o que é específico daquele app e nunca é portado |

Sufixos tendem a se manter (`button-gradient`). Nomes da marca antiga, como `text-wcu`, podem mudar. Data e critério da virada não existem. ([[lyraui-04-arquitetura]])

## O que ela detém

- [[fundamentos-visuais]] e o tema (CLIENT light, WORKER dark).
- [[voz-e-escrita]].
- [[figma-lyraui]] e a documentação no ZeroHeight.
- Definition of Done: tema, tipagem, stories, 80% de cobertura, acessibilidade, documentação, exports públicos. ([[lyraui-04-arquitetura]])

## Princípios

Aprendizagem, Evolução, Interatividade e Amizade. São distintos dos pilares (artista, estética, cuidado, eficiência, simplicidade) e das características da voz. ([[lyraui-12-principios]])

## Fonte da verdade

A LyraUI se descreve como SSoT de tokens e padrões de código. O ZeroHeight é a SSoT de design. O Storybook é a vitrine técnica de hoje. A fronteira entre os três não está decidida. ([[lyraui-14-ferramentas]])

Ver [[kit-visual]], [[engenharia-de-software]], [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

O board pede biblioteca de componentes e biblioteca de design system ([[board-estrutura-dos-apps]]). A LyraUI segue em discovery. O retrato de 21/10 do legado permanece: 12 pacotes no repositório `library-design-system`. Nenhuma linha deste retrato passa a usar o nome LyraUI por causa do board. `@wecareu/auth-flow` continua sem evidência de instalação.

O board pede telas no Figma ([[board-design-no-figma]]). A LyraUI segue em discovery. Pedir a tela no Figma não cria a tela no app. O retrato de 21/10 do legado permanece.
