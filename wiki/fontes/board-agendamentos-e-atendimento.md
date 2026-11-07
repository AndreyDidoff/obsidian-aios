---
tipo: fonte
arquivo: "ingeridos/board-agendamentos-e-atendimento.md"
origem: "extração via IA (Cursor) do board Azure DevOps da organização piresbno1992, projeto WeCareU, em 2026-10-21; retrato de trabalho, não decisão de produto; em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Agendamentos e atendimento", "Sistema de agendamentos"]
---

# Agendamentos e atendimento

Porta: [[board-indice]]. Extração em 2026-10-21. Organização `piresbno1992`, projeto WeCareU. Retrato de trabalho, não decisão de produto. Em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Estado no board não é pé do produto. New, Active ou Completed não significa entregue no app nem no [[mvp]].

Área WeCareU\GLOBAL, salvo a história 144, que está em WeCareU\ARTIST.

Nenhum item deste bruto traz critério de aceite. O único comentário está na história 144.

## O que este tema pede

O board pede um sistema de agendamentos e um sistema de check-in e check-out. Pede salvamento, telas de agendamento do cliente e do artista, cluster, pesquisa, listagem, aceitar ou recusar, e importar agendamentos de outras plataformas. No check-in, pede informativo de chegada e aprovação da chegada. Não pede chat livre nem texto livre.

## Épico 334 — Sistema de agendamentos

Estado no board: New. Responsável: nenhum. Sem descrição.

### História 144 — Criar sistema de salvamento de agendamentos

Estado no board: New. Área: WeCareU\ARTIST. Responsável: Bruno Pires de Almeida ([[bruno]]). Sem descrição. Sem tarefas.

Comentário de Andrey Didoff do Nascimento em 2025-08-01: a história está pareada com WECAREU-6, em `https://wecareu.atlassian.net/browse/WECAREU-6`, e traz um marcador getint.io. O comentário não descreve o salvamento.

### História 372 — Tela de Agendamento do Cliente

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 373 — **[BE] Criar um Cluster de controle de agenda e agendamentos**

Estado no board: New. Responsável: nenhum. Sem descrição.

O título nomeia um Cluster. Cluster é o nome que o board usa. Não confirma a arquitetura.

#### Tarefa 374 — **[BE] Integrar Cluster de Agendamento com WeCareU**

Estado no board: New. Responsável: nenhum. Sem descrição.

O título repete Cluster e nomeia WeCareU. São nomes do board. Não confirmam a arquitetura.

#### Tarefa 376 — **[BE] Criar Pesquisa entre agendamentos**

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 377 — **[BE] Criar Endpoint de Listagem de agendamentos**

Estado no board: New. Responsável: nenhum. Sem descrição.

### História 375 — Tela de Agendamento do Artista

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 378 — **[BE] Replicar sistemas de gerenciamento de agendamento do Cliente para o Artista**

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 379 — **[BE] Aceitar/Recusar Agendamento**

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 380 — **[BE] Importar Agendamentos de outras plataformas**

Estado no board: New. Responsável: nenhum. Sem descrição.

O título pede importar agendamentos de outras plataformas. É pedido do board, não decisão de integração.

## Épico 339 — Sistema de check-in e check-out

Estado no board: New. Responsável: nenhum. Sem descrição.

### História 383 — Sistema de interação do atendimento residencial

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 381 — **[BE] Criar informativo de chegada no cliente**

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 382 — **[BE] Criar Aprovação de chegada do Artista**

Estado no board: New. Responsável: nenhum. Sem descrição.

## O que isto não decide

Não decide entre chatbot e tela. As histórias 372 e 375 pedem tela de agendamento. Não pedem chat livre nem texto livre. O alvo continua chatbot, sem texto livre. ([[decisoes-2026-10-20]]) O item 13 de [[contradicoes-e-lacunas]] segue encaminhado.

Não decide quando o endereço aparece. O épico 339 pede check-in e check-out. As tarefas 381 e 382 pedem informativo de chegada e aprovação da chegada. O item 16 segue aberto.

Não decide prazo, 5 estrelas internas nem foto. Este tema não trata de avaliação.

Não prova que a casca "Tab Schedules" ou "Tab ChatSchedules" do retrato de 21/10 foi preenchida. ([[agenda]], [[conversa-do-agendamento]], [[agenda-do-artista]])

A tarefa 380 pede importar agendamentos de outras plataformas. É pedido do board, não decisão de integração.
