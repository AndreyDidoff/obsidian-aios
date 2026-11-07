> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Telefones

## O que isso é para o app

Telefone, nesta nota, é um número da pessoa que o aplicativo pede e guarda no backend de apoio. A porta é `beautiful/api/Phone`. O aplicativo usa essa porta para manter os telefones da pessoa logada. Esta nota descreve o que o aplicativo já pode pedir. A tela que mostraria o telefone fica de fora.

## O que a pessoa já consegue fazer por este backend

Pelo aplicativo, a pessoa logada já pode:

- Ver a lista dos próprios telefones.
- Guardar um telefone.
- Editar um telefone.
- Apagar um telefone, pelo identificador desse telefone.

A lista é da pessoa logada: o pedido usa o identificador da sessão. Guardar, editar e apagar encaminham o telefone, ou o identificador do telefone, junto com o login.

No código, várias dessas ações estão nomeadas como se fossem foto. O que o aplicativo lista, guarda, edita e apaga por ali é telefone.

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[01-o-que-e-este-backend]].

A lista usa o identificador da pessoa da sessão. Guardar, editar e apagar encaminham o telefone recebido. Esta nota não separa cliente de profissional.

## Em que pé está

No ar. O aplicativo já pode pedir lista, inclusão, edição e exclusão de telefone. O serviço de telefone está ligado na subida deste backend. Se a marca de pessoa logada vale na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido, como em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

Não descreve tela nem os dados que compõem um telefone. Não descreve telefone de outra pessoa. Não descreve endereço, foto, relato nem documento de validação.

## Ligações

Leitura mais próxima: [[02-cliente-e-profissional]] [[04-cadastro]] [[08-enderecos]] [[13-o-que-a-pessoa-pode-ver]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

A lista é da pessoa logada. Guardar, editar e apagar, nesta porta, encaminham o que o aplicativo enviou. Não dá para afirmar, só com esta leitura, se um telefone de outra pessoa seria recusado mais adiante.

Os dados que formam um telefone não estão declarados nesta porta.
