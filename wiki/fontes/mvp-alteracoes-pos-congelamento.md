---
tipo: fonte
arquivo: ingeridos/06-alteracoes-pos-congelamento.md
origem: deltas do dono depois do congelamento dos arquivos 00 a 04; o cliente prevalece sobre o congelado
criado: 2026-11-05
atualizado: 2026-11-05
---

# Alterações após o congelamento

Este arquivo só registra o delta. Os arquivos 00 a 04 não são reescritos. Onde o delta muda [[mvp-final]] ou [[spec-busca-e-ranqueamento]], no app do cliente prevalece este arquivo. O detalhamento fechado do cliente está em [[mvp-funcoes-e-telas]]. Cada item aponta a seção no `05`.

- Card do grupo B sem data: o card não mostra a data; o cliente abre o perfil e inicia o agendamento para ver os horários. O grupo B segue a mesma regra. Muda a spec. Seção: `Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono]`.
- Card sem horários livres, em nenhum grupo. Muda a spec (D-02). Seção: `Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono]`.
- Serviço com preço no MVP, mostrado ao cliente no agendamento. A faixa de preço do card continua digitada pelo artista. Muda o `04` e o `01`. Seções: `Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono]` e `Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO]`.
- Uma foto de divulgação, obrigatória, sem aprovação prévia; denúncia no perfil e remoção pela equipe. No MVP ela não aparece no perfil. Seções: `Registro de detalhamento: M05/M02 Foto de divulgação e tag no card [DEFINIDO pelo dono]` e `Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO]`.
- Listagem inicial sem data, ofício ou serviço: lista única, sem grupos A/B. Disponibilidade e A/B só depois que o cliente escolhe uma data. Muda a spec. Seção: `Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono]`.
- Pré-agendamento: retenção temporária do horário; o cadastro do cliente ocorre antes do fluxo, nunca com horário retido. Seções: `M06 Pré-agendamento [DEFINIDO pelo dono]` e `Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO]`.
- Vários endereços salvos, com nome, e escolha na home como local de atendimento. Muda o `04`. Seções: `Registro de detalhamento: Home do cliente [DEFINIDO]` e `Endereço de atendimento e troca pela listagem [DEFINIDO]`.
- Cancelamento sem motivo: registra quem e quando. Muda M06-F05. Seção: `Cancelamento pelo cliente (M06-F05) [DEFINIDO]`.
- Detalhe do agendamento fora do MVP: o cartão não é tocável e não há tela de detalhe. Seção: `Registro de detalhamento: Home do cliente [DEFINIDO]`.
- Cadastro em chatbot, sem SMS: o celular só é coletado; a chave de validação é o CPF. Conflito com `01`, `04` e a spec. Seção: `Cadastro do cliente: formato e dados [DEFINIDO]`.
- Avaliação no próprio cartão, sem card separado. Muda o `04` no caso "prestador não compareceu". Seção: `Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO]`.
- Lembretes de atendimento e de reagendamento v0 entram no MVP. Muda o `04` §5. Seção: `Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]`.
- Sem central de notificações: só push. O push de confirmação do agendamento fica fora do MVP. Seção: `Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO]`.
- Bloqueio sem desbloqueio pelo usuário e sem tela de bloqueados; o desbloqueio é só pela equipe. Diverge de `01`, `04` e M12-F02. Seção: `Bloqueio (M12-F02) [DEFINIDO]`.
- Sanção no MVP: só suspensão por tempo indeterminado, por conta e por app. Seção: `5. Conta suspensa ou banida pelo backoffice [DEFINIDO]`.
- Convite sem vínculo: só mensagem de atenção, sem link de aterrissagem, sem cruzamento de dados e sem vínculo automático da reserva ao cadastro. Muda M07. Seção: `Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO]`.
- Biometria vale para o desbloqueio do app e não substitui o login. Seção: `Sessão do cliente [DEFINIDO]`.
- 401 genérico: qualquer perda de autorização volta como o mesmo 401, sem motivo; o motivo de suspensão ou banimento só aparece na tentativa de login. Seção: `Sessão do cliente [DEFINIDO]`.
- Termos de Uso, Política de Privacidade e e-mails transacionais diferidos; não bloqueiam o fechamento do cliente. Seção: `Pendências do app do cliente [ATUALIZADO]`.
- Legenda de pagamento fora do app no resumo da confirmação, sob o preço estimado; não aparece no cartão da Home nem da Agenda. Seção: `M06 Confirmação do agendamento [DEFINIDO]`.
- Fechamento do cliente: detalhamento de produto do Cliente para o MVP fechado; o próximo bloco é o lado do Artista. Seção: `Pendências do app do cliente [ATUALIZADO]`.
