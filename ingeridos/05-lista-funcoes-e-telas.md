# WeCareU — Lista de funções e telas do MVP

Origem: `04-mvp-final.md` e `01-mvp-e-releases.md`. Inventário dos módulos M01–M14 e registros de detalhamento (lado do cliente já detalhado e fechado onde indicado; lado do artista e painel ainda a detalhar). Ordem sugerida na seção 4.

Marcadores canônicos: [DEFINIDO] decisão do dono · [RECOMENDADO] recomendação · [PENDENTE] aberto · [HIPÓTESE] a validar com dados.
Marcadores de processo neste arquivo: [ALTERADO] / [REMOVIDO] ajuste sobre o inventário ou sobre os congelados; [A CRIAR] funcionalidade nova ainda inexistente no app/backend; [ATUALIZADO] seção de pendências revista; [FUTURO] fora do MVP; [EM LAPIDAÇÃO] regra geral [DEFINIDO] com detalhe por tela ainda [PENDENTE].
Funções vêm de decisões [DEFINIDO]. Telas já detalhadas num registro [DEFINIDO] herdam esse status; telas só listadas no inventário e ainda não detalhadas seguem [RECOMENDADO] até o detalhamento. Itens com `(app)` = aparece no app; `(back)` = só backend, sem tela; `(painel)` = painel de operação.

Legenda de apps: **C** = app do cliente. **P** = app do prestador. **B** = painel de backoffice.

---

## M01. Conta e identidade (C, P)

**Funções**
- M01-F01 Cadastro do cliente (inclui endereço) (app C) [DEFINIDO: ver "Cadastro do cliente: formato e dados [DEFINIDO]"]
- M01-F02 Cadastro do prestador, entra como "pendente" (app P)
- M01-F03 Verificação do telefone por código SMS, para cliente e prestador (app + back) [ALTERADO: no CLIENTE não há SMS OTP no MVP, por custo; o celular é só coletado. Para o prestador, a definir no lado do artista] (lado do cliente: ver "Cadastro do cliente: formato e dados [DEFINIDO]")
- M01-F04 Login (app C, P) [DEFINIDO (lado do cliente): ver "Login e recuperação de senha do cliente [DEFINIDO]"]
- M01-F05 Recuperação de senha (app C, P) [DEFINIDO (lado do cliente): ver "Login e recuperação de senha do cliente [DEFINIDO]"]
- M01-F06 Aceite de termos e consentimento (LGPD) (app C, P) [DEFINIDO (lado do cliente): ver "Cadastro do cliente: formato e dados [DEFINIDO]"]
- M01-F07 Identidade única com dois papéis: o prestador também é cliente, sem auto-agendamento (back) [DEFINIDO: ver "Dois apps e cadastro unificado"]
- M01-F08 Alteração de dados do perfil (app C, P) [DEFINIDO (lado do cliente): ver "Editar Perfil do cliente e troca de e-mail [DEFINIDO]"]
- M01-F09 Alteração do endereço do cliente (app C) [DEFINIDO: ver "Endereço de atendimento e troca pela listagem [DEFINIDO]"]
- M01-F10 Sair da conta (app C, P) [DEFINIDO (lado do cliente): ver "Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]"]
- M01-F11 Exclusão de conta do cliente (soft delete; processo de 30 dias; afeta só o usuário do app C, nunca os dados do papel de artista; ver Excluir conta do cliente) (app C; exclusão no app P a definir) [DEFINIDO: ver "Excluir conta do cliente [DEFINIDO]"]

**Telas**
- C: welcome (5 slides), login, cadastro em formato chatbot, confirmação de e-mail (modal), recuperação de senha por código, aceite dos termos, perfil, editar perfil, Meus endereços, excluir conta (4 modais + tela de motivo obrigatória e modais por opção). Sem verificação de SMS no MVP.
- P: login, cadastro, verificação de SMS, recuperação de senha, termos e consentimento, "aguardando aprovação" (estado pendente), perfil pessoal, editar dados, excluir conta.

---

## M02. Perfil profissional do prestador (P)

**Funções**
- M02-F01 Escolha do ofício
- M02-F02 Cadastro de serviços: nome, duração e preço de cada serviço
- M02-F03 Foto do perfil
- M02-F04 Regiões de atendimento: várias (no MVP a região é o bairro do CEP), com atalho "selecionar a zona toda" em São Paulo
- M02-F05 Perfil público do artista, como o cliente vê (foto, serviços, regiões, avaliação). O telefone pessoal do prestador não aparece. [DEFINIDO (lado do cliente): ver "Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]"]

**Telas (P)**
- Perfil profissional (resumo), escolher ofício, lista de serviços, criar/editar serviço, foto, regiões de atendimento (seleção de regiões; no MVP, bairros; atalho para a zona toda em São Paulo), pré-visualização do perfil público.

---

## M03. Agenda do prestador (P)

**Funções**
- M03-F01 Disponibilidade (dias e horários de atendimento)
- M03-F02 Antecedência mínima e máxima de marcação (padrão conservador, editável)
- M03-F03 Intervalo de deslocamento
- M03-F04 Bloqueio de horário sem dados (almoço etc.)
- M03-F05 Visualização da agenda (agendamentos e bloqueios)
- M03-F06 Cálculo do horário disponível (back): agenda, agendamentos, bloqueios, deslocamento e antecedência, com reserva atômica contra reserva dupla

**Telas (P)**
- Agenda (dia/semana), configurar disponibilidade, configurações de agenda (antecedência e deslocamento), criar/editar bloqueio.

---

## M04. Aprovação e estados do prestador (B, P)

**Funções**
- M04-F01 Fila de prestadores pendentes (painel)
- M04-F02 Aprovar ou reprovar, com critério: nome real, foto adequada, telefone verificado (painel)
- M04-F03 Estados do prestador: pendente, aprovado, reprovado, suspenso, banido (back)
- M04-F04 Prestador de outra cidade: aprovado, mas "não ativado na cidade" até o app chegar lá (back)
- M04-F05 Tag "Novo": 3 dias a partir do mais tardio entre aprovação e lançamento na cidade; lançamento na cidade controlado por `LANCAMENTO_PUBLICO_EM` (back)
- M04-F06 Aviso ao prestador do resultado da aprovação (push/app)

**Telas**
- B: lista de pendentes, detalhe do prestador para aprovar ou reprovar.
- P: estados pendente, reprovado, suspenso e "não ativado na cidade" (mensagens de status).

---

## M05. Busca e listagem (C)

**Funções**
- M05-F01 Filtros: ofício, serviço, data, região (nunca haverá filtro de horário; a região não é chip: vem do endereço de atendimento atual, ver "Endereço de atendimento e troca pela listagem") [DEFINIDO: ver "Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]"]
- M05-F02 Mostrar só ofícios e serviços com pelo menos 1 prestador aprovado na região do cliente [DEFINIDO: ver "Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]"]
- M05-F03 Listagem de prestadores: sem data, lista única por faixas de ranqueamento e desempates; com data, grupos A (data exata) e B (data próxima), faixas "Novo" e demais, desempate por nota, volume e sorteio estável (back) [DEFINIDO: ver "Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]" e "Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]"]
- M05-F04 Busca vazia: mensagem de região sem Artista (texto aprovado em `07` (Listagem, parte A)) [DEFINIDO: ver "Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]"]
- M05-F05 Perfil do artista e escolha de horário disponível [DEFINIDO: ver "Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]" e "M06 Passo 2: data e horário [DEFINIDO]"]
- M05-F06 Exibição da nota (a partir de 3 avaliações) e de "Poucas avaliações" [DEFINIDO: ver "Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]"]
- M05-F07 O prestador-cliente aparece na listagem, inclusive para si mesmo, sem poder agendar para si [DEFINIDO: ver "Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]" e "Registro de detalhamento: Dois apps e cadastro unificado [DEFINIDO]"]

**Telas (C)**
- Início/busca com filtros, listagem de resultados, busca vazia, perfil do artista (horários no fluxo de agendamento).

---

## M06. Agendamento do cliente (C)

**Funções**
- M06-F01 Agendamento instantâneo, sem aceite do prestador [DEFINIDO: ver "Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO]"]
- M06-F02 Confirmação do agendamento [DEFINIDO: ver "M06 Confirmação do agendamento [DEFINIDO]"]
- M06-F03 Consulta de agendamentos: futuros e passados [DEFINIDO: ver "Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO]"]
- M06-F04 Detalhe do agendamento [REMOVIDO do MVP: o cartão não é tocável e não há tela de detalhe] (ver "Registro de detalhamento: Home do cliente [DEFINIDO]")
- M06-F05 Cancelamento pelo cliente (SEM motivo no MVP; guarda quem e quando; "Cancelar agendamento" só até o horário de início) [DEFINIDO: ver "Cancelamento pelo cliente (M06-F05) [DEFINIDO]"]
- M06-F06 Aviso ao cliente quando o prestador cancela [DEFINIDO: ver "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]"]

**Telas (C)**
- Resumo e confirmação do agendamento, agendamento confirmado, meus agendamentos (futuros e passados), cancelar agendamento (modal de confirmação, sem motivo). Sem tela de detalhe.

---

## M07. Reserva manual e convite (P)

**Funções**
- M07-F01 Criar reserva manual: nome e celular do cliente obrigatórios
- M07-F02 Caixa "o cliente autorizou o contato"
- M07-F03 Envio do SMS de convite para baixar o app (custo por conta da empresa; limite diário de convites por prestador)
- M07-F04 Vínculo da reserva manual ao cliente quando ele se cadastra [ALTERADO: fora do MVP; não há link nem cruzamento de dados entre a reserva manual e o cadastro do cliente] (ver "Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO]")
- M07-F05 Reserva manual ocupa a agenda; no MVP não há vínculo ao cadastro do cliente, não gera cartão/avaliação/nota [DEFINIDO]
- M07-F06 Registro da origem do cliente (app, convite do prestador, indicação)
- M07-F07 Experiência do cliente convidado: link do SMS, instalar, cadastrar, ver o agendamento (app C) [ALTERADO: no MVP o convite é só uma mensagem para chamar a atenção; sem link de aterrissagem, sem cadastro com o agendamento já visível] (ver "Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO]")

**Telas**
- P: nova reserva manual, confirmação do convite enviado.
- C: nenhuma no MVP (ver convite do cliente abaixo).

---

## M08. Agendamentos recebidos e dados do cliente (P)

**Funções**
- M08-F01 Lista de agendamentos do prestador (dia, futuros, passados)
- M08-F02 Detalhe do agendamento
- M08-F03 Perfil do cliente com privacidade: antes de 00:00:01 do dia anterior só nome, foto e região; depois, dados de todos os clientes do dia; agendamento dentro da janela libera na hora
- M08-F04 Cancelamento pelo prestador (guarda quem, quando e motivo)
- M08-F05 Histórico de atendimentos do artista [DEFINIDO]

**Telas (P)**
- Agendamentos (lista), detalhe do agendamento, perfil do cliente, cancelar agendamento (motivo).

---

## M09. Atendimento (P)

**Funções**
- M09-F01 Check-in por barra de arrastar [DEFINIDO: no MVP o artista pode fazer check-in a qualquer momento; FUTURO: trava de geolocalização, só libera perto do cliente, como o Uber]
- M09-F02 Cronômetro do atendimento
- M09-F03 Check-out por barra; atendimento concluído
- M09-F04 "Cliente ausente"
- M09-F05 Impedir iniciar o próximo atendimento sem encerrar o anterior (check-out, cancelamento ou cliente ausente)
- M09-F06 Encerramento automático às 00:00:00 de atendimento não fechado, igual ao manual e nunca como ausência (back)

**Telas (P)**
- Atendimento do dia (próximo cliente), atendimento em andamento (cronômetro e barra de check-out), confirmação de "cliente ausente".

---

## M10. Avaliação (C, P)

**Funções**
- M10-F01 Cliente avalia o prestador, 1 a 5, uma por atendimento concluído, sem texto [DEFINIDO: ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]"]
- M10-F02 Opção "O Artista não compareceu": o cartão fica sem avaliação nos dois desfechos da mediação; se a mediação concluir que houve atendimento, o cliente perde o direito de avaliar; nunca há avaliação retida (ver "Fluxo de avaliação do cliente (M10)") [DEFINIDO: ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]"]
- M10-F03 Publicação da nota com atraso (sigilo) e média ponderada (prior 4,7, peso 10), exibida a partir de 3 avaliações (back)
- M10-F04 Prestador vê as avaliações recebidas
- M10-F05 [detalhado, lado do cliente] Avaliação no próprio cartão de agendamento: estrelas só com check-out do artista; toque simples e contador de 10 s (texto aprovado em `07` (Avaliação)), cada toque reinicia; envio ao fim do contador ou ao trocar de página; segundo plano mantém o contador; app fechado perde a nota; nota imutável após envio; uma por agendamento; cancelado não gera avaliação; prazo de 7 dias. [DEFINIDO: ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]"]
- M10-F06 [detalhado] Seção "Aguardando avaliação" na home e na Agenda (check-out move o cartão; sem check-out vai à meia-noite pelo check-out automático). [DEFINIDO: ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]"]
- M10-F07 [detalhado] Link "O Artista não compareceu" no rodapé do cartão, 30 min após o fim previsto, com ou sem check-out; modal de confirmação ("Voltar" destaque / "Sim, não compareceu"), modal de agradecimento; cartão vai para anteriores como sem avaliação; sem tags de análise ou resultado ao cliente; se a mediação determinar que o atendimento aconteceu, o cliente não pode avaliar. [DEFINIDO: ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]"]
- M10-F08 [detalhado] Sigilo: artista vê só a nota agregada; atraso de publicação 24h–72h.
- M10-F09 [detalhado] Push de avaliação: (1) no check-out; (2) dia seguinte 10:00, agrupado, só se houver pendência; sujeito ao toggle "Avaliações". Textos aprovados em `07` (Notificações), C-11-A01 e C-11-A02. [DEFINIDO: ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]" e "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]"]

**Telas**
- C: avaliar atendimento, reportar "O Artista não compareceu".
- P: minhas avaliações.

---

## M11. Notificações (C, P)

**Funções**
- M11-F01 Push de novo agendamento ao prestador (obrigatório)
- M11-F02 Um único reenvio, com prazo fixo, se o prestador não visualizar; registrar "visualizado"
- M11-F03 Push de cancelamento para o outro lado (prestador cancela avisa cliente; cliente cancela avisa prestador) [DEFINIDO (lado do cliente): ver "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]"]
- M11-F04 Push do resultado da aprovação (ver M04-F06)
- M11-F05 Permissão de notificação no app (iOS e Android) [DEFINIDO (lado do cliente): ver "M06 Confirmação do agendamento [DEFINIDO]"]
- M11-F06 Lembrete do atendimento ao cliente (antecipado às 18:00 do último dia com mais de 24 h e outro 2 h antes) [DEFINIDO] (ver "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]")
- M11-F07 Lembrete mensal de reagendamento versão 0 (25 dias após o último atendimento concluído; abre a home) [DEFINIDO] (ver "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]")
- M11-F08 Push de avaliação ao cliente (no check-out e no dia seguinte às 10:00 se houver pendência) [DEFINIDO] (ver "Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]")
- M11-F09 Push de confirmação do agendamento: fora do MVP [DEFINIDO] (ver "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]")
- M11-F10 Aviso fixo na home quando a permissão de push está negada [DEFINIDO] (ver "Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]")

**Telas**
- C, P: solicitação de permissão de notificação. [ALTERADO: NÃO haverá tela/central de notificações no MVP, só push; vale para o cliente e foi definido sem exceção.]

---

## M12. Segurança e confiança (C, P)

**Funções**
- M12-F01 Denúncia (cliente denuncia prestador, prestador denuncia cliente) [DEFINIDO (lado do cliente): ver "Denúncia do cliente (M12-F01) [DEFINIDO]"]
- M12-F02 Bloqueio (cliente bloqueia prestador, prestador bloqueia cliente) [ALTERADO: sem desbloqueio pelo usuário e sem tela de bloqueados; desbloqueio só pela equipe via suporte] (lado do cliente: ver "Bloqueio (M12-F02) [DEFINIDO]")
- M12-F03 Contato da WeCareU [DEFINIDO (lado do cliente): ver "Registro de detalhamento: Home do cliente [DEFINIDO]"]
- M12-F04 Sanção nos termos: no MVP só existe a **suspensão por tempo indeterminado**, até o usuário falar com o suporte (sem advertência e sem strikes; banimento permanente e strikes são [FUTURO]) [DEFINIDO (lado do cliente): ver "5. Conta suspensa ou banida pelo backoffice [DEFINIDO]"]

**Telas**
- C: denunciar (com atalho "Bloquear também"), bloquear, contato da WeCareU (WhatsApp). Sem lista de bloqueados.
- P: denunciar, bloquear, contato da WeCareU (WhatsApp). Sem lista de bloqueados (a confirmar no lado do artista).

---

## M13. Painel de operação (B)

**Funções**
- M13-F01 Login do painel e controle de acesso (Andrey e Bruno no início)
- M13-F02 Aprovação de prestador (ver M04)
- M13-F03 Lista de denúncias e mediação
- M13-F04 Mediação do "não compareceu": decretar ou não o não comparecimento
- M13-F05 Bloqueio, suspensão e banimento de usuário
- M13-F06 Consulta de usuários e agendamentos para mediação [RECOMENDADO]

**Telas (B)**
- Login, aprovações, denúncias, detalhe da denúncia/mediação, usuários (busca e ações).

---

## M14. Fundações sem tela (back)

- M14-F01 API com contrato versionado e erros de negócio com código e mensagem prontos
- M14-F02 Registro dos fatos de negócio (lista na seção 6 do `04-mvp-final.md`)
- M14-F03 Base de bairros por cidade (CEP/IBGE), com hierarquia cidade, zona, bairro
- M14-F04 Lançamento público por cidade (`LANCAMENTO_PUBLICO_EM`) [DEFINIDO: controla **somente** a tag "Novo"; não esconde nem libera artista: o artista aparece na listagem assim que é aprovado/liberado, pois quanto mais artistas na listagem, melhor]
- M14-F05 Provedor de SMS (convites; no cliente não há código SMS no MVP; código do prestador a definir no lado do artista)
- M14-F06 Provedor de push
- M14-F07 Regras de ranqueamento da spec (faixas, desempate, sorteio estável na sessão)
- M14-F08 Configurações da spec (`CFG.*`) usadas no MVP

