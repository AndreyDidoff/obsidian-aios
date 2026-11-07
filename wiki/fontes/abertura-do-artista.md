---
tipo: fonte
arquivo: "ingeridos/Abertura do artista.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_worker; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Abertura do artista"]
---

# Abertura do artista

Volta para [[mapa-do-app-do-artista]].

**Pé:** construído. Quem não tem sessão vê o logo, seis slides e dois caminhos: **Cadastrar**, que abre o [[cadastro-do-artista]], e **Já tenho uma conta**, que abre o login. Recusar localização ou notificação não impede o avanço. O app avisa e segue. O app não guarda a escolha. Não há registro invertido nesta abertura. A biometria não dispara nesta tela.

Agenda, preço, check-in, check-out e pagamento aparecem na cópia dos slides e ainda não têm área. Isso é promessa de tela, não decisão de produto. O [[mvp]] continua gratuito, sem pagamento no lançamento. ([[decisoes-2026-10-20]]) O que falta está em [[o-que-ainda-nao-esta-no-app-do-artista]]. Ver [[contradicoes-e-lacunas]].

## A primeira tela

A abertura já é o carrossel: logo, seis bolinhas e um botão. Nos três primeiros slides, **Próximo**. No quarto, **Permitir localização**. No quinto, **Permitir notificações**. No sexto, **Cadastrar**. **Já tenho uma conta** fica o tempo todo embaixo. Não há uso sem conta e não há porta antes do carrossel.

Dá para arrastar. Arrastar troca o slide e o texto do botão. A permissão só é pedida quando a pessoa toca o botão no slide de localização ou no de notificação. Arrastar por cima desses dois pula o pedido.

Quem abre o app com sessão ainda válida vê esta tela só enquanto a sessão é conferida. Se a conferência aceita, cai nas abas, começando pelo [[inicio-do-artista]]. Se não há sessão, permanece aqui. Se a conferência falha por um motivo que não é sessão recusada, o app entra nas abas mesmo assim.

## Os seis slides

1. **Bem-vindo a WeCareU.** Apresentação. Não pede nada.
2. **Seja valorizado.** Promete perfil 100% gratuito, sem comissão, clientes, agendamento automático e pagamento direto no app. O restante do app não tem área de comissão nem de pagamento. A aba Planos abre "Tab Plans".
3. **Gerencie seu negócio.** Promete agenda, escolha de horários e de preços, check-in e check-out automáticos. Não há tela para isso. A aba Agenda abre "Tab Schedules". A aba Pedidos abre "Tab Orders". O início mostra um próximo atendimento de exemplo.
4. **Permissão de localização.** Fala em clientes próximos e em mapa. Nesta abertura o app só pede a permissão do aparelho. Não abre mapa, não lista clientes e não preenche endereço. Existe uma tela com o texto "Tab Clients"; ela não entra neste caminho nem nas abas.
5. **Permissão de notificações.** Fala em novos agendamentos, mensagens de clientes e lembretes. Aceitar aqui não abre uma central de avisos.
6. **Comece Agora.** **Cadastrar** abre o cadastro. Não entra nas abas e não entra no login.

Se a pessoa **recusa** localização ou notificação, o carrossel segue e aparece o aviso **Permissão Negada**, já por cima do slide seguinte. Dá para fechar o aviso ou abrir os ajustes do aparelho. Se o pedido de permissão falha, não aparece aviso. O carrossel segue.

## Para onde a pessoa vai

- **Cadastrar**, no último slide: [[cadastro-do-artista]].
- **Já tenho uma conta**: [[entrar-senha-e-biometria-do-artista]]. O atalho **Entrar com Biometria** só existe dentro do login, e só depois que a pessoa já ligou isso.
- Sessão ainda válida: abas, começando pelo [[inicio-do-artista]].
- Sair, a partir do [[perfil-do-artista]]: volta para esta abertura. A confirmação diz **Sair da WeCareU** e "Tem certeza que deseja sair da sua conta WeCareU?". **Sair** encerra a sessão no serviço quando o serviço responde; se o serviço falha, a saída local acontece mesmo assim. A biometria ligada é desligada e a credencial guardada some.
