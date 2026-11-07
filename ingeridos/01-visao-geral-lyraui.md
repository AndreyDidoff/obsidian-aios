> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 01 · Visão geral e propósito da LyraUI

Tags: #lyraui #wecareu #design-system #visao-geral

---

## 1. Status: leia antes de tudo

- **LyraUI está em fase de discovery.** Não foi implementada no código.
- **LyraUI está sendo construída em paralelo ao MVP da WeCareU.** Ela entrará como uma versão futura do app, na chamada "virada de chave".
- Tudo que este documento descreve sobre a LyraUI é o **alvo**, não o que roda em produção.
- O que roda hoje no app é o **legado** em `@wecareu/*`, tratado como ponto de partida a ser migrado. Ver [[06-catalogo-e-inventario-legado]].

---

## 2. LyraUI x WeCareU: quem é quem

| | **WeCareU** | **LyraUI** |
|---|---|---|
| O que é | A empresa e o produto: plataforma que conecta clientes a profissionais de beleza e bem-estar (Artistas) | O Design System oficial e exclusivo da WeCareU |
| Estado | MVP em produção | Discovery, em paralelo ao MVP, não implementada |
| Papel | Entrega o serviço às pessoas usuárias | Garante a mesma identidade, linguagem e comportamento em todos os pontos de contato digitais |
| Escopo de pacote (alvo) | `@wecareu/*`: templates e pages universais, e tudo que não é design system nem biblioteca de componentes | `@lyra-ui/*`: Design System e Biblioteca de componentes |
| Escopo de pacote (hoje) | `@wecareu/*`: todos os componentes vivem aqui, inclusive os que irão para a LyraUI | Ainda não existe como pacote |

Regra de leitura: quando um documento disser "WeCareU", ele fala da empresa, do produto ou dos apps em uso. Quando disser "LyraUI", fala do sistema de design futuro. Detalhes de contexto da empresa em [[02-contexto-wecareu]] e do produto atual em [[03-estado-atual-do-produto]].

---

## 3. O que é a LyraUI

- É o Design System oficial e exclusivo da WeCareU.
- É mais que uma biblioteca de componentes: é a infraestrutura que unifica a identidade visual e técnica da empresa em todos os pontos de contato digitais.
- Funciona como a **Única Fonte da Verdade (SSoT, Single Source of Truth)**: centraliza diretrizes, tokens e padrões de código, para que Design e Engenharia colaborem com agilidade.
- É também uma **entidade/persona** que se identifica como o design da WeCareU. Ela detém as regras, o tom, a voz e a estrutura do app. Ver [[10-voz-e-tons]].

Quem trabalha em uma solução para a WeCareU deve tratar a LyraUI como ponto de partida para consistência, escala e qualidade.

---

## 4. Objetivos

1. **Identidade coesa.** Unificar a experiência visual e a redação entre todas as plataformas, para que a pessoa usuária sinta que está sempre no mesmo ecossistema WeCareU.
2. **Eficiência multiplataforma.** Oferecer elementos desenvolvidos de forma unificada, reduzindo redundância de código e garantindo o mesmo comportamento de um componente no iOS, no Android e na Web.

---

## 5. Propósito

Segundo o guia de voz, a LyraUI existe para **criar conexões e padronizar**: unir clientes, profissionais da beleza e bem-estar, empresas e prestadores de serviço em um único ambiente coeso. Também existe para integrar os times, facilitar o desenvolvimento e evoluir diariamente, conectando a essência de cuidado (Care) com bons resultados.

---

## 6. O que a LyraUI cobre

| Camada | Pertence a | Escopo (alvo) |
|---|---|---|
| Sub-atomic e Atoms | LyraUI, Design System | `@lyra-ui/*` |
| Molecules e Organisms | LyraUI, Biblioteca de Componentes | `@lyra-ui/*` |
| Templates e Pages universais | WeCareU compartilhado (não é LyraUI) | `@wecareu/*` |
| Atomic Design específico de um app | Dentro do próprio app (não é LyraUI) | Nunca portado para outro app |

