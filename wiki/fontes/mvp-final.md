---
tipo: fonte
arquivo: ingeridos/04-mvp-final.md
origem: fechamento de produto do Release 1, escrito pelo consultor com decisões do dono marcadas
criado: 2026-11-03
atualizado: 2026-11-03
---

# MVP final (Release 1)

Documento de fechamento do conjunto de funções. Sem código, sem datas de entrega e sem estimativa. O histórico está em [[mvp-e-releases]]. As emendas na spec estão em [[mvp-mudancas-na-spec]]. Em 03/11 o dono disse que este fechamento lista as funções e as telas; o detalhe de cada uma vem depois ([[decisoes-2026-11-03]]).

## Funções que entram

**Cliente.** Cadastro com endereço, bairro e telefone verificado por SMS; login; recuperação de senha; termos e consentimento; perfil; sair; exclusão de conta. Listagem com filtros de ofício, serviço, data e região. Só aparecem ofícios e serviços com pelo menos um artista aprovado na região. Perfil do artista; agendamento instantâneo; consulta de agendamentos; cancelamento; aviso quando o artista cancela. Avaliação de 1 a 5, com opção "prestador não compareceu". Denúncia, bloqueio e desbloqueio. Contato da WeCareU.

**Artista.** Cadastro que entra pendente, com telefone verificado por SMS; login; termos; perfil e foto; exclusão de conta. Ofício, serviços e duração; várias regiões, com atalho de zona; disponibilidade; antecedência mínima e máxima; intervalo de deslocamento; bloqueio de horário. Reserva manual (nome e celular obrigatórios, caixa de autorização) e convite por SMS. Agenda; dados do cliente pela regra de privacidade. Check-in e check-out por barra, cronômetro, "cliente ausente" e cancelamento. O que não for fechado vira fechado às 00:00:00, sem ser falta. Push de novo agendamento, com um reenvio se não for visualizado. Ver avaliações. Denúncia, bloqueio e desbloqueio. Contato da WeCareU.

**Operação.** Painel mínimo: aprovação de artista, lista de denúncias e bloqueio de usuário. No início aprovam [[Andrey Didoff]] e [[bruno]]. Critério: nome real, foto adequada e telefone verificado por SMS. Mediação pela empresa. Sanções (advertência, suspensão, banimento) ficam nos termos.

## Funções que ficam fora

Verificação de identidade, pagamento no app, penalidade, planos, pontos, "Subir agora", trava de geolocalização, artista avaliando cliente, prazo de cancelamento, feature flags, analytics de uso (mapas de calor, funil), lembretes, remarcação, chat, portfólio, favoritos, outros endereços, login social, resposta a avaliação e prazo de reenvio do push configurável pelo produto. A ordem dos releases seguintes será discutida perto do lançamento do MVP.

## Regras escritas junto com o conjunto

O documento marca como [DEFINIDO]: pagamento fora do app; reserva instantânea sem aceite e sem horário duplicado; privacidade (antes de 00:00:01 do dia anterior, o artista vê só nome, foto e região; depois, os dados de todos os clientes do dia); cancelamento sem prazo mínimo, guardando quem cancelou, quando e o motivo; "não compareceu" retém a avaliação até a mediação; ordenação com faixa "Novo" (3 dias) e depois os demais, desempate por nota, volume e sorteio; uma identidade com dois papéis; busca vazia sem promessa de aviso. Lançamento público de São Paulo em 01/01/2027. O parecer do advogado é dado como concluído pelo dono, sem apontar o arquivo do texto.

O que está [RECOMENDADO] não entra como decisão: a lista de fatos que o backend grava, e reservas manuais fora de volume e nota até o cliente vincular a conta. Métricas não têm limiar numérico. O beta mede a linha de base.

O próprio documento diz que o escopo está fechado e que informação futura só detalha. O arquivo de telas anunciado em [[decisoes-2026-11-03]] é esse detalhe.
