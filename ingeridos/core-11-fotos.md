> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Fotos

## Onde isso mora

1. No app. A foto de perfil existe no cadastro. Esta nota não reescreve essa tela.
2. No BFF. [[bff-fotos]]. O app fala com api.wecareu.app.
3. No projeto Br.Photos.API, no host https://photosapimicroservice.bptsoftware.com.br/
4. No Mongo [[banco-mongo-photos]]. O banco se chama Photos e a coleção se chama photos. OwnerId está sem destino único em [[banco-mongo-relacoes]]. Usuario.FkFoto e Enterprise.Logo não se amarram a esta coleção: estão sem destino único em [[banco-sql-relacoes]].

## O que isso é

É o serviço que guarda a foto de um dono num documento da coleção photos. Cada documento leva o conteúdo da foto em texto, no campo DtFotos, o dono em OwnerId, o tipo, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O único tipo nomeado é perfil. A lista do dia a dia devolve toda foto que continua em uso, de qualquer dono. O dono fica gravado e não entra nessa lista nem na abertura.

## O que já se consegue fazer

Listar as fotos em uso. O pedido pergunta ao login se o acesso vale. Se o login não aceita, a lista é recusada. Se aceita, voltam todos os documentos ativos, sem separar por dono nem por tipo. Foto desligada não volta.

Abrir uma foto pelo identificador do documento. A resposta é uma lista com esse documento, inclusive quando a foto já está desligada. Se não houver documento com esse identificador, a lista vem com um vazio e a chamada ainda responde sucesso. A regra de acesso é a mesma da lista.

Incluir uma foto. O serviço gera um identificador novo e ignora o identificador que veio no pedido. O resto entra como veio: conteúdo, dono, tipo, se está em uso, datas e quem mudou. Quando o pedido não marca o contrário, a foto nasce em uso, com a data de agora. Se o tipo não vem, grava zero, e zero não é perfil. Não pergunta se o acesso vale. Não confere se o dono existe, se o tipo é perfil nem o formato do conteúdo. Não deixa trilha. Pedido que não fecha como documento é recusado.

Editar uma foto. O pedido manda o documento inteiro e essa versão substitui a daquele identificador. Pergunta ao login se o acesso vale, com a mesma regra da lista. As datas e quem mudou são as do pedido; o serviço não carimba a alteração. Identificador que não existe responde sucesso e não cria documento. Não deixa trilha. Pedido que não fecha como documento é recusado.

Apagar uma foto. O documento continua na coleção, fica fora de uso e deixa de aparecer na lista. Ainda pode ser aberto pelo identificador. O pedido pergunta ao login se o acesso vale. Se não houver documento com esse identificador, a chamada ainda responde que apagou.

## Em que pé está

Listar, abrir, gravar, substituir e desligar estão escritos e respondem sobre a coleção photos do banco Photos. A lista devolve toda foto em uso, de qualquer dono. Abrir usa o identificador do documento e também devolve foto já desligada. Incluir não pergunta se o acesso vale e sempre grava com identificador novo. Listar, abrir, editar e desligar recusam o pedido quando o login não aceita o acesso e seguem quando aceita. A autenticação preparada na subida do serviço não entra no caminho do pedido. Nenhuma das cinco operações escreve trilha, embora a trilha esteja ligada no serviço. Desligar um identificador inexistente responde sucesso. OwnerId segue sem destino único em [[banco-mongo-relacoes]], e Usuario.FkFoto e Enterprise.Logo seguem sem destino único em [[banco-sql-relacoes]].

## O que esta nota não cobre

Não cobre a tela de cadastro do aplicativo. Não cobre o BFF por dentro; o elo é [[bff-fotos]]. Não cobre o cadastro do login, que chama a inclusão e copia o identificador para FkFoto, nem a logo da empresa, que chama a abertura com o valor de Logo. Não cobre arquivo em nuvem, miniatura nem corte. Não reproduz senha, connection string nem identificador de empresa ou aplicativo.

## Incertezas

A configuração deste projeto declara NoSQLDB como MongoDB, banco Photos e coleção photos. No Windows e no Linux o Mongo só é preparado quando a variável NoSQLDB vale MongoDB; nos outros casos o arranque prepara Dynamo, que não é esta coleção. Se essa variável vier vazia, o registro do serviço ainda cai no Mongo por causa do arquivo, sem ter preenchido banco e coleção por esse caminho. O compose do serviço br.photos.api não define NoSQLDB nem o nome do banco. A configuração de desenvolvimento grava a coleção na chave MongoDbCollectionName, e o código lê PhotosCollectionName, então essa chave não preenche a coleção. Por este repositório não dá para fechar qual armazenamento o host publicado está usando agora. O conteúdo em DtFotos é texto opaco: o serviço não diz se isso é a imagem em si ou um endereço.
