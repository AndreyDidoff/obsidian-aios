# WeCareU — Conferência: documento de MVP x especificação de busca e ranqueamento (v0.3.1)

Fonte de verdade sobre busca, agenda, avaliações e ranking: `especificacao-busca-e-ranqueamento.md` (v0.3.1). Este arquivo lista apenas o que precisa mudar ou ser acrescentado nela por causa das decisões do MVP.

## A. Conflitos: o que precisa mudar na spec

1. **Ativação exige identidade verificada (§6.9, D-13) e CPF único.** O MVP exclui a verificação. Ativação passa a ser: aprovação manual + perfil completo + agenda configurada. `ativado_em` vira `aprovado_em`; o status `ativo` da spec corresponde a "aprovado". D-13 vai para o release de verificação. Recomendado coletar CPF (autodeclarado) no cadastro para manter a regra de uma ativação por pessoa contra recriação de conta para ganhar "Novo".
2. **Conclusão do atendimento (§6.11, D-03).** A spec auto-conclui em 24h; o MVP conclui pelo check-out do prestador. Substituir a regra. Em `agendamentos` acrescentar `check_in_em`, `check_out_em` e o status `em_atendimento`. "Cliente ausente" = `falta_cliente`. "Não compareceu" reportado pelo cliente = `falta_prestador` pendente de mediação (estado intermediário que a spec não tem).
3. **Região (§6.5).** Manter a spec: hierarquia cidade → zona → bairro, e o ancestral cadastrado cobre os bairros. Em R10 do MVP, o atalho "selecionar a zona toda" é só interface.
4. **Antecedência (§5).** `ANTECEDENCIA_MIN_MIN` é global na spec; o MVP quer mínima e máxima por prestador. Mover a mínima para `prestadores` (padrão 120 min) e criar `antecedencia_max_dias`, que não existe na spec.
5. **Exibição de nota (D-05).** Abaixo de `NOTA_EXIBIR_MIN_N` (3) a spec mostra "Novo" ou "Poucas avaliações". Colide com a tag "Novo" da faixa 2. Mostrar só "Poucas avaliações" e reservar "Novo" para a tag.
6. **Cancelamento tardio.** A spec define tardio como menos de 12h (`LIMITE_CANCELAMENTO_TARDIO_H`); o MVP diz "sem prazo". O app segue sem trava de cancelamento, mas o prestador deve ser avisado desde o cadastro de que a regra existe e será aplicada retroativamente sobre os dados. A penalidade permanece; a saída é a contestação com motivo (H2.3), por exemplo para segurança. (Corrige a recomendação anterior de "cancelar sem penalidade".)
7. **Janela do "Novo" (D-16) [DEFINIDO pelo dono: lançamento público = cidade de São Paulo inteira].** `LANCAMENTO_PUBLICO_EM` é um instante único, mas o marketing de clientes é por região. Em zona sem marketing os 3 dias passam sem clientes. `LANCAMENTO_PUBLICO_EM` = quando o marketing de clientes liga em São Paulo (sem zona). Prestadores de outras cidades se cadastram normalmente, mas a tag "Novo" só ativa quando o app chegar oficialmente na cidade [DEFINIDO]. Na spec: `LANCAMENTO_PUBLICO_EM` passa a ser por cidade (nulo até o lançamento da cidade), e `novo_ate` só é calculado quando houver data para a cidade do prestador.

## B. Lacunas: a spec não cobre

- **Reserva manual.** Precisa de `origem` (app | manual), `cliente_id` anulável com telefone do cliente e vínculo posterior quando o cliente se cadastra. Ocupa agenda, mas não entra em `volume_90d`, avaliação nem janela de penalidade até haver cliente vinculado. [RECOMENDADO]
- **Reserva atômica.** Reserva instantânea sem aceite exige impedir reserva dupla do mesmo slot (cliente x cliente, cliente x reserva manual). Adicionar critério de aceite.
- **Motivo do cancelamento.** Acrescentar `motivo_cancelamento` além de quem cancelou e quando.
- **Origem do cliente.** Acrescentar o campo (convite do prestador | indicação | orgânico) para medir a H3.
- **Privacidade (R3 do MVP).** A liberação de endereço e telefone por horário não está na spec. É regra de API, não de ranking.

- **Encerramento à meia-noite.** Atendimento em andamento às 00:00:00 vira fechado, sem distinção do manual e sem ser falta. Substitui a auto-conclusão de 24h da spec (D-03).
- **Telefone verificado.** Campo de telefone verificado por SMS (prestador e cliente) no cadastro.
- **Push visualizado.** Registrar envio, reenvio único e visualização do push de novo agendamento.
- **Avaliação retida.** Avaliação de atendimento com "não compareceu" fica retida até mediação; se decretado, não existe avaliação.
- **Ofícios exibidos.** Só ofícios e serviços com pelo menos 1 prestador aprovado na região do cliente.

## C. Confirmações pendentes

- D-00 (avaliações no MVP), D-04 (nota bayesiana 4,7 / peso 10) e D-05 (exibição a partir de 3 avaliações) podem passar a [DEFINIDO] se o dono confirmar. Já estão no escopo do MVP.
- P5 do MVP: a regra já está fechada na spec (`max(ativado_em, LANCAMENTO_PUBLICO_EM)`); falta definir a data/gatilho (por zona).
- O piso de amostra do Release 2 já está definido na spec: 20 atendimentos.

## D. O que não muda na spec

Filtros do MVP, grupos A e B, faixas, desempate, ordem das fases, buffer só em torno de agendamentos, nota bayesiana, janela mista de penalidade, modo sombra, vitrine mínima e piso de qualidade permanecem como estão.
