# WeCareU — Alterações após o congelamento dos arquivos 00 a 04

Os arquivos 00 a 04 estão na base de conhecimento e não são mais alterados. Este arquivo reúne o que foi definido ou alterado depois da carga e que ainda não está na base. Qualquer novo item entra aqui ou nos arquivos 05 em diante. Cada seção abaixo traz só o **delta** em relação aos congelados (ou à spec) e o ponteiro da regra completa no `05`.

Marcadores canônicos: [DEFINIDO] · [RECOMENDADO] · [PENDENTE] · [HIPÓTESE].
Marcadores de processo neste arquivo: [ALTERADO] / [REMOVIDO] quando o item muda algo dos congelados ou do inventário; [FUTURO] fora do MVP; [EM LAPIDAÇÃO] regra geral definida, detalhe por tela pendente.

## 1. Mudança em relação à spec de busca (originalmente na seção E do `02`)

- **Card do grupo B sem data real [DEFINIDO pelo dono, MVP].** A spec (H1.3 e seção do grupo B) mostra a data real do próximo horário no card, com botão que agenda aquele horário. No MVP o card **não** mostra a data; o cliente abre o perfil e inicia o agendamento para ver os horários. O grupo B continua definido pela mesma regra (horário em data próxima, até 14 dias).
- Regra completa no `05`, seção `Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]`.

## 2. Mudança em relação à spec (D-02)

- **Card sem horários livres do dia [DEFINIDO pelo dono, MVP].** A D-02 diz que o card mostra os horários livres do dia. No MVP o card **não** mostra horários, em nenhum grupo.
- Regra completa no `05`, seção `Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono]`.

## 3. Decisões de detalhamento já registradas no `05`

- Estados da listagem do cliente → `05`, seção `Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]`.
- Conteúdo do card de artista → `05`, seção `Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono]`.
- Pedido de notificação sai do Welcome e passa a ser feito **somente no início do chat de agendamento** (não há pedido após a confirmação); listagem vazia passa a mostrar mensagem → `05`, seções `Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]`, `M06 Confirmação do agendamento [DEFINIDO]` (item "Pedido de notificações antes de todo agendamento") e `Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]`.

## 4. Serviço com preço no MVP [DEFINIDO pelo dono]

- O `04` e o `01` descrevem o cadastro de serviço com "duração". No MVP o serviço também tem **preço**, mostrado ao cliente no agendamento. A faixa de preço do card continua digitada pelo artista, separada dos preços dos serviços.
- Regra completa no `05`, seções `Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono]` e `Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO]`.

## 5. Foto de divulgação única e denúncia de foto [DEFINIDO pelo dono]

- No MVP o artista tem **uma** foto de divulgação, sem filtro prévio; denúncia no perfil e remoção pela equipe. O critério de aprovação do `04` ("foto adequada") cobre a foto de perfil; a foto de divulgação **não** é aprovada antes de publicar.
- Foto de divulgação **obrigatória** no cadastro do artista (a de perfil também). Descrição curta do card: até 28 caracteres, opcional, sem moderação prévia, com validação de conteúdo no backend (sem equivalente nos congelados); regra no `05`, seção `Registro de detalhamento: M05/M02 Descrição curta do card [DEFINIDO pelo dono]`.
- A foto de divulgação **não** aparece no perfil no MVP (a do card é vertical e a do topo seria horizontal); a denúncia da foto é pelo botão "Denunciar Artista", com opção de selecionar a foto. Galeria é [FUTURO].
- Regra completa no `05`, seções `Registro de detalhamento: M05/M02 Foto de divulgação e tag no card [DEFINIDO pelo dono]` e `Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]`.

## Perfil do Artista visto pelo cliente: diferenças em relação ao Figma [DEFINIDO]

- **Sai do Figma:** idade ("23 Anos"), botão "Compartilhar" (futuro) e aba Favoritos na barra inferior.
- **Nota:** só as estrelas, sem contagem de avaliações; com menos de 3 avaliações aparece "Poucas avaliações" no lugar das estrelas (informado pelo backend).
- **Rodapé:** "Na WeCareU desde" + mês e ano da **aprovação** do Artista (no Figma: "Perfil criado em"); botão "Denunciar Artista" (no Figma: "Denunciar Perfil") e novo botão "Bloquear Artista".
- **Serviços:** título continua "Serviços", agrupados por categoria, com nome, duração e preço; apenas informativos.
- Regra completa no `05`, seção `Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]`; bloqueio em `Bloqueio (M12-F02) [DEFINIDO]`.