---

## 4. Ordem sugerida de detalhamento [RECOMENDADO]

1. M01 Conta e identidade
2. M02 Perfil profissional
3. M03 Agenda
4. M04 Aprovação e estados
5. M05 Busca e listagem
6. M06 Agendamento
7. M07 Reserva manual e convite
8. M08 Agendamentos recebidos e dados do cliente
9. M09 Atendimento
10. M10 Avaliação
11. M11 Notificações
12. M12 Segurança e confiança
13. M13 Painel de operação
14. M14 Fundações

Motivo: segue a dependência real (conta, depois oferta, depois demanda, depois atendimento, depois reputação e operação). Cada módulo só usa o que já foi fechado antes.

## 5. Modelo de detalhamento de cada módulo [RECOMENDADO]

Objetivo, atores, pré-condições, ações do usuário (uma a uma), regras de negócio, estados e transições, mensagens e erros, casos de borda, notificações, fatos registrados, o que fica fora e critérios de aceite.

## 6. Quadros transversais, a montar ao fim [RECOMENDADO]

- Estados do agendamento e quem pode mudá-los.
- Permissões: quem vê o quê.
- Mapa de notificações: evento, quem recebe, texto.
- Fatos de negócio por módulo (fecha a seção 6 do `04`).

---

## Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]

Quatro situações da listagem (textos aprovados em `07` (Listagem, parte A)):

1. **Região sem Artista aprovado.** Mensagem, frase e ação aprovadas em `07` (Listagem, parte A). A ação é **"Trocar endereço"** e abre o formulário de endereço (a região vem do CEP). Sem promessa de aviso (R11).
2. **Há artistas na região, mas nenhum com horário na data escolhida.** Mensagem aprovada em `07` (Listagem, parte A), sem prometer data no card. Lista do grupo B abaixo. **Mudança em relação à spec (H1.3, grupo B):** o card **não** mostra a data real do horário; o cliente entra no perfil e inicia o agendamento para ver os horários. Decisão de MVP para não complicar.
3. **Há artistas na região, mas nenhum com horário na data nem nos próximos 14 dias.** Mensagem aprovada em `07` (Listagem, parte A). Ação: botão "Escolher outra data", que abre "Pesquisar".
4. **Falha de conexão ou servidor.** Mensagem e botão "Tentar de novo" aprovados em `07` (Listagem, parte A). Tratada à parte da listagem vazia.

**Mudanças no que já existe no app:**
- Notificação: o pedido de permissão de push sai do Welcome (que passa a pedir só a localização) e é feito **somente no início do chat de agendamento** (ver "M06 Confirmação do agendamento", item "Pedido de notificações antes de todo agendamento"); não existe pedido após a confirmação. Sem permissão, a home mostra um aviso fixo (ver Notificações do cliente).
- Listagem vazia: hoje não mostra nada; passa a mostrar as mensagens acima.
- Card do artista do grupo B: sem data real (diverge da spec; divergência registrada no `06` §1 — não alterar o `02`).

- [DEFINIDO] Sem fluxo novo para quem não acha data no MVP (por exemplo, perfil abrindo na primeira data livre): fica para o futuro.

---

## Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono]

Layout (conforme imagem do app): à esquerda, foto de divulgação (com indicação de que há mais fotos, seta); à direita, foto do artista e nome, descrição curta, nota em estrelas e preço.

- O ofício **não** entra no card: o artista pode ter vários ofícios (por exemplo, barbeiro, cabeleireiro, esteticista).
- Sem horários livres no card (resolve o conflito com D-02 da spec: o card do MVP não mostra horários).
- Futuro: mais itens no card, incluindo card de destaque para planos.

**Aviso de controle de versão:** arquivos 00 a 04 estão congelados (já na base de conhecimento). Mudanças daqui para frente só no 05 em diante. Divergências pós-congelamento (ex.: card do grupo B sem data real) ficam no `06` e neste arquivo.

**Preço no card [DEFINIDO pelo dono]:** o card mostra a faixa de preço que o artista informa no cadastro (valor mínimo e máximo), não um valor calculado por busca. Motivo: calcular o preço do serviço filtrado para cada card encareceria a consulta da listagem. O preço real de cada serviço aparece na etapa de agendamento.
- [DEFINIDO] Faixa de preço do card: digitada pelo artista no cadastro (mínimo e máximo), sem cálculo a partir dos serviços no MVP. Futuro: a faixa do card passa a ser calculada a partir dos preços dos serviços.
- [DEFINIDO, substitui a definição anterior de card sem símbolo] O preço no card segue a regra de moeda aprovada: sempre com "R$", no formato "R$ 10 a R$ 150".
- [DEFINIDO] M02-F02 passa a incluir **preço** em cada serviço (nome, duração e preço), no MVP. O preço de cada serviço aparece ao cliente na etapa de agendamento. A faixa do card continua digitada pelo artista, sem relação automática com os preços dos serviços.

## Registro de detalhamento: M05/M02 Foto de divulgação e tag no card [DEFINIDO pelo dono]

- **Foto de divulgação no MVP: 1 foto por artista.** Sem filtro prévio. O cliente pode denunciar a foto no perfil do artista, e a equipe pode removê-la. Recusa automática inteligente: nos planos, fora do MVP.
- **Futuro:** plano de card destaque permite várias fotos (quantidade a definir). Por isso o card já é desenhado com a seta de galeria; no MVP, com 1 foto, a seta não deve aparecer. [RECOMENDADO]
- **Tag no card:** selo no canto superior direito do card, sobreposto à borda, com ícone e texto (exemplo: "Premium" com coroa, em cor de destaque). A tag "Novo" segue o mesmo visual. Uma tag por card.
- Consequência: a denúncia (M12-F01) passa a poder ter como alvo a foto de divulgação, e o painel (M13) precisa de ação de remover a foto do artista.

## Registro de detalhamento: M05/M02 Descrição curta do card [DEFINIDO pelo dono]

- Limite de **28 caracteres** no MVP.
- Sem moderação prévia. Denúncia e remoção pela equipe, como na foto.

**Decisões fechadas da descrição curta [DEFINIDO pelo dono]**
- Validação de conteúdo no backend: bloqueio de telefone, e-mail, URLs, "@" de redes sociais e tentativa de injeção de script.
- Descrição **não obrigatória**; o app indica que usá-la é o ideal. Sem descrição, o espaço fica vazio, para manter o tamanho padrão entre os cards.
- Risco aceito no MVP: conteúdo impróprio ou contorno da validação (ex.: "arroba", "ponto com", número por extenso). Camadas de segurança entram aos poucos, conforme as releases. Denúncia cobre o resto.

## Pontos para o Bruno (backend) — registrados a pedido do dono

**Itens a implementar pelo Bruno (não esquecer):** lista consolidada; a regra completa continua na seção de origem indicada entre parênteses.

*Listagem e perfil do Artista*
- **"Poucas avaliações":** a API da listagem e do perfil informa explicitamente que o Artista tem poucas avaliações (limite de 3, configurável no backend) e, nesse caso, não envia a nota. O app não conta avaliações nem conhece o limite. ("M05/M02-F05 Perfil do artista visto pelo cliente")
- **Paginação do perfil do Artista:** categorias de 5 em 5, serviços de cada categoria de 5 em 5 e regiões atendidas de 10 em 10, com "ver mais" por consulta. ("M05/M02-F05 Perfil do artista visto pelo cliente")
- **Paginação da listagem:** 10 cards por página, ordem estável por sessão. ("M05 Scroll infinito")
- **Sorteio de desempate mantido ao atualizar** [RECOMENDADO]; renovar só em nova busca ou nova sessão. ("M05 Arrastar para atualizar")
- **Lista sem data:** sem grupos A/B nem checagem de agenda; com data, grupos A/B. ("M05 Filtros e tela \"Pesquisar\"")
- **Chips só com oferta:** categorias e serviços com pelo menos 1 Artista aprovado na região (M05-F02). ("M05 Filtros e tela \"Pesquisar\"")
- **Limite futuro do calendário:** valor configurável no backend, acompanhando o horizonte da agenda do artista. ("M05 Filtros e tela \"Pesquisar\"")
- **Validação de texto livre** (descrição curta e longa; bloqueio de telefone, e-mail, URL, "@" e script; escape na saída) e ações do painel de remover foto e limpar descrição. ("Pontos para o Bruno", notas 1 a 4; "M05/M02 Descrição curta do card")

