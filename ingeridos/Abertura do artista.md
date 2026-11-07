---
tipo: extração
tema: Abertura do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: construído; recusar permissão não trava, e agenda, preço, check-in e pagamento ainda são só promessa
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Abertura do artista

Volta para [[Mapa do app do artista]].

**Pé:** construído. Quem não tem sessão vê o logo, seis slides e dois caminhos: seguir até o [[Cadastro do artista]], ou ir para [[Entrar, senha e biometria do artista]]. Recusar localização ou notificação não impede o avanço. O app não guarda a escolha. Agenda, preço, check-in, check-out e pagamento aparecem na promessa dos slides e ainda não têm área. A biometria não dispara nesta tela.

## A primeira tela

Não há uma porta separada antes do carrossel. A abertura já é o carrossel, com o logo da WeCareU em cima, seis bolinhas e um botão embaixo.

O botão muda conforme o slide:

- Nos três primeiros, **Próximo**.
- No quarto, **Permitir localização**.
- No quinto, **Permitir notificações**.
- No sexto, **Cadastrar**. Abre o [[Cadastro do artista]].

**Já tenho uma conta** fica o tempo todo embaixo e abre o login. Não há botão de voltar para uma tela anterior: esta é a primeira.

Dá para arrastar para o lado. Arrastar troca o slide e o texto do botão. A permissão só é pedida quando a pessoa toca o botão estando no slide de localização ou no de notificação. Arrastar por cima desses dois slides pula o pedido. O leitor de tela anuncia o título e o texto do slide. A dica do carrossel diz "Deslize para navegar entre as permissões", inclusive nos slides que ainda são só promessa. Cada bolinha se anuncia como "Página" e o número.

Quem abre o app com uma sessão ainda válida vê esta tela só enquanto a sessão é conferida. Se a conferência aceita, sai da abertura e cai nas abas, começando pelo [[Início do artista]]. Se não há sessão, permanece aqui. Se a conferência falha por um motivo que não é sessão recusada, o app entra nas abas mesmo assim.

## Os slides, na ordem

### 1. Bem-vindo a WeCareU

"A plataforma que valoriza seu talento como artista da beleza e bem estar. Conecte-se com clientes apaixonados por beleza e bem estar e transforme sua paixão em sucesso!"

É apresentação. Não pede nada e não abre outra área.

### 2. Seja valorizado

"Destaque-se como Artista que você é! Perfil 100% gratuito, sem comissões. Uma plataforma que atrai clientes para você com agendamento automático e pagamentos direto no app."

O slide afirma perfil grátis, zero comissão, agenda automática e pagamento dentro do app. O restante do app não tem área de comissão nem de pagamento. A aba Planos abre uma tela com o texto "Tab Plans".

### 3. Gerencie seu negócio

"Gerencie agendamentos com facilidade. Escolha seus horários e preços. Check-in e Check-out automático. Foque no que você faz de melhor!"

O slide afirma agenda, escolha de horário e de preço, check-in e check-out. Não há tela para escolher horário, preço, check-in, check-out ou pagamento. A aba Agenda abre "Tab Schedules". A aba Pedidos abre "Tab Orders". O [[Início do artista]] mostra um próximo atendimento de exemplo, com nome, data, hora e serviços escritos na tela, sem vir de um agendamento. O que esses slides prometem e o app ainda não tem está em [[O que ainda não está no app do artista]].

### 4. Permissão de localização

"Para conectar você com clientes próximos e mostrar sua localização no mapa, precisamos da sua permissão de localização. Isso ajuda a encontrar clientes na sua região!"

O slide fala em clientes próximos e em mapa. Nesta abertura o app só pede a permissão do aparelho. Não abre mapa, não lista clientes e não preenche endereço. Existe uma tela de clientes com o texto "Tab Clients"; ela não entra neste caminho nem nas abas. O mapa que o slide menciona não tem tela.

O que acontece ao tocar **Permitir localização**:

- Se a permissão **já estava aceita**, o sistema não pergunta de novo e o carrossel segue.
- Se a pessoa **aceita** agora, o carrossel segue. Nada mais acontece com o ponto nesta tela.
- Se a pessoa **recusa**, o carrossel segue do mesmo jeito e aparece um aviso por cima do slide seguinte. Título: **Permissão Negada**. Texto: "A permissão de localização é importante para conectar você com clientes próximos. Deseja abrir as configurações para ativar manualmente?" **Não usar localização** fecha o aviso. **Permitir localização** abre os ajustes do aparelho. O slide já mudou: o aviso não espera a resposta.
- Se o pedido de permissão falha, não aparece aviso. O carrossel segue.

O app não grava, por conta própria, se a pessoa aceitou ou recusou. A decisão fica só no sistema do aparelho. Não há registro invertido nesta abertura.

### 5. Permissão de notificações

"Receba notificações sobre novos agendamentos, mensagens de clientes e lembretes importantes. Nunca perca uma oportunidade de negócio!"

O mesmo desenho da localização. **Permitir notificações** pergunta ao sistema. Aceitar, recusar ou já ter aceito antes: o carrossel segue. Recusar abre o aviso **Permissão Negada**, com o texto "As notificações são importantes para você não perder agendamentos e mensagens. Deseja abrir as configurações para ativar manualmente?" **Não usar notificações** fecha. **Permitir notificações** abre os ajustes. Falha no pedido: segue em silêncio. O app também não grava essa escolha. Aceitar aqui não abre uma central de avisos e não mostra uma notificação.

### 6. Comece Agora

"Cadastre-se gratuitamente e comece hoje! Junte-se à comunidade de artistas que estão transformando o mercado de beleza e bem estar no Brasil."

**Cadastrar** abre o [[Cadastro do artista]]. Não entra nas abas e não entra no login.

## Biometria nesta abertura

A abertura não oferece digital nem reconhecimento facial e não tenta entrar sozinha. O atalho **Entrar com Biometria** só existe dentro do login, e só depois que a pessoa já ligou isso. O restante está em [[Entrar, senha e biometria do artista]].

## Para onde a pessoa vai

- **Cadastrar**, no último slide: [[Cadastro do artista]].
- **Já tenho uma conta**: login.
- Sessão ainda válida, depois da conferência: abas, começando pelo [[Início do artista]].
- Sair da conta, a partir do [[Perfil do artista]]: volta para esta abertura. A confirmação diz **Sair da WeCareU** e "Tem certeza que deseja sair da sua conta WeCareU?". **Sair** encerra a sessão no serviço da WeCareU quando o serviço responde; se o serviço falha, a saída local acontece mesmo assim. A biometria ligada é desligada e a credencial guardada some.
