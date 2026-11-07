# WeCareU — MVP final (Release 1)

Documento de fechamento do MVP, no nível de produto. Sem código, sem datas, sem estimativas. Detalhe e histórico: `01-mvp-e-releases.md`. Mudanças na spec de busca: `02-mudancas-na-especificacao.md`. Riscos e pendências: `03-revisao-riscos-e-pendencias.md`.

Marcadores: [DEFINIDO] decidido pelo dono ou pela spec. [RECOMENDADO] recomendação minha. [PENDENTE] aberto. [HIPÓTESE] a validar com dados.
Aviso: pontos de LGPD, CDC e relação prestador-plataforma são para validar com advogado.

## 1. Tese e público

- App de agendamento de beleza e bem-estar em domicílio. O prestador ("artista") vai até o cliente. 100% gratuito no lançamento; monetização futura por ranqueamento pago. [DEFINIDO]
- Dois apps (cliente e prestador). Lançamento público: cidade de São Paulo inteira. Qualquer cidade pode cadastrar prestadores; a tag "Novo" só ativa quando o app chegar oficialmente na cidade do prestador. [DEFINIDO]
- Estratégia: oferta primeiro (prestador), demanda depois (cliente). O prestador adota o app como agenda; os clientes chegam por convite dele e depois por marketing. [DEFINIDO]
- Hipóteses a provar: H1 o prestador usa o app como agenda mesmo antes da demanda orgânica; H2 o cliente convidado instala, vê o agendamento e conclui o atendimento; H3 (objetivo central) alguém que nunca viu o prestador acha, marca, é atendido e marca de novo. [HIPÓTESE]
- O MVP não prova: que o ranqueamento pago funciona, nem que a desintermediação não acontece.

## 2. Princípios [DEFINIDO]

1. Toda regra de negócio fica no backend. O app só apresenta e coleta dados de uso.
2. MVP mínimo viável; o resto entra em releases.
3. Qualidade de empresa de grande porte, com equipe de 2 pessoas e apoio de IA.
4. Nunca haverá filtro de horário na busca: a listagem cheia sustenta a descoberta e a venda futura de planos.

## 3. Escopo: o que entra

**Cliente**
- Cadastro com endereço/bairro e telefone verificado por SMS; login; recuperação de senha; termos e consentimento; perfil; sair; exclusão de conta.
- Listagem de prestadores com filtros de ofício, serviço, data e região. Só aparecem ofícios e serviços com pelo menos 1 prestador aprovado na região do cliente.
- Perfil do artista; agendamento instantâneo; consulta de agendamentos; cancelamento; aviso quando o prestador cancela.
- Avaliação do prestador (1 a 5, mínima), com opção "prestador não compareceu".
- Denúncia, bloqueio e desbloqueio; contato da WeCareU.

**Prestador**
- Cadastro (entra como pendente) com telefone verificado por SMS; login; termos; perfil e foto; exclusão de conta.
- Ofício, serviços e duração, regiões de atendimento (várias, com atalho de zona), disponibilidade, antecedência mínima e máxima, intervalo de deslocamento, bloqueio de horário.
- Reserva manual para cliente próprio (nome e celular obrigatórios, caixa de autorização) e convite por SMS.
- Agenda e agendamentos recebidos; dados do cliente conforme a regra de privacidade.
- Fluxo de atendimento: check-in e check-out por barra, cronômetro, "cliente ausente", cancelamento. Atendimento não fechado vira fechado às 00:00:00, sem ser falta.
- Push de novo agendamento, com um reenvio fixo se não for visualizado.
- Ver avaliações recebidas; denúncia, bloqueio, desbloqueio; contato da WeCareU.

**Operação**
- Painel mínimo: aprovação de prestador, lista de denúncias, bloqueio de usuário. Aprovam Andrey e Bruno no início.
- Critério de aprovação: nome real, foto adequada, telefone verificado por SMS. Sem indicação de outro prestador.
- Mediação de denúncias pela empresa; sanções (advertência, suspensão, banimento) nos termos.

## 4. Regras de produto que mais importam [DEFINIDO]

- Pagamento direto com o prestador, fora do app.
- Reserva instantânea, sem aceite; horário calculado da agenda, bloqueios, deslocamento e antecedência. Sem reserva dupla do mesmo horário.
- Privacidade: antes de 00:00:01 do dia anterior ao atendimento, o prestador vê do cliente só nome, foto e região. Depois, vê os dados de todos os clientes do dia, para planejar rotas. Agendamento já dentro da janela libera na hora.
- Cancelamento sem prazo mínimo no MVP; guarda-se quem cancelou, quando e o motivo.
- "Não compareceu": avaliação retida até a mediação; se decretado, não existe avaliação.
- Ordenação: faixa "Novo" (3 dias, a partir do mais tardio entre aprovação e lançamento na cidade), depois os demais, com desempate por nota, volume e sorteio estável na sessão. Nota com média ponderada (prior 4,7, peso 10), exibida a partir de 3 avaliações.
- Prestador também pode ser cliente (uma identidade, dois papéis), aparece na listagem, mas não agenda para si.
- Busca vazia: "ainda estamos chegando na sua região", sem prometer aviso.

