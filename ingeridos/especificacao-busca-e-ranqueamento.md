# App de Agendamento de Beleza e Bem-Estar — Especificação de Busca, Disponibilidade e Ranqueamento

| Campo | Valor |
|---|---|
| Versão | 0.3.1 (rascunho para validação) |
| Data | 23/10/2026 |
| Escopo | MVP gratuito + evolução em 4 fases até o ranqueamento pago completo |
| Público | Produto, engenharia e agentes de IA |
| Mudança da v0.2 | Destaque de novos incorporado ao MVP; penalidade antecipada para a Fase 2; planos + pontos passam a Fase 3; "subir agora" passa a Fase 4. v0.3.1: regra de contagem da janela de "novo" a partir do lançamento público fechada como [DEFINIDO] (D-16) |

---

## 0. Como usar este documento

**Marcadores de status**

- **[DEFINIDO]**: decisão do dono do produto.
- **[RECOMENDADO]**: proposta desta especificação. Vale como padrão até alguém decidir o contrário.
- **[PENDENTE]**: decisão em aberto, listada na seção 11 com recomendação.

**Regras para agentes de IA que implementarem este documento**

1. Nunca escreva constantes no código. Use `CFG.*` (seção 5).
2. `rank_score` é interno. Não exibir nem retornar em API pública.
3. Fases 2, 3 e 4 têm flag própria. Faixa 3 e faixa 1 só ativam com a flag da fase ligada.
4. Registrar os eventos de atendimento desde a Fase 1, mesmo que nada os use ainda.
5. Timestamps em UTC no banco. Regras de calendário (dia, horário de atendimento) em `America/Sao_Paulo`.
6. Cada fase adiciona uma camada. Não reescreva a camada anterior.

---

## 1. Visão geral

Marketplace de serviços de beleza e bem-estar com **atendimento em domicílio**: o prestador vai até o cliente na data e hora combinadas. Lançamento 100% gratuito. A monetização futura é por **ranqueamento pago**.

**Princípios**

1. **Disponibilidade vem antes de ranking.** Ninguém aparece sem vaga real.
2. **Ranking progressivo.** Cada fase soma uma camada, sem reescrever a anterior.
3. **Dinheiro compra faixa, não apaga mérito.** Dentro de cada faixa, quem entrega melhor aparece primeiro.
4. **Transparência.** O que é pago é identificado como tal.
5. **Dados primeiro.** Eventos que a penalidade vai precisar são gravados desde o dia 1.

---

## 2. Glossário

| Termo | Definição |
|---|---|
| Ofício | Tipo de profissional (ex.: manicure, massagista). |
| Serviço | Subcategoria do ofício (ex.: alongamento em gel). Tem duração e preço por prestador. |
| Região | Nó de uma hierarquia normalizada (cidade → zona → bairro). |
| Slot | Horário de início em que o serviço cabe inteiro na agenda. |
| Buffer | Tempo de deslocamento reservado antes e depois de cada agendamento. |
| Grupo A | Prestadores com slot livre na data pedida. |
| Grupo B | Prestadores sem slot na data pedida, mas com slot em data próxima. |
| Faixa | Bloco de ordenação (1 a 4). Faixas nunca se misturam. |
| `rank_score` | Pontuação interna que ordena prestadores dentro da mesma faixa. Escala inteira em milésimos (4860 = 4,860). |
| Nota bayesiana | Média de avaliações suavizada por um valor prior. Evita que 1 avaliação defina a posição. |
| Ocorrência penalizável | Falta ou cancelamento tardio **causado pelo prestador**. |
| Ativação | Momento em que o prestador cumpre os requisitos para aparecer nas buscas. |

---

## 3. Mapa de fases

**Ordem de lançamento [DEFINIDO]**

| Fase | Nome | Entrega | Faixas ativas | Flag |
|---|---|---|---|---|
| 1 | MVP | Busca, agenda, agendamento, avaliações, destaque de novos, ranking base | 2 e 4 | — |
| 2 | Penalidade | Faltas e cancelamentos tardios reduzem o `rank_score` | 2 e 4 | `PENALIDADE_MODO` |
| 3 | Planos + pontos | Assinatura e pontos avulsos de ranqueamento | 2, 3 e 4 | `FF_PLANOS` |
| 4 | Subir agora | Destaque pago por hora, com limite diário | 1, 2, 3 e 4 | `FF_SUBIR_AGORA` |

**Dependências**

- Fase 2 usa os eventos gravados desde a Fase 1.
- Fase 3 usa a penalidade da Fase 2 no piso de qualidade dos pontos.
- Fase 4 reaproveita a regra de elegibilidade por distância de data criada na Fase 1 (destaque de novo).

### 3.1 Mesma busca, quatro fases

Busca: manicure, sábado 31/10/2026, cliente em Santana. Ordem do **Grupo A** em cada fase (elenco da seção 6.10; detalhes nas seções de cada fase):

| Pos. | Fase 1 | Fase 2 | Fase 3 | Fase 4 |
|---|---|---|---|---|
| 1 | Ana | Ana | Ana | Eva |
| 2 | Bia | Carla | Duda | Ana |
| 3 | Carla | Duda | Carla | Duda |
| 4 | Duda | Eva | Eva | Carla |
| 5 | Eva | Bia | Bia | Bia |

O Grupo B (Fabi, Hana) vem depois do Grupo A em todas as fases.

### 3.2 Implicações da ordem escolhida

1. **No lançamento coletivo, todos são "novos" ao mesmo tempo.** Se todos os prestadores forem ativados antes do lançamento público, a janela de 3 dias seria gasta antes de qualquer cliente chegar. Regra [DEFINIDO]: a contagem começa em `max(ativado_em, LANCAMENTO_PUBLICO_EM)` (D-16).
2. **A penalidade chega cedo, com pouco histórico.** O piso de amostra (20 atendimentos) evita punir quem tem poucos atendimentos. Lançar em modo sombra (D-15).
3. **Planos vêm depois da penalidade.** O piso de qualidade dos pontos já nasce completo (nota e taxa de faltas).
4. **A primeira receita só chega na Fase 3.** Planejar o caixa para o período entre o lançamento e os planos.

---

## 4. Arquitetura do ranking (vale para todas as fases)

### 4.1 Pipeline de uma busca

1. **Filtros duros:** ofício, serviço, região. Eliminam, não ranqueiam.
2. **Disponibilidade:** o prestador precisa ter slot livre na data pedida (Grupo A) ou em data próxima (Grupo B).
3. **Grupo:** A se há slot na data pedida, senão B.
4. **Faixa:** 1 a 4 conforme a situação do prestador (só as faixas das fases já lançadas).
5. **Score:** `rank_score` (e bônus de pontos, a partir da Fase 3).
6. **Desempate:** volume dos últimos 90 dias, depois sorteio.