*Agendamento*
- **Agendamento com o próprio perfil:** o backend valida e recusa, com erro específico, qualquer agendamento em que o Artista seja a mesma identidade do cliente logado (ver "Artista que também é cliente").
- **Horários oferecidos:** só janelas livres >= tempo total estimado (mais deslocamento) [RECOMENDADO]. ("M06 Agendamento do cliente")
- **Pré-agendamento:** estado "pré-agendado" na agenda; retenção de 10 min, uma única extensão de 10 min (20 min no total), liberação no "×" do topo e na expiração; controle e validação no backend. ("M06 Pré-agendamento")
- **Revalidação na confirmação:** artista ativo e sem bloqueio, horário livre, serviços, preços e retenção válida; serviço removido recalcula duração e preço. ("M06 Regras de consistência do agendamento")
- **Confirmação idempotente:** pedido repetido não duplica; após timeout o app consulta o resultado antes de nova tentativa. ("M06 Regras de consistência do agendamento"; "2. Falhas em ações e padrão de mensagens", Timeout)
- **Dados congelados na confirmação:** preço total, serviços, duração, nome do artista e cópia do endereço. ("M06 Regras de consistência do agendamento"; "Endereço de atendimento e troca pela listagem")
- **Número do agendamento (#):** único e sequencial, gerado após a confirmação. ("Registro de detalhamento: Home do cliente")
- **Cancelamento:** registra quem e quando, sem motivo; marca de "cancelamento tardio" (menos de 24 h do início); recusa após o início (hora do servidor); devolve o horário à agenda e envia push ao artista [RECOMENDADO]. ("Cancelamento pelo cliente (M06-F05)"; "M06 Regras de consistência do agendamento")

*Endereço*
- **Endereço repetido:** comparação por CEP, número e complemento, feita no backend. ("Endereço de atendimento e troca pela listagem")
- **Mínimos de validação do endereço** [DEFINIDO para o app; valores exatos ficam com o Bruno, sem bloquear o app]: valores exatos a fechar (recomendação: CEP com 8 dígitos; rua, bairro e cidade com mínimo de 2 caracteres). ("Welcome: slide 5 (endereço)")
- **Campos do endereço salvos separadamente** (CEP, rua, bairro, número, complemento, nome, cidade, UF). ("Cadastro do cliente: formato e dados")

*Avaliação e notificações*
- **Nota:** atraso aleatório de publicação de 24 h a 72 h (`PUBLICACAO_ATRASO_H`), média bayesiana (prior 4,7, peso 10), exibida com n >= 3; prazo de 7 dias para avaliar; check-out automático às 00:00:00. ("Fluxo de avaliação do cliente (M10)")
- **"O Artista não compareceu":** registro e envio à mediação; se a mediação concluir que houve atendimento, o cliente perde o direito de avaliar. ("Fluxo de avaliação do cliente (M10)")
- **Push de avaliação:** no check-out e no dia seguinte às 10:00, agrupado, só com pendência; sujeito ao interruptor "Avaliações". ("Fluxo de avaliação do cliente (M10)")
- **Lembretes:** antecipado às 18:00 do último dia com mais de 24 h e outro 2 h antes; reagendamento 25 dias após o último atendimento concluído; valores configuráveis; não enviar se cancelado. ("Notificações do cliente (M11)")
- **Serviço principal no push:** informar qual é o serviço principal do agendamento (o pré-selecionado na listagem) e a quantidade dos demais. ("Notificações do cliente (M11)")

*Conta, sessão e segurança*
- **Validade do código de recuperação de senha:** 5 minutos, configurável no backend (vale também para "Alterar senha" logado). ("Login e recuperação de senha do cliente")
- **Limites de tentativas:** bloqueio temporário após 5 códigos errados e após 5 senhas erradas no login; reenvio após 60 s; números e tempos configuráveis. ("Login e recuperação de senha do cliente")
- **Link de confirmação de e-mail:** reenvio com intervalo de 60 s; o novo invalida o anterior; expiração. Troca de e-mail: confirmação no antigo, depois no novo. ("Confirmação de e-mail do cliente"; "Editar Perfil do cliente e troca de e-mail")
- **Sessão:** 401 genérico para qualquer perda de autorização; matar o token na troca de senha, no bloqueio e após 2 meses sem acesso; renovar o refresh token após 7 dias. ("Sessão do cliente")
- **Biometria** [a validar]: token do aparelho emitido pelo backend (revogável), nunca a senha. ("Login e recuperação de senha do cliente")
- **Aceite dos Termos:** gravar versão, data e hora. ("Cadastro do cliente: formato e dados")
- **Unicidade:** só CPF e e-mail; celular pode repetir. ("Cadastro do cliente: formato e dados")
- **Exclusão de conta:** bloqueio com agendamento ativo; "conta em processo de exclusão" por 30 dias; reativação no login; depois soft delete só do usuário do app C; gravar motivo, texto livre e desfecho [A CRIAR]. ("Excluir conta do cliente")
- **Soft delete** de todos os dados. ("Endereço de atendimento e troca pela listagem")
- **Bloqueio permanente:** cancelar os agendamentos futuros entre as duas pessoas ao bloquear, remover o Artista da listagem e da busca do cliente, e impedir a abertura do perfil (ver "Bloqueio (M12-F02)").
- **Sanção:** suspensão por tempo indeterminado registrada por conta **e por app**; cancela os agendamentos futuros com push ao outro lado; mensagem só na tentativa de login. ("5. Conta suspensa ou banida pelo backoffice")
- **Denúncia:** ao backoffice com motivo, #, denunciante e denunciado; alvo pode ser a foto de divulgação; sem ação automática. ("Denúncia do cliente (M12-F01)")

*Estados gerais*
- **Versão mínima:** receber versão e plataforma em toda requisição, manter a versão mínima por plataforma e devolver o erro específico com prioridade sobre as demais validações. ("3. Versão mínima do app")
- **Manutenção:** ligada e desligada pela equipe por configuração, com erro específico prioritário. ("4. Fora do ar e manutenção")
- **Hora do servidor:** regras de horário decididas no backend; devolver a hora do servidor nas respostas com prazo [RECOMENDADO, a confirmar]. ("7. Hora do servidor como referência")
- **Valores de carregamento e timeouts** [DEFINIDO para o app; valores exatos ficam com o Bruno, sem bloquear o app]: hoje 30 s para qualquer ação e para o skeleton; valores a fechar com o Bruno, com redução na migração para a nuvem. ("2. Falhas em ações e padrão de mensagens"; "Carregamento inicial das telas (skeleton)")

*Convite*
- **Link do SMS de convite:** um único link curto que redireciona para a loja certa (iOS ou Android), sem aterrissagem e sem cruzar dados; o Bruno escolhe o encurtador e mede o custo real por segmento (ver "Convite ao cliente pela reserva manual do artista").

Notas operacionais (a regra de produto da descrição curta está no bloco acima):
1. Contra injeção de script, a validação textual é só uma camada; a defesa principal é tratar o texto como texto puro ao gravar e ao exibir (escape de saída).
2. A validação da descrição (e qualquer texto livre do artista) fica no backend.
3. A mesma validação vale para qualquer outro texto livre público que surgir (por exemplo, nome exibido); a aplicação em cada módulo é decisão de backend e fica na lista do Bruno (não bloqueia o app).
4. Painel precisa de ação de remover foto e de limpar descrição do artista; a denúncia pode ter como alvo a foto de divulgação e a descrição.

- [DEFINIDO] Foto de divulgação **obrigatória** no cadastro do artista (a foto de perfil também). **Card de artista: fechado.**

## Registro de detalhamento: M05 Scroll infinito [DEFINIDO pelo dono]

- Paginação com ordem estável por sessão (regra da spec, no backend).
- **10 cards por página.** A próxima página carrega quando o usuário chega perto do fim da lista, não só no último card.
- **Carregando próxima página:** indicador de carregamento no rodapé, mantendo os cards já exibidos.
- **Falha ao carregar a próxima página:** cards já carregados permanecem; rodapé mostra a mensagem de falha com a ação "Tentar de novo" (texto aprovado em `07` (Listagem, parte A)). Sem tela de erro substituindo a lista.
- **Fim da lista:** duas linhas, aprovadas em `07` (Listagem, parte A). Vale só para a listagem de artistas; o rodapé da Agenda é revisado no fluxo 9.
- **Scroll infinito: fechado.**

## Registro de detalhamento: M05 Arrastar para atualizar [DEFINIDO pelo dono]

- Atualizar **recalcula a listagem** com o estado atual (ranqueamento, planos, agenda). A ordem **pode** mudar, mas só por mudança real, não por embaralhamento. Exemplos: artista cancelou plano de ranqueamento (sai da lista); comprou plano de ranqueamento (entra); comprou "Subir agora" (sobe); entre outros eventos.
- Motivo: quem atualiza quer ver algo novo ou artistas que passaram a ter plano desde a última consulta.
- **Ponto para o Bruno [RECOMENDADO]:** manter o sorteio de desempate da sessão ao atualizar, para que artistas sem mudança real não troquem de posição por acaso. Renovar o sorteio apenas em nova busca ou nova sessão.
- **Arrastar para atualizar: fechado.**

## Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]

- **Topo da listagem:** logo, ícone de lupa (abre "Pesquisar") e o **endereço de atendimento atual** com ícone de localização, exibido pelo **nome do endereço** (ex.: "Casa") e, se não tiver nome, pela **região** (ex.: "Santana"), nunca pelo endereço completo. Tocar nele abre a modal de troca de endereço (ver "Endereço de atendimento e troca pela listagem").
- **Filtros selecionados no topo da listagem [DEFINIDO]:** quando há filtros aplicados, o topo mostra (1) a **data escolhida** em texto ao lado do logo, junto da lupa (formato e exemplo aprovados em `07` (Listagem, parte B): ícone de calendário, sem rótulo "Data:", ex.: "25 de maio, quarta") e (2) uma **faixa de chips** com os filtros de categoria e serviço aplicados (texto do chip aprovado em `07` (Listagem, parte B); ex.: "Cabeleireiro - Luzes"), logo abaixo e antes da barra do endereço. A faixa rola na horizontal quando os chips não cabem. Sem filtros, a faixa e a data não aparecem. A faixa de chips é **rolável na horizontal e os chips que não cabem aparecem cortados na borda direita**, para dar a sensação de que dá para rolar. Os chips e a data são **só informativos, sem "×"** (evita toque acidental que removeria um filtro): tocar em qualquer chip ou na data tem a **mesma ação da lupa** e abre a tela "Pesquisar" com os filtros preenchidos, onde se remove ou altera e se toca em "Aplicar filtros". Assim a lista só atualiza em "Aplicar filtros". O texto do chip segue o da área "Filtros selecionados" da tela "Pesquisar".
- **Tela "Pesquisar":** campo de texto; chips de ofício; chips de serviços (aparecem abaixo, em cascata, ao selecionar um ofício); área "Filtros selecionados" com chips removíveis (ex.: "Cabeleireiro - Luzes"); calendário "Data do atendimento".
- **Campo de texto:** busca por nome de ofício e de serviço, como atalho para busca por categoria.
- **Data:** data única no MVP.
- **Estado inicial [DEFINIDO]:** usa o endereço de atendimento atual (último escolhido); **sem filtro de data, ofício ou serviço**. O backend traz todos os artistas da região (sem grupos A/B, pois não há data). Os grupos A e B e as mensagens de "sem horário" só valem depois que o cliente escolhe uma data.
- **Sem data, lista única [DEFINIDO]:** sem data escolhida não há grupos A/B nem checagem de agenda; a lista é única, ordenada só pelas faixas de ranqueamento e desempates. Disponibilidade vira filtro condicional à data (mudança sobre a spec). Motivo de negócio: o ranqueamento é o que gera receita; sem filtro específico, a listagem enche a tela de artistas ranqueados.
- **Filtros: fechado, exceto detalhes de UI abaixo se surgirem.**
- **Aplicar filtros [DEFINIDO]:** os filtros só atualizam a lista ao tocar no botão "Aplicar filtros" (abaixo do calendário na tela "Pesquisar"). Não atualiza a cada toque.
- **Campo de texto [DEFINIDO]:** ao digitar, a tela mostra só os chips de categoria e serviço que combinam (na tela o termo é "categoria"; "ofício" é termo interno, ver `07`, regra 9). O texto nunca vira filtro sozinho: o filtro só existe quando o cliente toca no chip. Sem correspondência, aparece a mensagem aprovada em `07` (Listagem, parte B) e os chips ficam sem filtro. Os chips de categoria e serviço seguem M05-F02 (só os que têm pelo menos 1 Artista aprovado na região do endereço de atendimento atual).
- **Calendário [DEFINIDO]:** datas passadas bloqueadas, e hoje bloqueado quando já não houver horário possível. Limite máximo no futuro: **não existe hoje; fica como valor configurável no backend** (deve acompanhar o horizonte em que o artista pode abrir agenda).
- **Limpar filtros e persistência [DEFINIDO]:** a tela "Pesquisar" tem o link "Limpar filtros" (texto aprovado em `07` (Listagem, parte B)). Ao fechar e reabrir o app, a listagem volta ao estado inicial, sem filtros, mantendo o endereço de atendimento atual (que persiste).
- **Artista indisponível [DEFINIDO]:** se o artista ficar indisponível (suspenso, bloqueado ou removido) depois de a lista ou o perfil carregarem, o toque em "Agendar agora" abre a modal aprovada em `07` (Listagem, parte B); o botão "Ver Artistas" volta à listagem recarregada.
- **Artista que também é cliente [DEFINIDO]:** ao tocar em "Agendar agora" no próprio perfil, abre a modal de aviso (texto aprovado em `07` (Listagem, parte B)). **O backend valida e é a fonte da verdade:** ao iniciar o agendamento (pré-agendamento), se o artista do agendamento for a mesma identidade do cliente logado, o backend recusa com erro específico, independentemente do app; o app mostra a mesma modal quando receber esse erro (o app pode checar antes, comparando as identidades, só para poupar a chamada). Vale também para qualquer outra via que crie agendamento.
- **Voltar do perfil do artista [DEFINIDO]:** ao voltar para a listagem, **a lista é recarregada** (o cliente ficou fora um tempo e algo pode ter mudado: plano, exclusão, bloqueio etc.). Mantêm-se os filtros e a posição de rolagem sempre que possível. Risco aceito: o artista que o cliente olhava pode sair da lista. Vale também para o retorno vindo do cadastro pelo balão (a lista é recarregada).

## Registro de detalhamento: M05 Balões de incentivo de cadastro [DEFINIDO pelo dono]

- Frases que convidam o cliente a se cadastrar, com botão "Criar conta". Aparecem **apenas para clientes sem cadastro**.
- Ficam **entre os cards** da listagem, em posição **aleatória**, com **mínimo de 3 cards de distância** entre balões.
- Textos dos 3 balões e do botão "Criar conta": texto aprovado em `07` (Listagem, parte C).
- Visual: ícone de robô roxo sobreposto ao canto superior esquerdo do balão, texto roxo em negrito, botão salmão na borda inferior direita (textos aprovados em `07` (Listagem, parte C)).
- **Ação do botão [DEFINIDO]:** abre o cadastro de cliente; ao concluir, volta à listagem com os mesmos filtros e a mesma posição de rolagem, sem balões (destino de quem veio do balão).
- A listagem ainda não está desenvolvida.
- **Rotatividade [DEFINIDO]:** os textos alternam; o mesmo texto não aparece em dois balões seguidos na mesma lista.
- **Sem dispensar [DEFINIDO]:** não há "X"; o balão é insistente de propósito e some quando o cliente se cadastra.
- **Listagem do cliente: fechada** (cards, scroll infinito, atualizar, filtros, balões).

## Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]

Estrutura da tela no MVP, de cima para baixo (textos aprovados em `07` (Perfil do Artista, parte A)):
- Cabeçalho: seta de voltar com rótulo "Voltar" (no MVP o perfil só é aberto pela listagem); foto grande do artista; nome; estrelas da nota (ou "Poucas avaliações"); descrição curta. Sem idade (ver "Idade removida").
- Ação: botão "Agendar agora". Sem "Compartilhar" (ver "Compartilhar fora do MVP").
- Bloco "Sobre mim": descrição longa com "Ler mais"; cidade; região; "Regiões que atende" (lista parcial com botão "Ver mais"; ver "Sobre mim" abaixo).
- Bloco "Serviços" (roxo): serviços agrupados por categoria, com "Ver mais" (ver "Serviços no perfil"). O título continua "Serviços" ("ofício" nunca aparece na interface).
- Rodapé: "Na WeCareU desde" + mês e ano (o Figma antigo usa "Perfil criado em"); botões "Denunciar Artista" e "Bloquear Artista".
- Barra inferior: 4 abas, sem Favoritos (ver abaixo).
- **Barra inferior [DEFINIDO]:** o Figma mostra Início, Favoritos, Artistas, Agenda, Perfil; no MVP são 4 abas, sem Favoritos (ver "Navegação inferior do cliente").
- **Aviso [DEFINIDO]:** o Figma está desalinhado do MVP. Em caso de divergência, vale o `05`/`06`.
- **Avaliações no perfil [DEFINIDO]:** o perfil mostra **somente as estrelas da nota, sem contagem de avaliações**, junto ao cabeçalho (perto do nome). Uma seção de avaliações é feature futura.
- **"Poucas avaliações" vem do backend [DEFINIDO]:** a API da listagem e do perfil informa explicitamente se o Artista tem poucas avaliações (limite de 3, configurável no backend) e, nesse caso, não envia a nota; o app só exibe o que o backend indicou e **não conta avaliações nem conhece o limite**. Com poucas avaliações (menos de 3) aparece o texto "Poucas avaliações" **no lugar das estrelas** (não é uma tag). O card da listagem segue a mesma regra. Sem lista de avaliações individuais e sem comentário em texto no MVP, só estrelas. **Mudança em relação ao Figma:** a tela não tem a nota.
- **Idade removida [DEFINIDO]:** o perfil não mostra idade; o cadastro do artista não coleta data de nascimento para exibição. **Mudança em relação ao Figma.**
- **Compartilhar fora do MVP [DEFINIDO]:** o botão "Compartilhar" não existe no MVP; feature futura (exigiria link profundo e página pública do perfil). **Mudança em relação ao Figma.**
- **Foto de divulgação no perfil [DEFINIDO]:** não aparece no perfil do artista no MVP (a foto do card é vertical e o topo do perfil é horizontal, o que prejudicaria a imagem). Galeria é feature futura. **Denúncia da foto:** pelo botão "Denunciar Artista", com opção de selecionar a foto como alvo da denúncia.
- **Denunciar Artista [DEFINIDO]:** o botão fica no rodapé do perfil. O fluxo completo está em "Denúncia do cliente (M12-F01)".
- **"Sobre mim" [DEFINIDO]:** campos exibidos: descrição longa (com "Ler mais"), cidade, região, regiões que atende. **"Regiões que atende" [DEFINIDO]:** mostra as primeiras regiões e o botão "Ver mais", que expande **de 10 em 10** (sem "entre outros" e sem reticências). Ao cliente só se exibem cidade e região (no MVP a região é o bairro do CEP); bairro e zona brutos ficam só no cadastro interno. Cidade e região vêm do endereço coletado nos dados pessoais do artista no cadastro. A descrição longa é **opcional**; o cadastro indica que preenchê-la é recomendável. Mesma validação de texto da descrição curta (bloqueio de telefone, e-mail, URL, @ e script, no backend).
- **Futuro [DEFINIDO]:** "perfil completo" como gamificação, com selo de certificado ao preencher todos os campos, como em redes sociais. Por isso o MVP não força o preenchimento de tudo.
- **"Na WeCareU desde" (Figma antigo: "Perfil criado em") [DEFINIDO]:** o perfil mostra mês e ano da **aprovação** do artista (não do cadastro).
- **Serviços no perfil [DEFINIDO]:** o título do bloco continua "Serviços"; os serviços são agrupados por categoria (termo interno: ofício; ver `07`, regra 9). Cada serviço mostra nome, duração e preço. **Cada categoria é expansível e tem o seu próprio botão "Ver mais"** (não há "Ver mais serviços" geral, pois o bloco já é uma caixa). **Paginação do bloco [DEFINIDO]:** aparecem **5 categorias**, cada uma com **5 serviços**; o "Ver mais" de cada categoria carrega **mais 5 serviços**, e o "Ver mais" do fim do bloco carrega **mais 5 categorias** (cada uma também com 5 serviços). O backend precisa paginar nessa mesma medida (ver "Itens a implementar pelo Bruno (não esquecer)"). Os serviços são **apenas informativos**; o agendamento começa só pelo botão "Agendar agora". **Mudança em relação ao Figma** (que ainda mostra "Serviços" no modelo antigo).
- **"Agendar agora" [DEFINIDO]:** leva ao agendamento (M06), detalhado em "Registro de detalhamento: M06 Agendamento do cliente". Texto do botão aprovado em `07` (Perfil do Artista, parte A).
- **Perfil do artista visto pelo cliente: fechado.** O cliente sem cadastro que toca em "Agendar agora" segue o cadastro prévio (ver M06) e a barra inferior segue a navegação do cliente.

## Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO]

- **Formato [DEFINIDO]:** passo a passo em estilo chat bot, **sem inteligência por trás**: perguntas fixas em sequência.
- **Passo 1 (tela do Figma; textos aprovados em `07` (Agendamento em chat, parte A)):** campo "Pesquisar serviços"; chips de filtro; serviços selecionados como chips removíveis ("×"); aviso "Tempo total estimado" dos serviços selecionados; botão "Pronto"; "×" no topo para fechar o fluxo.
- **Pré-seleção [DEFINIDO]:** vem selecionado o **serviço** filtrado na listagem, como chip removível ("×"); o cliente pode adicionar outros, **somente os que aquele artista atende**. Sem copy própria: o chip já selecionado, com o botão "Pronto" já habilitado, basta. **Só vem pré-selecionado se o cliente escolheu um serviço na listagem** (só categoria não pré-seleciona nada).
- **Tempo total estimado [DEFINIDO]:** o aviso passa a se chamar "Tempo total estimado" (era "média"). É a soma das durações cadastradas dos serviços selecionados. A palavra "estimado" é proposital: o tempo real pode diferir (imprevistos no atendimento) e a WeCareU não se responsabiliza pelo horário real. **Mudança em relação ao Figma.**
- **Regra de backend [RECOMENDADO]:** os horários oferecidos são só os de janela livre >= tempo total estimado (mais deslocamento).
- **"Pronto" [DEFINIDO]:** desabilitado enquanto não houver ao menos um serviço selecionado.

### M06 Passo 2: data e horário [DEFINIDO]
- Pergunta do robô: texto aprovado em `07` (Agendamento em chat, parte A). A resposta do passo 1 aparece no chat como mensagem do cliente (serviços escolhidos).
- Em vez de calendário, **cartões por data** (ex.: "25 de maio, quarta"), cada um com **chips de horário livre**; o horário escolhido fica destacado com "×" para desfazer; "Ver mais datas" carrega mais dias.
- **Aviso fixo [DEFINIDO]:** texto aprovado em `07` (Agendamento em chat, parte A). O aviso **não promete avaliação** de quem não compareceu (a avaliação só existe com check-out do Artista); remete ao link "O Artista não compareceu" da Agenda.
- Topo da tela (Figma), **elemento fixo da barra do chat, separado das mensagens** (item próprio em `07` (Agendamento em chat, parte A), C-08-A05): sem lupa no MVP; menu de três pontos e "×". O menu de três pontos abre um menu com "Preciso de ajuda", que leva ao WhatsApp do suporte da WeCareU. Botão "Pronto" ao final.
- O desenho mostra lista de datas com horários (não calendário com dias desabilitados).

### M06 Passo 2: ordem das datas e situações sem horário
- **[DEFINIDO]** Datas em ordem cronológica. Se o cliente escolheu uma data na listagem, ela vem como primeira opção. "Ver mais datas" traz as datas seguintes.
- **[DEFINIDO]** Sem data escolhida na listagem: mostrar as datas de hoje em diante (respeitando a antecedência mínima do artista).
- **Situações sem horário, mensagens e ações [DEFINIDO]:**
  1. Data sem horário, com datas próximas: texto aprovado em `07` (Agendamento em chat, parte A).
  2. Nada na data nem em 14 dias: texto aprovado em `07` (Agendamento em chat, parte A). Ações: "Alterar serviços" e "Escolher outra data".
  3. Sem data escolhida: sem mensagem, datas de hoje em diante.
  4. Sem data e sem horário: texto aprovado em `07` (Agendamento em chat, parte A). Ação: "Ver Artistas".
  As ações só levam a telas já existentes; nenhum fluxo novo no MVP.

### M06 Pré-agendamento [DEFINIDO pelo dono]
- Ao tocar em "Pronto" na escolha de data e horário, o app **pré-agenda** aquele horário (retenção temporária). Se o cliente não finalizar o agendamento, o horário é **liberado**.
- Regra de backend: a retenção e a liberação são do backend.
- **Mudança em relação à spec:** a agenda passa a ter um estado "pré-agendado" (retido), que bloqueia o horário para outros clientes enquanto dura.
- **Retenção do pré-agendamento [DEFINIDO]:** 10 minutos, com contador visível. **Onde fica o contador [DEFINIDO]:** numa **faixa fixa logo abaixo do topo do chat**, que não rola com a conversa (uma mensagem do chat se perderia), visível desde o "Pronto" da data e horário até a confirmação, o "×" do topo ou a expiração. **A faixa não tem "×" próprio** (não pode ser dispensada). **Extensão [DEFINIDO]:** **2 minutos antes de expirar**, o robô envia uma mensagem que **interrompe o fluxo** (aparece no fim do chat, mesmo que o cliente esteja em outro passo) oferecendo **estender por mais 10 minutos** (ação na própria mensagem). **Expiração [DEFINIDO]:** se expirar sem confirmação, o horário é liberado, a faixa some, os botões das mensagens anteriores que dependiam do horário (ex.: "Confirmar agendamento") ficam desativados, e o robô avisa em mensagem que também **interrompe o fluxo**, levando o cliente de volta à escolha de data e horário. Textos aprovados em `07` (Agendamento em chat, parte A).
- **Extensão [DEFINIDO]:** apenas **uma** extensão de 10 minutos (20 minutos no total). Passando disso, o horário é liberado e o cliente recomeça pela escolha de data.
- **Regra de backend [RECOMENDADO]:** retenção e extensão são controladas e validadas no backend; o contador do app apenas exibe.

### M06 Aviso de extensão única e endereço
- **[DEFINIDO]** A mensagem que oferece a extensão deve avisar que **só é possível estender 1 vez**.
- **[DEFINIDO]** O robô **não confirma o endereço** no chat: é dado sensível já selecionado antes (na listagem). Suficiente para o MVP.

### M06 Confirmação do agendamento [DEFINIDO]
- Mensagem do robô e resumo: textos aprovados em `07` (Agendamento em chat, parte A). Cartão com foto e nome do artista, nota, data (formato "25 de maio, quarta"), horário (formato "12h") e serviços escolhidos em chips; legenda "Agendamento confirmado".
- **Resumo da confirmação [DEFINIDO]:** além de artista, nota, data, horário e serviços, inclui o **"Preço estimado"** (só o total, sem valor por serviço; "estimado" porque o preço pode mudar no atendimento e a WeCareU não se compromete com o valor final) e a **região de atendimento**. Logo abaixo do preço, a legenda operacional **"O pagamento é feito direto com o Artista"** (texto aprovado em `07` (Agendamento em chat, parte A), C-08-A21): deixa claro que o pagamento é **fora do app**, direto com o Artista; o detalhe jurídico fica nos Termos (diferidos). A legenda **não** aparece no cartão da Home/Agenda (lá basta o rótulo "Preço estimado"). O mesmo rótulo de preço será conferido no cartão de agendamento no fluxo 9. **Mudança em relação ao Figma.**
- **Confirmação [DEFINIDO]:** o resumo traz o botão "Confirmar agendamento". Ao tocar, os botões somem e aparece a legenda "Agendamento confirmado". No Figma, botões e legenda estão juntos na mesma tela, mas a intenção é essa sequência. O pré-agendamento (10 min + 1 extensão) vale até o toque.
- **Após a confirmação [DEFINIDO]:** mensagem final do robô com a ação "Ver meus agendamentos", que leva à **Agenda** [DEFINIDO; corrige a versão anterior que levava à Home] (não existe tela de detalhe do agendamento, M06-F04 fora do MVP). A permissão de notificações **não é mais pedida aqui** (ver abaixo).
- **Pedido de notificações antes de todo agendamento [DEFINIDO]:** se a permissão de push ainda não foi concedida, o robô pergunta **no início do chat de agendamento** (depois do pedido de foto, se houver, e antes do passo 1), para ganhar destaque; o cliente pode escolher "Agora não" e seguir. Se a permissão estiver negada no aparelho, o botão vira "Abrir ajustes". **Ao escolher "Agora não"** o robô responde com uma mensagem avisando que o cliente só verá os avisos dentro do app (texto aprovado em `07` (Agendamento em chat, parte A)). Risco: repetir em todo agendamento incomoda; **não repetir dentro do mesmo agendamento**. Substitui o pedido depois da confirmação.
- **Cadastro antes do agendamento [DEFINIDO]:** ao tocar em "Agendar agora", o front verifica se o cliente está logado. Se não estiver, vai ao fluxo de cadastro; ao concluir, é **logado automaticamente** (fluxo já previsto) e segue para o fluxo de agendamento. O cadastro nunca ocorre com horário pré-agendado, pois pode levar muito tempo (ex.: 1 hora) e não pode reter agenda. Isso resolve o caso do cliente sem cadastro que ficou pendente na seção do perfil.
- **Retomada após o cadastro [DEFINIDO]:** o app guarda a intenção (artista, serviços e data da listagem) durante o cadastro e, ao concluir, retoma o agendamento do mesmo artista com essas seleções pré-preenchidas.
- **Fluxo de agendamento do cliente (chat): fechado** (serviços, data e horário, situações sem horário, pré-agendamento de 10 min com 1 extensão, confirmação, cadastro prévio).

## Registro de detalhamento: Home do cliente [DEFINIDO]
- Exibida sempre que o cliente entra logado e ao finalizar um agendamento.
- Estrutura (nessa ordem): **Vamos agendar**, **Avalie seu atendimento** (nome funcional "Aguardando avaliação", usado nas regras de M10), **Próximo agendamento** (nome funcional "Próximos agendamentos"; a Home mostra só o próximo). Títulos aprovados em `07` (Home); os títulos da Agenda são revisados no fluxo 9. Seção sem itens fica oculta. Sem agendamento futuro nem avaliação pendente, a home mostra só "Vamos agendar".
- Cabeçalho (Figma, com a lupa removida): logo, saudação "Olá, <nome>!" e foto. **Não há nota do cliente** (não existe nota do lado do cliente no MVP; mudança em relação ao Figma).
- **Foto e nome na Home [DEFINIDO]:** ficam gravados no storage local do aparelho. A Home valida com o backend ao carregar: se mudaram, atualiza o storage; se não, mantém. Por isso a Home **não** usa skeleton para foto e nome.
- Lupas removidas no MVP [DEFINIDO]: a lupa da home e a lupa do topo do chat de agendamento não existem no MVP (a lupa da listagem de artistas, que abre "Pesquisar", permanece).
- **Bloco "Vamos agendar" e seleção de endereço [DEFINIDO]:** o bloco tem um campo "Endereço" **fictício** (na prática um botão com aparência de campo). Ao tocar nele abre um **formulário em modal** com os campos do endereço (CEP, rua, número, bairro, cidade, estado, complemento) mais o **nome do endereço (obrigatório)** e os botões "Salvar" e "Cancelar". "Salvar" **salva o endereço, o torna o endereço de atendimento atual e leva à listagem**. Abaixo do campo fictício fica a **lista dos 2 últimos endereços usados** (só endereços salvos, ordenados pelo último uso, sem marcação do atual), com o botão "Ver mais" dentro da caixa (carrega 5 por vez, abaixo dos já exibidos; o contexto da caixa já deixa claro que são endereços). Tocar em um item da lista o torna o atual e leva à listagem. O cliente pode salvar vários endereços (muda o `04`, que deixava "outros endereços" fora do MVP; registrado no `06`). Edição, exclusão e demais ações ficam em engrenagem > Meus endereços, não na home (ver "Endereço de atendimento e troca pela listagem"). "Ver todos" foi substituído por "Ver mais" dentro da caixa (texto aprovado em `07` (Home)).
- Ícone de olho: os endereços aparecem ocultos (com o nome dado, ex.: "Casa", ou, sem nome, a região, ex.: "Santana"); ao tocar no olho, mostra o endereço completo. Princípio de privacidade visual e regra por tela: ver "Dados sensíveis (olho) por tela [DEFINIDO]".
- Cartão de agendamento (o mesmo na home e na Agenda; o que muda é o que o cliente vê nele conforme o momento): artista (foto, nome, nota), data, horário, serviços, **"Preço estimado"** (só o total, com o mesmo rótulo do resumo do agendamento), "#" + número do agendamento (número único e sequencial, gerado após a confirmação, por isso só aparece depois dela: no cartão e no resumo exibido após confirmar). Menu de três pontos com "Cancelar agendamento" e "Preciso de ajuda" (futuro: "Reagendar" e outras). O cartão não leva a tela de detalhe ao tocar (mudança em relação ao Figma, que não mostra preço nem menu).
- "Preciso de ajuda": serve só para falar com a WeCareU (M12-F03); o agendamento (#) vai identificado. Contato da WeCareU: WhatsApp com mensagem pré-preenchida (inclui o #), sem tela nova no MVP. **[DEFINIDO]** Denunciar é outro item do menu ("Denunciar Artista", M12-F01), nos cartões passados.
- **Comportamento do "Preciso de ajuda" [DEFINIDO]:** (1) no menu de três pontos do chat de agendamento: vai direto ao WhatsApp do suporte. (2) No cartão de agendamento futuro (home e Agenda): vai direto ao WhatsApp com o # preenchido, pois ainda não há o que denunciar. (3) No cartão passado, aguardando avaliação ou cancelado pelo artista: o menu de três pontos tem **dois itens separados**, "Preciso de ajuda" (vai direto ao WhatsApp com o # preenchido, como nos futuros) e **"Denunciar Artista"** (abre a tela de denúncia com o Artista já selecionado e o # anexado), porque a denúncia entrega os dados estruturados ao backoffice (motivo, #, quem é quem) para a mediação. **[DEFINIDO; substitui a escolha intermediária "Falar com a gente / Denunciar"]:** "Preciso de ajuda" e "Denunciar" são coisas diferentes e não ficam atrás do mesmo item.
- **Regra do "Cancelar agendamento" [DEFINIDO]:** o "Cancelar agendamento" só existe até o horário de início do agendamento. Depois disso, o menu do cartão mostra só "Preciso de ajuda", com o comportamento do item (3). Evita cancelar um atendimento que já passou e confusão com as regras de "não compareceu" e de cancelamento em cima da hora.
- Vários agendamentos futuros: a home mostra o próximo agendamento na seção "Próximo agendamento" e o botão "Ver mais agendamentos", que abre a aba Agenda.

### Cancelamento pelo cliente (M06-F05) [DEFINIDO]
- Sem motivo no MVP. O sistema registra quem cancelou e quando (necessário para o futuro). No futuro o cliente poderá ser penalizado por muitos cancelamentos ou por cancelar em cima da hora, definido como até 24 horas antes do atendimento (a spec previa `LIMITE_CANCELAMENTO_TARDIO_H` de 12; o dono definiu 24 para o futuro). Motivo: cancelamento tardio dá prejuízo ao artista, e o artista pesa mais que o cliente para a WeCareU.
- Modal de alerta (componente único de modal do app: título, ×, texto, botão de destaque, botão em texto). Textos e botões aprovados em `07` (Agenda e do cartão de agendamento): destaque "Não cancelar" (caminho seguro) e texto "Cancelar agendamento".
- Ao tocar em "Cancelar agendamento", o app envia ao backend; o modal só fecha com ok do backend. Falha: o modal permanece aberto com o erro aprovado em `07` (Agenda e do cartão de agendamento) e "Tentar de novo"; o cliente nunca deve achar que cancelou sem o backend confirmar.
- Depois do cancelamento, o cartão permanece na home com opacidade reduzida e o texto "Cancelado" no lugar das estrelas até acabar o dia (some) ou o cliente agendar outro horário; depois só no histórico da Agenda. Efeitos no backend [RECOMENDADO]: o horário volta à agenda do artista, push ao artista, registro de quem e quando. Sem reembolso ou remarcação (pagamento fora do app).

### M06 Regras de consistência do agendamento [DEFINIDO]
- **Sobreposição [DEFINIDO]:** o cliente **pode** ter vários agendamentos no mesmo horário com artistas diferentes (ex.: manicure e cabeleireiro) e **pode** agendar com o mesmo artista em horário anterior ou subsequente ao já agendado (ex.: agenda para outra pessoa, como um menor). **Não há bloqueio de sobreposição** do cliente. Pré-agendamentos simultâneos também são permitidos.
- **Limite de agendamentos futuros [DEFINIDO: fora do MVP]:** não há limite de agendamentos ativos por cliente nem por artista. **Risco aceito e reconfirmado pelo dono (2026-11-05):** como o agendamento é instantâneo, sem aceite e sem pagamento, um cliente mal-intencionado pode ocupar a agenda de um artista. Ajuste em atualização futura.
- **Revalidação na confirmação [DEFINIDO]:** ao tocar em "Confirmar agendamento", o backend revalida tudo (artista ativo e sem bloqueio com o cliente, horário ainda livre, serviços, preços, retenção válida). Se o horário ou o artista não estiverem mais disponíveis, o robô avisa (textos aprovados em `07` (Agendamento em chat, parte A), sem o gancho "Algo mudou") e leva de volta à escolha de data. Se o **preço** de um serviço mudou durante o agendamento, o robô informa com texto explicativo (texto aprovado em `07` (Agendamento em chat, parte A)), e mostra o resumo atualizado; **não há segunda confirmação**, pois o próprio "Confirmar agendamento" já vale como aceite do novo valor. Serviço removido: o robô avisa e volta à escolha de serviços.
- **Serviço removido pelo Artista durante o agendamento [DEFINIDO]:** o robô informa e oferece duas ações: **continuar sem o serviço removido** (o horário retido continua válido, pois a duração só diminui; o resumo volta com o "Preço estimado" atualizado) ou **"Alterar serviços"** (libera o horário e volta ao passo 1). Se o serviço removido era o único, só existe "Alterar serviços". O backend recalcula duração e preço.
- **Confirmação idempotente [DEFINIDO]:** toque duplo ou timeout nunca criam dois agendamentos; falha de rede mantém o botão para nova tentativa (padrão de estados gerais).
- **Saída do fluxo [DEFINIDO]:** o "×" do topo libera o horário retido na hora, sem modal de confirmação no MVP. Com o app fechado, o horário só é liberado pela expiração. Ao reabrir, o chat não é retomado: o app volta à listagem.
- **Dados congelados na confirmação [DEFINIDO; regra de backend]:** além do endereço, ficam gravados no agendamento preço total, serviços, duração e nome do artista. Mudanças posteriores do artista (preço, serviço, nome) não alteram agendamentos existentes. Esta regra **mora no backend**.
- **Cancelamento tardio [DEFINIDO]:** o backend registra a marca de "cancelamento tardio" (menos de 24h do início) além de quem e quando. No MVP não há penalização nem aviso na modal de cancelamento; **a modal ganha a mensagem de penalidade quando o sistema de penalidade entrar em vigor**.
- **Artista suspenso, banido ou excluído com agendamentos futuros de clientes [RECOMENDADO, fechar no lado do artista]:** mesmo efeito do cancelamento pelo artista (cancelamento automático, push e cartão "Cancelado" no cliente).

### M10 Falha no envio da avaliação [DEFINIDO]
- Se o envio ao fim do contador de 10 s falhar, o app tenta uma segunda vez em silêncio. Falhando de novo, as estrelas voltam vazias e aparece a mensagem aprovada em `07` (Avaliação). O prazo de 7 dias permite nova tentativa.

## Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO]
- Seções (nomes funcionais; títulos de tela aprovados em `07` (Agenda e do cartão de agendamento): "Avalie seu atendimento", "Próximo agendamento"/"Próximos agendamentos", "Agendamentos anteriores"): **Aguardando avaliação**, **Próximos agendamentos**, **Agendamentos anteriores**, com as mesmas regras de mudança de seção da home; seção vazia fica oculta. Título "Próximo agendamento" com um e "Próximos agendamentos" com mais de um; destaque roxo só no primeiro.
- Próximos: todos os futuros, do mais próximo ao mais distante. Anteriores: do mais recente ao mais antigo, scroll infinito de 10 por página, rodapé com os mesmos estados da listagem de artistas (carregando, erro com "Tentar de novo", fim da lista), com textos próprios aprovados em `07` (Agenda e do cartão de agendamento). Falha ao carregar a Agenda: erro com "Tentar de novo" (mesmo bloco).
- Os cartões seguem o definido na home ("Preço estimado", #, menu de três pontos, o estado "Cancelado" com opacidade, sem nota do cliente). Menu nos futuros: "Cancelar agendamento" e "Preciso de ajuda". Nos passados: "Preciso de ajuda" (WhatsApp com # pré-preenchido) e "Denunciar Artista". [FUTURO] "Reagendar" nos passados: reaproveita artista e serviços do atendimento anterior e abre direto o fluxo de agendamento.
- Estados dos anteriores: avaliado (estrelas dadas), passado o prazo de 7 dias sem avaliar ("Sem avaliação"), cancelado (opacidade, sem avaliar, mantém #), e sem avaliação após "não compareceu". **[DEFINIDO]** "Cancelado" e "Sem avaliação" são textos que ocupam **o lugar das estrelas de avaliação** no cartão, não tags no topo do cartão: reaproveitam o mesmo espaço.
- Lupa do topo removida na Agenda do cliente (existe no Figma porque a tela é compartilhada com o artista; na Agenda do artista a mesma tela terá navegação por dias no topo, a detalhar no lado do artista).
- Estado vazio: texto aprovado em `07` (Agenda e do cartão de agendamento); botão "Agendar agora" que leva à listagem de Artistas.
- Chegada vinda de "Denunciar Artista" (fluxo de exclusão de conta, motivo "Tive um problema com um Artista"): abre uma modal explicando como denunciar (texto aprovado em `07` (Agenda e do cartão de agendamento); ver Excluir conta do cliente).
- Sem tela de detalhe do agendamento no MVP (M06-F04 fora).

## Registro de detalhamento: Aba Perfil do cliente [DEFINIDO]
- Tela do Figma (MVP): logo, engrenagem no topo, foto, nome, bloco "Sobre mim" (no Figma: Cidade, Bairro, Zona, Endereço com reticências e olho; no MVP: Cidade, Região e Endereço, ver abaixo), "Na WeCareU desde" + mês/ano (Figma antigo: "Perfil criado em"), botão que no Figma antigo se chama "Denunciar Perfil" (no app do cliente o vocabulário aprovado é "Denunciar Artista"; nesta tela da visão própria o botão não aparece), barra inferior. O cliente não tem descrição curta (o campo do Figma é do artista). A tela ganhará mais dados no futuro. A engrenagem leva às opções de perfil, app, notificações etc. Textos da aba Perfil aprovados em `07` (Perfil e da engrenagem).
- Visão própria x visão do artista [DEFINIDO]: o artista **só vê o perfil do cliente a partir do agendamento**, e o que ele vê são **dados do agendamento, não do cliente em si**: por exemplo, o endereço daquele agendamento (cópia guardada na confirmação), sujeito ao desbloqueio do endereço (regra do lado do artista, a detalhar). "Voltar para Agendamentos" e o botão de denúncia (no Figma antigo: "Denunciar Perfil"; no vocabulário aprovado do app do cliente: "Denunciar Artista"; rótulo final no app do artista a fechar no lado do artista) aparecem só na visão do artista e ficam ocultos na visão do próprio cliente. Os demais campos do perfil visto pelo artista (nome, foto, "Na WeCareU desde") serão fechados no lado do artista.
- "Sobre mim" do cliente mostra o endereço de atendimento atual (o último escolhido), com cidade e região derivadas dele (só o próprio cliente vê esta tela com esses dados; [DEFINIDO] rótulos Cidade e Região — não Bairro/Zona). **[DEFINIDO]** A aba Perfil mostra só cidade, região e o endereço de atendimento atual com olho para revelar; **não há lista de endereços na aba Perfil**. A lista e o gerenciamento (editar, excluir, nomear; não existe "definir como principal") ficam só em engrenagem > Meus endereços (texto aprovado em `07` (Perfil e da engrenagem); o Figma antigo usa "Gerenciar Endereços"). O artista nunca vê a lista de endereços do cliente.

## Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]
- Estrutura (textos aprovados em `07` (Perfil e da engrenagem)): a tela chama-se "Configurações" (não "Meu Perfil"); Dados pessoais > Editar perfil; Segurança > Alterar senha e interruptor de biometria; Endereços > Meus endereços; Notificações; Ajuda > Central de Ajuda e Sobre o app; Legal > Termos de Uso e Política de Privacidade; "Sair da conta". Novo: "Excluir conta" no fim do menu, em vermelho.
- Editar Perfil: definido (ver seção "Editar Perfil do cliente e troca de e-mail" abaixo).
- Alterar senha [DEFINIDO]: com o cliente logado, usa o mesmo fluxo de código por e-mail da recuperação de senha (tela "Vamos confirmar que é você" mostra o e-mail cadastrado mascarado, envia o código de 5 dígitos (válido por 5 min), depois a tela de nova senha com os mesmos critérios, limites de 5 erros e reenvio após 60 s). Ao finalizar a troca, o cliente é deslogado e enviado à tela de login. Isso também mata o token nos outros dispositivos (regra de sessão).
- Configurações de Notificação **[DEFINIDO]**: com a permissão de push negada no aparelho, o topo da tela mostra o mesmo aviso da home (com o botão que abre os ajustes do aparelho) e os interruptores ficam como estão. Aviso fixo da tela e rótulos aprovados em `07` (Notificações). Estrutura (grupos "Serviços" com Agendamentos e Avaliações e "Geral" com Segurança e manutenção; Promoções e Ofertas oculto no MVP): Agendamentos (lembrete, cancelamento; confirmação fora do MVP) sempre ligado, não pode ser desligado (impacta o artista; muda o Figma, que mostra o botão); Avaliações (lembrete de avaliar) pode ser desligado; Promoções e Ofertas pode ser desligado, oculto no MVP até existir campanha; Sistema (segurança e manutenção) sempre ligado. "Artistas que você segue" removido do MVP (Favoritos está fora do MVP; volta junto com Favoritos).
- Central de Ajuda: hoje aponta para wecareu.app/suporte (página ainda não criada). No MVP abre o WhatsApp da WeCareU com mensagem pré-preenchida, até a página web existir; vale também para o link "Central de Ajuda" em "Sobre o App" (mensagem pré-preenchida aprovada em `07` (Agenda e do cartão de agendamento), C-09-A05). [FUTURO] página web de suporte.
- Sobre o app: mantém versão, descrição e links úteis (textos aprovados em `07` (Perfil e da engrenagem)).
- Termos de Uso e Política de Privacidade: telas desenvolvidas, mas com textos defasados, que não representam a realidade atual. Texto novo é entrega separada, escrito com o advogado: cobrir CPF, endereço, localização e pagamento fora do app. A tela exibe o texto com versão e data da última atualização; o aceite no cadastro registra a versão aceita.
- **Mudança de versão dos Termos e da Política [RECOMENDADO, validar com o advogado]:** no MVP, o aceite registra a versão aceita e, quando o texto muda, a equipe envia e-mail de aviso aos usuários. O **re-aceite obrigatório** (tela que bloqueia o uso até aceitar, com opção de recusar) vale só para mudança relevante (nova finalidade, novo compartilhamento ou novo tipo de dado), sinalizada pelo backend, e é **[FUTURO]**. Base: a LGPD exige informar previamente o titular sobre mudança de finalidade e, quando o uso depende de consentimento, novo consentimento.
- Meus endereços (Figma antigo: "Gerenciar Endereços"): adicionar, editar, remover e nomear; não existe endereço principal. O agendamento guarda uma cópia do endereço na confirmação: editar ou excluir um endereço salvo não altera agendamentos já feitos. Mudança de endereço = cancelar e reagendar. Regras de exclusão no bloco "Endereço de atendimento e troca pela listagem".
- Excluir conta: ver seção própria abaixo. "Sair da conta" já existe e leva ao login **[DEFINIDO]**: antes de sair abre uma modal de confirmação simples (textos aprovados em `07` (Perfil e da engrenagem); botão de destaque "Cancelar", botão em texto "Sair", pela regra do caminho seguro em destaque), para evitar toque acidental.
- Textos das telas de Configurações: aprovados em `07` (Perfil e da engrenagem). Os e-mails transacionais já têm modelos prontos e serão revisados num bloco próprio no fim do `07` ("E-mails transacionais") [PENDENTE — diferido] (ver "Pendências do app do cliente").

## Registro de detalhamento: Navegação inferior do cliente [DEFINIDO]
- 4 abas no MVP: Início, Artistas, Agenda, Perfil. Favoritos fora do MVP (o Figma mostra 5; Favoritos é removido).
- Logado: a barra aparece sobre todas as páginas. Deslogado: a barra aparece ao chegar na listagem; ao tocar em aba que exige login (Início, Agenda, Perfil), abre a tela de bloqueio (título, subtexto, botão "Criar conta" e link "Já tenho conta": texto aprovado em `07` (Listagem, parte C)).
- Após concluir cadastro ou login pela tela de bloqueio, o cliente vai para a listagem de artistas, não para a aba tocada (Início e Agenda estariam vazios para um cliente novo; a listagem é onde há utilidade). No fluxo de agendamento é diferente: retoma o artista e as seleções.
- Aba Artistas (logado): abre a listagem sem filtros, com o endereço de atendimento atual (o último escolhido) do cliente. Deslogado, a aba Artistas fica livre.
- O deslogado só chega à listagem passando pelo welcome, que pede o endereço; ao logar ou cadastrar, o endereço já existe e vira o endereço salvo e o endereço de atendimento atual. Sem pergunta extra de endereço na listagem.

## Endereço de atendimento e troca pela listagem [DEFINIDO]
- **Não existe "endereço principal".** O app trabalha com o **endereço de atendimento atual: sempre o último endereço escolhido** pelo cliente (na home, na listagem ou no welcome/cadastro). Motivo: o cliente não precisa entender nem gerenciar uma feature de "principal"; a lista de endereços salvos serve só para reutilizar.
- **Persistência:** o endereço de atendimento atual permanece ao fechar e reabrir o app, até o cliente escolher outro. Vale também para o deslogado (inicia com o endereço do welcome).
- **Troca pela listagem [DEFINIDO]:** ao tocar no endereço do topo abre uma **folha inferior com o mesmo bloco da Home** (campo fictício + lista dos 2 últimos endereços salvos com "Ver mais", olho para ver o endereço completo), em vez de uma modal sobre outra modal; tocar no campo fictício abre o mesmo formulário. **Deslogado:** o formulário **não tem nome nem lista**, e o botão é "Usar este endereço" no lugar de "Salvar"; o endereço vale só para a listagem (quem se cadastrar depois informa o endereço de novo no cadastro).
- **Exibição por nome:** no topo da listagem e na modal aparece o nome do endereço; endereço sem nome aparece oculto pela região (ex.: "Santana"), e o olho revela o endereço completo, igual na home.
- **Efeito da troca:** muda o local de atendimento da listagem e dos agendamentos feitos a partir dela; os filtros de ofício, serviço e data são mantidos e a lista é recalculada; se a nova região não tiver artistas valem as mensagens de lista vazia já definidas.
- **Como funciona a pesquisa de endereço [DEFINIDO]:** na Home e na modal da listagem, a pesquisa é **por CEP**, o mesmo componente e as mesmas regras do welcome (slide 5) e do cadastro: CEP com 8 dígitos, consulta ao CEP, e, quando o CEP não traz rua ou bairro, o cliente informa manualmente. Não existe busca por texto livre nem sugestões ao digitar no MVP (exigiria provedor pago; fica como [FUTURO]).
- **Validação:** igual à da home: CEP inválido ou não encontrado gera mensagem de erro no formulário. O erro é "Não encontramos esse CEP" (texto aprovado em `07` (Home)).
- **Todo endereço novo do cliente logado é salvo [DEFINIDO]:** não existe endereço usado sem salvar para o cliente logado. O endereço entra pelo formulário (Home ou folha da listagem) com nome obrigatório e "Salvar"/"Cancelar"; complemento é opcional e só obrigatório quando o número é 0. Por isso o **chat de agendamento não pergunta nada sobre endereço** (nem complemento, nem nome, nem "quer salvar?"); o bot segue sem confirmar o endereço. Decisão do dono: elimina codificação desnecessária.
- **Endereço repetido [DEFINIDO]:** se o cliente tenta salvar um endereço igual a um já salvo (mesmo CEP, número e complemento), o app **não cria um segundo e avisa o cliente** (mensagem dentro do formulário, acima dos botões, apenas informando que o endereço já existe, sem citar o nome do endereço salvo, para não exigir consulta extra no app ou no backend); o formulário permanece aberto e o cliente pode cancelar e escolher o endereço na lista. O app não assume nem troca o endereço sozinho. Regra de comparação a cargo do backend.
- **Excluir endereço [DEFINIDO]:** só é possível em **Perfil > Meus endereços**, nunca pela home ou pela listagem. O cliente **não pode ficar sem endereço**: no último endereço salvo, a opção de excluir abre a modal aprovada em `07` (Perfil e da engrenagem). Se o endereço excluído é o atual, o atual passa a ser o endereço salvo mais recente que restar.
- **Endereço vinculado ao agendamento [DEFINIDO, backend]:** o endereço fica salvo **vinculado ao agendamento** (cópia na confirmação), de forma que, mesmo se o endereço do cliente for editado ou excluído, ele **não sai do histórico** de agendamentos. O artista vê o endereço do agendamento, não o cadastro do cliente.
- **Soft delete e LGPD [DEFINIDO, backend]:** todos os dados são tratados com soft delete: nada é apagado de verdade pelo app. Quem quiser a eliminação conforme a LGPD precisa pedir ao suporte.
- **Impactos:** removido "definir como principal" do Perfil e de Meus endereços; o agendamento continua guardando uma cópia do endereço na confirmação.

## Dados sensíveis (olho) por tela [DEFINIDO]

**Princípio [DEFINIDO]:** dados sensíveis ficam ocultos por padrão em todo o app, com o olho para revelar. O olho de senha (mostrar/ocultar) é outro mecanismo e continua só nos campos de senha.

**O que conta como sensível [DEFINIDO]:**
- Sensível: endereço completo (rua, número, complemento, CEP), CPF, e-mail, celular, sexo e data de nascimento.
- Não sensível: nome do endereço ("Casa"), cidade, região, nome exibido (nome social ou primeiro nome), foto, dados públicos do Artista, cartão de agendamento (Artista, data, horário, serviços, preço, #).

**Máscara padrão [DEFINIDO]:**
- Endereço: mostra o nome ("Casa") ou, sem nome, a região ("Santana"); o olho revela o completo.
- CPF: `***.***.***-**` com olho.
- E-mail: `m***@gmail.com` (já usado em "Vamos confirmar que é você" / Alterar senha).
- Celular: `(11) 9****-****` com olho.
- Sexo e data de nascimento (cadastro em chat e telas equivalentes): **100% ocultos** — a bolha ou o campo mostra só o ícone de olho (como no Figma); ao tocar no olho, revela o valor.
- Senha: bolinhas, com olho de mostrar/ocultar.

**Estado do olho [DEFINIDO]:** o olho é **por item** e **por sessão de tela**. Ao sair da tela, volta a ocultar (não grava "sempre revelado"). Depois de revelar, **timeout de 5 segundos** volta a ocultar sozinho.

**Por tela [DEFINIDO]:**
- **Home:** lista dos 2 últimos endereços e o campo atual com olho. Cartões de agendamento **sem olho** (o endereço não aparece no cartão).
- **Listagem (topo e folha):** topo mostra nome ou região, sem olho. Folha com a lista: olho igual ao da Home.
- **Aba Perfil:** Cidade e Região visíveis. Endereço de atendimento atual com olho. Sem lista de endereços nesta aba.
- **Meus endereços (engrenagem):** cada linha com nome visível e endereço mascarado com olho. No formulário de editar, os campos vêm preenchidos e legíveis (a pessoa está editando).
- **Cadastro em chat:** CPF, nome completo, celular, endereço e e-mail mascarados no histórico, com olho. Sexo e data de nascimento 100% ocultos (só o ícone). Nome social e foto visíveis. Senha com olho de mostrar/ocultar.
- **Login, recuperação e Alterar senha:** e-mail mascarado na tela "Vamos confirmar que é você". Campo de senha com olho de mostrar/ocultar. Sem outro olho.
- **Editar perfil:** CPF só leitura, mascarado com olho. E-mail e celular mascarados com olho até tocar no campo para editar. Sexo e data de nascimento com olho. Nome completo (só leitura), nome social e foto visíveis.
- **Chat de agendamento e resumo:** sem endereço e sem olho (o robô não confirma o endereço). Cartão da confirmação sem endereço.

## Pendências do app do cliente [ATUALIZADO]
**Fechamento do app do Cliente [DEFINIDO]:** o detalhamento de produto do app do cliente para o MVP está **fechado**. Skeleton, dados sensíveis (olho), copy de tela (16 fluxos + C-08-A21) e a legenda de pagamento fora do app no resumo estão concluídos. A releitura de fechamento (`wecareu-releitura-fechamento-cliente.md`) não encontrou lacuna bloqueante; os riscos R1–R8 foram **reconfirmados** pelo dono (mantidos).
Itens diferidos (entram na base de conhecimento assim; **não bloqueiam** o início do lado do Artista):
- [PENDENTE — diferido, entra na base de conhecimento] Textos legais: Termos de Uso e Política de Privacidade, com o advogado (ver "Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO]"). Não bloqueia o detalhamento do app do cliente nem o início do lado do Artista.
- [PENDENTE — diferido, entra na base de conhecimento] Bloco de e-mails transacionais (já há modelos prontos): entra como bloco próprio no fim do `07` ("E-mails transacionais"). Não bloqueia o detalhamento do app do cliente nem o início do lado do Artista.
Próximo bloco (lado do Artista; fora do fechamento do Cliente):
- [PENDENTE] Lado do Artista: "Bloquear cliente" (tela, botão e modais de confirmação, resultado e falha) no app do artista (ver "Bloqueio (M12-F02) [DEFINIDO]").
- [PENDENTE] Revisão do lado do Artista (Agenda do artista com navegação por dias, desbloqueio de endereço, check-in/check-out, SMS OTP do prestador, exclusão no app P etc.).

## Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]
- Quem avalia e quando: o cartão de agendamento é o mesmo (não existe card de avaliação separado); o que o cliente vê muda conforme o momento. Antes e durante o horário do serviço: cartão em "Próximos agendamentos". 30 minutos após o fim do horário previsto, sem check-out: continua em "Próximos"; aparece "O Artista não compareceu" no rodapé, sem estrelas. 30 minutos após o fim, com check-out: aparecem as estrelas para avaliar e "O Artista não compareceu" no rodapé.
- A avaliação (estrelas) só aparece se houver check-out do artista (check-out é o status "finalizado"). O link "O Artista não compareceu" aparece em ambos os casos, no rodapé do cartão (longe das estrelas, para evitar toque acidental), na home e na Agenda, 30 minutos após o fim previsto (ex.: previsto até 13:30, aparece às 14:00), sem exigir status finalizado.
- Seção "Aguardando avaliação": com o check-out, o cartão sai de "Próximos agendamentos" e vai para "Aguardando avaliação". Sem check-out, o cartão fica em "Próximos" até a meia-noite e depois sobe para "Aguardando avaliação" (o check-out automático, às 00:00:00, o levaria para lá de qualquer forma). Sai de "Aguardando avaliação" quando a avaliação é enviada, o "não compareceu" é confirmado ou passam 7 dias do fim do atendimento; vai então para os anteriores.
- Envio: toque simples nas estrelas (1 a 5), sem botão de confirmar. Abaixo, contador de 10 segundos com aviso (texto aprovado em `07` (Avaliação)). Cada novo toque reinicia os 10 segundos e altera a nota. Se o cliente não tocar mais ou trocar de página, o envio dispara ao backend. Em segundo plano o contador continua; app fechado nos 10s: nada é enviado e o cliente fica sem avaliar (aceito).
- Depois do envio: o cartão mostra "Obrigado pela avaliação" por alguns segundos e a nota fica nas estrelas do cartão; a nota não pode ser alterada (evita pressão do artista sobre o cliente). Só estrelas, sem texto, no MVP. Uma nota por agendamento no MVP (o tratamento por serviço ou critério fica em aberto para o futuro). Prazo de 7 dias; passado o prazo, "Sem avaliação" na Agenda e avaliação indisponível.
- Cancelado não gera avaliação e não entra no cálculo. Cancelado pelo artista também segue assim.
- Sigilo: o artista vê só a nota agregada (média e quantidade), nunca a individual nem quem avaliou. A nota só entra na média depois de atraso aleatório de 24h a 72h (`PUBLICACAO_ATRASO_H`), para o artista não deduzir quem avaliou mal. Nota bayesiana (prior 4,7, peso 10), exibida com n ≥ 3.
- Modal "O Artista não compareceu?" (padrão de alerta): textos aprovados em `07` (Avaliação); botão de destaque "Voltar", botão em texto "Sim, não compareceu". O modal só fecha com ok do backend; em falha mostra o erro dentro da modal e o cliente toca de novo no botão. Ao confirmar: gera registro e vai para a mediação; o cartão fica sem avaliação nos dois desfechos (nunca há avaliação retida).
- Depois de confirmar: abre outro modal de agradecimento (texto aprovado em `07` (Avaliação)) com botão único "Fechar". O cartão vai para "Agendamentos anteriores" apenas como sem avaliação, sem tag "em análise", sem resposta da mediação e sem mostrar resultado ao cliente (evita confusão; o resultado fica só no backoffice). Se a mediação concluir que o atendimento aconteceu após o cliente ter clicado em "não compareceu", o cliente perde o direito de avaliar (anti má-fé) e o cartão fica sem estrelas. Impacto: backoffice e penalização futura do cliente.
- Push de avaliação (sujeitos ao toggle "Avaliações"): (1) no check-out (ou no fechamento automático à meia-noite); (2) no dia seguinte às 10:00, agrupado, uma única frase para 1 ou mais pendentes, só se houver avaliação pendente (se o cliente avaliou ou confirmou "não compareceu" antes, não sai). O toque abre a Agenda no cartão a avaliar. Textos aprovados em `07` (Notificações).

## Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]
- Não há tela, centro ou histórico de notificações no app no MVP: apenas push (e as seções da home e da Agenda). Tela de histórico é futura.
- Push de confirmação do agendamento: fora do MVP (geraria mais uma tela de confirmação).
- Textos dos pushes aprovados em `07` (Notificações). O lembrete antecipado cita o serviço principal e a quantidade dos outros ("Corte feminino e mais 2 serviços"), sem falar de cancelamento: o push apenas lembra do agendamento, não incentiva cancelar. **[Para o Bruno]** o backend precisa indicar qual é o serviço principal do agendamento (o escolhido na listagem, pré-selecionado) e a quantidade dos demais, para montar o texto.
- Lembrete do atendimento (no MVP, dois pushes): um antecipado e um 2 horas antes. O antecipado sai às 18:00 do último dia em que ainda haja mais de 24h até o atendimento, para o cliente poder cancelar sem cair em "em cima da hora" (ex.: atendimento quinta 10:00, push terça 18:00; quinta 20:00, push quarta 18:00). Agendamento feito com menos de 24h de antecedência não recebe o antecipado. O de 2h só sai se houver mais de 2h de margem ao agendar. Valores configuráveis no backend; não enviados se cancelado.
- Cancelamento pelo artista (obrigatório, no MVP; segue à risca o cancelamento pelo cliente): push com artista, data e hora do atendimento cancelado, em tom de desculpa, sem oferta de escolher outro horário (nada de reagendar pelo push). O toque abre a home, onde o cartão aparece com opacidade reduzida e o texto "Cancelado" no lugar das estrelas até o fim do dia ou até o cliente agendar outro horário; depois vai aos anteriores como "Cancelado", sem avaliação. Texto aprovado em `07` (Notificações).
- Lembrete mensal de reagendamento, versão 0 (MVP): push que lembra o cliente de agendar de novo e abre a home (traz o cliente de volta e lembra da existência do app no começo). Dispara 25 dias após o último atendimento concluído (a antecedência permite ao cliente se planejar), um push por atendimento, só se não houver agendamento futuro; regra e valor configuráveis no backend; texto aprovado em `07` (Notificações). Versão 1 (futura): o toque abre o fluxo de agendamento já preenchido com artista e serviços da última vez, junto com o "Reagendar".
- Permissão de push negada: a home mostra um aviso fixo acima das seções (texto aprovado em `07` (Home); botão "Abrir ajustes") com botão que abre os ajustes do aparelho; some quando a permissão é concedida. Motivo: cancelamento pelo artista e lembretes protegem o artista.
- Copys dos pushes e das Configurações de Notificação: aprovadas em `07` (Notificações).

## Registro de detalhamento: M01 do cliente (welcome, cadastro, login, senha, sessão, conta) e início de M12 (denúncia e bloqueio)
Todas as telas e textos abaixo são do app do cliente. As copys de tela estão aprovadas em `07` (catálogo; o `05` aponta o bloco). O welcome foi planejado do zero pelo dono, sem partir do que existia no Figma, para não criar viés.

### Welcome do cliente: estrutura [DEFINIDO]
- Logo da empresa fixa no topo.
- Carrossel (onboarding) com **5 slides**: 3 de apresentação (cada um com imagem, título e subtítulo), 1 de solicitação de localização (penúltimo) e 1 de endereço (último). Não usar fotos reais (exigiria pagar modelo): usar ilustração, ícone ou desenho.
- Cada slide tem o botão "Próximo"; o último tem "Ver Artistas" (textos aprovados em `07` (Welcome)).
- Fora do carrossel, abaixo: a frase fixa "Já tenho conta", que leva à tela de login (a tela de login tem também "Criar conta").
- Sem botão voltar. Com indicadores de página (bolinhas) e swipe entre slides.
- O welcome aparece só para quem nunca entrou no app (deslogado). Logado abre direto na home. Deslogado pelo servidor vê a tela de login. "Sair" voluntário leva ao login, não ao welcome.
- Não existe trava nem validação de região, nem existirá (existe apenas marketing por região). Qualquer endereço válido libera "Ver Artistas"; a listagem trata a falta de artistas com as mensagens de erro já definidas.

### Welcome: slides de apresentação [DEFINIDO]
- Slide 1 (por que o prestador é chamado de Artista; enaltece a profissão): imagem de ilustração. Título e subtítulo: texto aprovado em `07` (Welcome). Ideias de base do dono: o que uma manicure faz pintando uma unha é arte (tanto que "nail design" hoje leva o nome de design); o cabeleireiro pega algo "feio" e transforma em "belo", que é a essência do artista. O tom deve ser de um amigo contando para outro, não de propaganda de jornal.
- Slide 2 (facilidade de agendamento): ícones em 3 passos (escolher, marcar, receber). Título e subtítulo: texto aprovado em `07` (Welcome).
- Slide 3 (confiança): título e subtítulo aprovados em `07` (Welcome). (Evita citar avaliações, porque a nota só aparece com 3 ou mais avaliações.)

### Welcome: slide 4 (localização) [DEFINIDO]
- Ícone de pino de mapa. Título e subtítulo: texto aprovado em `07` (Welcome).
- Botão "Próximo": ao tocar, abre a permissão de localização do sistema.
- Se a permissão for negada, o botão continua "Próximo" (sem beco sem saída) e o cliente cai no slide 5 com os campos vazios.
- **Sem link "Prefiro digitar o endereço" [DEFINIDO]:** não existe atalho para pular o pedido de permissão; quem nega é porque não quer, e o fluxo segue igual ("Próximo" e slide 5 com campos vazios). Depois do welcome nada no app depende da localização do aparelho: todo endereço novo é pesquisado ou digitado, e a home valida o endereço pesquisado e mostra mensagem de erro quando ele é inválido.

### Welcome: slide 5 (endereço) [DEFINIDO]
- Título e botão "Ver Artistas": texto aprovado em `07` (Welcome). Botão desabilitado até haver endereço completo válido.
- Campos (rótulos aprovados em `07` (Welcome)): CEP, Rua, Número, Bairro, Cidade, Estado, Complemento, Nome do endereço.
- Preenchidos pela localização do aparelho quando houver (a localização já traz o CEP e abre os campos desbloqueados). Todos os campos são sempre editáveis (a localização pode ter pegado a rua ao lado).
- Sem CEP válido, os demais campos ficam bloqueados: o cliente precisa digitar um CEP válido. Com CEP válido, rua, bairro, cidade e estado são preenchidos e todos passam a ser editáveis. CEP inválido ou não encontrado: mensagem no campo aprovada em `07` (Welcome) e o resto continua bloqueado.
- Validação e trava de entrada, com mínimos (valores exatos ficam com o Bruno, ver lista do Bruno; o app segue a recomendação; recomendação: CEP com 8 dígitos e máscara; rua, bairro e cidade obrigatórios com mínimo de 2 caracteres). Estado: select nativo com a sigla de 2 letras (UF), preenchido pelo CEP e editável. CEP e número usam o teclado numérico nativo.
- Número: obrigatório, só dígitos (letras vão para o complemento). Sem número, o cliente digita 0. O app não altera o valor: se o número for 0, mostra a observação "Ver complemento" ao lado (texto aprovado em `07` (Welcome)) e o complemento se torna obrigatório. A observação vale no welcome, em "Meus endereços" e na cópia do endereço no agendamento (visão do artista).
- Complemento: opcional (obrigatório se o número for 0). Nome do endereço: opcional, com "Casa" sugerido (texto aprovado em `07` (Welcome); ex.: "Casa", "Trabalho").

### Cadastro do cliente: formato e dados [DEFINIDO]
- Formato: conversa estilo chatbot, mais amigável (bot pergunta, o cliente responde por um campo de mensagem, com botões de escolha quando aplicável). Erros aparecem acima do campo de mensagem (ex.: "CPF inválido"). Dados sensíveis no histórico do chat seguem "Dados sensíveis (olho) por tela [DEFINIDO]": CPF, nome completo, celular, endereço e e-mail mascarados com olho; sexo e data de nascimento 100% ocultos (só o ícone de olho na bolha, como no Figma); nome social e foto ficam visíveis; senha com olho de mostrar/ocultar.
- Entrada: quem chega pelo welcome vai à listagem sem cadastro; o cadastro é pedido ao tocar em aba bloqueada ou ao agendar. A tela de login tem o botão "Criar conta" (quem clica em "Já tenho conta" cai no login e pode ir ao cadastro de lá).
- Dados, nesta ordem: 1) CPF (obrigatório, validado); 2) nome completo (mín. nome e sobrenome); 3) celular (11 dígitos com DDD: DDD + 9 + 8 dígitos, com máscara; coletado, sem SMS OTP no MVP por custo); 4) sexo (botões: Masculino, Feminino, Não binário, Prefiro não dizer); 5) nome social (opcional, botão "Pular" para quem não tem); 6) data de nascimento (mín. 18 anos; no futuro haverá versão infantil, no MVP não vale; erro de idade: texto aprovado em `07` (Cadastro, parte A)); 7) foto (botões "Depois" e "Sim"); 8) endereço (se veio do welcome, o bot pergunta se quer cadastrar aquele endereço; depois pergunta se tem complemento, qual é, e que nome dar ao endereço, ex.: "Casa"; se não veio do welcome, é pedido); 9) e-mail (usado para entrar na conta, é o username); 10) senha + repetir senha; 11) aceite dos termos de uso e da política de privacidade.
- Critérios da senha (checklist visível): mínimo 8 caracteres, 1 número, 1 letra minúscula, 1 letra maiúscula, 1 símbolo (! @ # $ % * ( ) } { + = | / ? \ -).
- **Aceite dos termos [DEFINIDO]:** uma única caixa obrigatória com dois links ("Termos de Uso" e "Política de Privacidade"), que abrem as telas de Legal sem perder o cadastro. O backend grava versão, data e hora do aceite. Marketing não entra no MVP (promoções ocultas); quando houver campanha, o consentimento de marketing será uma caixa separada e opcional.
- **Menor de 18 anos [DEFINIDO]:** mensagem de erro no campo e o cadastro não segue (texto aprovado em `07` (Cadastro, parte A)). Nada do menor é enviado ao backend (o CPF só é checado no passo 1). **A regra de 3 dias de dados guardados não se aplica:** esse cadastro não será retomado, e os dados guardados no aparelho são apagados.
- **Sem passo de conferência [DEFINIDO]:** não há tela extra para conferir CPF e nome antes de concluir (o CPF inválido não passa, e erro no nome completo é corrigido pelo suporte); o cadastro já é extenso.
- **CPF ou e-mail de conta em processo de exclusão [DEFINIDO]:** durante os 30 dias o cadastro com o mesmo CPF ou e-mail cai na modal "já cadastrado", depois no login, e o login reativa a conta (regra de Excluir conta). Conta suspensa ou banida segue o item 5 dos estados gerais.
- Finalidade dos dados extras (sexo, nome social, nascimento, foto): entender o público que entrou no app, onde melhorar no marketing e facilitar a verificação do cliente no futuro.
- Unicidade: só CPF (identificador único de pessoa) e e-mail (username) são únicos; o celular pode se repetir entre contas. A chave de validação do cadastro é o CPF; celular e e-mail são usados, junto com o CPF, para validar a conta (sem SMS OTP no MVP). No futuro: autenticação facial e coleta de documento.
- Modal "CPF já cadastrado" e modal "e-mail já cadastrado" (padrão de alerta; Figma antigo): textos e botões aprovados em `07` (Cadastro, parte A); botão de destaque "Entrar" (leva ao login) e botão em texto "Tentar de novo" (no caso de e-mail, "Usar outro e-mail"). Não revela dados da conta. Existe modal equivalente para CNPJ, que é do lado do artista.

- **Endereço no cadastro em campos separados [DEFINIDO]:** o cadastro (sem welcome ou quando o cliente toca em "Usar outro") pede o endereço por **CEP como busca**; o app preenche rua, bairro e cidade, e o bot pergunta número, complemento e nome do endereço. Rua e bairro só são perguntados à mão quando o CEP não os traz, sempre antes do número. CEP, rua, bairro, número, complemento, nome, cidade e UF são salvos **separadamente** no backend. O link "Alterar CEP" permite refazer a busca. Textos: ver `07`, "Textos finais aprovados do Cadastro, parte A".
- **Aceite junto da senha [DEFINIDO]:** a caixa de aceite aparece na mesma mensagem da senha (sem passo separado) e o cadastro **não conclui sem ela marcada**. Substitui a posição "passo 11" da lista acima; o restante da regra do aceite permanece.

### Cadastro do cliente: foto [DEFINIDO]
- No cadastro o bot pergunta se o cliente quer subir uma foto de perfil (botões "Depois" e "Sim"), com aviso explicando por que é obrigatória para agendar (texto aprovado em `07` (Cadastro, parte B); substitui o "por questões de segurança" do Figma, que soa vago). Motivo da obrigatoriedade: facilitar o Artista a encontrar, identificar e lembrar do cliente.
- O aviso explicando a foto vem **antes** da escolha, na mesma mensagem do bot, acima de "Depois" e "Sim". Quem escolhe "Depois" segue o cadastro sem nova insistência. Textos aprovados em `07` (Cadastro, parte B).
- Quem pulou ("Depois") precisa enviar a foto para agendar: no chat de agendamento, o pedido da foto é a primeira mensagem enviada pelo bot e **não tem opção "Depois"** (texto aprovado em `07` (Cadastro, parte B / Agendamento em chat, parte A)). Sem foto não há agendamento.
- Modal "Enviar foto" (do Figma, vale também para o cliente; usado ao escolher a foto): título, textos, dica, opções de origem e estados do botão "Salvar"/"Cancelar" aprovados em `07` (Cadastro, parte B). O texto original do Figma ("fica visível a todos", "aparecer para os clientes e receber agendamentos") é do artista e não serve ao cliente.

### Cadastro do cliente: retomada e conclusão [DEFINIDO]
- As respostas ficam salvas no armazenamento seguro (secure storage) do aparelho, exceto a senha, que o cliente preenche de novo. Ao reabrir, o bot cumprimenta e retoma na próxima pergunta sem resposta, com o histórico mascarado.
- Validade dos dados guardados: 3 dias. Passado o prazo, são apagados e o chat recomeça do zero. Também são apagados ao concluir o cadastro.
- Conclusão: mensagem final de boas-vindas do bot e logado automaticamente. Destino conforme a origem: quem veio do welcome, do login ou da tela de bloqueio da navegação vai à listagem de artistas; quem veio de "Agendar agora" retoma o agendamento do mesmo artista, com serviços e data pré-selecionados (a intenção é guardada durante o cadastro, e o cadastro nunca ocorre com horário pré-agendado, porque pode demorar e não pode reter agenda). O e-mail de verificação chega em segundo plano.
- O cadastro do **artista será diferente** (retomada, fluxo e conclusão): tratar na etapa do artista.

### Confirmação de e-mail do cliente [DEFINIDO]
- O e-mail é apenas coletado no cadastro e a conta é liberada na hora. Depois chega um e-mail com link para confirmar (disparo de e-mail é gratuito).
- Ao clicar no link com o cliente logado e o link válido: o app abre e mostra um modal com a mensagem de e-mail confirmado e o botão "OK" (textos desta seção aprovados em `07` (Cadastro, parte B)).
- Link expirado: modal com "Reenviar e-mail de confirmação".
- Cliente deslogado ou com sessão expirada ao clicar: vai ao login e depois à home; precisa clicar de novo no link do e-mail.
- Cliente com e-mail não confirmado vê um aviso no topo da home, abaixo da foto e do nome, com botão "Reenviar e-mail" (intervalo de 60 s entre reenvios; o e-mail novo invalida o link anterior). O aviso não pode ser dispensado e, ao confirmar o e-mail, **some por completo** (aviso, botão e contagem de espera). **Não exibe o e-mail do cliente** (quem quiser vê em Perfil > configurações). A região também serve a alertas futuros.

### Login e recuperação de senha do cliente [DEFINIDO]
- Tela de login (Figma antigo; textos finais aprovados em `07` (Login e recuperação de senha)): logo, título, campos E-mail e Senha, botão "Entrar" (estados habilitado/desabilitado), link "Esqueci minha senha", "Criar conta" (substitui "Cadastrar" do Figma), "Voltar". Erro de login: mensagem única acima do campo, sem indicar se errou o e-mail ou a senha (texto aprovado em `07`).
- Recuperação de senha em 3 passos (Figma antigo; textos finais aprovados em `07` (Login e recuperação de senha)), por **código** (o link por e-mail é só para confirmar o e-mail do cadastro): passo 1 (e-mail + "Enviar código"/"Cancelar"); passo 2 (código de 5 dígitos, validar/reenviar/cancelar/voltar); passo 3 (nova senha + "Alterar senha").
- **Ações dos botões na recuperação de senha [DEFINIDO]:** "Cancelar" sai do fluxo e leva ao login em qualquer passo. "Voltar" volta um passo e existe só nos passos 2 e 3 (no passo 1 seria redundante com "Cancelar", então o passo 1 tem só "Enviar código" e "Cancelar"; isso difere do Figma). "Reenviar código" fica desabilitado por 60 s com a contagem em segundos. Ao alterar a senha com sucesso, o cliente é levado ao login e vê um toast de confirmação. A ação "Alterar senha" tem o mesmo nome na recuperação e no menu do perfil. Textos aprovados em `07` (Login e recuperação de senha); o bloqueio do código e o do login seguem os limites configuráveis do backend.
- **Biometria alterada no aparelho [DEFINIDO]:** após o login, aparece uma modal oferecendo ativar a biometria de novo ("Ativar" em destaque, "Agora não"); textos aprovados em `07` (Login e recuperação de senha).
- Segurança: o passo 1 sempre segue para o passo 2, sem revelar se o e-mail existe (a mensagem "E-mail não encontrado" do Figma deixa de existir).
- Limites do código: bloqueio temporário após 5 erros; "Reenviar código" liberado após 60 segundos.
- **Validade do código [DEFINIDO]:** o código vale **5 minutos** (valor configurável no backend; ver lista do Bruno). A tela mostra a contagem regressiva e, expirado, o erro de código expirado (textos aprovados em `07` (Login e recuperação de senha), C-03-A10 e C-03-A12). Vale também para "Alterar senha" logado.
- **Tentativas de senha no login [DEFINIDO]:** o backend bloqueia temporariamente após 5 senhas erradas, com mensagem única acima do campo (texto aprovado em `07` (Login e recuperação de senha)); número de tentativas e tempo configuráveis no backend. O campo de senha tem olho para revelar.
- **Biometria [DEFINIDO]:** vale para o desbloqueio do app e **não substitui o login**. O que existe hoje no app deve ser ajustado para seguir esta definição. Textos das modais aprovados em `07` (Login e recuperação de senha).
  - **Oferta:** logo após o primeiro login com sucesso no aparelho, em uma modal (texto aprovado em `07` (Login e recuperação de senha)), com "Ativar" e "Agora não". Se recusar, o app não pergunta de novo sozinho. Não é oferecida no cadastro (já é extenso).
  - **Ativar e desativar depois:** interruptor em engrenagem > Segurança (hoje já existe um interruptor de biometria; passa a seguir esta regra). Ativar abre **a mesma modal da oferta**; desativar abre uma **modal de confirmação** que fala das vantagens de manter. Se o aparelho não tem biometria cadastrada, a opção não aparece.
  - **O que ela faz:** com sessão válida, o app abre pedindo a biometria ao voltar ao primeiro plano depois de um tempo configurável no app. Também pode ser usada para **renovar o refresh token** e para quem foi **deslogado por inatividade**. **Não vale** para troca de senha em outro app, bloqueio ou conta suspensa: nesses casos o token morre e vale a regra de sessão, sem biometria.
  - **Falha:** após algumas tentativas ou se o cliente cancelar, aparece "Usar senha", que desloga e leva ao login. A senha nunca deixa de funcionar.
  - **Biometria alterada no aparelho** (digital ou rosto novo): a opção é desativada e o app pede para ativar de novo após o login.
  - **Deslogado:** não existe biometria. **Se o cliente tocar em "Sair da conta", a biometria é desativada** (será oferecida de novo no próximo login).
  - **Modal de ativar [DEFINIDO]** (oferta pós-login e interruptor ligado em Segurança): texto aprovado em `07` (Login e recuperação de senha); destaque "Ativar"; texto "Agora não".
  - **Modal de desativar [DEFINIDO]** (confirmação ao desligar o interruptor): texto aprovado em `07` (Login e recuperação de senha); destaque "Manter ativada"; texto "Desativar".
  - **[Para o Bruno, a validar]:** como a biometria pode reentrar após inatividade, o aparelho precisa guardar uma credencial no armazenamento seguro; recomendação de segurança: um token do aparelho emitido pelo backend (revogável), nunca a senha.

### Sessão do cliente [DEFINIDO]
- O cliente fica logado até acontecer uma destas condições: (a) troca de senha em outro app (ou na futura plataforma web): o backend mata o bearer token; (b) cliente bloqueado: o backend mata o token; (c) mais de 2 meses sem acessar: o app mata o token no backend ou o próprio backend o mata. O app verifica o token a cada vez que volta ao primeiro plano e desloga se estiver inválido.
- Mais de 7 dias sem acessar (e menos de 2 meses): o app pede ao backend a renovação do refresh token e segue logado. Menos de 7 dias: segue logado.
- Falha de renovação por falta de internet não desloga: o app tenta de novo quando a conexão voltar e só desloga se o backend recusar.
- **Mensagem única de sessão [DEFINIDO]:** o backend devolve um **401 genérico** para qualquer perda de autorização (expiração, troca de senha em outro aparelho, bloqueio ou suspensão), **sem informar o motivo**, por segurança. O app, ao deslogar por 401, mostra sempre a mesma mensagem curta acima do campo do login (texto aprovado em `07` (Sessão)). Só a **tentativa de login** de conta suspensa ou banida recebe a mensagem de contatar o suporte (Estados gerais, item 5).

### Editar Perfil do cliente e troca de e-mail [DEFINIDO]
- Editáveis pelo cliente: nome social, celular, sexo, data de nascimento (mín. 18 anos), foto e e-mail. Nome completo e CPF só mudam pela equipe, via suporte (dados sensíveis e base da verificação futura).
- **Máscara na tela [DEFINIDO]:** CPF (só leitura) mascarado com olho. E-mail e celular mascarados com olho até tocar no campo para editar, aí revelam. Sexo e data de nascimento mascarados/ocultos com olho (mesma regra do cadastro). Nome completo (só leitura), nome social e foto ficam visíveis. Ver "Dados sensíveis (olho) por tela [DEFINIDO]".
- Troca de e-mail: o cliente preenche o novo e-mail e clica no botão; se o e-mail novo já estiver em uso, o app avisa antes de disparar qualquer e-mail (modal de e-mail já cadastrado, sem o botão "Entrar"). Se estiver livre, dispara um e-mail para o e-mail ANTIGO avisando que será mudado, com um botão de confirmação. Ao clicar, o cliente volta ao app e o e-mail é trocado; em seguida dispara o e-mail de confirmação para o e-mail NOVO e o app mostra que é preciso confirmar o novo (aviso da home). O e-mail novo passa a ser o username.
- Até confirmar no e-mail antigo, o e-mail continua o antigo; um novo pedido invalida o anterior; o link expira como o link de confirmação de e-mail. Sem acesso ao e-mail antigo, a troca é pelo suporte (WhatsApp).
- **Nome exibido [DEFINIDO]:** o perfil, a Home e o artista (no agendamento) mostram o **nome social, se existir; senão o primeiro nome** do cliente. O nome completo só é visto pelo próprio cliente (em Editar Perfil) e pela equipe.
- **Salvar [DEFINIDO]:** botão "Salvar" desabilitado até haver alteração. **Sem modal de descarte no MVP:** sair da tela com alterações não salvas descarta sem aviso. Celular com a mesma validação do cadastro; data de nascimento com mínimo de 18 anos (mensagem de erro de campo, padrão do item 2 dos estados gerais); sexo com as mesmas opções do cadastro. A troca de foto reaproveita a modal "Enviar foto" (galeria e câmera, estados gerais item 6).
- "Alterar senha" logado: ver engrenagem (mesmo fluxo de código, desloga ao finalizar e envia ao login).

### Excluir conta do cliente [DEFINIDO]
- **Conta unificada [DEFINIDO]:** se o cliente também é artista, a exclusão **não apaga nem aplica soft delete nos dados do artista**; somente o usuário do app de cliente recebe o soft delete. O papel de artista permanece como está. [PENDENTE no lado do artista: como fica o login único e a senha quando só o app C foi excluído.]
- Regra: a exclusão é bloqueada enquanto houver agendamento ativo (cancelar ou concluir antes). No futuro, um sistema pode cancelar tudo automaticamente; no MVP fica o mais simples.
- A conta só é excluída de fato 30 dias depois; até lá fica marcada no backend como "conta em processo de exclusão". Se o cliente entrar nesse prazo, a conta é reativada **na hora, sem nenhum aviso ou modal**, como estava (retenção: quem voltou queria algo no app; se quiser sair, refaz o fluxo). Passados os 30 dias a conta passa a **excluída** (soft delete no backend: nada é apagado fisicamente pelo app); a eliminação de dados pedida pelo titular, conforme a LGPD, é tratada pelo suporte (procedimento e prazos de guarda a validar com o advogado). **A copy do app não promete remoção física dos dados** nem expõe o detalhamento da retenção: o que cabe informar fica na Política de Privacidade.
- Modal 1, agendamentos em aberto (bloqueia a exclusão): textos aprovados em `07` (Excluir conta); botão de destaque "Ver meus agendamentos" (leva à Agenda); botão em texto "Voltar".
- Modal 2, retenção: textos aprovados em `07` (Excluir conta); botão de destaque "Quero ficar"; botão em texto "Continuar com a exclusão"; o link do WhatsApp ("fale com a gente") fica dentro do texto, mantendo o padrão de duas opções por modal.
- **Motivo da exclusão [DEFINIDO]:** nova tela entre a retenção (modal 2, após "Continuar com a exclusão") e a confirmação com senha (modal 3). Título e opções aprovados em `07` (Excluir conta); escolha única; botão de destaque "Continuar", **desabilitado até escolher uma opção; não existe botão "Pular"** (escolher é obrigatório, o texto livre é opcional). Opções e o que cada uma faz:
  1. "Não uso mais o app": segue direto para a confirmação com senha, sem modal.
  2. "Não encontrei Artistas na minha região": modal (textos aprovados em `07` (Excluir conta)); destaque "Vou esperar" (fecha o fluxo e o cliente continua com a conta) e texto "Continuar com a exclusão" (segue para a senha).
  3. "Tive um problema com um Artista": modal (textos aprovados em `07` (Excluir conta)); destaque "Denunciar Artista" (fecha o fluxo de exclusão e leva à Agenda, aba dos agendamentos passados, onde aparece uma modal explicativa (ver abaixo); o cliente escolhe o atendimento e usa "Denunciar Artista" no menu do cartão, que já traz Artista e # preenchidos) e texto "Continuar com a exclusão" (segue para a senha).
  4. "Prefiro agendar por outros meios": modal "Quer contar mais?" (textos aprovados em `07` (Excluir conta)), campo de texto **opcional** (máx. 500 caracteres) e destaque "Continuar com a exclusão". No futuro, esta opção ganhará a escolha de concorrentes.
  5. "Outro motivo": mesma modal da opção 4 (campo opcional, máx. 500 caracteres). Não há campo de texto na própria tela de opções.
  - A modal das opções 4 e 5 e as demais têm "×" para fechar (volta à tela de opções). A modal da opção 2 e a da 3 que levam a "ficar" encerram o fluxo sem excluir.
  - O motivo escolhido, o texto livre e o desfecho (excluiu, ficou ou foi denunciar) são gravados no backend para análise de retenção, **inclusive quando o cliente desiste** [DEFINIDO]; sem ação automática. **[A CRIAR]** Nada disso existe hoje no app ou no backend: a tela de motivo, as modais por opção e a gravação do motivo e do desfecho são funcionalidade nova.
  - **Modal explicativa na Agenda [DEFINIDO, a criar]:** ao chegar na Agenda pelo botão "Denunciar Artista" (e só nessa chegada), a Agenda abre rolada até "Agendamentos anteriores" e mostra uma modal explicativa (texto aprovado em `07` (Agenda e do cartão de agendamento)), com botão único "Entendi".
- Modal 3, confirmação com senha: textos aprovados em `07` (Excluir conta); campo de senha com olho; destaque "Cancelar" e texto vermelho "Excluir minha conta" (caminho seguro em destaque); erro de senha acima do campo.
- Modal 4, aviso de arrependimento em até 30 dias: título "Sua conta será desativada" (não promete exclusão física) e texto aprovados em `07` (Excluir conta); botão único "Entendi".

### Denúncia do cliente (M12-F01) [DEFINIDO]
- Pontos de entrada: "Denunciar Artista" (rodapé do perfil do Artista, com opção de selecionar a foto como alvo) e "Denunciar Artista" no menu do cartão de agendamento passado (item separado de "Preciso de ajuda"). Vindo do agendamento, o número do agendamento é anexado e preenchido automaticamente (ajuda a mediação).
- Tela (estrutura do Figma; textos aprovados em `07` (Denúncia)): topo, aviso, 3 grupos expansíveis (cada um com título e descrição), botão "Denunciar" (destaque; desabilitado até marcar um motivo) e "Cancelar". Erro de envio dentro da tela, acima do botão. Campo de descrição (placeholder aprovado em `07` (Denúncia)); obrigatório só em "Outros"; limite de 500 caracteres. No motivo "Fotos" o cliente seleciona a foto do perfil e/ou fotos da galeria (a galeria é futura; no MVP há 1 foto de divulgação, que não aparece no perfil) e pode descrever.
- Grupo 1 (Figma antigo: "Informações diferentes" / "Informação diferentes"): título, descrição e motivos aprovados em `07` (Denúncia) — "Problemas com o perfil".
- Grupo 2 (Figma antigo: "Problemas com atendimento"): título, descrição e motivos aprovados em `07` (Denúncia). **[DEFINIDO]** o motivo "Quis fazer o agendamento por fora da WeCareU" absorve o antigo "Solicitou dados pessoais ou sensíveis pelo chat". **[DEFINIDO]** "Fez check-in sem mim" foi removido: é o mesmo fato do link "O Artista não compareceu", que já tem modal e mediação.
- Removidos [DEFINIDO]: "Não me atendeu na data ou hora marcada" e "Não me atendeu" (são o mesmo fato do link "O Artista não compareceu", que já tem modal e mediação; evita duas ocorrências para o mesmo caso; eram motivos antigos). Não existe chat entre cliente e artista (descartado), por isso o motivo do chat foi substituído.
- Grupo 3 (Figma antigo: "Comportamento indesejado"): título, descrição e motivos aprovados em `07` (Denúncia).
- Modal pós-denúncia: textos aprovados em `07` (Denúncia); botão de destaque "Voltar" e botão em texto "Bloquear também" (abre a confirmação do bloqueio, M12-F02).
- Check-in sem o cliente [DEFINIDO]: não tem motivo próprio na denúncia (cai em "O Artista não compareceu"). No MVP o artista pode fazer check-in a qualquer momento; no futuro haverá trava de geolocalização (o check-in só libera quando o Artista chega perto do cliente, como faz o Uber). "Me obrigou a dar nota alta" e "Me obrigou a avaliar na frente dele" são mantidos porque a nota é sigilosa, mas a pressão pode ocorrer na hora do atendimento.
- **Repetição e retorno [DEFINIDO]:** não há trava contra denúncias repetidas no MVP (o backoffice agrupa por alvo e por #). O denunciante **não recebe retorno** sobre o resultado, só a modal "Denúncia enviada" (texto aprovado em `07` (Denúncia)).
- Tratamento no MVP [DEFINIDO]: nenhum motivo tem ação automática. Toda denúncia vai para o backoffice com o motivo, o # do agendamento (quando houver), quem denunciou e quem foi denunciado; a equipe aplica manualmente, quando cabível, a suspensão por tempo indeterminado (M12-F04; não existe advertência no MVP). Campo de descrição (placeholder aprovado em `07` (Denúncia)): opcional, com limite de 500 caracteres, e obrigatório apenas no motivo "Outros".

### Bloqueio (M12-F02) [DEFINIDO]
- Bloqueio de usuário **está no MVP** (`01`, `04`; requisito das lojas). Tem fluxo próprio (detalhado abaixo); não haverá bloqueio na avaliação (a ideia original de bloquear ao avaliar foi descartada).
- **[DEFINIDO]** Bloquear **não** fica só dentro da denúncia: quem só quer bloquear não deve ser obrigado a denunciar. Há **dois pontos de entrada para o mesmo fluxo de bloqueio**: o atalho "Bloquear também" no modal pós-denúncia e o botão "Bloquear Artista" no rodapé do perfil do Artista. O fluxo tem uma modal de confirmação e uma modal de resultado (textos aprovados em `07` (Denúncia), C-12-15, C-12-15B e C-12-15C).
- **Falha e destino [DEFINIDO]:** se o bloqueio falhar, o erro aparece dentro da própria modal, acima dos botões, com "Tentar de novo". Depois de bloquear pelo perfil, o app volta à lista de Artistas recarregada; depois de bloquear pelo "Bloquear também", volta ao ponto de origem da denúncia (Agenda ou perfil), onde o perfil do Artista já não abre.
- **Divergência do Figma [DEFINIDO]:** o Figma mostra "Você poderá desbloqueá-lo nas configurações do app" e o botão "Desfazer"; ambos **saem**, pois o bloqueio é permanente e só o suporte desfaz. O Figma também não avisa do cancelamento dos agendamentos futuros; a modal de confirmação passa a avisar.
- **Não haverá tela de bloqueados nem desbloqueio pelo usuário** (nunca): o bloqueio é permanente para o usuário. O desbloqueio, quando necessário, é feito pela equipe via suporte, e o modal do bloqueio avisa que é permanente. Isso altera o M12-F02 e as listas "bloqueados (lista e desbloquear)" dos perfis acima.
- Efeitos do bloqueio [DEFINIDO]: (1) cliente bloqueia artista: o artista some da listagem e da busca desse cliente e o cliente não consegue abrir o perfil dele. (2) Artista bloqueia cliente: o cliente não consegue agendar com esse artista, que deixa de aparecer na listagem dele; o artista não perde nada. (3) Agendamentos futuros entre os dois são cancelados automaticamente, e o app avisa quem bloqueia (no modal, antes de confirmar) e quem foi bloqueado (pelo push de cancelamento) que isso ocorrerá; agendamentos passados permanecem como histórico. (4) Quem é bloqueado não recebe aviso de bloqueio: para ele, o outro simplesmente não aparece (só vê o cancelamento dos agendamentos futuros, se houver). (5) **Atendimento já iniciado, aguardando avaliação ou concluído [DEFINIDO]:** o cancelamento automático vale só para agendamentos futuros; os demais não são cancelados. O cartão passado continua na Agenda com nome e foto congelados no agendamento, e a avaliação e a denúncia seguem disponíveis ao cliente mesmo com o artista bloqueado, suspenso ou excluído; só o perfil do artista deixa de abrir. (6) Texto do modal: informa que o bloqueio é permanente, que agendamentos futuros com essa pessoa serão cancelados e que, para desfazer, é só falar com o suporte (textos aprovados em `07` (Denúncia); C-12-15, C-12-15B e C-12-15C).

## Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO]
- O objetivo da função é só chamar a atenção do cliente para baixar o app, não vinculá-lo ao agendamento. O cliente convidado recebe uma única mensagem (SMS), com texto aprovado em `07` (Texto final aprovado do SMS de convite); nome do Artista, data e hora variáveis. O texto é curto de propósito, porque o custo por segmento é da empresa. **[DEFINIDO]** O texto **não promete acompanhamento do atendimento**, pois no MVP não há vínculo entre a reserva manual e o cadastro.
- **Descadastro do SMS [DEFINIDO: fora do MVP; risco aceito]:** no MVP o destinatário do convite não tem meio de parar de receber convites (nem link, nem contato no texto, nem lista de números suprimidos). No futuro haverá outra forma de parar as notificações por SMS. Risco (LGPD e incômodo) aceito pelo dono para o MVP.
- No MVP não há link de aterrissagem, não há cruzamento de dados entre a reserva manual e o cadastro do cliente e não há vínculo automático. O máximo permitido é o link da App Store (e da loja Android equivalente) na mensagem. **[DEFINIDO]** A mensagem leva um único link curto, que redireciona para a loja certa conforme o aparelho (iOS ou Android); o redirecionamento não é página de aterrissagem e não cruza dados. **Para o Bruno:** escolher o encurtador/redirecionador e medir o custo real por segmento.
- Por isso o celular não ser verificado nem único não gera risco de exposição de dados: nenhum dado do agendamento é mostrado a quem se cadastra com aquele celular. No futuro entram formas de validar o cadastro e vincular a reserva.
- Consequências: a reserva manual ocupa a agenda do artista, mas não gera cartão no app do cliente, avaliação nem nota no MVP (não há cliente vinculado); o fluxo do lado do artista (nome e celular obrigatórios, caixa "o cliente autorizou o contato", limite diário de convites, custo de SMS por conta da empresa) será detalhado no lado do artista.

## Registro de detalhamento: Dois apps e cadastro unificado [DEFINIDO]
- O app do cliente e o app do artista são dois apps separados. O artista pode ser cliente e o cliente pode ser artista. O cadastro (identidade) é unificado entre os apps, e por isso o filtro "o artista não agenda consigo mesmo" é feito no backend.
- Futuro: quem já é cliente e se cadastra como artista (ou o inverso) recebe boas-vindas, o app aproveita os dados já cadastrados e pede só o que falta para aquele app. Fora do MVP.
- MVP: o cadastro é único, sem pedir dados adicionais para a pessoa que já tem conta no outro app. [A confirmar no lado do artista: quais dados o app do artista exige além dos do cliente, ex.: CNPJ, e como isso convive com "sem dados adicionais".]

## Registro de detalhamento: Região (conceito) [DEFINIDO]
- **Região não é bairro.** Região é o nome de lugar que o cliente e o artista reconhecem para aquela área, e pode agrupar ou substituir bairros. Em todo o app, onde se lê "região" não se deve registrar nem exibir "bairro".
- Regras futuras (cidades grandes): bairros que são na verdade jardim ou vila (ex.: "Jardim Belém") não viram região; usa-se o bairro de referência (ex.: "Ermelino Matarazzo"). Bairros pequenos colados que a população conhece pelo nome de um vizinho mais famoso usam esse nome (ex.: "Chora Menino" é chamado de "Imirim").
- Cidades pequenas: a regra se inverte e a região é a cidade inteira (bairro seria micro demais); cidades muito pequenas e próximas podem formar uma região única, pois o artista consegue atender todas.
- **MVP [DEFINIDO]:** a região é o próprio bairro (o que vem do CEP), para não criar esforço desnecessário agora. Depois a equipe migra todos os cadastros existentes para a região correta, e os novos cadastros já entram com a região certa. A regra fina de cálculo da região (além do MVP) permanece futura / não fechada.

## Carregamento inicial das telas (skeleton) [DEFINIDO]

**Regra geral [DEFINIDO]:**
- O carregamento inicial de uma tela usa **skeleton**: blocos que imitam o formato do conteúdo, **sem nenhum texto** (portanto sem copy). **Cor, forma exata e animação ficam para o designer no Figma.**
- **Formato e posição [DEFINIDO]:** o skeleton de cada item tem o **mesmo tamanho e a mesma posição** do conteúdo real (card, linha, chip, foto). Ao ser substituído pela informação, a tela não "pula" nem gera desconforto. Vale para qualquer skeleton do app.
- **O que é fixo fica real [DEFINIDO]:** topo, logo, barra inferior, títulos de seção que sempre existem e botões. Só o que vem do backend vira skeleton. Seção que pode não existir (ex.: "Avalie seu atendimento") **não** aparece com título no skeleton: entra como cartão genérico, sem título.
- O skeleton vale até a resposta do backend ou até o timeout de 30 segundos (ver "Carregando e travas"). Se estourar o timeout ou falhar, aparece o erro da tela (texto aprovado em `07` (Estados gerais / Listagem)) com "Tentar de novo".
- **Carregamento parcial [DEFINIDO]:** cada seção carrega e falha sozinha. Se uma falhar, o erro aparece só nela (texto aprovado em `07`) com "Tentar de novo", e o resto da tela segue normal. A tela inteira só vira erro se tudo falhar.
- Atualizar arrastando mantém o conteúdo atual e mostra só o indicador de puxar. Ação do usuário continua com o overlay e os botões travados. Paginação continua com o indicador no rodapé (ver "Scroll infinito").
- **Sem skeleton [DEFINIDO]:** Welcome / carrossel, Login e recuperação de senha, e Cadastro em chat. Não têm dados do backend. A consulta de CEP usa o estado de ação do botão.

**Lapidação por tela [DEFINIDO]:**

| Tela | Skeleton | Status |
|---|---|---|
| Listagem de Artistas | Topo e chips de filtro reais; 4 cards skeleton no formato e posição do card real (foto vertical, nome, nota, faixa de preço). Paginação: indicador no rodapé | DEFINIDO |
| Perfil do Artista | Foto, nome, nota e descrição em skeleton; lista de serviços: 3 linhas skeleton; regiões: chips skeleton. Botão "Agendar agora" desabilitado até carregar | DEFINIDO |
| Home | Foto e nome **reais** (vêm do storage local; a Home valida com o backend ao carregar e só atualiza se mudou). Campo "Endereço" em skeleton. Bloco "Vamos agendar" com título e botões reais. Cartões: 1 cartão genérico sem título, no formato do cartão real | DEFINIDO |
| Agenda (Próximos e Anteriores) | Título e abas reais; 3 cartões genéricos sem título, no formato e posição do cartão real | DEFINIDO |
| Agendamento em chat | Mensagens do robô reais, sem skeleton. Só serviços do Artista (3 linhas) e horários (grade de 6 botões) viram skeleton dentro da bolha do robô, no formato do conteúdo real | DEFINIDO |
| Pesquisar (filtros) | Chips de serviço e categoria em skeleton (6 chips), no formato dos chips reais. Calendário é local e não precisa de skeleton | DEFINIDO |
| Configurações de Notificação | Rótulos dos grupos reais (fixos). Só os interruptores em skeleton (estado vem do backend e da permissão do aparelho) | DEFINIDO |
| Perfil / engrenagem (Configurações) | Foto, nome e campos de "Sobre mim" em skeleton, no formato do item; menu real. Em Meus endereços: 3 linhas skeleton no formato da linha. Em Editar perfil: campos pré-preenchidos em skeleton até chegar o dado | DEFINIDO |
| Welcome / carrossel; Login e recuperação; Cadastro em chat | Sem skeleton | DEFINIDO |

## Estados gerais do app (todas as telas, cliente) [DEFINIDO]
Itens mapeados: 1) sem internet; 2) falha em ação e padrão de mensagens de erro; 3) versão mínima do app; 4) backend fora do ar e manutenção; 5) conta suspensa ou banida; 6) permissão de câmera/galeria na foto; 7) hora do servidor como referência.

