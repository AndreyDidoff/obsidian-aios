---
tipo: fonte
arquivo: "ingeridos/13-o-que-a-pessoa-pode-ver.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["O que a pessoa pode ver"]
---

# O que a pessoa pode ver

A consulta que o aplicativo usaria para saber o que mostrar à pessoa logada. Caminho `beautiful/api/System`. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Não nomeia área, menu nem o que aparece em cada área. As telas em si não estão neste backend. Esta nota não descreve as outras portas.

## O que está publicado

- A **lista de permissões**.
- A **lista de grupos**.
- A partir de uma lista de grupos, o **conjunto combinado** de telas, grupos e permissões.

As três consultas levam o login recebido. A combinada parte da lista de grupos enviada e devolve telas, grupos e permissões juntos. O conteúdo de cada área não está nesta porta.

## Quem pode

A porta está marcada como exigindo pessoa logada, e cada uma das três consultas também. Essa marca pode não valer na entrada: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

Esta nota não nomeia papel, cargo nem um tipo de pessoa. O código desta porta não separa cliente de profissional e não declara um papel de administração.

## Em que pé está

**No ar.** Permissões, grupos e a combinação a partir de uma lista de grupos estão publicados. O serviço desta consulta está ligado na subida deste backend. A marca de pessoa logada pode não valer na entrada, a mesma lacuna de sessão.

## O que esta nota não cobre

As telas. Área, menu e o que aparece dentro de cada área. O que a pessoa faz em endereço, telefone, foto, relato, documento, serviço, plano ou bloqueio: isso está nas outras portas. Aqui só está a consulta.

## Incertezas

O código não declara o nome de nenhuma tela nem de nenhum papel. Esta nota não inventa esses nomes.

Também não está declarado se a lista de permissões e a lista de grupos são o catálogo inteiro ou só o que cabe à pessoa logada. As duas listas levam o login recebido, sem um identificador de pessoa lido nesta porta. A consulta combinada usa a lista de grupos enviada.

Ver [[beautiful-api]].