### 4.2 Chave de ordenação final

```
ORDER BY
  grupo ASC,                          -- A antes de B
  faixa ASC,                          -- 1, 2, 3, 4
  (grupo = 'B' ? dist_dias : 0) ASC,  -- só no grupo B
  score_efetivo DESC,                 -- rank_score (+ bônus de pontos na faixa 3)
  volume_90d DESC,
  hash(sessao_id, prestador_id) ASC   -- sorteio estável por sessão
```

O sorteio usa seed por sessão para a paginação não embaralhar entre páginas.

### 4.3 Elegibilidade das faixas 1 e 2

As faixas 1 e 2 só valem quando `dist_dias <= JANELA_PROXIMA_BOOST_DIAS` (data igual ou próxima, conforme definido). Fora dessa janela, o prestador é tratado pela faixa base (3 se tem plano, 4 se não tem).

### 4.4 Materialização

Os campos de ranking ficam **pré-calculados** na tabela `prestadores`. A busca só calcula disponibilidade e ordena. Recalcular quando:

- uma avaliação é publicada;
- um atendimento muda para um status final;
- job diário: expira janelas (volume 90 dias, `novo_ate`, ocorrências, pontos e destaques).

---

## 5. Parâmetros de configuração (`CFG`)

| Parâmetro | Valor | Status | Fase |
|---|---|---|---|
| `BAYES_M` (nota prior) | 4,7 | [RECOMENDADO] | 1 |
| `BAYES_C` (peso do prior) | 10 | [RECOMENDADO] | 1 |
| `NOTA_EXIBIR_MIN_N` | 3 | [RECOMENDADO] | 1 |
| `PUBLICACAO_ATRASO_H` | aleatório entre 24 e 72 | [DEFINIDO] o atraso; faixa [RECOMENDADO] | 1 |
| `JANELA_ALTERNATIVA_DIAS` | 14 | [RECOMENDADO] | 1 |
| `BUFFER_PADRAO_MIN` | 30 (configurável pelo prestador) | [DEFINIDO] a configuração; valor [RECOMENDADO] | 1 |
| `PASSO_SLOT_MIN` | 30 | [RECOMENDADO] | 1 |
| `ANTECEDENCIA_MIN_MIN` | 120 | [RECOMENDADO] | 1 |
| `JANELA_VOLUME_DIAS` | 90 | [RECOMENDADO] | 1 |
| `NOVO_DIAS` | 3 | [DEFINIDO] | 1 |
| `JANELA_PROXIMA_BOOST_DIAS` | 2 | [RECOMENDADO] | 1 e 4 |
| `LANCAMENTO_PUBLICO_EM` | data do lançamento público | [DEFINIDO] a regra; data a informar | 1 |
| `JANELA_PENALIDADE_ATEND` | 50 | [DEFINIDO] | 2 |
| `JANELA_PENALIDADE_DIAS_MAX` | 90 | [RECOMENDADO] | 2 |
| `PISO_AMOSTRA_PENALIDADE` | 20 | [RECOMENDADO] | 2 |
| `LIMITE_CANCELAMENTO_TARDIO_H` | 12 | [RECOMENDADO] | 2 |
| `PESO_PONTO_MILLI` | 10 | ilustrativo | 3 |
| `TETO_BOOST_MILLI` | 300 | ilustrativo | 3 |
| `PISO_NOTA_BOOST_MILLI` | 4000 | ilustrativo | 3 |
| `TETO_PENALIDADE_BOOST` | 15% | ilustrativo | 3 |
| `VITRINE_MIN_FAIXA4_TOP10` | 2 | [RECOMENDADO], opcional | 3 |
| `SUBIR_AGORA_MAX_H_DIA` | 3 | [DEFINIDO] | 4 |
| `SUBIR_AGORA_MAX_CARDS` | 3 | [RECOMENDADO] | 4 |

**Flags:** `PENALIDADE_MODO = off | shadow | on` (Fase 2), `FF_PLANOS` (Fase 3), `FF_SUBIR_AGORA` (Fase 4). Todas começam desligadas. O destaque de novo é parte do MVP e não tem flag.

---

## 6. FASE 1 — MVP

### 6.1 Objetivo

Lançar um marketplace gratuito em que o cliente encontra um prestador **com vaga real** para a data que quer, na região dele, e agenda. Quem acabou de chegar recebe exposição inicial. O ranking é simples e preparado para as próximas fases.

### 6.2 Histórias

| ID | História |
|---|---|
| H1.1 | Como **cliente**, quero filtrar por ofício, serviço, data e região, para ver só quem pode me atender. |
| H1.2 | Como **prestador**, quero cadastrar horários, bloqueios, tempo de deslocamento, duração dos serviços e regiões atendidas, para não receber agendamentos que não posso cumprir. |
| H1.3 | Como **cliente**, quando ninguém tem vaga na minha data, quero ver quem tem vaga em data próxima, com a data real no card, para decidir sem refazer a busca. |
| H1.4 | Como **cliente**, quero agendar o horário escolhido. |
| H1.5 | Como **cliente**, quero avaliar o prestador (1 a 5 estrelas) depois do atendimento concluído. |
| H1.6 | Como **prestador novo**, quero aparecer em destaque nos meus primeiros dias, para conseguir clientes antes de ter avaliações. |
| H1.7 | Como **cliente**, quero ver quem é novo identificado com a tag "Novo", para saber que ainda não tem histórico. |

### 6.3 Escopo

**Dentro**

- Filtros: ofício, serviço, data, região **[DEFINIDO]**.
- Região do cliente comparada com as regiões atendidas cadastradas pelo prestador **[DEFINIDO]**.
- Agenda com horário de atendimento, agendamentos existentes, bloqueios e tempo de deslocamento **[DEFINIDO]**.
- Lista em dois grupos: match exato de data e datas próximas **[DEFINIDO]**.
- Avaliação de 1 a 5 estrelas, com atraso de publicação **[PROPOSTO]**: o desenho de ranking as pressupõe. Confirmar em D-00.
- Destaque de novo na plataforma por 3 dias, com tag "Novo" **[DEFINIDO]**.
- Ranking com faixa 2 (novos) e faixa 4 (demais), ordenado por nota bayesiana.
- Registro de eventos de atendimento (cancelamentos, faltas) e da data de ativação do prestador.

**Fora**

- Penalidade (Fase 2), planos e pontos (Fase 3), "subir agora" (Fase 4).
- Comentário em texto nas avaliações (evita custo de moderação) **[RECOMENDADO]**.
- Cálculo de deslocamento por distância real (usa buffer fixo) **[RECOMENDADO]**.
- Filtro por horário. O MVP filtra por data **[DEFINIDO]**. O card mostra os horários livres do dia.

### 6.4 Modelo de dados (essencial)