## Listagem inicial sem data [DEFINIDO]

- **Muda a spec** (presume data sempre presente): ao chegar na listagem não há filtro de data, ofício ou serviço; lista única por faixas de ranqueamento e desempates, sem grupos A/B e sem checagem de agenda. Disponibilidade e A/B só depois que o cliente escolhe uma data.
- Com filtros aplicados, o topo da listagem mostra a data e uma faixa de chips com os filtros selecionados.
- Regra completa no `05`, seção `Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]` (item "Filtros selecionados no topo da listagem"); paginação e atualizar em `Registro de detalhamento: M05 Scroll infinito [DEFINIDO pelo dono]` e `Registro de detalhamento: M05 Arrastar para atualizar [DEFINIDO pelo dono]`.
- Campo de texto, calendário (limite futuro configurável no backend), limpar filtros, artista indisponível, artista tocando no próprio perfil e recarga da lista ao voltar do perfil: regras no `05`, seção `Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]`.

## Agendamento do cliente [DEFINIDO]

- **Novo em relação aos congelados / spec:** estado de agenda "pré-agendado" (retenção temporária ao tocar em "Pronto"); cadastro do cliente **antes** do fluxo (nunca com horário retido); resumo com preço total e região; "Tempo total estimado" no lugar de "média".
- **Preço estimado:** o resumo e o cartão de agendamento (Home e Agenda) mostram só o total, com o rótulo "Preço estimado"; o Figma não tinha esse rótulo.
- **Serviço principal:** na listagem o cliente escolhe um serviço (não só uma categoria); esse serviço vem pré-selecionado no agendamento (o cliente pode adicionar outros, só os que aquele Artista atende) e vira o "serviço principal" do push antecipado.
- **Retenção do horário:** 10 minutos, com uma única extensão de 10 minutos oferecida 2 minutos antes de expirar; o contador fica em faixa fixa abaixo do topo do chat, sem "×" próprio; a mensagem de oferta da extensão interrompe o fluxo. Passando de 20 minutos no total, o horário é liberado.
- Regra completa no `05`, seções `Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO]`, `M06 Pré-agendamento [DEFINIDO pelo dono]`, `M06 Aviso de extensão única e endereço` e `M06 Confirmação do agendamento [DEFINIDO]`.

## Endereços salvos do cliente [DEFINIDO]

- **Muda o `04`**, que deixava "outros endereços" fora do MVP: no MVP o cliente salva vários endereços com nome e escolhe um na home como local de atendimento. A pesquisa é só por CEP (sem busca por texto nem sugestões; provedor pago é [FUTURO]). Todo endereço novo do cliente logado é salvo pelo formulário; o deslogado só "usa" o endereço, sem salvar. O chat de agendamento não pergunta o endereço. Não cria endereço repetido (CEP, número e complemento iguais) e o cliente não pode ficar sem endereço (modal impede excluir o último); edição e exclusão em Meus endereços (engrenagem), não na aba Perfil.
- Home do cliente **não** mostra nota do cliente (não há nota do cliente no MVP).
- Regra completa no `05`, seções `Registro de detalhamento: Home do cliente [DEFINIDO]` e `Endereço de atendimento e troca pela listagem [DEFINIDO]`.

## Cancelamento pelo cliente [DEFINIDO]

- **Muda M06-F05 / congelados** (que previam guardar motivo): sem motivo no MVP; registra quem e quando. Futuro: penalização (muitos cancelamentos ou até 24 h antes), alterando o `LIMITE_CANCELAMENTO_TARDIO_H` de 12 h da spec.
- Cartão cancelado permanece na home (opaco, com o texto "Cancelado" no lugar das estrelas) até o fim do dia ou novo agendamento.
- Regra completa no `05`, seção `Cancelamento pelo cliente (M06-F05) [DEFINIDO]`.

## M06-F04 Detalhe do agendamento removido do MVP [DEFINIDO]

- **Fora do MVP:** o cartão de agendamento não é tocável; não há tela de detalhe.
- Regra completa no `05`, seção `Registro de detalhamento: Home do cliente [DEFINIDO]`.

