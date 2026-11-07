> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Documentos para validação

## O que isso é para o app

Documento para validação, nesta nota, é um conjunto de documentos que o aplicativo envia e consulta no backend de apoio, dentro de um fluxo de validação. A porta é `beautiful/api/Validation`. O aplicativo consulta um conjunto pelo identificador dele, limitado à pessoa logada, e também envia, edita e apaga esse conjunto. Esta nota descreve o que o aplicativo já pode pedir. A tela que mostraria o documento fica de fora.

## O que a pessoa já consegue fazer por este backend

Pelo aplicativo, a pessoa logada já pode:

- Consultar um conjunto de documentos, pelo identificador desse conjunto.
- Enviar um conjunto de documentos.
- Editar um conjunto de documentos.
- Apagar um conjunto de documentos, pelo identificador desse conjunto.

A consulta pede o identificador do conjunto e o identificador da pessoa na sessão. A exclusão faz o mesmo. Enviar e editar encaminham o conjunto que o aplicativo enviou.

Não há, nesta porta, uma lista de todos os conjuntos. A consulta é de um conjunto por vez.

No código, a ação de apagar está nomeada como se apagasse a pessoa. O que ela apaga é o conjunto de documentos.

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[01-o-que-e-este-backend]].

Consultar e apagar usam o identificador do conjunto e o identificador da pessoa na sessão. Enviar e editar encaminham o conjunto recebido. Esta nota não separa cliente de profissional.

## Em que pé está

No ar. O aplicativo já pode consultar um conjunto pelo identificador, enviar, editar e apagar. O serviço de validação está ligado na subida deste backend. Uma lista de todos os conjuntos não faz parte desta porta. Se a marca de pessoa logada vale na entrada, fica em aberto: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido, como em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

Não descreve tela. Não descreve o passo em que alguém aprova ou recusa o conjunto, porque esta porta mostra consulta, envio, edição e exclusão. A foto pedida fora deste conjunto está em [[10-fotos]]. Não cobre endereço, telefone nem relato.

## Ligações

Leitura mais próxima: [[04-cadastro]] [[02-cliente-e-profissional]] [[10-fotos]] [[13-o-que-a-pessoa-pode-ver]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

Existe um fluxo de validação. Não dá para afirmar quais documentos entram no conjunto. O código não declara RG, CPF, certificado nem outro tipo, e esta nota não escolhe um.

Enviar e editar encaminham o conjunto recebido. Não dá para afirmar, só com esta leitura, se um conjunto enviado em nome de outra pessoa seria recusado mais adiante. Os passos posteriores da validação, além de consultar, enviar, editar e apagar o conjunto, não aparecem nesta porta.
