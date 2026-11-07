# WeCareU — MVP e sequência de releases

Documento de planejamento estratégico. Sem datas e sem estimativas de prazo: a ordem e os critérios de passagem entre releases substituem o calendário.

**Marcadores**

- [DEFINIDO] decisão tomada pelo dono do produto (ou já fixada na especificação de busca e ranqueamento).
- [RECOMENDADO] recomendação do consultor, ainda não confirmada.
- [PENDENTE] decisão aberta. Cada pendente traz recomendação na seção 7.
- [HIPÓTESE] algo a validar com dados. Nenhum número de mercado foi usado; limiares de métrica estão como [PENDENTE] para calibrar no beta.

**Aviso jurídico.** Pontos de LGPD, CDC e relação prestador-plataforma são sinalizações para validar com advogado. Este documento não substitui orientação jurídica.

**Especificação de busca e ranqueamento:** recebida (v0.3.1). Conferência feita em `02-mudancas-na-especificacao.md`.

---

## 1. Tese do produto e público

### 1.1 Visão [DEFINIDO]

App de agendamento de serviços de beleza e bem-estar com atendimento em domicílio: o prestador (chamado "artista" no produto) vai até o cliente na data e hora combinadas. Lançamento 100% gratuito. Monetização futura por ranqueamento pago.

### 1.2 Estratégia de entrada [DEFINIDO]

- Oferta primeiro. Foco inicial em trazer prestadores. Mensagem: app 100% gratuito, "vai que um cliente te chama por ele".
- Demanda depois. Marketing para clientes só começa com base mínima de prestadores por região.
- O prestador atende N regiões e aparece em N listagens.
- Clientes chegam também por mensagens e indicações dos próprios prestadores.
- A listagem de prestadores faz parte do MVP: é nela que a monetização futura acontece.

### 1.3 Hipóteses que o MVP precisa provar

| # | Hipótese | Status |
|---|---|---|
| H1 | O prestador adota o app como sua agenda e continua usando, mesmo antes de a demanda orgânica chegar. Reserva manual e agenda são o motivo de uso. | [HIPÓTESE] |
| H2 | O cliente convidado pelo prestador (SMS/WhatsApp) instala o app, vê o agendamento e conclui o atendimento. | [HIPÓTESE] |
| H3 | Objetivo central do MVP: alguém que nunca viu o prestador consegue achar, marcar e ser atendido, e depois marca de novo. | [DEFINIDO] (frase); verificação depende de o marketing de clientes começar |

Intenção estratégica [DEFINIDO]: converter o prestador em usuário do app.

> Observação da revisão: a separação "cliente do app" x "cliente trazido pelo prestador" foi marcada como não métrica de decisão, mas a H3 só é verificável com ela. Recomendado registrar a origem do cliente como dado (ver `03`).

### 1.4 Público

- Prestadores: todos os ofícios de beleza e bem-estar. Cadastro aberto a qualquer cidade e estado. Marketing inicial focado na cidade de São Paulo, dividida em regiões. Já existem profissionais conhecidos como beta testers. [DEFINIDO]
- Clientes: pessoas que querem atendimento em casa. Marketing só depois da base de prestadores. [DEFINIDO]
- Plataformas: dois apps (cliente e prestador), React Native/Expo, já em desenvolvimento. Motivo: o prestador também pode ser cliente e no futuro haverá atendimento de salões. [DEFINIDO]

### 1.5 O que o MVP não prova

- Não prova que a monetização por ranqueamento funciona.
- Não prova que a desintermediação não acontece (risco aceito, seção 6).
- A liquidez só é medida depois que o marketing de clientes começar.

---

## 2. Escopo do MVP

### 2.1 O que entra, por jornada

**Cliente** [DEFINIDO] (exceto onde marcado)

- Cadastro (com endereço/bairro), login, recuperação de senha, termos e consentimento.
- Perfil e alteração de dados; sair da conta; exclusão de conta [RECOMENDADO] (exigida pela Apple e direito do titular na LGPD).
- Listagem de prestadores com filtros: ofício, serviço, data, região.
- Perfil do artista (serviço, região, avaliação, foto).
- Agendamento (reserva instantânea), consulta de agendamentos (futuros e passados), cancelamento.
- Avaliação do prestador, com opção de indicar que o prestador não compareceu.
- Denúncia, bloqueio e desbloqueio de prestador.
- Contato da WeCareU.
- Privacidade do contato: endereço e telefone do cliente não aparecem na listagem.
- Aviso quando o prestador cancela [RECOMENDADO].

