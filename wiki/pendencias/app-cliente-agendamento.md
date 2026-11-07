---
tipo: pendencia
superficie: app-cliente
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[conversa-do-agendamento]]", "[[inicio]]", "[[agenda]]"]
---

# Ajustes do app do cliente: agendamento

Esta página lista o que o app do cliente precisa mudar no agendamento para chegar ao alvo do MVP. Não é a especificação do produto.

### Chat de agendamento
- **Alvo:** O agendamento é um passo a passo em estilo chatbot, sem texto livre: perguntas fixas em sequência, primeiro os serviços (com "Tempo total estimado" e "Pronto" desabilitado até haver um serviço) e depois a data e o horário em cartões com chips, não em calendário. O menu de três pontos do chat tem "Preciso de ajuda" e leva ao WhatsApp do suporte. Se faltar cadastro, ele acontece antes, e não há horário retido durante o cadastro. ("M06 Agendamento do cliente" e "M06 Confirmação do agendamento", [[mvp-funcoes-e-telas]])
- **Hoje:** A tela existe e é casca. No centro está "Tab ChatSchedules" e, embaixo, uma linha. Nenhuma aba abre esta tela e nenhum botão do app aponta para ela. Nem a Agenda nem o Início levam até aqui. ([[conversa-do-agendamento]])
- **Ajuste:** Substituir a casca "Tab ChatSchedules" por um chat de perguntas fixas, sem texto livre, com serviços e depois data e horário em cartões, aberto por uma ação de agendar, e com "Preciso de ajuda" no menu de três pontos. Se o cliente não estiver logado, o cadastro acontece antes e nenhum horário fica retido durante o cadastro.

### Confirmação e retenção
- **Alvo:** "Pronto", na escolha de data e horário, segura o horário por 10 minutos, com contador numa faixa fixa abaixo do topo do chat e uma única extensão de 10 minutos, oferecida 2 minutos antes de expirar. O resumo traz "Preço estimado" (só o total) e a legenda "O pagamento é feito direto com o Artista"; essa legenda não vai no cartão da home nem da Agenda. "Confirmar agendamento" conclui, "Ver meus agendamentos" abre a Agenda e não há tela de detalhe. ("M06 Pré-agendamento" e "M06 Confirmação do agendamento", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve esta tela.
- **Ajuste:** O retrato não tem esta tela. Criar, no chat, a retenção de 10 minutos ao tocar em "Pronto" na data e no horário, com uma extensão de 10, e o resumo com "Preço estimado" e a legenda "O pagamento é feito direto com o Artista", sem repetir essa legenda no cartão da home ou da Agenda; "Confirmar agendamento" conclui e "Ver meus agendamentos" abre a Agenda, sem tela de detalhe.

### Cartão do agendamento
- **Alvo:** O cartão é o mesmo na home e na Agenda: foto, nome e nota do artista, data, horário, serviços, "Preço estimado" (só o total) e o número do agendamento depois da confirmação, sem a legenda de pagamento e sem endereço. O toque no cartão não abre outra tela. O menu de três pontos tem "Cancelar agendamento" e "Preciso de ajuda"; "Preciso de ajuda" abre o WhatsApp com o número do agendamento. A home mostra só o próximo. ("Home do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** No Início, "Próximos agendamentos" mostra dois cartões de exemplo, iguais para qualquer conta. O de Karen Watanabe traz a nota 4,5, "Data:" 25 de Maio, "Quarta" e "12h00", serviços em etiquetas, e não traz foto, preço, duração nem situação. O segundo traz endereço, olho e menu; o olho e o menu não respondem ao toque. "Vamos agendar?" ocupa a largura do cartão e o toque não abre a lista, a Agenda nem a conversa. O cartão de exemplo permanece mesmo sem horário da pessoa. ([[inicio]])
- **Ajuste:** Trocar os cartões de exemplo do Início pelo próximo agendamento real, com foto, nome, nota, data, horário, serviços, "Preço estimado" e número, sem endereço, sem olho e sem a legenda de pagamento. O toque no cartão não abre outra tela, e o menu de três pontos responde com "Cancelar agendamento" e "Preciso de ajuda", este último abrindo o WhatsApp com o número do agendamento.

### Agenda
- **Alvo:** A Agenda separa "Aguardando avaliação", "Próximos agendamentos" e "Agendamentos anteriores"; a seção vazia fica oculta. Com check-out, o cartão vai para "Aguardando avaliação". Sem check-out, fica em "Próximos" até a meia-noite e só então vai para "Aguardando avaliação". Não há tela de detalhe. ("Aba Agenda do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** A aba existe e é casca. O centro diz "Tab Schedules". Não há lista de horários, status, cancelar nem remarcar, e não há agendamento vindo de lugar nenhum. Nenhuma outra tela a abre; o único caminho é a barra. O cartão "Próximos agendamentos" fica no Início e não é esta aba. ([[agenda]])
- **Ajuste:** Substituir a casca "Tab Schedules" pela Agenda com "Aguardando avaliação", "Próximos agendamentos" e "Agendamentos anteriores", também aberta por "Ver mais agendamentos" e por "Ver meus agendamentos". Com check-out o cartão vai para "Aguardando avaliação"; sem check-out fica em "Próximos" até a meia-noite; o toque no cartão não abre outra tela.

### Cancelamento
- **Alvo:** "Cancelar agendamento" não pede motivo e só existe até o horário de início; depois disso o menu do cartão fica só com "Preciso de ajuda". A modal só fecha com ok do backend e, então, o cartão mostra "Cancelado", com opacidade reduzida, até o fim do dia. ("Cancelamento pelo cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve esta tela.
- **Ajuste:** O retrato não tem esta tela. Criar o cancelamento no menu de três pontos do cartão, sem pedir motivo e só até o horário de início, com modal que só marca "Cancelado" depois do ok do backend.

### Avaliação
- **Alvo:** A avaliação é no próprio cartão, de 1 a 5, sem texto, com contador de 10 segundos, uma vez e em até 7 dias. As estrelas só aparecem com check-out, 30 minutos após o fim previsto. "O Artista não compareceu" não deixa nota retida. ("Fluxo de avaliação do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve esta tela.
- **Ajuste:** O retrato não tem esta tela. Criar a avaliação no próprio cartão, de 1 a 5, sem texto, com contador de 10 segundos, uma única vez e em até 7 dias, com estrelas só após o check-out; "O Artista não compareceu" não deixa nota retida.

### Pushes
- **Alvo:** Entram o lembrete (antecipado e 2 horas antes), o reagendamento versão 0 e os pushes de avaliação e de cancelamento pelo artista. Não entra push de confirmação nem central de notificações. A permissão, se ainda não foi concedida, é pedida uma vez no início do chat; negada no aparelho, a home mostra um aviso fixo que abre os ajustes. ("Notificações do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve esta tela.
- **Ajuste:** O retrato não tem esta tela. Criar o lembrete antecipado e o de 2 horas antes, o reagendamento versão 0 (abre a home, sem fluxo preenchido) e os pushes de avaliação e de cancelamento pelo artista, sem push de confirmação e sem central de notificações; a permissão é pedida uma vez no início do chat e, se negada, a home mostra um aviso fixo.
