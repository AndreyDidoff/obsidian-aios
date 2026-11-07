> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Endereços

## O que isso é para o app

Endereço, nesta nota, é um local da pessoa que o aplicativo pede e guarda no backend de apoio. A porta é `beautiful/api/Address`. O aplicativo usa essa porta para manter os endereços da pessoa logada. Esta nota descreve o que o aplicativo já pode pedir. A tela que mostraria o endereço fica de fora.

## O que a pessoa já consegue fazer por este backend

Pelo aplicativo, a pessoa logada já pode:

- Ver a lista dos próprios endereços.
- Criar um endereço.
- Editar um endereço.
- Apagar um endereço, pelo identificador desse endereço.

A lista sai da pessoa que está na sessão. A exclusão também usa o identificador dessa pessoa. Criar e editar encaminham o endereço que o aplicativo enviou.

No código, a ação de apagar está nomeada como se fosse foto. O que ela apaga é o endereço.

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[01-o-que-e-este-backend]].

A lista e a exclusão usam o identificador da sessão. Criar e editar encaminham o endereço recebido. Esta nota não separa cliente de profissional: o código desta porta fala em pessoa logada.

## Em que pé está

No ar. O aplicativo já pode pedir lista, criação, edição e exclusão de endereço. O serviço de endereço está ligado na subida deste backend. Se a marca de pessoa logada vale na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido, como em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

Não descreve tela, mapa nem o formato dos dados que compõem um endereço. Não descreve endereço de outra pessoa. Não descreve telefone, foto, relato nem documento de validação.

## Ligações

Leitura mais próxima: [[02-cliente-e-profissional]] [[04-cadastro]] [[09-telefones]] [[13-o-que-a-pessoa-pode-ver]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

Criar e editar encaminham o endereço recebido. Nesta porta não aparece uma segunda conferência que troque esse endereço pelo identificador da sessão. Não dá para afirmar, só com esta leitura, se um endereço enviado em nome de outra pessoa seria recusado mais adiante.

Os campos de um endereço não estão declarados nesta porta.
