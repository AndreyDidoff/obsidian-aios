---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[spec-busca-e-ranqueamento]]", "[[mvp-final]]", "[[mvp-alteracoes-pos-congelamento]]", "[[mvp-copys-cliente]]", "[[mvp-mudancas-na-spec]]", "[[spec-ranqueamento-listagem]]", "[[listagem-e-algoritmo-de-busca]]", "[[plano-de-negocios-interno]]", "[[plano-de-negocios-investidores]]", "[[brainstorming-wecareu]]", "[[planos-para-o-futuro]]", "[[planos]]", "[[ssot-produto-negocios]]", "[[encontrar-profissionais]]", "[[board-listagem]]"]
---

# Ranking

A ordem da listagem. A regra vigente é a spec v0.3.1 ([[spec-busca-e-ranqueamento]]). A fórmula de 20/10 (+10.000 do plano, Acampamento, plano imediato, desempate por distância) fica como histórico. Ver [[contradicoes-e-lacunas]].

## Exibição no cliente

O cliente não muda a fórmula. Muda o card. Sem data escolhida, a lista é única, pelas faixas, sem grupos A e B. Com data, voltam os grupos. O card não mostra horários nem a data do grupo B. Abaixo de 3 avaliações o cliente vê "Poucas avaliações", sem número. A tag "Novo" continua a da faixa. ([[mvp-alteracoes-pos-congelamento]])

O retrato da lista de 21/10, mais abaixo, é estado atual.

## No MVP ([[mvp-final]])

Não há plano pago. Duas faixas, que não se misturam:

1. **Novo** (faixa 2): 3 dias, com a tag "Novo". A contagem começa no mais tardio entre a aprovação e o lançamento público da cidade. Só vale se a vaga está no dia pedido ou até 2 dias depois. Fora disso, cai na faixa de baixo.
2. **Demais** (faixa 4): todo o resto.

Dentro da faixa, a ordem é a nota bayesiana (prior 4,7, peso 10), depois o volume dos últimos 90 dias, depois um sorteio estável na sessão. Quem tem vaga no dia pedido vem antes de quem só tem vaga em data próxima. → [[busca-e-filtros]]

A nota que o cliente vê é a média simples, a partir de 3 avaliações. Abaixo disso, o texto pedido pela conferência é "Poucas avaliações". "Novo" fica para a tag da faixa. A publicação da nota atrasa entre 24 e 72 horas.

Penalidade, pontos, planos e "Subir agora" não entram neste release. Nas fases posteriores da spec, quem assina fica acima de quem não paga e abaixo de quem ainda está na janela "Novo". "Subir agora" fica acima de todos, com teto de horas e de cards.

## Estrutura que a decisão de 20/10 descrevia ([[decisoes-2026-10-20]])

1. Uma **regra única de ranqueamento** ordena todo mundo.
2. A listagem mostra primeiro o **bloco de pagantes**, ordenado por essa regra.
3. Em seguida, o **bloco de não pagantes**, ordenado pela mesma regra.
4. Os cards de pagantes têm cor, tamanho e imagens de destaque.

Pagar compra posição de bloco e destaque visual, mas não altera a regra dentro do bloco. Isso concilia o "perfil gratuito ranqueia apenas por avaliações" ([[plano-de-negocios-interno]]) com o destaque dos pacotes pagos ([[plano-de-negocios-investidores]]).

No [[mvp]] não há planos pagos, então existe um bloco só. ([[decisoes-2026-10-20]])

## Entradas da regra

- Avaliações e estrelas dos clientes. ([[plano-de-negocios-interno]]) → [[avaliacoes]]
- Engajamento. ([[plano-de-negocios-interno]])
- Na busca, a ordem segue "filtros, regras internas e planos", não a distância. ([[brainstorming-wecareu]]) → [[busca-e-filtros]]
- Ideias futuras: boost/selo "Na sua região hoje" para Artistas com agendamento próximo; destaque como prêmio de missões de marca; categorias VIP. ([[planos-para-o-futuro]], [[planos]])

## Fórmula de 20/10, substituída ([[decisoes-2026-10-20]])

Confirmada em 2026-10-20 e substituída em 03/11 por [[spec-busca-e-ranqueamento]]. Os números abaixo são o histórico. O limiar de penalidade desta fórmula era **50 avaliações**. A spec nova usa 50 atendimentos finalizados, e só na fase de penalidade, fora do MVP.

**Filtro base**, antes de qualquer ponto: região, todas as especialidades pedidas e horário disponível. → [[busca-e-filtros]]

**Score** ([[spec-ranqueamento-listagem]]):

1. Plano de listagem ativo: +10.000. Sem plano: 0. Como a nota vale no máximo 5.000, o bloco de pagantes fica acima dos demais pela matemática, que é o que a decisão dos dois blocos pede.
2. Nota média × 1.000 (4,8 vira 4.800).
3. Pontos avulsos, vendidos de 100 em 100 e **só para quem já assina**. ([[ssot-produto-negocios]])
4. Se houver pelo menos 50 avaliações, a taxa de cancelamento entra como percentual descontado. A outra fonte fala em "50 a 100" como faixa mínima. ([[listagem-e-algoritmo-de-busca]])

**Acima do score**, nesta ordem:

0. **Acampamento:** Artistas que o cliente já segue, no topo absoluto.
1. **Plano imediato:** pagantes reais acima de quem ganhou 3 dias grátis no cadastro (um cadastro por usuário); dentro de cada grupo, o horário livre mais cedo vem primeiro.
2. O score.

**Desempate:** menor distância, mais avaliações, sorteio na sessão.

## Em aberto

- "Pontos renovados periodicamente" nos pacotes pagos ([[plano-de-negocios-interno]]) não está na spec v0.3.1. Os pontos dessa spec têm validade, peso e teto, com valores ainda ilustrativos.
- O rótulo de patrocinado continua para a fase de planos. A spec pede rótulo "Destaque" ou "Patrocinado" e manda validar com o jurídico. O card do MVP ainda não tem arquivo de tela.
- Parâmetros marcados como recomendados na spec (buffer de 30 minutos, passo de 30 minutos, janela de 14 dias, destaque até 2 dias) valem até alguém decidir o contrário. Não foram reconfirmados no fechamento do MVP.

## A lista do app do cliente em 21/10

A lista de artistas é exemplo: foto, nota, distância e faixa de preço escritos na tela. Não vem dos artistas de verdade. ([[encontrar-profissionais]])

A regra vigente é a spec v0.3.1. Ela não está nesta lista. O retrato não implementa faixa "Novo", nota bayesiana nem grupos de data. Ver [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

A tarefa 446 pede o card de listagem gratuito e diz que, neste momento, farão somente cards de listagem gratuita ([[board-listagem]]). Há um anexo. O texto não descreve a imagem. A regra vigente é a spec v0.3.1. No [[mvp]] há a faixa "Novo" e a faixa dos demais. Não há bloco de pagantes.

A tarefa 447 pede uma tag de propaganda a cada 4 cards, chamada para o cliente se cadastrar, com três frases randômicas. Há anexos. O texto não descreve as imagens. Essa tag não é o rótulo de patrocinado. O rótulo continua em aberto. → [[contradicoes-e-lacunas]]

A tarefa 448 pede exibir os dados da API respeitando a ordenação da listagem. Está New. A tarefa 449 pede filtros para mudar a ordem e não descreve outra fórmula. A tarefa 362 fala em agrupar em ordem, com left join, e não define a regra de pontos. A regra vigente é a spec v0.3.1. O item 19 registra a troca da fórmula de 20/10.
