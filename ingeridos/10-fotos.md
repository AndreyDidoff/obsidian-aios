> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Fotos

## O que isso é para o app

Foto, nesta nota, é uma imagem que o aplicativo busca, guarda ou apaga no backend de apoio. A porta é `beautiful/api/Photo`. O aplicativo pede uma foto de cada vez, pelo identificador dela. Esta nota descreve o que o aplicativo já pode pedir. A tela que mostraria a foto fica de fora.

## O que a pessoa já consegue fazer por este backend

Pelo aplicativo, a pessoa logada já pode:

- Buscar uma foto, pelo identificador dessa foto.
- Guardar uma foto.
- Apagar uma foto, pelo identificador dessa foto.

Não há lista de fotos nesta porta. Não há edição de uma foto já guardada. O pedido de busca, de guarda e de exclusão encaminha a foto, ou o identificador dela, junto com o login que o aplicativo mandou.

A foto anexada a um relato é outra porta. Ela está em [[11-relatos]].

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[01-o-que-e-este-backend]].

Nesta porta, buscar, guardar e apagar não releem o identificador da sessão. Encaminham o identificador da foto, ou a foto enviada, junto com o login que o aplicativo mandou. Esta nota não separa cliente de profissional.

## Em que pé está

No ar para buscar uma foto pelo identificador, guardar e apagar. O serviço de foto está ligado na subida deste backend. Lista de fotos e edição de uma foto já guardada não fazem parte desta porta. Se a marca de pessoa logada vale na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido, como em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

Não descreve tela. Não descreve onde a foto aparece no aplicativo. Não cobre a foto de um relato: anexar, editar e tirar essa foto estão em [[11-relatos]]. Não cobre o conjunto de documentos de validação.

## Ligações

Leitura mais próxima: [[11-relatos]] [[12-documentos-para-validacao]] [[04-cadastro]] [[13-o-que-a-pessoa-pode-ver]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

O código não diz se esta foto é de perfil, de portfólio, de documento ou de outro uso. Nenhum desses usos está declarado nesta porta, e esta nota não escolhe um.

Também não está declarado se a foto fica restrita à pessoa logada. Buscar e apagar pedem o identificador da foto. Não dá para afirmar, só com esta leitura, se outra pessoa logada que conheça esse identificador obteria ou apagaria a mesma foto.