```sql
-- Catálogo
oficios(id, nome)
servicos(id, oficio_id, nome)
regioes(id, parent_id, tipo, nome)             -- tipo: cidade | zona | bairro

-- Prestador (campos de ranking são materializados)
prestadores(
  id, nome, status,                            -- pendente | ativo | suspenso
  buffer_min int default 30,
  ativado_em timestamptz,
  novo_ate timestamptz,                        -- max(ativado_em, LANCAMENTO_PUBLICO_EM) + NOVO_DIAS
  soma_notas int default 0, qtd_notas int default 0,
  nota_bayes_milli int default 4700,
  volume_90d int default 0,
  rank_score_milli int default 4700            -- na Fase 1 = nota_bayes_milli
)
prestador_servicos(prestador_id, servico_id, duracao_min, preco_centavos)
prestador_regioes(prestador_id, regiao_id)
agenda_horarios(prestador_id, dia_semana, inicio time, fim time)
agenda_bloqueios(id, prestador_id, inicio timestamptz, fim timestamptz, motivo)

-- Atendimento (grava eventos desde o dia 1)
agendamentos(
  id, prestador_id, cliente_id, servico_id, regiao_id,
  inicio timestamptz, fim timestamptz,
  status,   -- agendado | concluido | cancelado_cliente | cancelado_prestador
            -- | falta_cliente | falta_prestador
  cancelado_em timestamptz, concluido_em timestamptz, criado_em timestamptz
)

-- Avaliação
avaliacoes(
  id, agendamento_id UNIQUE, prestador_id, cliente_id,
  estrelas smallint CHECK (estrelas BETWEEN 1 AND 5),
  criado_em timestamptz, publicar_em timestamptz,
  contabilizada boolean default false
)
```

### 6.5 Região

**Regra:** o prestador atende o cliente se a região do cliente, ou qualquer ancestral dela, está em `prestador_regioes`.

**Memória de cálculo**

- O endereço do cliente (CEP) é convertido em `regiao_id` de bairro.
- A hierarquia permite marcar "Zona Norte" e cobrir todos os bairros dela.
- Texto livre para região quebra o filtro. Não usar.

**Exemplo**

Hierarquia: São Paulo → Zona Norte → Santana.

| Prestadora | Regiões cadastradas | Cliente em Santana | Motivo |
|---|---|---|---|
| Ana | Zona Norte | atende | Zona Norte é ancestral de Santana |
| Bia | Santana | atende | match direto |
| Iris | Zona Sul | não atende | sem relação com Santana |

### 6.6 Disponibilidade (slots)

**Regras** [DEFINIDO]

- O prestador define horário semanal de atendimento.
- Agendamentos existentes ocupam a agenda.
- O prestador pode bloquear períodos.
- O tempo de deslocamento é configurável pelo prestador.

**Regras de cálculo** [RECOMENDADO]

- O buffer vale **só em torno de agendamentos**. Bloqueio é decisão do prestador e não ganha buffer.
- O slot precisa caber **inteiro** na janela livre (duração do serviço do prestador).
- Slots alinhados ao grid de `PASSO_SLOT_MIN`.
- Descartar slots antes de `agora + ANTECEDENCIA_MIN_MIN`.

**Pseudocódigo**

```python
def slots_do_dia(p, servico, dia, agora):
    dur = p.duracao(servico)                              # minutos
    janelas = horario_semanal(p, dia)                     # ex.: [(09:00, 18:00)]
    ocupado = []
    for a in agendamentos_ativos(p, dia):
        ocupado.append((a.inicio - p.buffer, a.fim + p.buffer))   # buffer só aqui
    for b in bloqueios(p, dia):
        ocupado.append((b.inicio, b.fim))                          # bloqueio sem buffer
    slots = []
    for ini, fim in subtrair(janelas, ocupado):
        t = arredondar_para_cima(ini, CFG.PASSO_SLOT_MIN)
        while t + dur <= fim:
            slots.append(t)
            t += CFG.PASSO_SLOT_MIN
    return [s for s in slots if s >= agora + CFG.ANTECEDENCIA_MIN_MIN]
```

**Memória de cálculo (exemplo)**

Sábado 31/10/2026. Horário de atendimento 09:00–18:00. Serviço de 90 min. Buffer de 30 min.

| Item | Intervalo | Intervalo ocupado (com buffer) |
|---|---|---|
| Agendamento existente | 11:00–12:30 | 10:30–13:00 |
| Bloqueio do prestador | 15:00–16:00 | 15:00–16:00 (sem buffer) |

Janelas livres: 09:00–10:30, 13:00–15:00, 16:00–18:00.

| Janela livre | Tamanho | Slots possíveis (serviço de 90 min) |
|---|---|---|
| 09:00–10:30 | 90 min | 09:00 |
| 13:00–15:00 | 120 min | 13:00, 13:30 |
| 16:00–18:00 | 120 min | 16:00, 16:30 |

Total: **5 slots**. O início 17:00 não existe porque terminaria às 18:30, depois do fim do atendimento.

### 6.7 Busca e agrupamento

**Regras**

- **Grupo A:** tem pelo menos 1 slot na data pedida.
- **Grupo B:** não tem slot na data pedida, mas tem em até `JANELA_ALTERNATIVA_DIAS`. O card mostra a **data real** do próximo slot e o botão agenda aquele slot.
- `dist_dias` = distância em dias entre a data pedida e a data do slot mostrado. Em empate de distância, preferir a data posterior. Datas passadas são excluídas.
- O dia da semana igual (ex.: outro sábado) não é um grupo próprio. É apenas um caso de data próxima, coberto pela distância em dias dentro da janela.
- O Grupo A sempre vem antes do Grupo B. As faixas operam dentro de cada grupo.

### 6.8 Avaliações

**Entrada:** 1 a 5 estrelas, inteiro.

**Regras**

- Só pode avaliar quem teve agendamento **concluído**. Uma avaliação por agendamento (`agendamento_id` único).
- **Atraso de publicação** [DEFINIDO]: `publicar_em = criado_em + aleatório(24h, 72h)`. Motivo: se a média muda logo após o atendimento, o prestador deduz quem avaliou. A carga no servidor não é o motivo, porque a atualização é O(1).
- Um job periódico soma ao prestador (`soma_notas`, `qtd_notas`) as avaliações com `publicar_em <= agora` e `contabilizada = false`.

**Por que não começar todo mundo com 5000?** [RECOMENDADO, D-04]

Começar em 5000 e deixar cair coloca quem nunca atendeu à frente de quem tem histórico ótimo, e a função do destaque de novo já é cumprida pela faixa 2. A queda progressiva desejada é obtida pela **média bayesiana**, que equivale a começar em um valor prior e ir cedendo peso à realidade conforme chegam avaliações.

**Memória de cálculo**