### 1. Sem internet [DEFINIDO]
- Quando o aparelho fica offline, o app mostra um **overlay** com ícone de internet e a mensagem aprovada em `07` (Estados gerais). Substitui a ideia anterior de aviso fixo no topo.
- **Debounce:** o overlay só aparece depois de **3 segundos seguidos sem conexão** e só some quando a conexão volta e se mantém por **1 segundo**, para não piscar a cada micro perda de conexão.
- **Detecção:** combina o estado de rede do aparelho com falha de requisição por falta de conexão (o aparelho pode estar no Wi-Fi sem internet real); ambos entram no mesmo debounce.
- **Bloqueio:** o overlay cobre a tela inteira e impede qualquer toque, inclusive nas telas já carregadas. Vale em todas as telas (welcome, login, cadastro, chat de agendamento etc.). Ao voltar a conexão o app permanece onde estava, com o que o cliente digitou preservado, e recarrega só os dados da tela atual. Se a perda ocorrer durante o pré-agendamento de 10 minutos, o prazo segue correndo no backend e, ao voltar, vale o fluxo de expiração já definido.

### 2. Falhas em ações e padrão de mensagens [DEFINIDO]
- **Não existe "sistema de alert" flutuante.** O app usa quatro formas de mensagem: erro de campo, aviso embutido, toast e modal.
- **Erro de formulário ou de ação simples [DEFINIDO]** (login, cadastro, senha, editar perfil): a mensagem fica fixa acima ou abaixo do item que falhou; os campos ficam com borda vermelha e balançam para os lados (como o login faz hoje). Não some sozinha: sai quando o cliente edita ou tenta de novo. Mensagem genérica e "campo obrigatório": textos aprovados em `07` (Estados gerais). Mensagens que o app já conhece (ex.: CPF inválido, e-mail em formato errado, campo obrigatório) são validadas no próprio app, **sem chamar o backend**; mensagens específicas de regra de negócio vêm do backend.
- **Toast [DEFINIDO]:** mensagem que some sozinha (cerca de 3 segundos), só para informação sem importância, que não causa problema se for perdida (ex.: "Endereço salvo"). Nunca para erro.
- **Modal [DEFINIDO]:** para confirmações, decisões e também para **avisos e erros que precisam de confirmação** do cliente.
- **Aviso embutido [DEFINIDO]:** caixa fixa dentro da tela, no mesmo estilo do aviso de e-mail não confirmado, que não some sozinha. Usado para erro de ação complexa iniciada em um cartão (cancelar agendamento, avaliar, "Preciso de ajuda"). Regras:
  - **Posição:** no topo do conteúdo da tela: na home, na região reservada para alertas abaixo da foto e do nome; na Agenda, abaixo do título.
  - **Texto:** sem o número do agendamento, pois o cliente acabou de tocar em um cartão específico e sabe de qual se trata (no MVP, o aviso embutido cobre o "Preciso de ajuda" quando o WhatsApp não abre; o erro de cancelar fica na modal e o de avaliar no cartão; texto aprovado em `07` (Estados gerais)).
  - **Atenção:** o aviso de **erro** balança ao aparecer (e a cada nova falha) para chamar a atenção; avisos fixos informativos, como o de e-mail não confirmado, não balançam.
  - **Quando sai:** ao tocar no "×", ao concluir a ação com sucesso ou **ao sair da tela** (o erro é limpo, pois deixa de fazer sentido).
  - **Prioridade entre mensagens fixas [DEFINIDO]:** só **uma mensagem aparece por vez** na região de alertas, pela prioridade: **0** mensagem pontual (ex.: "Cancelar falhou", erro de ação do cartão), **1** aviso de push negado, **2** e-mail não confirmado. Sai a de maior prioridade, e quando ela some (por "×", sucesso ou saída da tela) volta a próxima da lista que ainda se aplicar.
  - **Convivência com outros avisos:** o aviso de erro **substitui** o aviso fixo que estiver na região (ex.: "e-mail não confirmado"), sem empilhar, para não empurrar o conteúdo para baixo. Quando o erro sai (por "×", sucesso ou saída da tela), o aviso fixo volta ao lugar.
  - Erro de ação iniciada **dentro de modal** fica dentro da própria modal, acima dos botões (padrão do erro de senha na exclusão de conta), sem aviso embutido.