## Perfil do cliente e engrenagem [DEFINIDO]

- **Delta vs Figma / congelados:** a tela da engrenagem passa a se chamar "Configurações" (no Figma: "Meu Perfil"); "Gerenciar Endereços" vira "Meus endereços"; "Excluir conta" no menu; "Artistas que você segue" removido (Favoritos fora); notificação de Agendamentos não desligável; Central de Ajuda via WhatsApp até existir wecareu.app/suporte; Termos/Política com textos defasados; agendamento guarda cópia do endereço.
- Regra completa no `05`, seção `Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]` (exclusão: `Excluir conta do cliente [DEFINIDO]`).
- Lista de endereços só em Meus endereços (Figma antigo: Gerenciar Endereços; não na aba Perfil), nome exibido (social, senão primeiro nome), Editar Perfil sem modal de descarte e confirmação ao sair da conta: regras completas no `05`, seções `Registro de detalhamento: Aba Perfil do cliente [DEFINIDO]`, `Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]` e `Editar Perfil do cliente e troca de e-mail [DEFINIDO]`.

## Navegação inferior do cliente [DEFINIDO]

- **Delta:** Favoritos fora da barra no MVP (4 abas). Deslogado vê a barra na listagem e tela de bloqueio nas abas restritas.
- Regra completa no `05`, seção `Registro de detalhamento: Navegação inferior do cliente [DEFINIDO]`.

## Avaliação do cliente no próprio cartão e seção "Avalie seu atendimento" [DEFINIDO]

- **Delta vs congelados / Figma:** avaliação no próprio cartão (sem card separado); seção na home e na Agenda com título de UI "Avalie seu atendimento" (nome funcional "Aguardando avaliação").
- **Muda o `04` no "prestador não compareceu":** o cliente não vê "em análise" nem resposta da mediação; cartão só sem avaliação + modal de agradecimento; a avaliação usa toque simples e contador de 10 s, e a falha de envio deixa as estrelas vazias com nova tentativa; se a mediação concluir que o atendimento aconteceu, o cliente perde o direito de avaliar.
- Regra completa no `05`, seção `Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]`.

## Notificações do cliente [DEFINIDO]

- **Diverge do `04`/M11:** sem tela/central de notificações no MVP, só push. Push de confirmação do agendamento fora do MVP.
- **Muda o `04` §5:** lembretes (atendimento e reagendamento v0) entram no MVP (no congelado estavam fora). Também: cancelamento pelo artista (sem oferta de reagendar) e aviso fixo na home se push negado. O lembrete antecipado dispara às 18:00 do último dia com mais de 24 h de antecedência, e há outro 2 h antes; o corpo cita o serviço principal e a quantidade dos demais, sem mencionar cancelamento (o backend informa qual é o principal e quantos são os outros).
- **Muda o `01`** (que deixava preferências de notificação fora do MVP): a tela de Configurações de Notificação existe no MVP, com Agendamentos e Segurança e manutenção sempre ligados e Avaliações desligável; Promoções e Ofertas oculto.
- **Push de avaliação (novo):** no check-out e no dia seguinte às 10:00, agrupado, só com avaliação pendente, sujeito ao interruptor "Avaliações".
- **Pedido de permissão de push:** só no início do chat de agendamento (sai do Welcome; sem pedido após a confirmação).
- Regra completa no `05`, seção `Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]` (push de avaliação em `Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]`; interruptores em `Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]`).

## "Preciso de ajuda" e contato da WeCareU [DEFINIDO]

- **Delta:** menu do cartão com "Cancelar agendamento" (só futuros até o início) e "Preciso de ajuda"; # sequencial após confirmação; contato WeCareU por WhatsApp pré-preenchido, sem tela nova; Central de Ajuda também via WhatsApp até wecareu.app/suporte.
- Cartão: o menu (três pontos) traz "Cancelar agendamento" (só até o início), "Preciso de ajuda" e, nos agendamentos passados, "Denunciar Artista" como item separado, com o Artista e o # anexados; o # aparece como número de pedido para rastreamento.
- Regra completa no `05`, seção `Registro de detalhamento: Home do cliente [DEFINIDO]` (Central de Ajuda em `Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]`).

