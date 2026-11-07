---
tipo: sintese
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-final]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[mvp-copys-cliente]]", "[[spec-busca-e-ranqueamento]]", "[[lyraui-01-visao-geral]]", "[[ssot-ecossistema-engenharia]]", "[[brainstorming-wecareu]]", "[[missao-e-valor]]", "[[pendencias]]", "[[plano-de-negocios-interno]]", "[[plano-de-negocios-investidores]]", "[[planos-para-o-futuro]]", "[[planos]]", "[[politica-de-privacidade]]", "[[seguranca-e-protecao-de-dados]]", "[[termos-de-uso-do-app]]", "[[cruzamento-como-ler]]", "[[cruzamento-bff-como-ler]]", "[[board-indice]]", "[[board-conta-e-acesso]]", "[[board-listagem]]", "[[board-inicio-do-cliente]]", "[[board-perfil]]", "[[board-favoritos]]", "[[board-agendamentos-e-atendimento]]", "[[board-review]]", "[[board-bloqueio]]", "[[board-denuncia]]", "[[board-servicos]]", "[[board-planos-e-assinaturas]]", "[[board-configuracoes]]", "[[board-estrutura-dos-apps]]", "[[board-design-no-figma]]", "[[board-bugs]]"]
---

# Visão geral

A [[wecareu]] é um marketplace de beleza e bem-estar em fase de MVP, construído por dois desenvolvedores ([[Andrey Didoff]] e [[bruno]]). O app conecta clientes a profissionais, chamados [[artista|Artistas]], e a [[estabelecimento|salões]].

## A aposta

Duas ideias sustentam o negócio:

1. **Identidade:** tratar o profissional de beleza como artista e dignificar seu trabalho. → [[missao-e-posicionamento]]
2. **Economia:** zero comissão sobre o serviço; o Artista entra de graça e paga, se quiser, por visibilidade. → [[modelo-de-receita]]

A receita virá de [[planos-de-assinatura]] (projeção de 20% de adesão) e de [[publicidade-e-marcas]], para quando houver escala. O lançamento é 100% gratuito; a monetização começa depois do [[mvp]].

## Como o produto funciona

- O cliente busca por categoria, serviço, região e data ([[busca-e-filtros]]); o resultado é ordenado pelo [[ranking]]: no MVP, a faixa "Novo" e depois os demais, por nota bayesiana. Nas fases posteriores, quem assina fica acima de quem não paga.
- O [[agendamento]] do cliente é reserva instantânea, em chatbot, com cadastro antes do horário retido. Chat livre continua fora. O [[atendimento-imediato]] fica fora deste release.
- A [[seguranca-do-atendimento]] libera o endereço do cliente ao artista às 00:00:01 do dia anterior. No cliente, o bloqueio não tem desbloqueio pelo usuário, e a sanção do MVP é só a suspensão.
- As [[avaliacoes]] do cliente não são obrigatórias e alimentam o ranking. O [[programa-de-pontos]] fica fora deste release.

## Onde está

O [[mvp]] é o app do cliente e o app do artista. O detalhe do cliente fechou em 05/11: gratuito, cadastro em chatbot sem SMS, listagem sem conta, reserva instantânea, avaliação opcional, bloqueio sem desbloqueio pelo usuário ([[mvp-funcoes-e-telas]], [[mvp-alteracoes-pos-congelamento]]). O lançamento público é São Paulo inteira, em 01/01/2027. O critério de pronto, antes disso, é os dois apps passarem no teste ponta a ponta em ambiente local até 31/12/2026. A publicação nas lojas fica fora. ([[decisoes-2026-11-05]]) O detalhe de tela do artista vem depois. Termos, política e e-mails transacionais continuam diferidos. Estabelecimentos, sites, planos pagos, atendimento imediato e programa de pontos ficam para depois. Quando o serviço puder ser pago pelo app, não haverá comissão: o Artista paga só a taxa do cartão, comunicada como taxa da operadora, não do app. Antes do lançamento faltam criptografia, revisão da Política de Privacidade e disparador de e-mails. O backlog de ideias é extenso ([[planos-para-o-futuro]], [[ia-no-dispositivo]]), e os planos Fidelidade e Agenda pessoal seguem sem definição.

