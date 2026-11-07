> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Relatos

## O que isso é para o app

Relato, nesta nota, é um registro da pessoa logada que o aplicativo pede e guarda no backend de apoio. A porta é `beautiful/api/Report`. O aplicativo lista os relatos dessa pessoa, grava, altera, apaga e trata as fotos ligadas a um relato. Esta nota descreve o que o aplicativo já pode pedir. A tela que mostraria o relato fica de fora.

## O que a pessoa já consegue fazer por este backend

Pelo aplicativo, a pessoa logada já pode:

- Ver a lista dos próprios relatos.
- Criar um relato.
- Editar um relato.
- Apagar um relato, pelo identificador desse relato.
- Anexar uma foto a um relato.
- Editar a foto de um relato.
- Tirar uma foto de um relato, pelo identificador do relato e pelo identificador da foto.

A lista sai da pessoa que está na sessão. A exclusão do relato também usa o identificador dessa pessoa. Criar e editar encaminham o relato que o aplicativo enviou. Anexar e editar a foto encaminham a foto do relato. Tirar uma foto aponta o relato e a foto.

A foto pedida sozinha, fora de um relato, está em [[10-fotos]].

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[01-o-que-e-este-backend]].

A lista e a exclusão do relato usam o identificador da sessão. Criar, editar, anexar foto e editar a foto do relato encaminham o que o aplicativo enviou. Tirar uma foto aponta o relato e a foto. Esta nota não separa cliente de profissional.

## Em que pé está

No ar. O aplicativo já pode pedir lista, criação, edição e exclusão do relato, e também anexar, editar e tirar uma foto desse relato. O serviço de relato está ligado na subida deste backend. Se a marca de pessoa logada vale na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido, como em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

Não descreve tela. Não descreve o texto, o motivo nem sobre quem é o relato, porque esta porta não declara esses dados. A foto geral, fora do relato, está em [[10-fotos]]. Não cobre endereço, telefone nem documento de validação.

## Ligações

Leitura mais próxima: [[10-fotos]] [[02-cliente-e-profissional]] [[05-servicos]] [[07-bloqueio]] [[13-o-que-a-pessoa-pode-ver]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

O código não diz se o relato é denúncia, avaliação ou registro de atendimento. Nenhum desses sentidos está declarado nesta porta, e esta nota não escolhe um.

Criar e editar encaminham o relato recebido. Não dá para afirmar, só com esta leitura, se um relato enviado em nome de outra pessoa seria recusado mais adiante. Também não está declarado o que a foto do relato mostra.
