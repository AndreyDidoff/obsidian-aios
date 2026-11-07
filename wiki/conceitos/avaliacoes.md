---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-final]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[spec-busca-e-ranqueamento]]", "[[lyraui-03-estado-atual]]", "[[brainstorming-wecareu]]", "[[planos-para-o-futuro]]", "[[plano-de-negocios-interno]]", "[[board-review]]", "[[core-01-conta]]", "[[inicio]]"]
---

# Avaliações (reviews)

Matéria-prima do [[ranking]].

## Alvo do cliente

A avaliação não é obrigatória. O cliente avalia no próprio cartão, de 1 a 5, sem texto, uma vez, em até 7 dias depois do atendimento concluído. As estrelas só aparecem com o check-out do artista. O envio espera 10 segundos de toque. A nota publica com atraso aleatório de 24 a 72 horas. Abaixo de 3 avaliações o cliente vê "Poucas avaliações", sem número. "O Artista não compareceu" não retém avaliação: o cartão fica sem nota nos dois desfechos da mediação. Se a mediação concluir que houve atendimento, o cliente perde o direito de avaliar. Cancelado não gera avaliação. ([[mvp-alteracoes-pos-congelamento]], [[spec-busca-e-ranqueamento]])

A obrigação de avaliar, da decisão de 21/10, não vale mais no app do cliente.

## O que o estado atual afirma ([[lyraui-03-estado-atual]])

Isto é estado atual, não alvo. Conflita com o alvo e vira pendência de ajuste:

- Estrelas **não são obrigatórias**. O app pede até 3 vezes, com prazo de 15 dias.
- Se ninguém avalia em 1 semana, o sistema grava **5 estrelas internas**, invisíveis ao cliente.
- Texto e foto estão sem prazo. Filtro por estrelas segue sem previsão.

Isso fica como retrato antigo, não como regra do [[mvp]]. Ver [[contradicoes-e-lacunas]].

## Definido no brainstorming ([[brainstorming-wecareu]])

- Estrelas obrigatórias; texto opcional.
- Fotos do cliente após o serviço, "como na AliExpress"; reviews com imagem têm prioridade.
- 3 reviews visíveis e botão "ver mais".
- Filtro por estrelas fica para a v2.

## Ideias futuras ([[planos-para-o-futuro]])

- **Tags no checkout** ("Pontual", "Mão Leve", "Ambiente Impecável") que viram badges no perfil, como as competências do LinkedIn. Clicar é mais fácil que escrever, e as tags geram dados estruturados para a [[busca-e-filtros]].
- **Foto para o portfólio:** no checkout, o cliente autoriza ou não o Artista a usar a foto do resultado.
- **"Gostou dos produtos utilizados hoje?"**: satisfação ligada à marca declarada pelo Artista, vendável a parceiros. → [[publicidade-e-marcas]]
- Pontos por avaliar. → [[programa-de-pontos]]

## O que o board pede em 21/10

A avaliação continua obrigatória no [[mvp]]. Prazo, 5 estrelas internas e foto continuam em aberto. ([[decisoes-2026-10-21]])

O épico 341, Sistema de review, está New e sem descrição. A tarefa 388 pede review de um atendimento e vincular a agendamento e serviço. As tarefas 389 e 390 pedem média por serviço e média geral do artista. Estão New. Isso não fecha prazo, estrelas internas nem foto. ([[board-review]])

## O que o serviço de conta grava ao nascer a conta

No cadastro de `Br.Login.API`, a conta nasce com cinco estrelas e nenhuma avaliação. ([[core-01-conta]]) Isso não é o fallback de tela 5,0 do Início ([[inicio]]) nem a decisão de avaliação obrigatória. O item 17 de [[contradicoes-e-lacunas]] permanece resolvido no alvo. Prazo, 5 estrelas internas e foto continuam em aberto. ([[decisoes-2026-10-21]])

Ver [[contradicoes-e-lacunas]].