**Prestador** [DEFINIDO] (exceto onde marcado)

- Cadastro (entra como "pendente"), login, recuperação de senha, termos e consentimento.
- Perfil, foto, alteração de dados; sair da conta; exclusão de conta [RECOMENDADO].
- Ofício, serviços, duração de cada serviço, regiões de atendimento (várias).
- Disponibilidade, antecedência da marcação (mínima e máxima), intervalo de deslocamento.
- Bloqueio simples de horário (almoço etc.), sem dados.
- Reserva manual para cliente próprio: nome e celular obrigatórios, caixa "o cliente autorizou o contato", disparo de SMS/WhatsApp convidando o cliente a baixar o app.
- Agendamentos recebidos, consulta de agendamentos, perfil do cliente (dados liberados pela regra de privacidade).
- Fluxo de atendimento: check-in por barra, cronômetro, check-out por barra, próximo cliente liberado. Saídas alternativas: cancelar ou "cliente ausente".
- Notificação push de novo agendamento. Obrigatória.
- Ver avaliações recebidas.
- Denúncia, bloqueio e desbloqueio de cliente.
- Contato da WeCareU.

**Operação / backoffice**

- Painel mínimo [DEFINIDO]: lista de denúncias e bloqueio de usuário.
- Aprovação de prestador (pendente → aprovado) [DEFINIDO].
- Ordenação da listagem conforme a especificação (faixa "Novo" + desempate) [DEFINIDO pela spec].

### 2.2 O que fica fora do MVP e por quê

| Fora | Por quê | Risco aceito |
|---|---|---|
| Verificação de identidade (documento + selfie) [DEFINIDO] | Custo alto no início. Substituída pela aprovação manual. | Prestador não verificado entra em casa de estranho; mitigado só pela aprovação manual. |
| Feature flags (inclusive por região) [DEFINIDO] | Entra como melhoria. | Listagem sempre ligada; busca vazia mostra mensagem sem promessa. |
| Pagamento no app [DEFINIDO] | Complexidade de repasse, estorno e disputa. | Desintermediação; disputa sem poder financeiro. |
| Penalidade, planos, pontos, "Subir agora" [DEFINIDO] | Ordem de lançamento do ranking. | Ranking sem monetização no início. |
| Trava de geolocalização no check-in [DEFINIDO] | Futuro. | Check-in e check-out colados são possíveis. Risco aceito de propósito. |
| Prestador avaliando cliente [DEFINIDO] | No MVP só se avalia o prestador. | Nenhuma reputação do cliente além de denúncia e bloqueio. |
| Prazo de cancelamento [DEFINIDO] | Entra depois. | Cancelamentos de última hora sem regra. Mitigado guardando os dados (R5). |
| Mensagem "avisamos quando chegar" [DEFINIDO] | Não há função de aviso. | Cliente em região vazia sai sem retorno. |
| Todo o restante da lista "pode esperar" | Ver seção 3.3. | Ver seção 3.3. |

### 2.3 Regras de negócio fechadas

- **R1.** Pagamento direto com o prestador, fora do app. [DEFINIDO]
- **R2.** Reserva instantânea: o cliente marca e o horário fica garantido, sem aceite do prestador. [DEFINIDO] Horário calculado da agenda: horário de atendimento, agendamentos, bloqueios, deslocamento, antecedência mínima e máxima. Push ao prestador obrigatório.
- **R3.** Privacidade do contato. [DEFINIDO]
  - A listagem mostra só a região. Rua, complemento e telefone do cliente aparecem apenas ao prestador daquela marcação, no perfil do cliente. O telefone pessoal do prestador fica fora do perfil público.
  - Dados do cliente liberados às 00:00:01 do dia anterior ao atendimento (atendimento às 14h do dia 14 libera às 00:00:01 do dia 13).
  - Agendamento já dentro da janela do dia anterior: liberação imediata. [RECOMENDADO]
  - **Revisão [DEFINIDO pelo dono]:** vale a regra de 1 dia antes (00:00:01 do dia anterior). Interpretação registrada: como o prestador já vê os dados dos clientes do dia desde o dia anterior, o bloqueio "próximo cliente só após check-out" deixa de ser regra de visibilidade dos dados. **Confirmado pelo dono:** o prestador vê os dados de todos os clientes do dia desde o dia anterior, para planejar rotas. Consequência: o ganho de privacidade é só contra visualização com mais de 1 dia de antecedência.
