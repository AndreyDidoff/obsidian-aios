---
tipo: sintese
criado: 2026-11-07
atualizado: 2026-11-07
fontes: ["[[contradicoes-e-lacunas]]"]
---

# Agendamento e contato

Este tema é do MVP. Os outros temas saem de [[contradicoes-e-lacunas]]. Os números são os daquela página.

## Contradições

| # | Tema | Conflito | Status |
| --- | --- | --- | --- |
| 4 | Contato cliente–Artista | "Sem chat" ([[brainstorming-wecareu]]) vs. "antes de se falarem" ([[planos]]) | **Resolvido no cliente:** cadastro e agendamento são chatbot, sem texto livre ([[mvp-funcoes-e-telas]]). O artista não herda este detalhe |
| 13 | Chat | [[ssot-backlog]] diz que não haverá chat; o catálogo tem a tela `ChatSchedules` ([[lyraui-06-catalogo-legado]]). No retrato de 21/10, ChatSchedules é casca nos dois apps | **Encaminhado no cliente:** o alvo é chatbot sem texto livre ([[mvp-funcoes-e-telas]]). A casca de 21/10 é estado atual e vira ajuste em [[app-cliente-agendamento]]. O artista não herda |
| 16 | Quando o endereço é liberado | Na confirmação vs. 24h antes vs. no checkout do cliente anterior vs. só bairro/região até o momento certo | **Resolvido no conjunto de funções:** às 00:00:01 do dia anterior o artista vê os dados de todos os clientes daquele dia; antes, só nome, foto e região; marcação já dentro da janela libera na hora ([[mvp-final]]). A tela espera o arquivo de detalhe |
| 33 | Lembretes e vários endereços | O conjunto de 03/11 deixava lembretes e outros endereços fora ([[mvp-final]]). O cliente os traz para o MVP ([[mvp-alteracoes-pos-congelamento]]) | **Resolvido no cliente:** os dois entram. O retrato fica encaminhado a [[app-cliente-agendamento]] e [[app-cliente-descoberta]] |

## Lacunas

- **Quando o endereço aparece para o artista:** resolvido no conjunto de funções. Às 00:00:01 do dia anterior, os dados de todos os clientes do dia; antes, nome, foto e região. O cliente não mudou esta regra. A tela do artista espera o detalhe desse lado. → [[seguranca-do-atendimento]], [[core-08-enderecos]], [[mvp-final]]
- **Cancelamento de agendamento** e penalidades fora dos termos. → [[termos-e-responsabilidades]]