```
nota_bayes = (C × m + soma_notas) / (C + n)
nota_bayes_milli = round(nota_bayes × 1000)

m = BAYES_M = 4,7      C = BAYES_C = 10      n = qtd_notas
```

| Caso | n | soma | Cálculo | Nota bayesiana | `milli` |
|---|---|---|---|---|---|
| Sem avaliações | 0 | 0 | (47 + 0) / 10 | 4,700 | 4700 |
| 1 nota 5 | 1 | 5 | (47 + 5) / 11 | 4,727 | 4727 |
| 1 nota 3 | 1 | 3 | (47 + 3) / 11 | 4,545 | 4545 |
| 1 nota 1 | 1 | 1 | (47 + 1) / 11 | 4,364 | 4364 |
| 10 notas, média 4,9 | 10 | 49 | (47 + 49) / 20 | 4,800 | 4800 |
| 40 notas, média 4,9 | 40 | 196 | (47 + 196) / 50 | 4,860 | 4860 |
| 50 notas, média 4,5 | 50 | 225 | (47 + 225) / 60 | 4,533 | 4533 |
| 40 notas média 4,9 + uma nota 1 | 41 | 197 | (47 + 197) / 51 | 4,784 | 4784 |

**Leitura:** uma nota 1 derruba um prestador estabelecido de 4,860 para 4,784 (−0,076) e um prestador novo de 4,700 para 4,364 (−0,336). O novo sente mais, porque tem menos histórico para amortecer.

**Exibição** [RECOMENDADO, D-05]

- `n < NOTA_EXIBIR_MIN_N`: mostrar "Novo" ou "Poucas avaliações", sem número.
- `n >= NOTA_EXIBIR_MIN_N`: mostrar a **média simples** (`soma / n`, uma casa decimal) e a contagem.
- O ranking usa a nota bayesiana. A média exibida pode diferir da posição na lista, e isso é esperado.

### 6.9 Destaque de novo na plataforma (faixa 2)

**Regras**

- Dura `NOVO_DIAS` (3) dias consecutivos **[DEFINIDO]**.
- Card com a tag "Novo" **[DEFINIDO]**.
- Faixa 2 fica **acima da faixa 4** (e, nas fases futuras, acima da 3). Dentro dela, critério de desempate padrão **[DEFINIDO]**.
- Só vale para buscas com `dist_dias <= JANELA_PROXIMA_BOOST_DIAS` (data igual ou próxima) **[DEFINIDO]**. Fora disso, o prestador é tratado pela faixa 4.
- A contagem começa na **ativação**, não no cadastro, e nunca antes do lançamento público: `novo_ate = max(ativado_em, LANCAMENTO_PUBLICO_EM) + NOVO_DIAS × 24h` **[DEFINIDO, D-16]**.
- **Ativação** = perfil completo (foto, descrição, ao menos 1 serviço com preço e duração, ao menos 1 região) + agenda configurada + identidade verificada (D-13) **[RECOMENDADO]**.
- Uma ativação por pessoa (CPF único), para impedir recriar conta e ganhar o destaque de novo **[RECOMENDADO]**.

**Memória de cálculo**

```
novo_ate    = max(ativado_em, LANCAMENTO_PUBLICO_EM) + 3 × 24h
em_destaque = agora < novo_ate  E  dist_dias <= 2
```

Ana foi ativada em 28/10/2026 às 15:00, depois do lançamento público. Então `novo_ate = 31/10/2026 15:00`.

**Ativação antes do lançamento público:** Lia foi ativada em 20/10/2026 e o lançamento público é em 28/10/2026 às 09:00. Então `novo_ate = max(20/10, 28/10 09:00) + 72h = 31/10/2026 09:00`. Sem essa regra, o destaque de Lia terminaria em 23/10, antes de qualquer cliente usar o app.

| Busca feita em | Data pedida | Slot de Ana | `dist_dias` | Em destaque? |
|---|---|---|---|---|
| 30/10 10:00 | 31/10 | 31/10 | 0 | **sim** (faixa 2) |
| 30/10 10:00 | 31/10 | 03/11 | 3 | não: fora da janela de 2 dias, faixa 4 |
| 31/10 16:00 | 31/10 | 31/10 | 0 | não: `agora > novo_ate`, faixa 4 |

### 6.10 Ranking da Fase 1

**Faixas ativas:** 2 e 4.

```python
def faixa_de(p, agora, dist):
    if dist <= CFG.JANELA_PROXIMA_BOOST_DIAS and agora < p.novo_ate:
        return 2        # novo na plataforma
    return 4            # demais
```

**Score:** `rank_score_milli = nota_bayes_milli` (sem penalidade).

**Exemplo completo**

Busca em 30/10/2026: manicure, serviço "alongamento em gel", sábado 31/10/2026, cliente em Santana.

Elenco usado nos exemplos de todas as fases:

| Prestadora | n | soma | Nota bayesiana (milli) | Atend. (últ. 50) | Ocorrências | Volume 90d | Slot | Observação |
|---|---|---|---|---|---|---|---|---|
| Ana | 0 | 0 | 4700 | 0 | 0 | 0 | sáb 31/10 | ativada em 28/10 (recém-chegada) |
| Bia | 40 | 196 | 4860 | 50 | 5 | 18 | sáb 31/10 | |
| Carla | 10 | 49 | 4800 | 12 | 0 | 12 | sáb 31/10 | |
| Duda | 1 | 5 | 4727 | 3 | 0 | 3 | sáb 31/10 | |
| Eva | 50 | 225 | 4533 | 50 | 1 | 22 | sáb 31/10 | |
| Fabi | 40 | 196 | 4860 | 40 | 0 | 15 | dom 01/11 (1 dia) | |
| Hana | 10 | 49 | 4800 | 10 | 0 | 8 | ter 03/11 (3 dias) | |
| Iris | — | — | — | — | — | — | — | não atende Santana: excluída |
| Júlia | — | — | — | — | — | — | — | não oferece o serviço: excluída |

Resultado da Fase 1:

| Pos. | Grupo | Faixa | Prestadora | Score |
|---|---|---|---|---|
| 1 | A | 2 | Ana (tag "Novo") | 4700 |
| 2 | A | 4 | Bia | 4860 |
| 3 | A | 4 | Carla | 4800 |
| 4 | A | 4 | Duda | 4727 |
| 5 | A | 4 | Eva | 4533 |
| 6 | B | 4 | Fabi (dom 01/11) | 4860 |
| 7 | B | 4 | Hana (ter 03/11) | 4800 |

**Leitura**

- Ana tem o menor score entre as ativas do Grupo A mas vem primeiro: faixa 2 vem antes da faixa 4.
- Bia, Carla, Duda e Eva ficam na faixa 4 e se ordenam pela nota bayesiana.
- Fabi e Hana estão no Grupo B, ordenados por faixa → distância → score. Nenhum dos dois é novo.
- Se dois prestadores empatarem em tudo, vale volume 90d e depois o sorteio.
- Depois de 31/10 às 15:00, Ana volta para a faixa 4 e é ordenada pela nota prior (4700) até acumular avaliações.