## Cadastro do cliente: sem SMS OTP e sem telefone verificado no MVP [DEFINIDO]

- **Conflito com `01`, `04` e a spec** (SMS OTP; mitigação "nome, foto e telefone verificado"): no MVP o celular é só coletado, sem SMS, por custo. Chave de validação = CPF; unicidade só CPF e e-mail. Risco aceito: celular falso ou de terceiros. Autenticação facial e documento ficam para o futuro.
- Regra completa no `05`, seção `Cadastro do cliente: formato e dados [DEFINIDO]`.

## Cadastro do cliente: novos dados e formato chatbot [DEFINIDO]

- **Não previstos nos congelados:** cadastro em chatbot com os 11 dados (CPF, nome, celular, sexo, nome social opcional, nascimento mín. 18, foto, endereço, e-mail, senha e termos); dados parciais no aparelho (sem senha) por 3 dias; e-mail só coletado com confirmação posterior; troca de e-mail no antigo e depois no novo.
- Regra completa no `05`, seções `Cadastro do cliente: formato e dados [DEFINIDO]`, `Cadastro do cliente: retomada e conclusão [DEFINIDO]`, `Confirmação de e-mail do cliente [DEFINIDO]` e `Editar Perfil do cliente e troca de e-mail [DEFINIDO]`.
- Aceite único de Termos e Política com versão registrada, menor de 18 anos bloqueado sem guardar dados e ausência de passo de conferência: regras completas no `05`, seção `Cadastro do cliente: formato e dados [DEFINIDO]`.

## Foto obrigatória do cliente para agendar [DEFINIDO]

- **Delta:** foto pedida no cadastro ("Depois" permitido); quem pulou recebe o pedido no chat de agendamento sem "Depois"; sem foto não agenda.
- Regra completa no `05`, seção `Cadastro do cliente: foto [DEFINIDO]`.

## Welcome do cliente [DEFINIDO]

- **Não partia do Figma nos congelados:** welcome de 5 slides (3 apresentação + localização + endereço CEP); sem fotos reais; sem trava/validação de região, nunca; só para quem nunca entrou no app.
- Regra completa no `05`, seção `Welcome do cliente: estrutura [DEFINIDO]` (slides em `Welcome: slides de apresentação [DEFINIDO]`, `Welcome: slide 4 (localização) [DEFINIDO]` e `Welcome: slide 5 (endereço) [DEFINIDO]`).

## Recuperação de senha e sessão do cliente [DEFINIDO]

- **Delta vs Figma / congelados:** recuperação por código por e-mail (válido por 5 min, configurável no backend) (sem revelar se o e-mail existe); link por e-mail só para confirmar e-mail do cadastro; "Alterar Senha" logado usa o mesmo fluxo e desloga ao finalizar; lupas da home e do chat removidas no MVP.
- Regra completa no `05`, seções `Login e recuperação de senha do cliente [DEFINIDO]`, `Sessão do cliente [DEFINIDO]` e `Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]` (lupas também em `Registro de detalhamento: Home do cliente [DEFINIDO]`).
- Bloqueio temporário por tentativas de senha no login: regra no `05`, seção `Login e recuperação de senha do cliente [DEFINIDO]`.
- **Biometria [DEFINIDO]:** vale para o desbloqueio do app e não substitui o login; oferta após o login; interruptor em Segurança; tratamento de biometria alterada; "Sair" desativa. O que existe hoje no app passa a seguir esta definição.
- **Sessão: 401 genérico [DEFINIDO]:** qualquer perda de autorização volta do backend como o mesmo 401, sem motivo, e o app mostra uma única mensagem no login; o motivo de suspensão ou banimento só aparece na tentativa de login.

## Excluir conta do cliente [DEFINIDO]

- **Não detalhado assim nos congelados:** exclusão bloqueada com agendamentos não concluídos / em aberto; efetiva após 30 dias ("em processo de exclusão"); login no prazo reativa na hora sem aviso; depois soft delete (sem remoção física; LGPD via suporte). Tela de motivo obrigatória (sem "Pular") + modais por opção; textos dos modais 3 e 4 sem prometer remoção física.
- Se o cliente também é artista, **só o usuário do app C** recebe o soft delete; dados do artista intactos.
- Regra completa no `05`, seção `Excluir conta do cliente [DEFINIDO]`.

