> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# O que a pessoa pode ver

## O que isso é para o app

Esta nota é a consulta que o aplicativo faz no backend de apoio para saber quais áreas mostrar à pessoa logada. A porta é `beautiful/api/System`. O aplicativo pede permissões, pede grupos e, a partir de uma lista de grupos, pede telas, grupos e permissões combinados. As telas em si não estão neste backend. Aqui existe a consulta que informa o que pode aparecer. O desenho de cada tela fica de fora.

## O que a pessoa já consegue fazer por este backend

Pelo aplicativo, a pessoa logada já pode pedir:

- A lista de permissões.
- A lista de grupos.
- A partir de uma lista de grupos, o conjunto combinado de telas, grupos e permissões.

As três consultas levam o login que o aplicativo enviou. A combinada parte da lista de grupos que o aplicativo envia e devolve telas, grupos e permissões juntos. Isso é o que o aplicativo consultaria para decidir quais áreas mostrar. O conteúdo de cada área não está nesta porta.

## Quem pode

A porta está marcada como exigindo pessoa logada, e cada uma das três consultas também. Se essa marca é aplicada na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[01-o-que-e-este-backend]].

Esta nota não nomeia papel, cargo nem um tipo de pessoa. O código desta porta não separa cliente de profissional e não declara um papel de administração.

## Em que pé está

No ar. O aplicativo já pode pedir permissões, grupos e a combinação a partir de uma lista de grupos. O serviço desta consulta está ligado na subida deste backend. Se a marca de pessoa logada vale na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido, como em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

Não descreve as telas. Não nomeia área, menu nem o que aparece dentro de cada área. Não cobre o que a pessoa faz em endereço, telefone, foto, relato, documento, serviço, plano ou bloqueio: isso está nas notas ligadas. Aqui só está a consulta que o aplicativo usaria para saber o que mostrar.

## Ligações

Leitura mais próxima: [[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[14-preparado-e-ainda-nao-oferecido]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

O código não declara o nome de nenhuma tela nem de nenhum papel. Esta nota não inventa esses nomes.

Também não está declarado se a lista de permissões e a lista de grupos são o catálogo inteiro ou só o que cabe à pessoa logada. As duas listas levam o login que o aplicativo enviou, sem um identificador de pessoa lido nesta porta. A consulta combinada usa a lista de grupos que o aplicativo envia.
