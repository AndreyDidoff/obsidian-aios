---
tipo: fonte
arquivo: ingeridos/gemini-code-1792527209448.md
origem: extração via IA (Gemini), snapshot de 2026-10-20; spec escrita para agentes de código
criado: 2026-10-20
atualizado: 2026-10-20
---

# Spec técnica do ranqueamento

Mesma regra de [[listagem-e-algoritmo-de-busca]], com campos e fórmula fechada. Confirmada como a regra definida em [[decisoes-2026-10-20]]. O limiar de 50 avaliações desta spec prevalece sobre a faixa "50 a 100" do texto narrativo.

## Fórmula

- Plano de listagem: +10.000 ou 0.
- Nota: média × 1.000 (4,8 vira 4.800; teto 5.000).
- Soma os pontos avulsos.
- Se `total_avaliacoes >= 50`, subtrai a taxa de cancelamento como percentual dos pontos (10% de 14.800 tira 1.480).

## Ordem

Prioridade 0: `is_following`. Prioridade 1: `has_plano_imediato`, pagantes reais acima dos 3 dias grátis, ambos pelo próximo horário livre. Prioridade 2: score decrescente. Desempate: menor distância, mais avaliações, `ORDER BY RAND()` na sessão.

Campos de entrada: `is_following`, `has_plano_imediato`, `has_plano_listagem`, `pontos_avulsos`, `avaliacao_media`, `total_avaliacoes`, `taxa_cancelamento`, `distancia_metros`, `proximo_horario_livre`.

Ver [[ranking]].
