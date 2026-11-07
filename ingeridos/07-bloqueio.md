> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Bloqueio

## O que isso é para o app

É a porta de bloqueio deste backend. Por ela o aplicativo pede para ver, registrar e remover um bloqueio da pessoa que está logada. O efeito desse bloqueio no restante do aplicativo não está escrito nesta porta.

## O que a pessoa já consegue fazer por este backend

O aplicativo já pode pedir, nesta porta:

- Ver os bloqueios da pessoa logada.
- Bloquear.
- Desbloquear.

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada do pedido fica em aberto, porque o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Veja [[01-o-que-e-este-backend]].

Estas ações não separam cliente de profissional.

## Em que pé está

**No ar.**

O serviço de bloqueio está ligado quando este backend sobe, e a configuração tem endereço de bloqueio.

## O que esta nota não cobre

- Se o bloqueio esconde perfil, chat ou agenda.
- Motivo, prazo e os demais dados de um bloqueio.
- Telas de bloquear alguém.
- Relatos, que são outra porta.

## Ligações

A sessão desta porta conversa com [[03-entrar-sair-e-senha]]. Cliente e profissional estão em [[02-cliente-e-profissional]]. O que a pessoa pode ver está em [[13-o-que-a-pessoa-pode-ver]]. Relatos são outra porta: [[11-relatos]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

- Não dá para afirmar se o bloqueio esconde perfil, chat ou agenda.
- Os campos do bloqueio (quem entra no registro, motivo, prazo) não estão neste repositório.
- Bloquear encaminha o pedido. Esta porta não mostra, nessa ação, que amarra o bloqueio à pessoa logada.
- Desbloquear aponta para um bloqueio já registrado. Esta porta não mostra, nessa ação, uma segunda leitura de que o registro é da pessoa logada.