- **R4.** Fluxo de atendimento. [DEFINIDO]
  - O prestador vê o primeiro agendamento e os dados; ao chegar faz check-in arrastando uma barra e o tempo começa; ao terminar faz check-out com a mesma barra e o próximo cliente aparece.
  - Atendimento concluído = check-out ou encerramento às 00:00:00 (R19, P8).
  - Para iniciar o próximo atendimento é preciso encerrar o anterior por check-out, cancelamento ou "cliente ausente". Atendimento não fechado é encerrado às 00:00:00 (R19, P8).
- **R5.** Cancelamento sem prazo mínimo no MVP [DEFINIDO]. Guardar quem cancelou, quando e o motivo [RECOMENDADO]. Cancelamento por qualquer lado avisa o outro por push.
- **R6.** Avaliação. [DEFINIDO] O cliente avalia o prestador, 1 a 5, nota atualizada com atraso por sigilo. Sem filtro de duração entre check-in e check-out. O cliente pode indicar que o prestador não compareceu (gera registro e vai para mediação). [RECOMENDADO] versão mínima (sem texto, uma por agendamento, só concluído) e média bayesiana (prior 4,7, peso 10). [DEFINIDO] "não compareceu" retém a avaliação até a mediação; se decretado, não existe avaliação (P4).
- **R7.** Aprovação de prestador: todo prestador novo entra como "pendente" e só aparece depois de aprovado no painel. Substitui a verificação de identidade no MVP e faz a triagem do que é publicado. [DEFINIDO] [DEFINIDO] Critério: nome real, foto adequada e telefone verificado por SMS (P2).
- **R8.** Mediação: denúncias e reclamações vão para a base da empresa, que faz a mediação. [DEFINIDO] Sanções possíveis: advertência, suspensão e banimento [RECOMENDADO], constando nos termos.
- **R9.** Reserva manual e convite. [DEFINIDO] Nome e celular obrigatórios, caixa de autorização, custo do disparo por conta da empresa, Andrey consulta o advogado. [RECOMENDADO] a mensagem diz quem agendou, quando, o link do app e como não receber mais contato; SMS antes de WhatsApp. **Revisão:** definir limite diário de convites por prestador; validade da caixa de autorização é ponto para o advogado.
- **R10.** Região. Unidade = bairro; prestador escolhe vários, com atalho "selecionar a zona toda" para São Paulo. [DEFINIDO] Região do cliente = bairro do endereço cadastrado. **Revisão (spec):** manter a hierarquia da spec (cidade → zona → bairro, ancestral cobre os bairros); o atalho é só interface. Fonte dos bairros: [DEFINIDO] base oficial CEP/IBGE (P6).
- **R11.** Busca vazia: mensagem "ainda estamos chegando na sua região", sem prometer aviso. [DEFINIDO]
- **R13. Lançamento público [DEFINIDO pelo dono].** O lançamento público é a cidade de São Paulo como um todo (sem divisão por zona). O cadastro de prestadores é aberto a qualquer cidade; o marketing de clientes foca em São Paulo. `LANCAMENTO_PUBLICO_EM` = data em que o marketing de clientes liga em São Paulo. **Outras cidades [DEFINIDO pelo dono]:** o prestador se cadastra normalmente e fica aprovado, mas a tag "Novo" (e a janela de 3 dias) só é ativada quando o app chegar oficialmente na cidade dele. Até lá o prestador fica em estado "não ativado na cidade" (trata-se como um plano gratuito ainda não ativado). Implica `LANCAMENTO_PUBLICO_EM` por cidade, vazio até o lançamento da cidade.
- **R14. Ofícios exibidos [DEFINIDO pelo dono].** O app só mostra ao cliente os ofícios e serviços com pelo menos 1 prestador aprovado na região dele. Isso evita busca vazia por ofício; a mensagem do R11 continua para o caso de região sem prestador.
- **R15. Verificação de telefone por SMS no MVP [DEFINIDO pelo dono].** Código SMS (OTP) no cadastro de prestador e de cliente. Sai de "pode esperar".
- **R16. Reenvio de push [DEFINIDO pelo dono].** Se o prestador não visualizar o novo agendamento, o push é reenviado após um prazo configurável. Registrar "visualizado pelo prestador". Sem cobrança do prestador. Um único reenvio, com prazo fixo (não configurável no MVP). Opção de configurar fica para o futuro.
- **R17. Arquitetura [DEFINIDO pelo dono].** Toda regra de negócio (agenda, slots, planos, ranking, penalidade, notas) fica no backend. O frontend só tem responsabilidade de apresentação e dados de uso do próprio app. Contrato de API versionado, com erros de negócio devolvidos com código e mensagem prontos.
- **R18. Analytics de uso do app fora do MVP [DEFINIDO pelo dono].** Mapas de calor, funil e abandono entram em release posterior (candidato: Release 2). No MVP ficam só os fatos de negócio gravados pelo backend. Abandono de cadastro pode ser inferido no backend (SMS enviado sem SMS validado).
- **R19. Decisões de fechamento do MVP [DEFINIDO pelo dono].**
  - P1: uma identidade com dois papéis, apps separados. O prestador-cliente aparece na listagem (inclusive para si), mas não pode agendar para si mesmo.
  - P3: avaliação mínima e nota bayesiana (prior 4,7, peso 10), conforme a spec de ranqueamento.
  - P4: avaliação com "não compareceu" fica retida até a mediação; se o não comparecimento for decretado, não existe avaliação.
  - P6: bairros por base oficial (CEP/IBGE).
  - P7: antes da janela do dia anterior, o prestador vê do cliente apenas nome, foto e região.
  - P8: o fluxo já impede atender o próximo sem fechar o anterior; só o último do dia corre risco. Regra: à meia-noite, atendimentos não fechados são encerrados automaticamente. Sem botão manual no MVP. O atendimento é tratado como fechado às 00:00:00, sem distinção do encerramento manual, e nunca como ausência. Penalizar ou avaliar esse caso fica para o futuro.
  - P9: nunca haverá filtro de horário na busca. Motivo estratégico: listagem enxuta mataria a descoberta e a venda futura de planos; o cliente abrir 2 a 3 prestadores antes de agendar é desejado.
  - P10: convite por SMS; WhatsApp depois.
  - P11: sanções (advertência, suspensão, banimento) nos termos, revisadas pelo advogado.
  - P12: antecedência mínima e máxima com padrão conservador, editável pelo prestador.