### 6.11 Eventos obrigatórios desde a Fase 1

Gravar, mesmo sem uso imediato, para a Fase 2 sair retroativa e sem migração:

- Todo status de `agendamentos` com `cancelado_em` e quem cancelou.
- Faltas de cliente e de prestador.
- Instante do cancelamento (para calcular "tardio" na Fase 2: `inicio - cancelado_em < LIMITE_CANCELAMENTO_TARDIO_H`).

**Conclusão do atendimento** [RECOMENDADO, D-03]: o prestador marca "concluído". Sem ação e sem report, o atendimento é concluído automaticamente 24h após o fim. O cliente pode reportar falta do prestador nesse prazo.

### 6.12 Critérios de aceite

- [ ] Busca retorna só prestadores que oferecem o serviço, atendem a região e têm slot válido.
- [ ] O slot calculado respeita duração, buffer em torno de agendamentos e bloqueios.
- [ ] Prestador sem slot na data aparece no Grupo B com a data real do próximo slot, dentro de 14 dias.
- [ ] Grupo A sempre antes do Grupo B.
- [ ] Prestador ativado entra na faixa 2 por 72 horas a partir de `max(ativado_em, LANCAMENTO_PUBLICO_EM)`, só em buscas com `dist_dias <= 2`.
- [ ] O card de prestador novo exibe a tag "Novo".
- [ ] Uma pessoa (CPF) não recebe o destaque de novo duas vezes.
- [ ] Avaliação só é permitida para agendamento concluído, uma por agendamento.
- [ ] A nota só muda após `publicar_em`.
- [ ] Paginação mantém a ordem estável dentro da sessão.
- [ ] Cancelamentos e faltas são gravados com timestamps.

### 6.13 Métricas de sucesso

- Percentual de buscas com pelo menos 1 resultado no Grupo A.
- Taxa de conversão busca → agendamento.
- Tempo até o primeiro agendamento de um prestador novo.
- Percentual de agendamentos concluídos sem falta ou cancelamento tardio.
- Percentual de prestadores ativos com agenda atualizada nos últimos 7 dias.

### 6.14 Riscos específicos da fase

- Cadastros falsos para ganhar o destaque de novo. Mitigar com verificação de identidade e CPF único.
- Cliente interpreta "Novo" como "pior". Explicar na tag ("Novo na plataforma").
- Janela de novo gasta antes do lançamento público. Mitigar com `LANCAMENTO_PUBLICO_EM`.

---

## 7. FASE 2 — Penalidade por faltas e cancelamentos tardios

### 7.1 Objetivo

Prestadores que faltam ou cancelam em cima da hora perdem posição. Isso protege o cliente e prepara o piso de qualidade que os pontos pagos vão exigir na Fase 3.

### 7.2 Histórias

| ID | História |
|---|---|
| H2.1 | Como **cliente**, quero que quem falta ou cancela em cima da hora apareça menos, para não perder meu horário. |
| H2.2 | Como **prestador**, quero ver minhas ocorrências e o impacto delas, para corrigir meu comportamento. |
| H2.3 | Como **prestador**, quero contestar uma ocorrência causada por força maior. |

### 7.3 Regras

- **Ocorrência penalizável** [DEFINIDO]: falta ou cancelamento tardio causado pelo prestador. Cancelamento feito pelo cliente nunca penaliza.
- **Janela** [DEFINIDO]: últimos 50 atendimentos finalizados.
- **Janela mista** [RECOMENDADO, D-14]: além dos 50 atendimentos, ocorrências com mais de 90 dias deixam de contar. Sem isso, um prestador penalizado aparece menos, atende menos, e a janela demora a andar (espiral de queda).
- **Penalidade proporcional** [DEFINIDO]: X% de ocorrências tira X% do `rank_score`.
- **Penalidade só afeta o ranking.** A nota exibida ao cliente não muda.
- **Lançamento em modo sombra** [RECOMENDADO, D-15]: ligar `PENALIDADE_MODO = shadow` por 2 a 4 semanas. O sistema calcula e registra o `rank_score` penalizado sem usá-lo na ordem. Compare as listas e ajuste parâmetros antes de passar para `on`.
- Como os eventos vêm desde a Fase 1, a penalidade nasce com histórico e pode atingir alguém logo no primeiro dia. Avisar os prestadores antes de ligar o modo `on`.
- A penalidade se aplica dentro das faixas 2 e 4. Prestadores novos ainda não têm atendimentos, então na prática ela os afeta pouco.

### 7.4 Mudanças de dados

```sql
ALTER TABLE prestadores
  ADD COLUMN atend_janela int default 0,
  ADD COLUMN ocorrencias_janela int default 0,
  ADD COLUMN taxa_penalidade_bp int default 0;   -- basis points: 1000 = 10%

-- Opcional, para a contestação (H2.3)
ALTER TABLE agendamentos
  ADD COLUMN justificativa text,
  ADD COLUMN ocorrencia_contestada boolean default false;
```

### 7.5 Memória de cálculo

```
atend_janela  = concluídos + ocorrências do prestador, nos últimos 50 finalizados e ≤ 90 dias
                (faltas e cancelamentos feitos pelo cliente ficam fora)
taxa          = min(1, ocorrencias_janela / max(atend_janela, PISO_AMOSTRA_PENALIDADE))
rank_score    = round(nota_bayes_milli × (1 − taxa))
```

O piso (`max(..., 20)`) evita que 1 falta em 2 atendimentos gere −50%.

| Caso | Atend. | Ocorr. | Taxa | Nota (milli) | `rank_score` | Observação |
|---|---|---|---|---|---|---|
| A | 50 | 5 | 5 / 50 = 10% | 4800 | 4800 × 0,90 = **4320** | Reproduz o exemplo do dono: 4800 perde 480 |
| B | 2 | 1 | 1 / 20 = 5% | 4700 | 4700 × 0,95 = **4465** | Sem o piso seria 1/2 = 50% → 2350 |
| C | 30 | 3 | 3 / 30 = 10% | 4860 | 4860 × 0,90 = **4374** | |
| D | 50 | 1 | 1 / 50 = 2% | 4533 | 4533 × 0,98 = **4442** | Arredondado |

### 7.6 Exemplo (elenco da Fase 1, penalidade em `on`)

| Prestadora | Nota | Ocorr. / atend. | Taxa | `rank_score` |
|---|---|---|---|---|
| Ana | 4700 | 0 / 0 | 0% | 4700 |
| Bia | 4860 | 5 / 50 | 10% | 4374 |
| Carla | 4800 | 0 / 12 | 0% | 4800 |
| Duda | 4727 | 0 / 3 | 0% | 4727 |
| Eva | 4533 | 1 / 50 | 2% | 4442 |
| Fabi | 4860 | 0 / 40 | 0% | 4860 |
| Hana | 4800 | 0 / 10 | 0% | 4800 |