- **Carregando e travas [DEFINIDO]:** toda ação que chama o backend mostra o overlay de carregamento e **trava todos os botões** até a resposta ou o timeout, para impedir vários pedidos ao backend (vale para todo o app).
- **Timeout [DEFINIDO]:** 30 segundos para qualquer ação, inclusive envio de foto, no MVP, porque o servidor é local; o valor será reduzido na migração para o servidor na nuvem (valores de carregamento e timeouts a fechar com o Bruno, ver lista do Bruno) [PENDENTE]. Estourou o timeout, vale o erro do tipo correspondente. Nas ações que criam algo (ex.: confirmar agendamento) o backend aceita o mesmo pedido repetido sem duplicar e o app consulta o resultado antes de permitir nova tentativa (exigência para o Bruno).

### 3. Versão mínima do app [DEFINIDO]
- **Como o app descobre:** o app envia a **versão e a plataforma (iOS ou Android) em toda requisição**; quando a versão está abaixo da mínima exigida, o **backend responde com um erro específico de "versão não suportada"**, que tem prioridade sobre qualquer outra validação. Não existe consulta pública separada: para o deslogado não faz sentido consultar o backend de alguém que nem entrou; ele descobre na primeira requisição real (login, checagem de CPF no cadastro, ida à listagem pelo welcome etc.). Para o logado, a descoberta ocorre em qualquer requisição e na checagem feita ao abrir o app e ao voltar ao primeiro plano (a mesma da sessão).
- **Tela de atualização obrigatória:** é uma **tela**, não uma modal: não fica por cima de nada e não tem para onde ir (sem "×" e sem voltar), com um único botão "Atualizar" que abre a página do app na loja certa (App Store ou Google Play). Os textos estão aprovados em `07` (Estados gerais) e aproveitam o espaço para promover o app (identidade da marca, benefício). O que o cliente digitou em fluxo em andamento é descartado; o cadastro retoma pelas regras de retomada já definidas.
- **Versão mínima por plataforma:** o backend mantém uma versão mínima para iOS e outra para Android (a aprovação nas lojas tem prazos diferentes).
- **Para o Bruno:** receber versão e plataforma em toda requisição, manter a versão mínima por plataforma e devolver o erro específico com prioridade sobre as demais validações.
- **Versão "recomendada" (atualização opcional, que o cliente pode dispensar): fora do MVP.**