- **R12.** Ordenação conforme a especificação. No MVP só duas faixas: "Novo na plataforma" (3 dias, tag "Novo") e não pagantes, com desempate por avaliação, volume e sorteio. [DEFINIDO pela spec] Janela "Novo" começa na aprovação do prestador ou no lançamento público, o que vier depois (`max(...)`, D-16 da spec).

---

## 3. Inventário de funções

Classes: **E** = essencial para a hipótese. **H** = habilitadora. **A** = pode esperar. Custo só em escala relativa (P/M/G) se for pedido.

### 3.1 Cliente (no MVP)

| Função | Classe | Por quê / risco se faltar | Depende de |
|---|---|---|---|
| Cadastro com endereço/bairro e telefone verificado por SMS | H | Sem ele não há agendamento nem região do cliente. | Termos |
| Login, recuperação de senha | H | Acesso básico. | Cadastro |
| Termos e consentimento | H | Base legal (LGPD). Sem isso não lança. | Advogado |
| Perfil e alteração de dados | H | Corrigir endereço e telefone. | Cadastro |
| Listagem de prestadores | E | É o produto. Sem ela não há H3. | Aprovação, região, agenda |
| Filtros: ofício, serviço, data, região | E | Sem filtro a busca não é útil. | Listagem, R10 |
| Perfil do artista | E | O cliente escolhe quem entra em casa. | Listagem |
| Agendamento (reserva instantânea) | E | É a conversão. | Agenda do prestador, push |
| Consulta de agendamentos | E | O cliente precisa ver o que marcou. | Agendamento |
| Cancelamento | E | Sem ele o cliente fica preso a um horário. | R5, push |
| Avaliação do prestador | E | Reputação, base do ranking. | Check-out |
| Denúncia | H | Requisito de loja e segurança. | Painel |
| Bloqueio e desbloqueio de prestador | H | Segurança e requisito de loja. | Perfil |
| Privacidade do contato | H | Segurança do endereço e do telefone. | R3 |
| Contato da WeCareU | H | Canal de última instância. Requisito de loja. | Nenhuma |
| Sair da conta | H | Básico. | Login |
| Exclusão de conta | H | Exigida pela Apple e pela LGPD. | Cadastro |
| Aviso de cancelamento pelo prestador | H | Sem ele o cliente espera quem não vem. | Push |

