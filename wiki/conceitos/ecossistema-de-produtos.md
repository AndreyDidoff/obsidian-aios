---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-21
fontes: ["[[decisoes-2026-10-20]]", "[[ssot-produto-negocios]]", "[[ssot-ecossistema-engenharia]]", "[[lyraui-06-catalogo-legado]]", "[[pendencias]]", "[[plano-de-negocios-interno]]", "[[plano-de-negocios-investidores]]", "[[brainstorming-wecareu]]", "[[planos-para-o-futuro]]", "[[mapa-do-app-do-cliente]]", "[[conversa-do-agendamento]]", "[[mapa-do-app-do-artista]]", "[[o-que-ainda-nao-esta-no-app-do-artista]]", "[[board-estrutura-dos-apps]]"]
---

# Ecossistema de produtos

## Superfícies

| Produto | Status | Fonte |
|---|---|---|
| App do cliente | **MVP**, em desenvolvimento | [[decisoes-2026-10-20]] |
| App do Artista | **MVP**, em desenvolvimento | [[decisoes-2026-10-20]] |
| App do Estabelecimento | pendente, fora do MVP | [[pendencias]] |
| Site do cliente | pendente | [[pendencias]] |
| Site de Artistas | pendente | [[pendencias]] |
| Site de Estabelecimento | pendente | [[pendencias]] |
| Site institucional | pendente | [[pendencias]] |
| Site de admin | pendente | [[pendencias]] |
| Disparador de e-mails | pendência importante | [[pendencias]] |

O [[mvp]] é só app do cliente e app do Artista ([[decisoes-2026-10-20]]). Isso substitui o escopo do [[plano-de-negocios-interno]], que incluía a versão web para locais. Todos os sites ficam fora do MVP.

O app terá três fluxos de chatbot: cadastro, finalização do cadastro e agendamento. ([[decisoes-2026-10-20]])

## Nomes no código

Snapshots de engenharia e de design batizam as superfícies: `ui-client` / `web-client`, `ui-worker` / `web-worker`, `ui-business` / `web-business`, `web-admin`, `web-wiki`. Domínios citados: cliente, artista, empresa, admin e wiki, todos em `wecareu.app`. ([[ssot-produto-negocios]], [[ssot-ecossistema-engenharia]])

O back confirmado é o BFF [[beautiful-api]] (`service_api` no Azure, CNAME `api.wecareu.app`). ([[decisoes-2026-10-20]])

O catálogo legado lista as telas que o CLIENT e o WORKER já teriam, entre elas `Listing`, `Plans`, `Orders` e `ChatSchedules`. ([[lyraui-06-catalogo-legado]]) A tela de chat existe no inventário e o produto diz que não há chat. No app do cliente, em 21/10, `ChatSchedules` é casca. ([[conversa-do-agendamento]]) No app do artista, a tela existe sem caminho e o centro diz "Tab ChatSchedules". ([[o-que-ainda-nao-esta-no-app-do-artista]]) Ver [[contradicoes-e-lacunas]].

## App do cliente em 21/10

Retrato do repositório `ui_client`. A versão marcada no app é **1.0.0**. Isso não diz que o [[mvp]] foi lançado. A decisão mantém o app do cliente em desenvolvimento. O retrato do artista está na seção seguinte. ([[mapa-do-app-do-cliente]], [[decisoes-2026-10-20]])

**Construído:** primeira entrada, criar conta, entrar com senha e biometria. **Parcial:** a lista de artistas (exemplo), o início, o perfil, os endereços e os avisos. **Casca:** a agenda e a conversa do agendamento. O detalhe de cada área está em [[app-do-cliente]]. ([[mapa-do-app-do-cliente]])

## App do artista em 21/10

Retrato do repositório `ui_worker`. A versão marcada no app é **1.0.0**. O nome na loja é **WeCareU - Artistas**. Isso não diz que o [[mvp]] foi lançado. A decisão mantém o app do Artista em desenvolvimento. ([[mapa-do-app-do-artista]], [[decisoes-2026-10-20]])

**Construído:** abertura, entrar com senha e biometria. O perfil é menu. **Parcial:** cadastro, início, endereços e avisos. **Casca:** Pedidos, Agenda e Planos. O detalhe está em [[app-do-artista]]. ([[mapa-do-app-do-artista]])

Como o código é organizado: [[engenharia-de-software]]. Como ele vai parecer: [[lyraui]].

## Tecnologia

- Expo + TypeScript no front-end; .NET no back-end; Android, iOS e Web. ([[plano-de-negocios-investidores]])
- SMS/WhatsApp para comunicação. ([[plano-de-negocios-interno]])
- Design no Figma (WeCareU-App) e no Excalidraw. ([[brainstorming-wecareu]])
- Futuro: analytics (Firebase/Mixpanel), mapa de calor e gravação de sessão, rastrear qual notificação trouxe o usuário de volta, integração com Instagram, app para TV. ([[planos-para-o-futuro]])

Responsável pela maior parte: [[Andrey Didoff]].

## O que o board pede em 21/10

O board pede os dois apps com Expo ([[board-estrutura-dos-apps]]). O épico 441, Create App using Expo, está Completed. As histórias 442 e 443 pedem `ui_client` e `ui_worker` com Expo. As duas estão Completed. Isso é pedido de fila. Flutter sem pai não entra nesta lista de produtos do [[mvp]]. A história 214 pede estrutura do app cliente em flutter e está fora dos épicos. O retrato de 21/10 permanece: `ui_client` 1.0.0 e `ui_worker` 1.0.0, os dois em desenvolvimento.
