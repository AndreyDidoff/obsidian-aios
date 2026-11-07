---
tipo: fonte
arquivo: ingeridos/03-estado-atual-do-produto.md
origem: extração via IA (Claude), snapshot de 2026-10-20; diz ter sido gerado em maio de 2026 a partir de brainstorming e do Tech Lead
criado: 2026-10-20
atualizado: 2026-10-20
---

# 03 · Estado atual do produto

Inventário do que estaria **em produção** versus na esteira, planejado ou sem previsão. É a fonte que mais conflita com [[decisoes-2026-10-20]], porque trata o MVP como já lançado.

## O que afirma existir hoje

- JWT stateless, Bearer token, headers fixos, **2FA para todos**, sessão por dispositivo (a mesma conta não pode estar em dois aparelhos no mesmo app).
- Conta global entre CLIENT e WORKER.
- Cadastro com nome, apelido, nome social, CPF, nascimento, **sexo, gênero e orientação sexual**, e-mail, senha, descrição e vários endereços.
- Busca com raio de ~10 km, filtros em E, ordenação por regras e planos.
- Agendamento **por telas, sem bot**; check-in e check-out; endereço liberado **na confirmação**.
- Tempo médio por serviço, configurado pelo Artista.
- Estrelas **não obrigatórias** (até 3 pedidos, prazo de 15 dias). Sem review em 1 semana, o sistema grava 5 estrelas internas, invisíveis ao cliente.
- Suporte só por e-mail. Sem comunicação direta cliente–Artista.

## Na esteira (críticos)

Endereço só 24h antes, senha aleatória no check-in, upload de documento, validação por foto/vídeo, filtro por dias.

## Sem previsão ou sem prazo

Bot de agendamento (sem prazo), agendas externas, aviso de lista com menos de 10, aviso de divergência de GPS, review escrito e com foto, filtro de reviews por estrelas, salões.

Ver [[mvp]], [[cadastro]], [[agendamento]], [[avaliacoes]], [[contradicoes-e-lacunas]].