### 3.2 Prestador (no MVP)

| Função | Classe | Por quê / risco se faltar | Depende de |
|---|---|---|---|
| Cadastro (status pendente, telefone verificado por SMS) | H | Entrada da oferta. | Termos, aprovação |
| Login, recuperação de senha | H | Acesso básico. | Cadastro |
| Termos e consentimento | H | Relação autônomo-plataforma e LGPD. | Advogado |
| Perfil, foto, alteração de dados | H | O cliente decide pela foto. Risco de reprovação da loja sem triagem. | Aprovação |
| Ofício, serviços, duração | E | Sem isso não há o que listar nem como calcular horário. | Cadastro |
| Regiões de atendimento (várias) | E | Define em quais listagens aparece. | R10 |
| Disponibilidade | E | Base do horário calculado. | Agenda |
| Antecedência mínima e máxima | E | Evita horários impossíveis no domicílio. | Disponibilidade |
| Intervalo de deslocamento | E | Sem ele dois clientes ficam colados. | Disponibilidade |
| Bloqueio simples de horário | E | Controle da agenda sem expor dados. | Disponibilidade |
| Reserva manual + convite SMS/WhatsApp | E | Motivo de uso antes da demanda (H1) e entrada de clientes (H2). | Caixa de autorização, advogado, disparo |
| Agendamentos recebidos e consulta | E | O prestador precisa ver o dia. | Agendamento |
| Perfil do cliente | H | Mostra os dados liberados pela regra de privacidade. | R3 |
| Check-in, cronômetro, check-out | E | Define "concluído" e libera avaliação. | Agendamentos |
| Cliente ausente | H | Sem o botão o prestador cancela (penalidade injusta) ou faz check-in falso. | Fluxo de atendimento |
| Cancelamento | E | Saída legítima do fluxo. | R5 |
| Push de novo agendamento | E | Sem aviso, o cliente espera quem nem sabe da marcação. | Agendamento |
| Ver avaliações recebidas | E | Retorno de reputação. | Avaliação do cliente |
| Denúncia, bloqueio e desbloqueio de cliente | H | Segurança do prestador. | Painel |
| Contato da WeCareU | H | Canal de última instância. | Nenhuma |
| Privacidade do contato | H | Telefone pessoal fora do perfil público. | R3 |
| Sair da conta, exclusão de conta | H | Loja e LGPD. | Cadastro |

Adicionar, por revisão: **verificação de telefone por SMS (R15)**, **reenvio único de push (R16)** e **encerramento automático à meia-noite (P8)**. Não há botão manual "encerrar atendimento".

### 3.3 Fora do MVP ("pode esperar")

| Função | Por que pode esperar | Quando reavaliar |
|---|---|---|
| Registro de falta (formal) | "Cliente ausente" e "não compareceu" cobrem o essencial. | Release de penalidade. |
| Lembretes (push, WhatsApp, SMS) e preferências de notificação | O push de novo agendamento cobre o crítico. | Quando houver faltas por esquecimento. |
| Remarcação, lista de espera, repetir agendamento, agendar para outra pessoa | Cancelar e marcar de novo resolve no começo. | Após volume de cancelamentos. |
| Portfólio, certificados, materiais, observações do atendimento | Serviço, região e foto bastam para escolher. | Se a conversão do perfil for baixa. |
| Chat | Abre caminho para combinar por fora. | Só com pagamento no app. |
| Suporte (central), histórico detalhado, lista de clientes do prestador | Contato da WeCareU cobre o início. | Quando o volume de contato crescer. |
| Favoritos, busca por nome, compartilhar perfil, indicação | Não testam a hipótese. | Após o objetivo central. |
| Outros endereços | Um endereço no cadastro basta. | Após uso real. |
| Entrada com conta externa | Atrito aceitável no começo. | Se o cadastro tiver abandono alto. |
| Sincronização com calendário | Não é decisiva. | Pós-MVP. |
| Resposta à avaliação, pausa de perfil e de serviço | O prestador pode usar o bloqueio. | Pós-MVP. |
| Plano de visibilidade, notificações de publicidade | Monetização vem depois. | Releases de planos. |
| Exportação de dados | Direito do titular, via pedido ao suporte no início (validar com advogado). | Antes de escala. |
| Contato de confiança | Segurança adicional. | Pós-verificação de identidade. |
| Prazo de cancelamento | Depende de penalidade. | Release de penalidade. |

