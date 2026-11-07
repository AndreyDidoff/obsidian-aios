---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-memoria-indice]]", "[[mvp-final]]", "[[mvp-e-releases]]", "[[mvp-mudancas-na-spec]]", "[[mvp-revisao-riscos]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[mvp-copys-cliente]]", "[[spec-busca-e-ranqueamento]]", "[[lyraui-03-estado-atual]]", "[[plano-de-negocios-interno]]", "[[plano-de-negocios-investidores]]", "[[pendencias]]", "[[termos-de-uso-do-app]]", "[[mapa-do-app-do-cliente]]", "[[encontrar-profissionais]]", "[[inicio]]", "[[agenda]]", "[[conversa-do-agendamento]]", "[[mapa-do-app-do-artista]]", "[[inicio-do-artista]]", "[[pedidos-do-artista]]", "[[agenda-do-artista]]", "[[planos-do-artista]]"]
---

# MVP

O alvo de produto é como o MVP precisa ser, não como o app está hoje. ([[decisoes-2026-11-05]]) O conjunto de funções fechou em 03/11 ([[mvp-final]]). O app do cliente fechou o detalhe em 05/11 ([[mvp-funcoes-e-telas]], [[mvp-alteracoes-pos-congelamento]], [[mvp-copys-cliente]]). Onde o cliente muda o fechamento de 03/11, prevalece o cliente. O detalhe de tela do artista vem depois. Tela, copy ou backend fora desse alvo viram pendência de ajuste: [[backend-mvp-listagem]], [[backend-mvp-agendamento]], [[backend-mvp-conta]], [[backend-mvp-avaliacao-e-avisos]], [[backend-mvp-fundacoes]], [[app-cliente-conta]], [[app-cliente-descoberta]], [[app-cliente-agendamento]] e [[app-cliente-copys]]. Criptografia, o disparador de e-mails e o acesso provisório do Swagger continuam na lista de antes do lançamento, abaixo.

## O que entra

Dois apps, cliente e artista, em desenvolvimento. ([[decisoes-2026-10-20]], [[mvp-final]])

O critério de pronto deste trimestre: os dois apps passam no teste ponta a ponta em ambiente local até 31/12/2026. Publicação nas lojas fica fora. O lançamento público continua São Paulo inteira, em 01/01/2027. ([[decisoes-2026-11-05]])

**Cliente.** Cadastro em chatbot, com CPF, sexo, nascimento a partir de 18 anos, foto, endereço e celular só coletado, sem SMS. Login, recuperação de senha por e-mail, termos, perfil, sair e exclusão em 30 dias. Vários endereços, sem um "principal". Listagem sem conta. Ao chegar, a lista é única, sem filtro aplicado. Categoria, serviço, data e região existem, e os grupos A e B só entram depois da data. Só entra categoria ou serviço com artista aprovado na região. Perfil do artista, agendamento instantâneo, consulta, cancelamento sem motivo até o início, e aviso quando o artista cancela. Avaliação de 1 a 5, opcional, e "O Artista não compareceu". Denúncia, bloqueio sem desbloqueio pelo usuário, e contato da WeCareU. Lembretes de atendimento e o reagendamento v0 entram. Não há central de notificações. ([[mvp-alteracoes-pos-congelamento]])

**Artista.** O inventário de 03/11 permanece. O detalhe de tela não chegou. SMS do prestador, exclusão no app do artista e o bloqueio de cliente ficam para esse detalhe. ([[mvp-funcoes-e-telas]])

**Operação.** Painel mínimo: aprovar artista, ver denúncias e bloquear usuário. Critério de aprovação: nome real, foto adequada e telefone por SMS. [[Andrey Didoff]] e [[bruno]] aprovam no início. A empresa media. As sanções ficam nos termos.

Lista completa e o que cada função sustenta: [[mvp-e-releases]].

## O que fica fora

Verificação de documento, pagamento no app, penalidade, planos, pontos, "Subir agora", trava de geolocalização no check-in, artista avaliando cliente, prazo de cancelamento, feature flags, mapas de calor e funil, remarcação, chat livre, portfólio, favoritos, login social e resposta à avaliação. ([[mvp-final]]) No cliente, lembretes e vários endereços entraram. SMS do cliente, central de notificações, desbloqueio pelo usuário e a tela de detalhe do agendamento saíram. ([[mvp-alteracoes-pos-congelamento]])

[[estabelecimento]] e os sites de [[pendencias]] continuam fora. A ordem dos releases depois deste fica para perto do lançamento.

## Regras já escritas na função

Estas regras estão [DEFINIDO]. No cliente, o delta de 05/11 prevalece sobre o fechamento de 03/11. ([[mvp-final]], [[mvp-alteracoes-pos-congelamento]], [[spec-busca-e-ranqueamento]])

