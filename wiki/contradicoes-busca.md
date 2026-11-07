---
tipo: sintese
criado: 2026-11-07
atualizado: 2026-11-07
fontes: ["[[contradicoes-e-lacunas]]"]
---

# Busca e ranking

Este tema é do MVP. Os outros temas saem de [[contradicoes-e-lacunas]]. Os números são os daquela página.

## Contradições

| # | Tema | Conflito | Status |
| --- | --- | --- | --- |
| 9 | Ranking | Gratuito "apenas por avaliações" vs. pacotes pagos sobem no ranking | **Atualizado em 03/11:** no [[mvp]] não há pagantes. A ordem é a faixa "Novo" e depois os demais ([[spec-busca-e-ranqueamento]]). Nas fases posteriores, quem assina fica acima de quem não paga e abaixo de quem está na janela "Novo" |
| 19 | Fórmula do ranking | [[spec-ranqueamento-listagem]] traz pesos, Acampamento e 3 dias de plano imediato. [[spec-busca-e-ranqueamento]] traz faixas, nota bayesiana e grupo por data | **Substituída em 03/11:** vale a spec v0.3.1. A fórmula de 20/10 fica como histórico. Penalidade, planos e "Subir agora" ficam fora do [[mvp]]. O card espera o arquivo de telas |
| 31 | Card sem data e sem horário | A spec v0.3.1 descreve grupos A e B e a data do grupo B no card. O cliente tira a data e os horários do card, e só separa A e B depois que há uma data ([[mvp-alteracoes-pos-congelamento]], [[spec-busca-e-ranqueamento]]) | **Resolvido no cliente:** prevalece o delta. A spec bruta não é reescrita. O retrato da lista de exemplo fica encaminhado a [[app-cliente-descoberta]] |

## Lacuna

- **Rótulo de patrocinado** nos cards pagos. O board pede, na tarefa 447 de [[board-listagem]], uma tag de propaganda a cada 4 cards, chamada para se cadastrar, com três frases randômicas. Há anexos. O texto não descreve as imagens. Essa tag não fecha esta lacuna. O rótulo continua em aberto. → [[ranking]]
