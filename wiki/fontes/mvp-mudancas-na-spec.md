---
tipo: fonte
arquivo: ingeridos/02-mudancas-na-especificacao.md
origem: conferência do MVP contra a spec de busca v0.3.1
criado: 2026-11-03
atualizado: 2026-11-03
---

# Mudanças do MVP na spec de busca

Lista o que [[spec-busca-e-ranqueamento]] precisa mudar por causa do [[mvp]]. Não reescreve a spec. Grupos A e B, faixas, desempate, ordem das fases, buffer só em torno de agendamentos, nota bayesiana, janela mista de penalidade, modo sombra, vitrine mínima e piso de qualidade permanecem.

## Conflitos a aplicar na spec

- Ativação no MVP é aprovação manual, perfil completo e agenda configurada. Verificação de identidade sai desta fase. `ativado_em` vira `aprovado_em`.
- Conclusão é o check-out. À meia-noite, atendimento aberto vira fechado, sem ser falta. A auto-conclusão de 24 horas sai.
- Região continua cidade, zona e bairro. O atalho "zona toda" é só interface.
- Antecedência mínima e máxima são do artista, não um único número global.
- A tag "Novo" fica para a faixa de destaque. Abaixo de 3 avaliações, o texto de nota é "Poucas avaliações".
- O app não trava cancelamento. O artista deve ser avisado de que a penalidade de menos de 12 horas existe e será aplicada sobre os dados já gravados. Isto está nesta conferência; [[mvp-final]] não repete o aviso.
- `LANCAMENTO_PUBLICO_EM` é por cidade. Em São Paulo, 01/01/2027, conforme [[mvp-final]].

## Lacunas que a spec não cobre

Reserva manual com origem e cliente anulável. Reserva sem horário duplicado. Motivo do cancelamento. Origem do cliente. Liberação de endereço e telefone por horário. Telefone verificado. Push enviado, reenviado e visualizado. Avaliação retida quando há "não compareceu". Ofícios exibidos só quando há artista aprovado na região.

Reserva manual fora de volume, nota e penalidade até o cliente vincular, e CPF autodeclarado para não repetir a janela "Novo", estão como recomendação. Não viraram decisão em [[mvp-final]].