---

## 4. Releases

Sem datas. Cada release avança quando os critérios de saída forem verdadeiros. Limiares [PENDENTE] devem ser calibrados com o beta.

### Release 1 — MVP: oferta e primeira marcação

- Objetivo: provar H1 e H2 e preparar H3.
- Escopo: seção 2.1. Fora: seção 2.2.
- Entrada: beta testers prontos; termos e política de privacidade revisados pelo advogado (inclusive disparo SMS/WhatsApp); aprovação de prestador funcionando; push de novo agendamento testado ponta a ponta; exclusão de conta presente e denúncia/bloqueio funcionando (revisão das lojas); responsável definido para denúncias e aprovações.
- Saída (limiares [PENDENTE]): pelo menos X prestadores aprovados por região-alvo com agenda configurada; pelo menos Y% dos aprovados usando a agenda na semana (H1); convites que viram download e cadastro (H2); depois de iniciado o marketing de clientes: buscas com resultado, busca → agendamento, agendamento → atendimento concluído e recompra (H3).
- Dependências: advogado, provedor de SMS/WhatsApp, aprovação das lojas (iOS e Android, dois apps).
- Riscos: seção 6.
- **Revisão recomendada:** dividir em **1a (oferta, H1 e H2)** e **1b (demanda, H3)**, com o gatilho de 1b definido por prestadores aprovados e com agenda ativa por bairro e ofício (limiares [PENDENTE]). Marketing de clientes começando com 1 ou 2 ofícios âncora e poucas zonas.

### Release 2 — Penalidade por falta e cancelamento tardio (modo sombra primeiro) [RECOMENDADO]

- Objetivo: reduzir faltas e cancelamentos tardios. Hipótese: a penalidade no ranking reduz as ocorrências.
- Escopo: definição de "tardio" (spec: menos de 12h), registro de falta formal, cálculo em modo sombra.
- Entrada: dados de cancelamento, cliente ausente e "não compareceu" coletados desde o MVP; piso de amostra de 20 atendimentos (definido na spec).
- Saída: sombra estável e sem injustiças evidentes nas denúncias; só então aplicar. Avisar prestadores antes.
- Risco: penalizar prestador por falha do cliente ou do app. Mitigação: contestação (H2.3 da spec).

### Release 3 — Verificação de identidade [RECOMENDADO], antes de qualquer monetização

- Objetivo: confiança formal, substituindo a aprovação manual.
- Escopo: documento + selfie, CPF único, bloqueio de novos agendamentos até concluir a verificação.
- Entrada: parecer do advogado sobre documentos e selfies (LGPD).
- Motivo da posição: vender visibilidade para quem não foi verificado amplifica o risco de segurança.

### Release 4 — Planos mensais + pontos avulsos

- Hipótese: prestador paga por visibilidade.
- Entrada: liquidez suficiente por região [PENDENTE]. Sem demanda o prestador não vê retorno.
- Pendentes: regras de pontos (validade, peso, teto), carência dos atuais, piso de qualidade, vitrine mínima.
- Jurídico: publicidade patrocinada identificável (CDC, art. 36).

### Release 5 — Subir agora

- Hipótese: o prestador paga por hora para preencher buraco na agenda.
- Entrada: buscas com data igual ou próxima em volume suficiente [PENDENTE]; plano pago funcionando.
- Pendente: significado de "hora" (P13 / D-06 da spec).

**Ordem das fases de ranqueamento.** A ordem definida é boa. O único risco é planos antes de haver demanda; por isso a entrada do Release 4 depende de liquidez e não de calendário.

**Melhorias do MVP (sem ordem fechada) [PENDENTE]:** feature flags por região, lembretes, remarcação, portfólio.

---

## 5. Métricas

**Prestador (H1):** cadastros iniciados → concluídos → aprovados; % de aprovados com serviços, regiões e disponibilidade configurados; % com pelo menos uma reserva manual; prestadores ativos por semana e retenção na semana seguinte; convites enviados por prestador.