### 4. Fora do ar e manutenção [DEFINIDO]
- **Fora do ar** (o aparelho tem internet, mas o servidor não responde, dá timeout ou devolve erro de servidor): não tem tela própria; usa o padrão de mensagens do item 2 (erro no formulário, aviso embutido ou, na listagem, a mensagem de falha da lista com "Tentar de novo", texto aprovado em `07` (Listagem, parte A)). O overlay de offline é só para falta de conexão do aparelho.
- **Manutenção:** é uma **tela**, como a de versão: sem para onde ir (sem "×" e sem voltar), com ícone, título e texto curtos, aproveitando o espaço para a marca (textos aprovados em `07` (Estados gerais)), e botão "Tentar de novo" que refaz a consulta. Existe porque não se pode confiar nas informações salvas no app.
- **Como o app descobre [DEFINIDO]:** igual à versão: o backend responde a qualquer requisição com um erro específico de "em manutenção", com prioridade sobre as demais respostas; o app descobre na primeira requisição real; para o logado vale também a checagem de sessão do primeiro plano.
- **Quem liga e desliga [DEFINIDO, para o Bruno]:** a equipe, por configuração no backend, sem publicar app.
- **Dados salvos no app [DEFINIDO]:** em manutenção o app não mostra nada guardado no aparelho. Ao sair da manutenção, recarrega os dados da tela em que o cliente estava, que permanece no mesmo lugar, com o que ele digitou preservado (diferente da tela de versão, que descarta o estado).
- **Sem horário de retorno [DEFINIDO]:** o texto da manutenção não informa horário de retorno, e isso não muda no futuro: a manutenção programada acontece de madrugada, em dias de pouco uso, e a manutenção por falha tem retorno imprevisível.
- **Ordem de prioridade entre os bloqueios [DEFINIDO]:** o overlay de offline fica acima de tudo; depois vêm a tela de versão, a tela de manutenção e, por último, os erros comuns.