## Bloqueio sem desbloqueio pelo usuário e denúncia [DEFINIDO]

- **Diverge de `01`/`04`/M12-F02** (bloquear e desbloquear): sem tela de bloqueados e sem desbloqueio pelo usuário; desbloqueio só pela equipe; atalho "Bloquear também" após denúncia e "Bloquear Artista" no perfil (dois pontos de entrada); sem Desfazer; sem bloqueio na avaliação; o bloqueio cancela só agendamentos futuros, e atendimentos já iniciados, avaliações e concluídos permanecem.
- Motivos de denúncia: removidos os de "não me atendeu" (cobertos por "O Artista não compareceu"); motivo de chat fundido em "Quis fazer o agendamento por fora da WeCareU". Sem motivo "Fez check-in sem mim" (equivale a "não compareceu"); sem trava de repetição e sem retorno ao denunciante. Sem ação automática; tudo ao backoffice.
- **Muda M06-F05** no que se refere a após o início: "Cancelar" só até o horário de início.
- Regra completa no `05`, seções `Bloqueio (M12-F02) [DEFINIDO]`, `Denúncia do cliente (M12-F01) [DEFINIDO]` e `Registro de detalhamento: Home do cliente [DEFINIDO]` (Preciso de ajuda / Cancelar).

## Convite ao cliente e cadastro unificado entre apps [DEFINIDO]

- **Muda M07-F03, F04 e F07 (`01`/`04`):** convite só mensagem de atenção, sem link de aterrissagem, sem cruzamento de dados e sem vínculo automático da reserva ao cadastro no MVP (no máximo link da loja).
- Dois apps com cadastro unificado (M01-F07): no MVP cadastro único sem pedir dados adicionais; backend impede auto-agendamento.
- Welcome / localização negada: sem link "Prefiro digitar o endereço".
- Regra completa no `05`, seções `Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO]`, `Registro de detalhamento: Dois apps e cadastro unificado [DEFINIDO]` e `Welcome: slide 4 (localização) [DEFINIDO]`.

## Endereço de atendimento (sem endereço principal) [DEFINIDO]

- **Delta:** não há "endereço principal"; vale o endereço de atendimento atual (último escolhido). Remove "definir como principal". Região ≠ bairro; no MVP região = bairro do CEP.
- Regra completa no `05`, seções `Endereço de atendimento e troca pela listagem [DEFINIDO]` e `Registro de detalhamento: Região (conceito) [DEFINIDO]`.

## Estados gerais do app (cliente) [DEFINIDO]

- **Sem equivalente nos arquivos 00 a 04:** overlay de sem internet; padrão de mensagens (erro de campo, toast, modal, aviso embutido); versão mínima do app; tela de manutenção; conta suspensa ou banida (motivo só na tentativa de login); permissão de câmera negada; hora do servidor como referência. Uma única mensagem fixa por vez na região de alertas da Home, com prioridade: 0 mensagem pontual, 1 push negado, 2 e-mail não confirmado.
- Regra completa no `05`, seção `Estados gerais do app (todas as telas, cliente) [DEFINIDO]` (prioridade das mensagens fixas em `2. Falhas em ações e padrão de mensagens [DEFINIDO]`).

## Agendamento do cliente: consistência e avaliação
- Sem bloqueio de sobreposição do cliente, sem limite de agendamentos futuros (risco aceito), revalidação na confirmação com aviso de mudança de preço, confirmação idempotente, saída do fluxo, dados congelados no backend, marca de cancelamento tardio e falha no envio da avaliação: regras completas no `05`, seções `M06 Regras de consistência do agendamento [DEFINIDO]` e `M10 Falha no envio da avaliação [DEFINIDO]`.

## Destino de "Ver meus agendamentos" [DEFINIDO]
- **Corrige o app atual / Figma**, onde a ação da mensagem final do agendamento levava à Home: passa a levar à **Agenda**, pois é lá que ficam os agendamentos e não existe tela de detalhe (M06-F04 fora do MVP). Vale também para o botão da modal "Você tem agendamentos em aberto" (Excluir conta).
- Regra completa no `05`, seções `M06 Confirmação do agendamento [DEFINIDO]` e `Excluir conta do cliente [DEFINIDO]`.

