---
tipo: pendencia
superficie: backend
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[mvp-final]]", "[[core-03-agenda]]", "[[o-que-ainda-nao-esta-no-app-do-artista]]", "[[abertura-do-artista]]"]
---

# Ajustes de backend: agendamento

Esta página lista o que o backend precisa mudar no agendamento para chegar ao alvo do MVP. Não é a especificação do produto.

Item com [RECOMENDADO] continua recomendação.

### Recusa de agendar consigo mesmo
- **Alvo:** O backend recusa, com erro específico, qualquer agendamento em que o Artista seja a mesma identidade do cliente logado. ("Artista que também é cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento. ([[core-03-agenda]])
- **Ajuste:** O retrato não mostra esta regra. Recusar com erro específico quando quem pede e quem atende são a mesma identidade; nenhuma ação confere quem chama.

### Janelas livres
- **Alvo:** [RECOMENDADO] Só oferece janela livre maior ou igual ao tempo total estimado, mais o deslocamento. ("M06 Agendamento do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento. ([[core-03-agenda]])
- **Ajuste:** O retrato não mostra esta regra. Limitar a oferta às janelas livres que caibam no tempo total estimado mais o deslocamento, e manter isto como recomendação.

### Pré-agendado de 10+10
- **Alvo:** O agendamento ganha o estado pré-agendado, que retém o horário por 10 minutos, com uma única extensão de 10 minutos, no máximo 20. O "×" do topo libera o horário na hora, e a expiração também libera. A retenção, a extensão e o controle ficam no backend. ("M06 Pré-agendamento", [[mvp-funcoes-e-telas]])
- **Hoje:** A marcação grava já como agendada, ou com o andamento que veio no pedido. Não há pré-agendado nem retenção. ([[core-03-agenda]])
- **Ajuste:** Criar o estado pré-agendado com retenção de 10 minutos e uma única extensão de 10, liberando o horário no "×" do topo e na expiração, com o controle no backend.

### Revalidação na confirmação
- **Alvo:** Na confirmação, o backend revalida artista ativo e sem bloqueio com o cliente, horário ainda livre, serviços, preços e retenção válida. Serviço removido recalcula duração e preço. ("M06 Regras de consistência do agendamento", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento. ([[core-03-agenda]])
- **Ajuste:** O retrato não mostra esta regra. Na confirmação, revalidar artista, horário, serviços, preços e retenção, e recalcular duração e preço se um serviço tiver sido removido.

### Confirmação idempotente
- **Alvo:** A confirmação é idempotente: pedido repetido não duplica. Depois de timeout, o app consulta o resultado antes de tentar de novo. ("M06 Regras de consistência do agendamento"; "2. Falhas em ações e padrão de mensagens", [[mvp-funcoes-e-telas]])
- **Hoje:** Não há confirmação idempotente. A marcação grava direto, já como agendada ou com o andamento que veio no pedido. ([[core-03-agenda]])
- **Ajuste:** Tornar a confirmação idempotente, para que pedido repetido não crie outro agendamento. Depois de timeout, consultar o resultado antes de nova tentativa.

### Dados congelados
- **Alvo:** A confirmação grava no agendamento o preço total, os serviços, a duração, o nome do artista e a cópia do endereço. Mudança posterior do artista não altera o agendamento já feito. ("M06 Regras de consistência do agendamento"; "Endereço de atendimento e troca pela listagem", [[mvp-funcoes-e-telas]])
- **Hoje:** Não há cópia congelada do endereço. ([[core-03-agenda]])
- **Ajuste:** Na confirmação, gravar a cópia congelada do preço total, dos serviços, da duração, do nome do artista e do endereço. Mudança posterior desses dados não altera o agendamento já confirmado.

### Número sequencial
- **Alvo:** O número do agendamento é único e sequencial, e nasce depois da confirmação. ("Registro de detalhamento: Home do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento. ([[core-03-agenda]])
- **Ajuste:** O retrato não mostra esta regra. Gerar um número único e sequencial somente depois da confirmação.

### Cancelamento sem motivo
- **Alvo:** O cancelamento do cliente não pede motivo. O backend registra quem cancelou e quando, e marca cancelamento tardio quando falta menos de 24 horas para o início. Recusa o cancelamento depois do início, pela hora do servidor. ("Cancelamento pelo cliente (M06-F05)"; "M06 Regras de consistência do agendamento", [[mvp-funcoes-e-telas]]) [RECOMENDADO] Devolver o horário à agenda do artista e enviar push ao artista.
- **Hoje:** O cancelado continua na lista porque a lista olha quem está ativo, não o andamento. Nenhuma ação confere quem chama nem preenche quem alterou. ([[core-03-agenda]])
- **Ajuste:** Registrar quem cancelou e quando, sem motivo, e a marca de cancelamento tardio abaixo de 24 horas. Recusar depois do início pela hora do servidor; devolver o horário e o push ao artista ficam como recomendação.

## Inventário do artista, sem tela

Sem desenho de tela.

### Check-in e check-out
- **Alvo:** Check-in e check-out por barra continuam no alvo. ([[mvp-final]])
- **Hoje:** o retrato lido não descreve este comportamento. ([[core-03-agenda]]) A abertura promete check-in e check-out, e essas áreas não existem. ([[abertura-do-artista]], [[o-que-ainda-nao-esta-no-app-do-artista]])
- **Ajuste:** O check-in e o check-out por barra continuam no alvo, e o retrato do artista não tem essas áreas. Sem desenho de tela.

### Pagamento gratuito
- **Alvo:** O alvo continua gratuito, com pagamento fora do app. ([[mvp-final]]; "Cancelamento pelo cliente (M06-F05)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento. ([[core-03-agenda]]) A abertura promete pagamento no app. A promessa é retrato. ([[abertura-do-artista]], [[o-que-ainda-nao-esta-no-app-do-artista]])
- **Ajuste:** O retrato não mostra esta regra. Manter o MVP gratuito, com pagamento fora do app. A promessa de pagamento na abertura fica como retrato.