**Convite (H2):** convite → download → cadastro do cliente → atendimento concluído.

**Marketplace (H3, depois do marketing):** % de buscas com resultado por região e ofício; busca → agendamento → atendimento concluído; recompra (mesmo prestador ou outro); cancelamentos por lado e tipo; "cliente ausente"; "prestador não compareceu"; % de atendimentos com avaliação.

**Qualidade e confiança:** denúncias por 100 atendimentos, tempo até mediação, bloqueios; atendimentos com check-in e check-out em intervalo muito curto (só observar); proxy de desintermediação [HIPÓTESE]: queda de agendamentos repetidos entre o mesmo par prestador-cliente após o primeiro.

---

## 6. Riscos

| # | Risco | Impacto | Mitigação | Status |
|---|---|---|---|---|
| 1 | Desintermediação após o primeiro contato | Mata a monetização futura | Dados do cliente só no dia anterior, sem chat, avaliação só dentro do app | Aceito |
| 2 | Estranho entra na casa de estranho sem verificação formal | Segurança | Aprovação manual; denúncia e bloqueio | Aberto: critério de aprovação (P2) |
| 3 | Cliente abre o app em região sem prestador | Churn de cliente | Marketing só onde há oferta; mensagem honesta | Mitigado |
| 4 | Prestador só usa o app se tiver utilidade própria | Sem H1 não há oferta | Agenda + reserva manual | [HIPÓTESE] |
| 5 | Convite por SMS/WhatsApp: LGPD, bloqueio do número, custo | Jurídico e operacional | Caixa de autorização, advogado, SMS primeiro, teto diário por prestador | Em andamento (Andrey) |
| 6 | Check-in/out sem geolocalização podem ser falsos | Avaliações e volume inflados | Aceito e planejado; cliente pode avaliar e reportar | Aceito |
| 7 | Prestador sem acesso ao próximo cliente (bateria, bug, rede, esquecimento do check-out) | Cliente sem atendimento | Botão "encerrar atendimento" no MVP; contato da WeCareU | Aberto (P8) |
| 8 | Reprovação nas lojas | Atrasa o lançamento | Exclusão de conta no MVP; aprovação manual cobre a triagem | Mitigado; confirmar nos textos atuais das lojas |
| 9 | Reservas manuais usadas para inflar volume ou avaliações | Distorce ranking | Reservas manuais fora de ranking até haver cliente vinculado [RECOMENDADO] | Aberto |
| 10 | Mediação, aprovações e denúncias dependem de pessoas | Gargalo operacional | Andrey e Bruno aprovam no início; contratar responsável no futuro | Aceito no início |
| 11 | Disputa sem dinheiro no app | Frustração | Escrever nos termos | Aberto |
| 12 | Relação prestador autônomo x plataforma | Risco de vínculo | Termos e fluxo revistos pelo advogado | Aberto |
| 13 | Dois apps e possível conta duplicada (prestador também é cliente) | Manutenção dobrada, auto-agendamento | P1 | Aberto |
| 14 | Prestadores fora de São Paulo se cadastram e não recebem demanda | Frustração e abandono | Mensagem clara no cadastro; aprovar só SP no início, demais em lista de espera [RECOMENDADO] | Aberto |
| 15 | Penalidade futura com poucos atendimentos | Injustiça | Modo sombra e piso de amostra de 20 | [RECOMENDADO] |
| 16 | Capacidade de entrega: 2 devs (Andrey, frontend Expo/React; Bruno, backend .NET) com apoio de IA, e padrão de qualidade de empresa de grande porte | Escopo grande para 2 pessoas | Release 1 com corte; ver `03` seção 5 | Aberto |
| 17 | Prestador exposto: reserva instantânea sem aceite, cliente desconhecido, sem reputação do cliente | Segurança e cancelamento de última hora | Prestador vê nome e tempo de conta do cliente; contestação de penalidade com motivo | Aberto (revisão) |
| 18 | Reserva dupla do mesmo slot (app x app, app x manual) | Conflito de agenda | Reserva atômica; critério de aceite | Aberto (revisão) |

---

## 7. Decisões

### 7.1 Definidas