A LyraUI vai do sub-atomic até os organisms. Acima disso, o que serve a todos os apps é WeCareU universal. Estrutura completa em [[04-arquitetura-e-estrutura-do-ds]].

Regras que a LyraUI detém, além dos componentes:
- Tom, voz e princípios de comunicação. Ver [[10-voz-e-tons]], [[11-escrita-e-ortografia]] e [[12-principios-de-design]].
- Padrões de organização do Figma e alinhamento com tokens. Ver [[07-figma-padroes-e-tokens]].
- Definition of Done dos componentes e convenções de nomenclatura. Ver [[04-arquitetura-e-estrutura-do-ds]].

---

## 7. Plataformas que a LyraUI vai atender

A LyraUI nasce para servir todo o ecossistema WeCareU, organizado em quatro plataformas segundo o guia de voz:

| Plataforma | Quem usa | Apps (mobile / web) |
|---|---|---|
| Clientes (WeCareU) | Clientes finais | `ui-client` / `web-client` |
| Artistas (WeCareU - Artistas) | Profissionais de beleza e bem-estar | `ui-worker` / `web-worker` |
| Empresas (WeCareU - Empresas) | Administradores e donos de locais de beleza | `ui-business` / `web-business` |
| Equipe interna WeCareU | Time da empresa | `web-admin` (acessos, moderações, aprovações) e `web-wiki` (guia de estilo e regras internas) |

> **Divergência a validar.** Os documentos de produto e de catálogo tratam apenas de dois apps hoje: **CLIENT** e **WORKER** (Artista). Salões de beleza (perfil Empresas) aparecem como funcionalidade futura, fora do escopo atual. Os nomes `ui-business`, `web-client`, `web-worker`, `web-business`, `web-admin` e `web-wiki` vêm do guia de voz e representam a visão-alvo da LyraUI, não apps existentes hoje.

---

## 8. Onde a LyraUI vive: Figma e ZeroHeight

- **Figma:** ambiente de criação e aplicação. Está sendo refeito para seguir os padrões da LyraUI, então não reflete o estado final.
- **ZeroHeight:** documentação de design e fonte de verdade.
- Os dois se retroalimentam.
- **Em aberto:** a relação entre Storybook (vitrine técnica dos componentes, que existe hoje) e ZeroHeight (documentação de design) ainda não está decidida. Não assumir como definida.

---

## 9. Linha do tempo resumida

1. **Hoje:** componentes e telas em `@wecareu/*` (legado). MVP em produção. Tema light no CLIENT e dark no WORKER.
2. **Agora:** LyraUI em discovery. Tokens, fundamentos visuais, voz, documentação e refação do Figma em andamento.
3. **Virada de chave (futuro):** rebrand de escopo, novo Atomic Design e novos repositórios. Tudo que for design system e biblioteca de componentes migra de `@wecareu/*` para `@lyra-ui/*`. Os sufixos tendem a se manter 1:1, e alguns nomes herdados da marca antiga podem ser revistos (ex.: `text-wcu`).

---

## 10. Pontos em aberto

- Data e critério da virada de chave: não definidos nos documentos.
- Relação Storybook x ZeroHeight: decisão aberta.
- Nome final do componente de texto (`text-wcu` → `@lyra-ui/text`, a confirmar).
- Quais apps além de CLIENT e WORKER entram de fato no escopo e quando.

---

## Mapa dos temas desta base

[[01-visao-geral-lyraui]] · [[02-contexto-wecareu]] · [[03-estado-atual-do-produto]] · [[04-arquitetura-e-estrutura-do-ds]] · [[05-sistema-de-tema]] · [[06-catalogo-e-inventario-legado]] · [[07-figma-padroes-e-tokens]] · [[08-regras-tecnicas-figma-api-mcp]] · [[09-fundamentos-visuais]] · [[10-voz-e-tons]] · [[11-escrita-e-ortografia]] · [[12-principios-de-design]] · [[13-glossario]] · [[14-ferramentas-e-forma-de-trabalho]]