Nova lista:

| Pos. | Grupo | Faixa | Prestadora | Score |
|---|---|---|---|---|
| 1 | A | 2 | Ana (tag "Novo") | 4700 |
| 2 | A | 4 | Carla | 4800 |
| 3 | A | 4 | Duda | 4727 |
| 4 | A | 4 | Eva | 4442 |
| 5 | A | 4 | Bia | 4374 |
| 6 | B | 4 | Fabi | 4860 |
| 7 | B | 4 | Hana | 4800 |

**Leitura:** Bia, que era 2ª na Fase 1 (a melhor nota entre as não novas), cai para a última do Grupo A por causa de 5 ocorrências em 50 atendimentos. A nota dela continua 4,9 de média; só a posição mudou.

### 7.7 Critérios de aceite

- [ ] Cancelamento do cliente nunca gera ocorrência.
- [ ] Cancelamento do prestador com menos de 12h do início gera ocorrência. Com mais de 12h, não.
- [ ] A taxa usa o piso de 20 atendimentos.
- [ ] Ocorrência com mais de 90 dias deixa de contar.
- [ ] A nota exibida ao cliente não é afetada pela penalidade.
- [ ] O prestador vê quantas ocorrências tem e quando cada uma expira.
- [ ] Em modo `shadow`, o `rank_score` penalizado é calculado e registrado, mas a ordem da lista não muda.
- [ ] Em modo `on`, a ordem usa o `rank_score` penalizado.

### 7.8 Riscos

- Motivos legítimos (doença, acidente). Mitigar com contestação.
- Registro de falta depende de reporte. Definir quem confirma (D-03).
- Penalizar de forma retroativa pode surpreender. Usar modo sombra e aviso prévio.

---

## 8. FASE 3 — Planos + pontos (faixa 3)

### 8.1 Objetivo

Receita recorrente. Quem assina aparece acima dos não pagantes e pode comprar pontos de ranqueamento para subir dentro da sua faixa.

### 8.2 Histórias

| ID | História |
|---|---|
| H3.1 | Como **prestador**, quero assinar um plano para aparecer acima de quem não paga. |
| H3.2 | Como **prestador assinante**, quero comprar pontos para subir dentro da minha faixa. |
| H3.3 | Como **cliente**, quero que o destaque pago não esconda quem tem boa nota. |
| H3.4 | Como **prestador não pagante**, quero continuar visível, para não ser expulso da plataforma gratuita. |

### 8.3 Regras

- Todo assinante fica na faixa 3, acima de toda a faixa 4 e **abaixo da faixa 2** (novos) **[DEFINIDO]**.
- Dentro da faixa 3: `rank_score` mais bônus de pontos, depois desempate padrão **[DEFINIDO]**.
- **Pontos** [RECOMENDADO, D-11]: têm validade, peso fixo e teto. O bônus só vale **dentro da faixa 3**.
- **Piso de qualidade** [RECOMENDADO]: o bônus só vale se `nota_bayes_milli >= PISO_NOTA_BOOST_MILLI` **e** `taxa_penalidade <= TETO_PENALIDADE_BOOST`. A penalidade (Fase 2) já existe, então o piso nasce completo.
- **Vitrine mínima** [RECOMENDADO, opcional, D-10]: entre as 10 primeiras posições de cada grupo, reservar ao menos `VITRINE_MIN_FAIXA4_TOP10` para a faixa 4 (rotação). Sem isso, com muitos assinantes, os não pagantes somem da primeira página.
- Rótulo "Destaque" ou "Patrocinado" nos cards de assinantes com bônus de pontos (CDC, art. 36). Validar com jurídico.
- A faixa 1 ainda não existe nesta fase.

### 8.4 Mudanças de dados

```sql
planos(id, nome, preco_centavos, periodicidade)
prestador_plano(prestador_id, plano_id, inicio, fim)
prestador_pontos(id, prestador_id, qtd, comprado_em, expira_em)
```

### 8.5 Memória de cálculo

```
pontos_ativos   = soma de qtd dos pontos não expirados
bonus_milli     = min(pontos_ativos × PESO_PONTO_MILLI, TETO_BOOST_MILLI)
passa_piso      = nota_bayes_milli >= 4000  E  taxa_penalidade <= 15%
score_efetivo   = rank_score_milli + (passa_piso ? bonus_milli : 0)
```

Valores ilustrativos: 1 ponto = 10 milli (0,01 estrela), teto = 300 milli (0,3 estrela).

| Caso | Nota | Taxa | `rank_score` | Pontos | Bônus | Passa o piso? | `score_efetivo` |
|---|---|---|---|---|---|---|---|
| Duda | 4727 | 0% | 4727 | 20 | min(200, 300) = 200 | sim | **4927** |
| Carla | 4800 | 0% | 4800 | 0 | 0 | sim | **4800** |
| Teto | 4300 | 0% | 4300 | 50 | min(500, 300) = 300 | sim | **4600** |
| Nota baixa | 3900 | 0% | 3900 | 30 | (300) | **não**: nota < 4000 | **3900** |
| Lia (hipotética) | 4600 | 20% | 3680 | 30 | (300) | **não**: taxa 20% > 15% | **3680** |

O caso de Lia mostra por que a penalidade vem antes: sem ela, Lia aplicaria o bônus e ficaria com 4600 + 300 = 4900.

### 8.6 Exemplo (elenco da Fase 1, Fases 2 e 3 ligadas; Carla e Duda assinam, Duda com 20 pontos)

| Pos. | Grupo | Faixa | Prestadora | Score efetivo |
|---|---|---|---|---|
| 1 | A | 2 | Ana (tag "Novo") | 4700 |
| 2 | A | 3 | Duda | 4927 |
| 3 | A | 3 | Carla | 4800 |
| 4 | A | 4 | Eva | 4442 |
| 5 | A | 4 | Bia | 4374 |
| 6 | B | 4 | Fabi | 4860 |
| 7 | B | 4 | Hana | 4800 |

**Leitura**

- Duda sai de 3ª para 2ª: assinou, comprou pontos e continua acima de Carla, que só assina.
- Carla sobe para o bloco de assinantes, acima de Eva e Bia.
- Ana (novo) continua acima das assinantes enquanto durar o destaque dela.
- Fabi e Hana (não pagantes) continuam depois de todo o Grupo A.

### 8.7 Critérios de aceite

- [ ] Assinante ativo entra na faixa 3. Plano vencido volta para a faixa 4.
- [ ] Bônus de pontos respeita peso, teto e piso de qualidade (nota e taxa).
- [ ] Pontos expirados não contam.
- [ ] Cards patrocinados têm rótulo.
- [ ] Se a vitrine mínima estiver ligada, nenhuma página inicial fica só com faixa 3 quando existe prestador elegível na faixa 4.
- [ ] Com `FF_PLANOS = false`, ninguém entra na faixa 3.

