---
tipo: fonte
arquivo: ingeridos/gemini-code-1792527188394.md
origem: extração via IA (Gemini), snapshot de 2026-10-20; o nome do arquivo é um identificador gerado, sem título estável
criado: 2026-10-20
atualizado: 2026-10-20
---

# Regras de listagem e algoritmo de busca

A fórmula de ranqueamento. Confirmada como regra definida em [[decisoes-2026-10-20]]. O par técnico, com os números fechados, é [[spec-ranqueamento-listagem]]. A faixa "50 a 100" deste texto não altera o limiar de 50 da spec.

## Pontos principais

1. Filtro base: região, especialidade com E (todas), data e hora disponíveis.
2. Score: plano de listagem +10.000; nota até 5.000; pontos avulsos de 100 em 100, só para assinantes.
3. Penalidade de cancelamento só a partir de 50 a 100 avaliações, para não punir novato.
4. Fura-fila, acima do score: quem o cliente segue ("Acampamento"); depois o plano imediato, ordenado pelo horário livre mais cedo. Novos usuários ganham 3 dias de plano imediato grátis, abaixo dos pagantes desse plano, um cadastro por usuário.
5. Desempate: distância, volume de avaliações, sorteio na sessão.

Ver [[ranking]].