### 5. Conta suspensa ou banida pelo backoffice [DEFINIDO]
- **Mensagem única e formal:** suspensa e banida mostram a mesma mensagem no login, acima do campo, no mesmo estilo da mensagem "sua sessão expirou". Ela **não revela o motivo nem se a sanção é temporária**, e o tom é formal, por ser algo sério (texto aprovado em `07` (Estados gerais)), com o link para o WhatsApp do suporte dentro do texto.
- **Quem já está logado:** segue a regra do token: o backend encerra a sessão, o app descobre ao voltar ao primeiro plano, desloga e leva à tela de login **sem mostrar a mensagem**. A mensagem só aparece quando o cliente tenta entrar de novo (a tentativa de login é que devolve o erro de conta suspensa ou banida).
- **Agendamentos futuros:** ao suspender ou banir, os agendamentos futuros do cliente são **cancelados automaticamente** e o artista recebe o push de cancelamento; os passados ficam como histórico (mesmo efeito do bloqueio).
- **Sem aviso ao cliente:** nenhum push nem e-mail automático avisa a sanção no MVP; a equipe explica pelo suporte quando ele procurar.
- **Novo cadastro com o mesmo CPF ou e-mail:** como são únicos, cai no modal de "já cadastrado", que leva ao login; lá o cliente tenta entrar e recebe a mensagem acima (igual ao caso do logado). Não há como contornar criando outra conta.
- **Conta única entre os apps [DEFINIDO]:** a sanção (suspensão ou banimento) vale **somente para o app em que foi aplicada**: quem é um mau cliente pode não ser um mau artista, e vice-versa. O backend precisa registrar a sanção por conta **e por app**.
- **[FUTURO, fora do MVP]:** sistema de **strikes**: o usuário é notificado de cada strike, a suspensão passa a ser por tempo, como punição, e cresce a cada strike; no 3º strike a saída é indefinida (banimento). No MVP **só existe a suspensão por tempo indeterminado**, aplicada manualmente pela equipe e mantida até o usuário falar com o suporte; **não existe advertência** e não há contagem automática. Advertência, banimento permanente e strikes são [FUTURO].