### 8.8 Riscos

- Percepção de "pay-to-win" se a faixa 3 dominar a primeira página. Usar vitrine mínima.
- Primeira receita da plataforma: o preço e a proposta de valor dependem de haver tráfego de clientes suficiente. Validar com dados do MVP antes de lançar.

---

## 9. FASE 4 — Subir agora (faixa 1)

### 9.1 Objetivo

Permitir que o prestador compre destaque por hora para preencher buracos na agenda. É a camada mais alta do ranking e a última a ser lançada.

### 9.2 Histórias

| ID | História |
|---|---|
| H4.1 | Como **prestador**, quero comprar destaque por hora para preencher um horário vago. |
| H4.2 | Como **cliente**, quero ver, identificados como destaque, prestadores com vaga na minha data. |
| H4.3 | Como **plataforma**, quero limitar o destaque a poucas horas por dia, para ele não perder valor. |

### 9.3 Regras

- Compra por hora, com máximo de `SUBIR_AGORA_MAX_H_DIA` (3) horas por dia, por prestador **[DEFINIDO]**.
- Só aparece para buscas com data igual ou próxima (`dist_dias <= JANELA_PROXIMA_BOOST_DIAS`) **[DEFINIDO]**.
- Faixa 1 fica acima da faixa 2. Dentro da faixa, usa o critério de desempate padrão **[DEFINIDO]**.
- Rotulagem como "Destaque" no card (CDC, art. 36). Validar com jurídico.
- **Limite de cards** [RECOMENDADO, D-08]: no máximo `SUBIR_AGORA_MAX_CARDS` (3) por busca. Os excedentes caem para a faixa base (3 ou 4) naquela busca.
- **Significado da "hora"** [PENDENTE, D-06]: janela de **exposição** (período do relógio em que o destaque está ativo) ou **horário do buraco** na agenda. Recomendado: exposição, e só vale se o prestador tem slot livre na data buscada (já garantido pelo filtro de disponibilidade).
- **Reaproveita da Fase 1** a regra de elegibilidade por distância de data (`JANELA_PROXIMA_BOOST_DIAS`) e a lógica de destaque temporário. A diferença: a faixa 2 é concedida automaticamente por 3 dias; a faixa 1 é comprada por hora.

### 9.4 Mudanças de dados

```sql
destaques_subir_agora(
  id, prestador_id,
  inicio timestamptz, fim timestamptz,   -- janela de exposição
  pago_em timestamptz, valor_centavos int
)
```

### 9.5 Memória de cálculo

**Limite diário**

```
horas_do_dia(prestador, dia) + horas_da_nova_compra <= 3
```

Exemplo: o prestador comprou 14:00–15:00, 15:00–16:00 e 20:00–21:00 (3 horas). Uma quarta compra no mesmo dia é rejeitada.

**Elegibilidade pela distância**

| Prestadora | Slot | `dist_dias` | Compra "subir agora"? | Faixa na busca |
|---|---|---|---|---|
| Eva | sáb 31/10 | 0 | sim | **1** |
| Fabi | dom 01/11 | 1 | sim | **1** (no Grupo B) |
| Hana | ter 03/11 | 3 | sim | **4**: fora da janela de 2 dias, o destaque não se aplica |

### 9.6 Exemplo (elenco anterior, todas as fases ligadas; Eva e Fabi compram "subir agora")

| Pos. | Grupo | Faixa | Prestadora | Score efetivo |
|---|---|---|---|---|
| 1 | A | 1 | Eva | 4442 |
| 2 | A | 2 | Ana (tag "Novo") | 4700 |
| 3 | A | 3 | Duda | 4927 |
| 4 | A | 3 | Carla | 4800 |
| 5 | A | 4 | Bia | 4374 |
| 6 | B | 1 | Fabi | 4860 |
| 7 | B | 4 | Hana | 4800 |

**Leitura**

- Eva sai de 4ª para 1ª, mesmo com score abaixo de Ana, Duda e Carla: faixa vence score.
- Fabi sobe dentro do Grupo B, mas continua depois de todo o Grupo A, porque o grupo vem antes da faixa (ver D-09).
- Hana pagou e não ganhou destaque, porque a data dela está a 3 dias, fora da janela. **A interface de compra precisa avisar isso antes do pagamento.**

### 9.7 Critérios de aceite

- [ ] Compra acima de 3 horas por dia é rejeitada.
- [ ] O destaque só tem efeito dentro da janela de exposição comprada.
- [ ] O destaque só tem efeito em buscas com `dist_dias <= 2`.
- [ ] No máximo 3 cards de faixa 1 por busca.
- [ ] Cards de faixa 1 exibem o rótulo "Destaque".
- [ ] Com `FF_SUBIR_AGORA = false`, nenhum prestador entra na faixa 1.

### 9.8 Riscos

- Prestador pagou e não foi exibido (excedente do limite de 3 ou data fora da janela). Definir crédito ou reembolso proporcional (D-08).
- Prestador sem agenda atualizada compra destaque e vende vaga que não tem. Reforça a necessidade de agenda confiável.

---

## 10. Transição para o modelo pago (Fase 3)

Quando os planos entrarem, quem hoje está bem posicionado de graça passa a ter concorrência paga. Como a Fase 3 é a primeira com dinheiro, é aqui que o impacto aparece. Para reduzir:

1. **Aviso antecipado** (sugestão: 30 dias) explicando o que muda e como a ordem é calculada.
2. **Período de carência** (D-12): prestadores já ativos ganham uma janela sem perder posição para assinantes novos.
3. **Vitrine mínima** de não pagantes na primeira página (D-10).
4. **Piso de qualidade** para o bônus de pontos (nota e taxa de faltas).
5. **Rótulos claros** de conteúdo patrocinado.
6. **Acompanhar** logo após o lançamento:
   - distribuição de exposição entre faixas;
   - percentual de buscas com faixa 4 na primeira página;
   - saída de prestadores não pagantes;
   - satisfação dos clientes.

---

## 11. Decisões pendentes

