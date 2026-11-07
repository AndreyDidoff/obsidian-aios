---
tipo: fonte
arquivo: ingeridos/05-lista-funcoes-e-telas.md
origem: detalhamento de funções e telas do MVP; lado do cliente fechado pelo dono
criado: 2026-11-05
atualizado: 2026-11-05
---

# Lista de funções e telas do MVP

Inventário dos módulos M01–M14 e detalhamento do app do cliente. Parte do fechamento anterior em [[mvp]] e [[mvp-final]]. O detalhamento do cliente está fechado onde o arquivo marca [DEFINIDO]. Artista (P) e painel (B) permanecem inventário: as telas deles estão nomeadas, sem registro de detalhamento.

O arquivo é o alvo de produto, não a descrição do app como está hoje. [A CRIAR] marca função ainda inexistente no app e no backend. Os textos de tela ficam apontados para o `07`; esta página não os reproduz.

Marcadores do próprio arquivo: [DEFINIDO] é decisão do dono; [RECOMENDADO] é recomendação; [PENDENTE] está aberto; [ALTERADO] e [REMOVIDO] ajustam o inventário; [FUTURO] fica fora do MVP. Função vem de [DEFINIDO]. Tela só listada no inventário, ainda sem registro, segue [RECOMENDADO].

## Módulos

**M01. Conta e identidade (C, P).** Cadastro, login, senha, termos, perfil, sair e exclusão. No cliente está fechado: sem SMS no MVP (o celular só é coletado), cadastro em chatbot e exclusão em soft delete de 30 dias só do usuário do app C; cadastro, SMS e exclusão do prestador seguem inventário.

**M02. Perfil profissional do prestador (P).** Ofício, serviços com nome, duração e preço, foto e várias regiões, com atalho de zona em São Paulo. O perfil público visto pelo cliente está fechado; as telas do prestador seguem inventário.

**M03. Agenda do prestador (P).** Disponibilidade, antecedência, deslocamento, bloqueio de horário e a agenda; o horário livre sai do backend, com reserva atômica contra horário duplicado. Inventário, sem detalhamento de tela.

**M04. Aprovação e estados do prestador (B, P).** Fila no painel, aprovar ou reprovar por nome real, foto adequada e telefone verificado, estados do prestador e o caso "não ativado na cidade". A tag "Novo" dura 3 dias; as telas seguem inventário.

**M05. Busca e listagem (C).** Filtros de ofício, serviço e data; a região vem do endereço de atendimento, sem filtro de horário, e só entra ofício ou serviço com artista aprovado na região. A listagem ranqueia, a nota aparece a partir de 3 avaliações, e quem é prestador e cliente aparece na lista sem poder agendar consigo — fechado no cliente.

**M06. Agendamento do cliente (C).** Reserva instantânea, sem aceite, com confirmação e consulta de futuros e passados; a tela de detalhe saiu do MVP. O cancelamento pelo cliente não pede motivo, vale até o horário de início, guarda quem e quando, e o cliente é avisado quando o prestador cancela — fechado no cliente.

**M07. Reserva manual e convite (P).** O prestador cria a reserva com nome e celular obrigatórios, caixa de autorização e SMS de convite por conta da empresa. No cliente o MVP é só a mensagem de atenção, sem link nem vínculo ao cadastro: a reserva ocupa a agenda e não gera cartão, avaliação nem nota, e as telas do prestador seguem inventário.

**M08. Agendamentos recebidos e dados do cliente (P).** Lista, detalhe, cancelamento com motivo e histórico, com a privacidade do cliente: antes de 00:00:01 do dia anterior, só nome, foto e região. Inventário, sem detalhamento de tela.

**M09. Atendimento (P).** Check-in e check-out por barra, cronômetro, "cliente ausente", trava para não iniciar o próximo sem encerrar o anterior, e encerramento às 00:00:00 sem contar como ausência. No inventário o check-in do MVP pode ser a qualquer momento, a trava de geolocalização é [FUTURO], e as telas do prestador seguem sem detalhamento.

**M10. Avaliação (C, P).** O cliente dá de 1 a 5, sem texto, uma nota por atendimento concluído, e pode marcar "O Artista não compareceu"; a nota publicada é a agregada, com atraso, a partir de 3 avaliações. O fluxo do cliente está fechado; o prestador ver as avaliações recebidas segue inventário.

**M11. Notificações (C, P).** Só push, sem central de notificações no MVP. No cliente estão fechados o aviso de cancelamento, os lembretes, o reagendamento, o push de avaliação e o aviso de permissão negada; o push de confirmação do agendamento ficou de fora, e o de novo agendamento ao prestador segue inventário.

**M12. Segurança e confiança (C, P).** Denúncia, bloqueio e contato da WeCareU. No cliente está fechado o bloqueio sem desbloqueio pelo usuário e sem lista de bloqueados, e a sanção do MVP é só a suspensão por tempo indeterminado; as telas do prestador seguem inventário.

**M13. Painel de operação (B).** Login (Andrey e Bruno no início), aprovação, denúncias, mediação do "não compareceu" e sanção de usuário; a consulta de usuários e agendamentos está [RECOMENDADO]. Inventário, sem detalhamento de tela.

**M14. Fundações sem tela (back).** API versionada, fatos de negócio, base de bairros, SMS, push, ranqueamento e configurações da spec. `LANCAMENTO_PUBLICO_EM` controla somente a tag "Novo": não esconde nem libera artista.

As seções 4, 5 e 6 (ordem de detalhamento, modelo de cada módulo e quadros transversais) estão [RECOMENDADO].

O lado do cliente também fecha, onde o arquivo marca [DEFINIDO], a home, o endereço de atendimento, o olho dos dados sensíveis, o skeleton, os estados gerais, a região no MVP (o bairro do CEP) e os dois apps com cadastro unificado.

## Pontos para o Bruno (backend)

Seção registrada a pedido do dono. Reúne o que o backend implementa — listagem, agendamento, endereço, avaliação, notificações, conta, sessão, sanção, versão mínima, manutenção, hora do servidor e o link do SMS — e aponta a regra completa na seção de origem. Valores exatos de validação de endereço e de timeout ficam com o Bruno e não bloqueiam o app.

## Pendências do app do cliente

O arquivo marca o detalhamento de produto do app do cliente como fechado. Termos de Uso, Política de Privacidade e o bloco de e-mails transacionais estão diferidos e não bloqueiam. O lado do artista vem depois: o bloqueio de cliente no app do prestador e a revisão desse lado (agenda, SMS, exclusão no app P e o restante) continuam [PENDENTE].