- Gratuito. Pagamento direto com o artista, fora do app.
- Reserva instantânea, sem aceite e sem dois clientes no mesmo horário.
- Antes de 00:00:01 do dia anterior, o artista vê do cliente só nome, foto e região. Depois, vê os dados de todos os clientes daquele dia. Marcação já dentro da janela libera na hora.
- Cancelamento do cliente sem motivo, só até o início. Guarda-se quem cancelou e quando. O cancelamento com menos de 24 horas fica marcado para a fase futura.
- "O Artista não compareceu" não retém avaliação. Se a mediação concluir que houve atendimento, o cliente perde o direito de avaliar.
- Ordenação: faixa "Novo" (3 dias, a partir do mais tardio entre a aprovação e o lançamento na cidade) e depois os demais. Desempate por nota bayesiana (prior 4,7, peso 10), volume de 90 dias e sorteio na sessão. → [[ranking]]
- Uma identidade, dois papéis. O artista aparece na listagem e não agenda para si.
- Busca vazia: "ainda estamos chegando na sua região", sem promessa de aviso.
- Nunca há filtro de horário na busca.
- Lançamento público: São Paulo inteira, 01/01/2027. Outra cidade cadastra artista; a tag "Novo" só liga quando o app chegar lá. → [[lancamento-e-marketing]]
- Regra de negócio no backend. O app apresenta.

O que o pacote deixa como recomendação não é decisão: reservas manuais fora de volume e nota até o cliente vincular, CPF para não repetir "Novo", teto diário de SMS e a lista de fatos que o backend grava. ([[mvp-mudancas-na-spec]], [[mvp-revisao-riscos]])

## O que o cliente fechou e o que ficou diferido

No app do cliente, o arquivo de telas chegou. ([[mvp-funcoes-e-telas]])

- Cadastro e agendamento são chatbot. Chat livre continua fora.
- A listagem abre sem conta. O cadastro acontece antes do agendamento, nunca com horário retido.
- A avaliação não é obrigatória.
- O cadastro pede sexo em quatro botões, CPF e nascimento. Não pede gênero nem orientação sexual. Não há SMS.
- O serviço tem preço. A faixa do card é digitada pelo artista.
- 2FA não está nas telas do cliente. A biometria só desbloqueia o app.
- Termos, Política de Privacidade e e-mails transacionais continuam diferidos. Não bloqueiam. ([[decisoes-2026-11-05]])

## Como o código estava em 21/10

Isto é estado atual, não alvo. O alvo é o desta página. O que divergir vira pendência de ajuste.

[[lyraui-03-estado-atual]] trata o MVP como já em produção (maio de 2026). A decisão de 20/10 mantém os dois apps em desenvolvimento. O lançamento público escrito em 03/11 é 01/01/2027. Até lá, o MVP não foi lançado. Ver [[contradicoes-e-lacunas]].

O retrato do `ui_client` 1.0.0 percorre abertura, visita sem conta, criar conta e entrar. Lista, agenda e conversa são casca ou exemplo. ([[mapa-do-app-do-cliente]], [[encontrar-profissionais]], [[inicio]], [[agenda]], [[conversa-do-agendamento]])

O `ui_worker` 1.0.0, nome **WeCareU - Artistas**, não tem uso sem conta. Início, Pedidos, Agenda e Planos são casca ou exemplo. ([[mapa-do-app-do-artista]], [[inicio-do-artista]], [[pedidos-do-artista]], [[agenda-do-artista]], [[planos-do-artista]])

Esse retrato é estado atual. O alvo do cliente é o de 05/11. O do artista, no que o cliente não mudou, continua o de 03/11.

## Antes do lançamento

| Item | Status | Página |
|---|---|---|
| Implementar criptografia | pendente | [[protecao-de-dados]] |
| Revisar a Política de Privacidade | pendente | [[cadastro]], [[protecao-de-dados]] |
| Disparador de e-mails | pendente | [[pendencias]] |
| Tirar o acesso provisório do Swagger | pendente | [[decisoes-2026-10-20]], [[protecao-de-dados]] |
| 2FA no app do cliente | fora das telas do cliente | [[mvp-funcoes-e-telas]] |
| Termos e política novos | diferido, não bloqueia | [[decisoes-2026-11-05]] |
| E-mails transacionais | diferido, não bloqueia | [[mvp-copys-cliente]] |
| Alinhar tela, copy e backend ao alvo | pendência de ajuste | as nove páginas do primeiro parágrafo |

[[mvp-final]] dá o parecer do advogado como concluído e não aponta o texto. Os termos da wiki continuam o rascunho de dezembro de 2024. Isso não fecha o item dos termos.

## Depois deste release

Penalidade, verificação de identidade, planos, pontos e "Subir agora" estão desenhados em [[spec-busca-e-ranqueamento]] e em [[mvp-e-releases]]. A ordem em que saem não faz parte deste fechamento. Pagamento do serviço pelo app, sem comissão, continua a decisão de outubro e não está neste release. → [[pagamentos]]