O retrato de 21/10, lido nos quatro repositórios, descreve quatro peças ([[cruzamento-como-ler]]). O [[app-do-cliente]] instala as doze do [[kit-visual]] e não instala o fluxo compartilhado. O [[app-do-artista]] não instala o kit nem o fluxo: campos e botões nascem no próprio app. O kit não é tela. O [[fluxo-de-entrada]] (`@wecareu/auth-flow` 0.1.0) existe e não está instalado em nenhum dos dois apps. Entrar, senha e biometria estão construídos em cada app, no percurso daquele app. Criar conta também está no código: três etapas no cliente e cinco no artista. Agenda e conversa são casca nos dois. O cartão do início é o mesmo exemplo. Pedidos e Planos existem só no artista, e são casca. O alvo do [[mvp]] no cliente é o de 05/11. O retrato de 21/10 é estado atual e não troca esse alvo. O que divergir vira pendência de ajuste. Conflitos em [[contradicoes-e-lacunas]].

Os dois apps falam com o mesmo backend de apoio ([[cruzamento-bff-como-ler]], [[beautiful-api]]). O que já conversa é a conta: abrir, entrar, senha e sair. Reabrir e o Início também pedem, em caminhos que este retrato não publica. No ar, sem pedido dos apps, ficam serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação e o que a pessoa pode ver. Planos e cupons são porta sem ligação. Lista de artistas, agenda, conversa, pedidos e o cartão do próximo atendimento não leem este backend. O alvo do [[mvp]] permanece.

## O que o board pede em 21/10

Entraram o mapa ([[board-indice]]) e doze temas de produto. Conta ([[board-conta-e-acesso]]), listagem ([[board-listagem]]), início ([[board-inicio-do-cliente]]), perfil ([[board-perfil]]), favoritos ([[board-favoritos]]), agendamentos ([[board-agendamentos-e-atendimento]]), review ([[board-review]]), bloqueio ([[board-bloqueio]]), denúncia ([[board-denuncia]]), serviços ([[board-servicos]]), planos ([[board-planos-e-assinaturas]]) e configurações ([[board-configuracoes]]) têm fonte. Estrutura tem fonte ([[board-estrutura-dos-apps]]). Design no Figma tem fonte ([[board-design-no-figma]]). Bugs têm fonte ([[board-bugs]]). Os 15 temas têm fonte. Nenhum tema do board segue em `raw/`. Estado de work item não é pé do produto. O alvo continua o [[mvp]], via [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Maduro vs. aberto

- **Mais maduro:** identidade de marca, regras do [[atendimento-imediato]], segurança do atendimento, estratégia B2B baseada em dados.
- **Mais aberto:** [[pagamentos]] (pós-MVP, gateway não escolhido), preços, o que o retrato de 21/10 ainda deixa em casca ou em exemplo, adequação dos documentos legais à LGPD ([[protecao-de-dados]], [[termos-e-responsabilidades]]), números financeiros. Quantidade de artistas e orçamento de marketing seguem sem número: a quantidade seria chute, e o orçamento só no fim de dezembro de 2026. ([[decisoes-2026-11-05]])

## Design e engenharia

A [[lyraui]] é o design system, em discovery e sem código próprio: voz, fundamentos visuais e Figma correm em paralelo ao MVP, e o que existe hoje é o legado `@wecareu/*`. A [[engenharia-de-software]] (Expo, .NET, SDD, Azure, Jest e Maestro) está documentada em snapshots que pedem conferência com o repositório. Esses snapshots também tratam o MVP como já lançado, o que a decisão de 20/10/2026 não confirma.

Detalhes em [[contradicoes-e-lacunas]].