## Formulário de endereço na Home e na listagem [DEFINIDO]
- **Delta vs Figma / `04`:** o campo "Endereço" do bloco "Vamos agendar" é fictício e abre um formulário em modal (CEP e demais campos, mais o nome do endereço); a folha de troca de endereço da listagem reutiliza o mesmo bloco. Cliente logado: sempre salva. Deslogado: "Usar este endereço", sem nome e sem lista. O chat de agendamento não pergunta endereço. Pesquisa só por CEP, com o mesmo componente do welcome e do cadastro.
- Regra completa no `05`, seções `Registro de detalhamento: Home do cliente [DEFINIDO]` e `Endereço de atendimento e troca pela listagem [DEFINIDO]`.

## Carregamento inicial das telas (skeleton) [DEFINIDO]
- **Sem equivalente nos congelados:** skeleton sem texto; formato e posição iguais ao conteúdo real (não gera "pulo"); o que é fixo fica real; seções opcionais entram como cartão genérico sem título; carregamento parcial por seção; sem skeleton em Welcome, Login/recuperação e Cadastro em chat. Cor e animação no Figma.
- Regra completa no `05`, seção `Carregamento inicial das telas (skeleton) [DEFINIDO]`.


## Dados sensíveis (olho) por tela [DEFINIDO]
- **Sem equivalente nos congelados:** dados sensíveis ocultos por padrão com olho para revelar. Sensível: endereço completo, CPF, e-mail, celular, sexo e data de nascimento. Não sensível: nome do endereço, cidade, região, nome exibido, foto, dados públicos do Artista, cartão de agendamento. Máscaras padrão; sexo e data de nascimento 100% ocultos no chat (só ícone). Olho por item e por sessão de tela; timeout de 5 s após revelar. Senha mantém olho de mostrar/ocultar.
- Regra completa no `05`, seção `Dados sensíveis (olho) por tela [DEFINIDO]`.

## Segurança, convite e lançamento (cliente)
- Sanção no MVP: só suspensão por tempo indeterminado (sem advertência, sem strikes), registrada por conta **e por app** (vale só no app em que foi aplicada); `LANCAMENTO_PUBLICO_EM` controla só a tag "Novo"; convite por SMS sem promessa de acompanhamento e sem descadastro (risco aceito); bloqueio preserva atendimentos já iniciados ou concluídos; denúncia sem trava de repetição e sem retorno: regras no `05`, seções `Bloqueio (M12-F02) [DEFINIDO]`, `Denúncia do cliente (M12-F01) [DEFINIDO]`, `Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO]` e `5. Conta suspensa ou banida pelo backoffice [DEFINIDO]`.

## Vocabulário de tela diferente do Figma [DEFINIDO]
- Na tela de login, o "Cadastrar" do Figma vira "Criar conta" (faz par com "Já tenho conta"); textos aprovados no `07`.
- Regra completa no `05`, seção `Login e recuperação de senha do cliente [DEFINIDO]`.

## Textos legais e e-mails transacionais [PENDENTE — diferido]
- **Decisão do dono:** Termos de Uso, Política de Privacidade (com o advogado) e o bloco de e-mails transacionais do `07` **não serão resolvidos agora**. Permanecem como pendência e entram na base de conhecimento assim. **Não bloqueiam** o fechamento do detalhamento do app do cliente nem o início do lado do Artista.
- Ponteiro no `05`, seção `Pendências do app do cliente [ATUALIZADO]`.

## Pagamento fora do app na UI do Cliente [DEFINIDO]
- **Delta:** no resumo da confirmação do agendamento, sob o "Preço estimado", entra a legenda **"O pagamento é feito direto com o Artista"** (`07` C-08-A21). Não aparece no cartão da Home/Agenda. Detalhe jurídico permanece nos Termos (diferidos).
- **Riscos R1–R8 reconfirmados** pelo dono (mantidos): instant book sem limite, sem SMS OTP no Cliente, demais aceites da releitura.
- **Fechamento do app do Cliente [DEFINIDO]:** detalhamento de produto do Cliente para o MVP fechado; próximo bloco = lado do Artista.
- Regra completa no `05`, seções `M06 Confirmação do agendamento [DEFINIDO]` e `Pendências do app do cliente [ATUALIZADO]`; copy em `07` (Agendamento em chat, parte A).