| Decisão | Origem |
|---|---|
| Gratuito no lançamento; monetização por ranqueamento | Prompt |
| Filtros do MVP: ofício, serviço, data, região | Prompt |
| Região = bairro; prestador escolhe vários; atalho de zona em São Paulo | Rodada 4 |
| Faixas de ranqueamento e critérios de desempate | Spec |
| Ordem: MVP, penalidade, planos + pontos, subir agora | Prompt |
| Oferta primeiro; marketing de clientes só após base mínima | Discovery |
| Objetivo do MVP (frase H3) | Discovery |
| Pagamento direto com o prestador, fora do app | Discovery |
| Reserva instantânea | Discovery |
| Privacidade: dados liberados às 00:00:01 do dia anterior; próximo cliente só após encerrar o anterior (em revisão, ver R3) | Discovery |
| Dois apps (cliente e prestador) | Discovery |
| Listagem obrigatória no MVP | Discovery |
| Push de novo agendamento obrigatório | Discovery |
| Reserva manual com nome, celular, caixa de autorização e convite por SMS/WhatsApp; Andrey consulta o advogado | Discovery |
| Check-in/check-out por barra; check-out conclui; saídas: cancelar ou "cliente ausente" | Discovery |
| Sem filtro de duração para avaliação; cliente pode indicar que o prestador não compareceu | Rodada 4 |
| Avaliação só do prestador | Discovery |
| Aprovação manual de prestador antes de aparecer | Rodada 4 |
| Verificação de identidade fora do MVP | Discovery |
| Painel mínimo: denúncias e bloqueio de usuário; feature flags como melhoria | Discovery |
| Denúncia vai para a base da empresa; empresa media | Discovery |
| Busca vazia sem promessa de aviso | Discovery |

### 7.2 Pendentes, com recomendação

| # | Pendente | Recomendação |
|---|---|---|
| P1 | O prestador também é cliente: uma conta ou duas? | Uma identidade com dois papéis, apps separados. Bloquear auto-agendamento. Exclusão de conta apaga os dois papéis. | **[DEFINIDO, ver R19]**
| P2 | Critério de aprovação do prestador | **Decidido:** nome real, foto adequada e telefone verificado por SMS. Sem exigência de indicação de outro prestador (não agrega valor e aumenta o MVP; possível uso futuro em gamificação). Aprovam Andrey e Bruno no início. |
| P3 | Confirmar avaliação mínima e nota bayesiana (prior 4,7, peso 10) | Confirmar. Equivale a D-00, D-04, D-05 da spec. | **[DEFINIDO, ver R19]**
| P4 | Avaliação com "prestador não compareceu" entra na média? | Fica retida até a mediação; não conta na média nesse período. | **[DEFINIDO, ver R19]**
| P5 | Definição de "lançamento público" para a janela do "Novo" | Decidido (R13): São Paulo inteira; outras cidades só ativam o "Novo" quando o app chegar lá. Resta a data de São Paulo. |
| P6 | Fonte da lista de bairros de cada cidade | Base de CEP/IBGE. Cadastrar só cidades com base disponível. | **[DEFINIDO, ver R19]**
| P7 | Dados do cliente em agendamento dentro da janela do dia anterior | Liberação imediata. | **[DEFINIDO, ver R19]**
| P8 | Prestador esquece o check-out e trava o fluxo | Botão "encerrar atendimento" no painel, ou via contato da WeCareU. **Recomendado no MVP.** (Menos grave após a revisão do R3, mas o atendimento sem check-out ainda não conclui nem libera avaliação.) | **[DEFINIDO, ver R19]**
| P9 | Horário desejado como filtro | Não no MVP. Só data; o horário aparece na página do prestador (alinhado à spec D-02). | **[DEFINIDO, ver R19]**
| P10 | Canal do convite: SMS ou WhatsApp | SMS primeiro; WhatsApp após modelo de mensagem aprovado. | **[DEFINIDO, ver R19]**
| P11 | Política de sanções e texto dos termos | Advertência, suspensão e banimento nos termos, revisados pelo advogado. | **[DEFINIDO, ver R19]**
| P12 | Valores padrão de antecedência mínima e máxima | Padrão conservador, editável pelo prestador. | **[DEFINIDO, ver R19]**
| P13 | Pós-MVP: significado de "hora" no Subir agora, regras de pontos, carência dos atuais | "Hora" = período de exposição; pontos com validade e teto; fundadores com benefício na carência. Decidir antes do Release 4. |
