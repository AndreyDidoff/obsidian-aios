---
tipo: fonte
arquivo: ingeridos/especificacao-busca-e-ranqueamento.md
origem: especificação v0.3.1, de 23/10/2026, escrita para produto, engenharia e agentes; rascunho para validação no cabeçalho, com decisões do dono marcadas no corpo
criado: 2026-11-03
atualizado: 2026-11-03
---

# Especificação de busca e ranqueamento (v0.3.1)

Fonte de verdade de busca, agenda, avaliação e [[ranking]] no pacote de 03/11. Substitui a fórmula de [[spec-ranqueamento-listagem]] (+10.000, Acampamento, plano imediato, desempate por distância). O que o [[mvp]] muda nela está em [[mvp-mudancas-na-spec]]. O card na tela espera o arquivo de detalhe ([[decisoes-2026-11-03]]).

## Fases

1. MVP: busca, agenda, agendamento, avaliações, destaque de novos. Faixas 2 e 4.
2. Penalidade, com flag. Faltas e cancelamento tardio reduzem o score.
3. Planos e pontos. Faixa 3, abaixo da faixa 2 e acima da 4.
4. "Subir agora", faixa 1, no máximo 3 horas por dia.

A ordem das fases 2 a 4 está nesta spec. [[mvp-final]] deixa a discussão dessa ordem para perto do lançamento do MVP.

## Busca no MVP

Filtros duros: ofício, serviço e região. A data separa o grupo A (vaga no dia pedido) do grupo B (vaga em até 14 dias, valor recomendado). O grupo A vem antes. Não há filtro de horário. O card mostra os horários livres do dia.

Dentro do grupo, a faixa 2 ("Novo", 3 dias, tag "Novo") vem antes da faixa 4. A janela começa em `max(aprovação, lançamento público da cidade)`. Fora de 2 dias de distância, o novo cai na faixa 4. Desempate: nota bayesiana (prior 4,7, peso 10), volume de 90 dias, sorteio estável na sessão. A nota exibida é a média simples, a partir de 3 avaliações. Abaixo disso, a conferência do MVP pede o texto "Poucas avaliações", e reserva "Novo" para a tag.

A nota publica com atraso aleatório de 24 a 72 horas. Só avalia quem teve atendimento concluído, uma vez, sem texto.

## O que o MVP não liga

Penalidade (janela de 50 atendimentos, teto de 90 dias, piso de amostra 20, cancelamento tardio em 12 horas, modo sombra antes de ligar). Planos, pontos, piso de qualidade, vitrine mínima e rótulo de patrocinado. "Subir agora". Verificação de identidade na ativação: no MVP a ativação é a aprovação manual.

`rank_score` é interno e não sai em API pública. Constantes ficam em configuração, não no código. Timestamps em UTC. Calendário em `America/Sao_Paulo`.