### 6. Permissão de câmera ou galeria na foto [DEFINIDO]
- **Contexto:** a foto é obrigatória para agendar, então uma permissão negada não pode travar o cliente.
- **Galeria [DEFINIDO, a validar no app atual]:** o app usa o **seletor de fotos do próprio sistema** (no iOS, o seletor do sistema, que roda fora do app e entrega só a foto escolhida; no Android, o seletor nativo). Esse seletor **não exige permissão de acesso à galeria**, então "galeria negada" não existe como situação. Conferido na documentação do Expo e da Apple: o diálogo do iOS "permitir a galeria inteira ou só fotos selecionadas" só aparece quando o app **pede explicitamente** a permissão da biblioteca antes de abrir o seletor, o que não é necessário para escolher uma foto. **Para o front:** não chamar o pedido de permissão da biblioteca antes de abrir o seletor; se o app atual chama, remover. [Mudança no que já existe, se aplicável.]
- **Câmera [DEFINIDO]:** a modal "Enviar foto" passa a ter duas opções, "Escolher da galeria" e "Tirar foto" (nova no MVP; o Figma só mostra o campo de envio). A permissão da câmera é pedida só quando o cliente toca em "Tirar foto". Se negar, aparece uma modal (textos aprovados em `07` (Estados gerais)); destaque "Abrir ajustes"; texto "Escolher da galeria". Nunca fica sem saída.

### 7. Hora do servidor como referência [DEFINIDO]
- Toda regra que depende de horário ("cancelar até o início do atendimento", fim do pré-agendamento de 10 min e da extensão, liberação de horários, check-in e similares) é decidida **pelo backend com a hora do servidor**, nunca pelo relógio do aparelho.
- [RECOMENDADO, a confirmar] O app pode usar o relógio do aparelho só para exibição (contagens regressivas), e o resultado final vem sempre do backend; se o backend recusar por horário, o app mostra o erro pelo padrão do item 2 e recarrega os dados da tela. Caso específico: cancelar após o início do atendimento mostra, dentro da modal de cancelamento, o texto aprovado em `07` (Estados gerais) com "Entendi", e o cartão recarrega.
- **Para o Bruno [RECOMENDADO, a confirmar]:** o backend devolve a hora do servidor nas respostas que dependem de prazo, para o app calcular contagens sem depender do aparelho.