| ID | Pergunta | Recomendação | Fase |
|---|---|---|---|
| D-00 | Avaliações entram no MVP? | Sim, na versão mínima: 1–5 estrelas, sem texto, só com atendimento concluído | 1 |
| D-01 | Reserva instantânea ou sujeita a aceite do prestador? | Instantânea, dentro de slot calculado, com notificação push obrigatória | 1 |
| D-02 | O horário desejado é filtro? | Não no MVP. Mostrar os horários livres do dia no card | 1 |
| D-03 | Quem confirma "concluído"? | Prestador marca; auto-conclui em 24h; cliente pode reportar falta no prazo | 1 |
| D-04 | Nota inicial: 5000 para todos ou média bayesiana? | Bayesiana (m = 4,7, C = 10). O destaque de novo vem da faixa 2 | 1 |
| D-05 | O que exibir como nota? | Média simples e contagem a partir de 3 avaliações | 1 |
| D-06 | A "hora" do "subir agora" é exposição ou horário do buraco? | Exposição, válida só com slot livre na data buscada | 4 |
| D-07 | Qual a janela de "data próxima" para faixas 1 e 2? | 2 dias | 1, 4 |
| D-08 | Limite de cards na faixa 1 e o que fazer com excedente pago | 3 cards; excedente cai para a faixa base e recebe crédito proporcional | 4 |
| D-09 | Ordem no Grupo B: faixa → distância → score, ou distância primeiro? | Faixa primeiro (mantém o valor comercial). Revisar com dados reais | 1–4 |
| D-10 | Precedência absoluta da faixa 3 sobre a 4? | Sim, com vitrine mínima de não pagantes na primeira página | 3 |
| D-11 | Regras dos pontos (validade, peso, teto, piso) | Validade de 30 dias; valores da seção 5 como ponto de partida | 3 |
| D-12 | Carência na transição | 60 dias, com aviso de 30 dias antes | 3 |
| D-13 | Verificação de identidade no cadastro | Documento + selfie, com unicidade por CPF. Validar LGPD com jurídico | 1 |
| D-14 | Janela mista da penalidade | 50 atendimentos e máximo de 90 dias | 2 |
| D-15 | Lançar a penalidade direto em `on`? | Não. Modo `shadow` por 2 a 4 semanas, depois `on` com aviso | 2 |
| D-16 | **FECHADA.** Quando começa a contar a janela de "novo" no lançamento coletivo? | **Decidido:** a partir de `max(ativado_em, LANCAMENTO_PUBLICO_EM)`, para não gastar o destaque antes de haver clientes | 1 |

---

## 12. Riscos

| Risco | Impacto | Mitigação |
|---|---|---|
| Agenda desatualizada gera disponibilidade falsa | Perde a confiança do cliente mais rápido que qualquer ranking ruim | Agenda simples; lembrete de atualização; penalidade na Fase 2 |
| Poucos prestadores por região | O ranking quase não importa | Lançar com densidade em uma região (ex.: uma zona de São Paulo) antes de abrir para tudo |
| Atendimento na casa do cliente entre desconhecidos, sem histórico | Risco de segurança para os dois lados | Verificação de identidade (D-13); avaliações; canal de denúncia |
| Avaliações falsas | Distorce o ranking, e fica pior quando houver ranking pago | Só avalia quem teve atendimento concluído; uma por agendamento; atraso de publicação |
| Cadastros falsos para ganhar destaque de novo | Distorce a faixa 2 e prejudica quem é real | Verificação de identidade e CPF único |
| Janela de "novo" gasta antes do lançamento público | Destaque sem efeito | `LANCAMENTO_PUBLICO_EM` (D-16) |
| Espiral de queda por penalidade | Prestador penalizado aparece menos e não consegue se recuperar | Janela mista de 90 dias (D-14) |
| Penalidade retroativa surpreende prestadores | Reclamações e saída de oferta | Modo sombra e aviso prévio (D-15) |
| Percepção de "pay-to-win" | Clientes veem destaque ruim; não pagantes saem | Piso de qualidade; vitrine mínima; rótulos |
| Primeira receita só na Fase 3 | Pressão de caixa no período do MVP | Planejar o caixa; validar demanda antes de definir o preço dos planos |
| Conformidade | CDC (publicidade identificável); LGPD (documentos e selfies) | Validar com assessoria jurídica antes da Fase 3 e da verificação de identidade |

---

## Apêndice A — Pseudocódigo da listagem

```python
def faixa_de(p, agora, dist):
    boost_elegivel = dist <= CFG.JANELA_PROXIMA_BOOST_DIAS
    if CFG.FF_SUBIR_AGORA and boost_elegivel and p.subir_agora_ativo(agora): return 1   # Fase 4
    if boost_elegivel and agora < p.novo_ate:                                 return 2   # Fase 1
    if CFG.FF_PLANOS and p.plano_ativo(agora):                                return 3   # Fase 3
    return 4                                                                              # Fase 1

def listar(busca, sessao_id, agora):
    candidatos = filtrar(busca.oficio, busca.servico, busca.regiao)   # SQL (filtros duros)
    linhas = []
    for p in candidatos:
        slot = proximo_slot(p, busca.servico, busca.data,
                            janela=CFG.JANELA_ALTERNATIVA_DIAS, agora=agora)
        if slot is None:
            continue
        dist = abs((slot.data - busca.data).days)
        grupo = "A" if dist == 0 else "B"
        faixa = faixa_de(p, agora, dist)
        bonus = bonus_pontos(p) if faixa == 3 and passa_piso(p) else 0
        linhas.append(Linha(p, slot, grupo, faixa, dist, score_do_prestador(p) + bonus))

    linhas = limitar_faixa1(linhas, CFG.SUBIR_AGORA_MAX_CARDS)     # Fase 4: excedente cai p/ faixa base
    linhas.sort(key=lambda l: (
        l.grupo,
        l.faixa,
        l.dist if l.grupo == "B" else 0,
        -l.score_efetivo,
        -l.p.volume_90d,
        hash_estavel(sessao_id, l.p.id),
    ))
    return aplicar_vitrine_minima(linhas)                            # Fase 3, se ligada

def score_do_prestador(p):
    if CFG.PENALIDADE_MODO == "on":                                  # Fase 2
        return p.rank_score_milli                                    # já penalizado
    return p.nota_bayes_milli                                        # off ou shadow: sem penalidade

def passa_piso(p):                                                   # Fase 3
    return (p.nota_bayes_milli >= CFG.PISO_NOTA_BOOST_MILLI
            and p.taxa_penalidade_bp <= CFG.TETO_PENALIDADE_BOOST * 100)
```

## Apêndice B — Resumo das fórmulas

```
nota_bayes_milli = round(1000 × (C × m + soma_notas) / (C + n))                 # Fase 1
novo_ate         = max(ativado_em, LANCAMENTO_PUBLICO_EM) + NOVO_DIAS × 24h      # Fase 1
taxa             = min(1, ocorrencias_janela / max(atend_janela, 20))           # Fase 2
rank_score_milli = round(nota_bayes_milli × (1 − taxa))                          # Fase 2 (na Fase 1, taxa = 0)
bonus_milli      = min(pontos_ativos × PESO_PONTO_MILLI, TETO_BOOST_MILLI)      # Fase 3 (só faixa 3, com piso)
score_efetivo    = rank_score_milli + bonus_milli                                # faixa 3 apenas
```
