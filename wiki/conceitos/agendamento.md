---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-final]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[lyraui-03-estado-atual]]", "[[ssot-backlog]]", "[[brainstorming-wecareu]]", "[[planos-para-o-futuro]]", "[[planos]]", "[[agenda]]", "[[conversa-do-agendamento]]", "[[inicio]]", "[[agenda-do-artista]]", "[[inicio-do-artista]]", "[[o-que-ainda-nao-esta-no-app-do-artista]]", "[[board-agendamentos-e-atendimento]]", "[[core-03-agenda]]"]
---

# Agendamento

## Alvo do cliente

A reserva é instantânea, sem aceite do artista. O fluxo é um chatbot. O cadastro do cliente acontece antes, nunca com horário retido. Ao tocar em "Pronto", o horário fica pré-agendado por 10 minutos, com uma única extensão de 10 minutos. O resumo mostra o preço total, com o rótulo "Preço estimado", e a legenda de que o pagamento é feito direto com o Artista. Não há tela de detalhe: o toque no cartão não abre outra tela. O menu de três pontos continua. O cancelamento do cliente não pede motivo e só vale até o horário de início. "Ver meus agendamentos" leva à Agenda. ([[mvp-final]], [[mvp-alteracoes-pos-congelamento]])

Quem está deslogado vê a lista. Não se cadastra no meio de um horário retido. ([[mvp-alteracoes-pos-congelamento]])

O endereço que o artista vê, e quando, continua o de 03/11: antes de 00:00:01 do dia anterior, só nome, foto e região. A tela do artista espera o detalhe desse lado. ([[mvp-final]])

O retrato de 21/10, abaixo, é estado atual.

## Estado atual e regras anteriores

- [[lyraui-03-estado-atual]] descreve o contrário como estado atual: agendamento **por telas, sem bot**, e o bot sem prazo. [[ssot-backlog]] registra "não haverá chat interno" como decisão de produto. As duas perdem para [[decisoes-2026-10-20]] no que o MVP vai ter; ficam como retrato possível do código de hoje. Ver [[contradicoes-e-lacunas]].
- Endereço para o artista: antes de 00:00:01 do dia anterior, só nome, foto e região. A partir dessa hora, os dados de todos os clientes do dia, para a rota. Marcação já dentro da janela libera na hora. ([[mvp-final]]) A tela que mostra esses dados espera o arquivo de detalhe.
- No [[mvp]], a lista abre sem conta. O cadastro é antes do fluxo, não no meio do horário retido. ([[mvp-alteracoes-pos-congelamento]]) A frase de 21/10, cadastrar no momento de agendar, foi substituída por esta.
- Integração com agendas externas (Google Agenda, Apple Calendar). ([[brainstorming-wecareu]])
- O chatbot confirma os serviços escolhidos. ([[brainstorming-wecareu]])
- Tempo médio de atendimento calculado a partir dos serviços.
- Busca de datas que encaixam no que o cliente quer.
- Atendimento a domicílio: o que o artista vê e quando está na regra acima. → [[seguranca-do-atendimento]]

## Modalidades

- Agendamento normal e [[atendimento-imediato]] (sem agendamento prévio). ([[planos]])
- Plano "Agenda pessoal", ainda a definir. ([[planos]])

## Ideias futuras ([[planos-para-o-futuro]])

- Artista informa o tempo médio de cada serviço; check-in e checkout para medir.
- Limite de agendamentos pessoais (fora do app) consecutivos, para que o app não vire só uma agenda.
- Sincronização com o calendário do celular com "filtro de privacidade", que trata eventos pessoais apenas como bloqueio de tempo.
- "Artista X está indo até você" quando o atendimento começa.
- Atalho "Agendar novamente" na tela inicial, que pula direto para os horários do mesmo Artista.
- Incentivo a marcar perto de outros clientes da mesma região, com um boost no [[ranking]].

## O que o app do cliente mostra em 21/10

O retrato de 21/10 continua casca. No cliente, o agendamento é chatbot e está fechado. A tela do artista ainda espera o detalhe desse lado. ([[mvp-alteracoes-pos-congelamento]], [[mvp-final]])

Neste retrato, a agenda é casca. A aba existe e o centro da tela diz "Tab Schedules". ([[agenda]]) A conversa do agendamento é casca. O centro diz "Tab ChatSchedules". Nenhuma aba abre essa tela. Nenhum botão aponta para ela. ([[conversa-do-agendamento]]) O cartão do início é exemplo: Karen Watanabe, 25 de Maio, 12h00, unhas e botox. **Vamos agendar?** não faz nada. ([[inicio]])

Ver [[contradicoes-e-lacunas]].

## O que o app do artista mostra em 21/10

O retrato de 21/10 continua casca. No cliente, o agendamento é chatbot e está fechado. A tela do artista ainda espera o detalhe desse lado. ([[mvp-alteracoes-pos-congelamento]], [[mvp-final]])

Neste retrato, a agenda do artista é casca. A aba existe e o centro da tela diz "Tab Schedules". ([[agenda-do-artista]]) O cartão do início é o mesmo exemplo: Karen Watanabe, 25 de Maio, 12h00, unhas e botox. **Vamos agendar?** não faz nada. ([[inicio-do-artista]]) A conversa do agendamento não está na barra. A tela existe e o centro diz "Tab ChatSchedules". Nenhum botão do Início, da Agenda ou do perfil a abre. ([[o-que-ainda-nao-esta-no-app-do-artista]]) [[conversa-do-agendamento]] descreve o cliente.

Ver [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

O retrato de 21/10 continua casca. No cliente, o agendamento é chatbot e está fechado. A tela do artista ainda espera o detalhe desse lado. ([[mvp-alteracoes-pos-congelamento]], [[mvp-final]])

O épico 334, Sistema de agendamentos, está New e sem descrição. A história 372 pede a tela do cliente. A história 375 pede a tela do artista. Não pedem chat livre. A história 144 pede salvamento e está New, com [[bruno]], sem descrição. A tarefa 380 pede importar agendamentos de outras plataformas. Está New e sem descrição. É pedido do board, não decisão de integração. O épico 339 pede check-in e check-out. Está New. Não decide quando o endereço aparece. A casca de 21/10 permanece: "Tab Schedules" e "Tab ChatSchedules". ([[board-agendamentos-e-atendimento]])

Ver [[contradicoes-e-lacunas]].

## O que o núcleo grava

A tela segue casca. O alvo segue chatbot. O núcleo tem marcação que a tela não lê e que a lista não acha. ([[core-03-agenda]], [[decisoes-2026-10-20]])
