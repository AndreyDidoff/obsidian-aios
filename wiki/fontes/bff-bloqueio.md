---
tipo: fonte
arquivo: "ingeridos/07-bloqueio.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Bloqueio"]
---

# Bloqueio

O que este backend publica para ver, registrar e remover um bloqueio da pessoa que está logada. O efeito desse bloqueio no restante do aplicativo não está escrito nesta porta. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela.

## O que está publicado

- **Ver** os bloqueios da pessoa logada.
- **Bloquear.**
- **Desbloquear.**

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada do pedido fica em aberto, porque o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Ver [[bff-o-que-e-este-backend]] e [[contradicoes-e-lacunas]].

Estas ações não separam cliente de profissional.

## Em que pé está

**No ar.**

O serviço de bloqueio está ligado quando este backend sobe, e a configuração tem endereço de bloqueio.

## O que esta nota não cobre

Se o bloqueio esconde perfil, chat ou agenda. Motivo, prazo e os demais dados de um bloqueio. Telas de bloquear alguém. Relatos são outra porta: [[bff-relatos]].

## Incertezas

Não dá para afirmar se o bloqueio esconde perfil, chat ou agenda.

Os campos do bloqueio (quem entra no registro, motivo, prazo) não estão neste repositório.

Bloquear encaminha o pedido. Esta porta não mostra, nessa ação, que amarra o bloqueio à pessoa logada.

Desbloquear aponta para um bloqueio já registrado. Esta porta não mostra, nessa ação, uma segunda leitura de que o registro é da pessoa logada.

Ver [[beautiful-api]], [[seguranca-do-atendimento]].

O board pede um sistema de bloqueio. O épico 335 está New e sem descrição. A história 147 está New e a descrição está ausente. As tarefas 364 e 365 estão New e sem descrição. ([[board-bloqueio]]) New é o estado do work item. Esta porta já está no ar como retrato de código. Isso não vem do estado do work item. O board não diz se o bloqueio esconde perfil, chat ou agenda. Esta porta também não diz. Bloqueio no board não vira shadowban nem check-in.