## 5. O que fica fora do MVP

Verificação de identidade (documento e selfie), pagamento no app, penalidade, planos, pontos, "Subir agora", trava de geolocalização, prestador avaliando cliente, prazo de cancelamento, feature flags, analytics de uso do app (mapas de calor, funil), lembretes, remarcação, chat, portfólio, favoritos, outros endereços, login social, resposta a avaliação, configuração do prazo de reenvio do push. A ordem dos releases seguintes será discutida depois.

## 6. Fatos de negócio que o backend registra [RECOMENDADO, para confirmação]

Lista a fechar antes do lançamento, porque o histórico não se recupera depois:
- Cadastro: usuário criado, telefone verificado (e SMS enviado sem verificação), prestador aprovado ou reprovado e por quem.
- Oferta: ofício, serviço, região, agenda configurada, bloqueio criado, primeiro agendamento do prestador.
- Convite: reserva manual criada, convite enviado, cliente baixou, cliente cadastrou, reserva vinculada ao cliente.
- Agendamento: criado (origem: app, convite do prestador, indicação), cancelado (por quem, quando, motivo), push enviado, reenviado e visualizado.
- Atendimento: check-in, check-out, encerrado às 00:00:00, cliente ausente, "não compareceu" reportado e seu desfecho.
- Reputação e segurança: avaliação criada, denúncia, bloqueio, sanção.
- Busca: buscas com e sem resultado, por região e ofício.

## 7. Critérios de passagem [HIPÓTESE; limiares PENDENTE, calibrar no beta]

- **Antes do lançamento:** termos e política de privacidade revisados pelo advogado, incluindo disparo de SMS; aprovação de prestador, push e SMS testados ponta a ponta; exclusão de conta, denúncia e bloqueio funcionando (lojas); responsável pelas aprovações e denúncias definido.
- **1a, oferta (H1, H2):** prestadores aprovados por região-alvo com agenda configurada; prestadores que continuam usando a agenda semana a semana; convites que viram download, cadastro e atendimento concluído.
- **1b, demanda (H3):** só liga o marketing de clientes quando houver prestadores aprovados e ativos por região e ofício. Começar com 1 ou 2 ofícios âncora. Depois: buscas com resultado, busca para agendamento, agendamento para atendimento concluído e recompra.
- **Saúde da operação:** tempo de aprovação, denúncias por atendimento, cancelamentos por lado, push visualizado, atendimentos encerrados à meia-noite.

## 8. Riscos restantes

1. **Segurança do prestador:** reserva instantânea com cliente desconhecido e sem reputação do cliente. Mitigação: nome, foto e telefone verificado, bloqueio e denúncia, contato da WeCareU.
2. **Segurança do cliente:** prestador entra na casa de um estranho sem verificação de identidade, só aprovação manual. Risco aceito de propósito; verificação é release posterior.
3. **Desintermediação:** pagamento e contato fora do app. Aceito.
4. **Encerramento à meia-noite:** atendimento que passa da meia-noite seria fechado às 00:00:00 com a duração cortada. [DEFINIDO] Risco aceito no MVP: cerca de 90% dos prestadores serão manicures, cabeleireiros e afins, que não atendem nesse horário. Reavaliar se entrarem ofícios noturnos.
5. **Liquidez por região:** sem prestadores suficientes, o cliente encontra listagem vazia. Mitigação: oferta primeiro, ofícios âncora, filtro de ofícios com oferta.
6. **Prestadores fora de São Paulo:** cadastram e não recebem demanda. Mitigação: mensagem clara no cadastro e estado "não ativado na cidade".
7. **Reservas manuais inflando volume ou nota:** ficam fora de ranking até haver cliente vinculado. [RECOMENDADO]
8. **Jurídico:** SMS de convite sem consentimento do cliente, relação autônomo x plataforma, termos de sanção. Depende do advogado.
9. **Capacidade:** 2 devs para escopo grande e padrão alto. Mitigação: corte do MVP e contrato de API versionado.
10. **Operação manual:** aprovações e mediação dependem de Andrey e Bruno; vira gargalo com o crescimento.

## 9. Pendências restantes

- **Escopo do MVP: fechado [DEFINIDO].** Informações futuras sobre o MVP só detalham, não alteram o escopo.
- **Métricas [DEFINIDO]:** não há dados nem planejamento de métricas ainda. Nenhum limiar numérico será fixado agora. O beta mede a linha de base (o que acontece de fato) e os limiares de passagem são definidos depois, com esses dados. Gatilho do marketing de clientes decidido por julgamento do dono sobre a linha de base.
- **Releases após o MVP, incluindo P13 (planos, pontos, "Subir agora"):** só serão discutidos perto do lançamento do MVP. Fora das pendências do MVP. [DEFINIDO]

- Lançamento público em São Paulo: 01/01/2027 (`LANCAMENTO_PUBLICO_EM`). [DEFINIDO]
- Parecer do advogado (SMS de convite, termos, LGPD): considerado concluído pelo dono. [DEFINIDO]
- A lista de fatos de negócio (seção 6) segue para o backend depois de passar pela base de conhecimento, que filtra o que já existe. Passo do dono.

