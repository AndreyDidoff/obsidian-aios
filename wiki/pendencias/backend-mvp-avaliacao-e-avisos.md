---
tipo: pendencia
superficie: backend
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[backend-mvp-conta]]"]
---

# Ajustes de backend: avaliação e avisos

Esta página lista o que o backend precisa mudar na avaliação e nos avisos para chegar ao alvo do MVP. Não é a especificação do produto.

A nota com que a conta nasce está em [[backend-mvp-conta]].

### Atraso de publicação e média
- **Alvo:** ("Fluxo de avaliação do cliente (M10)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Publicar a nota só depois de um atraso aleatório de 24 a 72 horas (`PUBLICACAO_ATRASO_H`) e calcular a média bayesiana com prior 4,7 e peso 10, exibida a partir de 3 avaliações. O prazo para avaliar é de 7 dias, o check-out automático ocorre à meia-noite e o cancelado não gera nota nem entra no cálculo.

### Não compareceu sem nota retida
- **Alvo:** ("Fluxo de avaliação do cliente (M10)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Registrar "O Artista não compareceu" e enviar à mediação, deixando o agendamento sem nota nos dois desfechos, sem avaliação retida. Se a mediação concluir que houve atendimento, o cliente perde o direito de avaliar.

### Push de avaliação
- **Alvo:** ("Fluxo de avaliação do cliente (M10)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Enviar o push no check-out, inclusive no fechamento automático à meia-noite, e outro no dia seguinte às 10:00, agrupado, só se ainda houver pendência. O envio respeita o interruptor "Avaliações" e não ocorre se o cliente já avaliou ou confirmou a ausência.

### Lembretes e reagendamento
- **Alvo:** ("Notificações do cliente (M11)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Enviar o lembrete às 18:00 do último dia em que ainda faltam mais de 24 horas e outro 2 horas antes, sem mandar o que não cabe pela margem nem nada se o atendimento foi cancelado. O reagendamento versão 0 sai 25 dias depois do último atendimento concluído, um push por atendimento, só sem agendamento futuro, com prazos configuráveis.

### Serviço principal no push
- **Alvo:** ("Notificações do cliente (M11)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Informar no push qual é o serviço principal do agendamento, o pré-selecionado na listagem, e a quantidade dos demais.

### Ausência de confirmação e central
- **Alvo:** ("Notificações do cliente (M11)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Não criar push de confirmação do agendamento nem central, tela ou histórico de notificações: no MVP o cliente só recebe push.
