---
tipo: sintese
criado: 2026-11-07
atualizado: 2026-11-07
fontes: ["[[contradicoes-e-lacunas]]"]
---

# Avaliação e sanção

Este tema é do MVP. Os outros temas saem de [[contradicoes-e-lacunas]]. Os números são os daquela página.

| # | Tema | Conflito | Status |
| --- | --- | --- | --- |
| 17 | Estrelas obrigatórias | Brainstorming: obrigatórias. Estado atual: opcionais, e 5 estrelas internas se ninguém avalia em 1 semana. A nota 5,0 do Início é fallback de tela ([[inicio]]) | **Resolvido no cliente:** a avaliação não é obrigatória ([[mvp-alteracoes-pos-congelamento]]). O artista não herda. A conta que nasce com cinco estrelas continua retrato de [[core-01-conta]] e fica encaminhada a [[backend-mvp-conta]] |
| 32 | Avaliação não retida | "Prestador não compareceu" segurava a nota até a mediação ([[mvp-final]]). No cliente, "O Artista não compareceu" não retém nota ([[mvp-alteracoes-pos-congelamento]]) | **Resolvido no cliente.** O artista não herda |
| 35 | Sanção do MVP | Advertência, suspensão e banimento aparecem em fontes anteriores. No cliente, a sanção deste release é só a suspensão por tempo indeterminado ([[mvp-alteracoes-pos-congelamento]]) | **Resolvido no cliente.** O retrato de bloqueio fica encaminhado a [[backend-mvp-conta]] |

## Lacunas

- **Pedido de denúncia e a porta de relato:** o board pede denúncia ([[board-denuncia]]). A porta [[bff-relatos]] não declara se o relato é denúncia, avaliação ou atendimento. O pedido fica ao lado. A porta não declara o sentido. No núcleo, [[core-12-relatos]] guarda a descrição e os dois identificadores; o retrato [[bff-relatos]] não declara texto, motivo nem sobre quem. As duas camadas ficam. Isso não fecha o sentido.
