---
tipo: fonte
arquivo: "ingeridos/core-11-fotos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Fotos"]
---

# Fotos

Retrato de 21/10 do projeto `Br.Photos.API`. Host `https://photosapimicroservice.bptsoftware.com.br/`. Mongo [[banco-mongo-photos]]. O banco se chama `Photos` e a coleção se chama `photos`.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. O elo com o BFF é o wikilink [[bff-fotos]]. Esta página não acrescenta a essa porta uma lista que o retrato do BFF não publica.

## Onde isso mora

1. No app. A foto de perfil existe no cadastro. Esta nota não reescreve essa tela.
2. No BFF. [[bff-fotos]]. O aplicativo fala com `api.wecareu.app`. Esta nota não reescreve o miolo dessa porta e não publica, para ela, uma lista que aquele retrato não traz.
3. Neste serviço: `Br.Photos.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O serviço que guarda a foto de um dono num documento da coleção `photos`. Cada documento leva o conteúdo da foto em texto, no campo `DtFotos`, o dono em `OwnerId`, o tipo, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O único tipo nomeado é perfil. Zero não é perfil. A lista do dia a dia devolve toda foto que continua em uso, de qualquer dono. O dono fica gravado e não entra nessa lista nem na abertura.

`OwnerId` está sem destino único em [[banco-mongo-relacoes]]. `Usuario.FkFoto` e `Enterprise.Logo` não se amarram a esta coleção: seguem sem destino único em [[banco-sql-relacoes]]. Não são constraint.

## O que já se consegue fazer

Listar as fotos em uso. O pedido pergunta ao login se o acesso vale. Se o login não aceita, a lista é recusada. Se aceita, voltam todos os documentos ativos, sem separar por dono nem por tipo. Foto desligada não volta.

Abrir uma foto pelo identificador do documento. A resposta é uma lista com esse documento, inclusive quando a foto já está desligada. Se não houver documento com esse identificador, a lista vem com um vazio e a chamada ainda responde sucesso. A regra de acesso é a mesma da lista.

Incluir uma foto. O serviço gera um identificador novo e ignora o identificador que veio no pedido. Sempre grava com identificador novo. O resto entra como veio: conteúdo, dono, tipo, se está em uso, datas e quem mudou. Quando o pedido não marca o contrário, a foto nasce em uso, com a data de agora. Se o tipo não vem, grava zero, e zero não é perfil. Não pergunta se o acesso vale. Não confere se o dono existe, se o tipo é perfil nem o formato do conteúdo. Não deixa trilha. Pedido que não fecha como documento é recusado.

Editar uma foto. O pedido manda o documento inteiro e essa versão substitui a daquele identificador. Pergunta ao login se o acesso vale, com a mesma regra da lista. As datas e quem mudou são as do pedido; o serviço não carimba a alteração. Identificador que não existe responde sucesso e não cria documento. Não deixa trilha. Pedido que não fecha como documento é recusado.

Apagar uma foto. O documento continua na coleção, fica fora de uso e deixa de aparecer na lista. Ainda pode ser aberto pelo identificador. O pedido pergunta ao login se o acesso vale. Se não houver documento com esse identificador, a chamada ainda responde que apagou. Não deixa trilha.

Listar, abrir, editar e desligar recusam quando o login não aceita e seguem quando aceita. Esta checagem não está invertida como a dos outros serviços desta leva. Incluir não pergunta se o acesso vale. A autenticação preparada na subida do serviço não entra no caminho do pedido. Nenhuma das cinco operações escreve trilha, embora a trilha esteja ligada no serviço.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito com ressalva | Listar, abrir, gravar, substituir e desligar estão escritos e respondem sobre a coleção `photos` do banco `Photos`. A lista devolve toda foto em uso, de qualquer dono. Incluir não pergunta se o acesso vale e sempre gera identificador novo. Listar, abrir, editar e desligar recusam quando o login não aceita e seguem quando aceita. Esta checagem não está invertida |
| Pela metade | `Usuario.FkFoto` e `Enterprise.Logo` seguem sem destino único. Nenhuma das cinco operações escreve trilha. Desligar um identificador inexistente responde sucesso |

## O que esta nota não cobre

A tela de cadastro do aplicativo. O BFF por dentro; o elo é [[bff-fotos]], e esta nota não lhe acrescenta uma lista que aquele retrato não publica. O cadastro do login, que chama a inclusão e copia o identificador para `FkFoto`, e a logo da empresa, que chama a abertura com o valor de `Logo`. Arquivo em nuvem, miniatura e corte. Senha, connection string e identificador de empresa ou de aplicativo.

## Incertezas

A configuração deste projeto declara `NoSQLDB` como MongoDB, banco `Photos` e coleção `photos`. No Windows e no Linux o Mongo só é preparado quando a variável `NoSQLDB` vale MongoDB; nos outros casos o arranque prepara Dynamo, que não é esta coleção. Se essa variável vier vazia, o registro do serviço ainda cai no Mongo por causa do arquivo, sem ter preenchido banco e coleção por esse caminho. O compose do serviço `br.photos.api` não define `NoSQLDB` nem o nome do banco. A configuração de desenvolvimento grava a coleção na chave `MongoDbCollectionName`, e o código lê `PhotosCollectionName`, então essa chave não preenche a coleção. Por este repositório não dá para fechar qual armazenamento o host publicado está usando agora. O conteúdo em `DtFotos` é texto opaco: o serviço não diz se isso é a imagem em si ou um endereço.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
