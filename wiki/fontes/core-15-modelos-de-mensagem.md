---
tipo: fonte
arquivo: "ingeridos/core-15-modelos-de-mensagem.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Modelos de mensagem"]
---

# Modelos de mensagem

Retrato de 21/10 do projeto `Br.Template.API`. Host `https://templateapimicroservice.bptsoftware.com.br/`. Mongo [[banco-mongo-template]]. O banco se chama `Template` e a coleção se chama `Template`. Esta nota não reproduz o texto do modelo.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. No BFF os modelos seguem só preparados ([[bff-preparado-e-ainda-nao-oferecido]]). Esta página não fecha isso.

## Onde isso mora

1. No app. Não há tela de modelos de mensagem.
2. No BFF. Os modelos estão só preparados em [[bff-preparado-e-ainda-nao-oferecido]]. O aplicativo fala com `api.wecareu.app`.
3. Neste serviço: `Br.Template.API`. O aplicativo não fala com ele. Fala com o BFF.

`IdEnterprise` aponta com força fraca para `Enterprise.Enterprise`. `IdSystem` aponta com força fraca para `Systems.Systems`. Os dois estão em [[banco-mongo-relacoes]]. Não é constraint.

## O que isso é

O cadastro do texto pronto de um modelo, separado por empresa e por sistema. Cada documento guarda o nome em `NameTemplate`, o tipo em `TemplateType` e o texto em `DataTemplate`. Também guarda o identificador, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O texto de `DataTemplate` fica no documento; esta nota não o reproduz.

O pacote ao lado nomeia três tipos: e-mail, contrato e termo de uso. Esta porta não lê esse número. O tipo que permanece é o texto que veio no pedido. Empresa e sistema são códigos soltos: gravar não procura a empresa nem o sistema.

A lista do dia a dia devolve o modelo que continua em uso daquela empresa e daquele sistema. O tipo que vai no endereço dessa lista não entra na consulta.

## O que já se consegue fazer

Listar os modelos em uso de uma empresa e de um sistema. O endereço ainda pede um tipo, e a lista ignora esse tipo. Modelo desligado não volta. O pedido pergunta ao login se o acesso vale. Se o login não aceita, a lista é recusada. Se aceita, voltam os documentos ativos daquele par, sem separar por tipo. Esta checagem não está invertida.

Abrir um modelo pelo identificador, dentro daquela empresa e daquele sistema. A resposta é uma lista com esse documento, inclusive quando já está desligado. Se não houver documento com esse trio, a lista vem com um vazio e a chamada ainda responde sucesso. Abrir não pergunta se o acesso vale.

Incluir um modelo. O serviço gera um identificador novo e ignora o identificador que veio no pedido. O resto entra como veio: nome, tipo, texto, empresa, sistema, se está em uso, datas e quem mudou. Quando o pedido não marca o contrário, o modelo nasce em uso, com a data de agora. Gravar não pergunta se o acesso vale. Não confere se a empresa ou o sistema existem, se o tipo é um dos três nomeados nem o que está escrito em `DataTemplate`. Não deixa trilha. Se o pedido não fecha como documento, a resposta ainda é sucesso e nada é gravado.

Editar um modelo. O pedido manda o documento inteiro e essa versão substitui a daquele identificador. A troca procura só o identificador: empresa e sistema que vierem no pedido passam a ser os do documento. O serviço lê o documento anterior e não usa essa leitura. Substituir não pergunta se o acesso vale. As datas e quem mudou são as do pedido; o serviço não carimba a alteração. Identificador que não existe responde sucesso e não cria documento. Não deixa trilha.

Apagar um modelo. O documento continua na coleção, fica fora de uso e deixa de aparecer na lista. Ainda pode ser aberto pelo identificador. O pedido pergunta ao login se o acesso vale. Se o login não aceita, o desligamento é recusado. Esta checagem não está invertida. A trilha do desligamento está comentada e não roda. Se não houver documento com esse trio, a chamada ainda responde que apagou.

A autenticação preparada na subida do serviço não entra no caminho do pedido. Só a lista e o desligamento perguntam ao login. Se essa pergunta estourar, o aviso da falha sai para o Discord e a chamada estoura de novo. O mesmo caminho vale para as outras falhas destas ações.

## Em que pé está

Listar, abrir, gravar, substituir e desligar estão escritos e respondem sobre a coleção `Template` do banco `Template`, sem tela no app e com os modelos só preparados em [[bff-preparado-e-ainda-nao-oferecido]]. A lista ignora o tipo que o endereço pede e devolve todo modelo em uso daquela empresa e daquele sistema. Abrir, gravar e substituir não perguntam se o acesso vale. Listar e desligar recusam o pedido quando o login não aceita; esta checagem não está invertida. O desligamento deixa o documento na coleção sem trilha. `IdEnterprise` e `IdSystem` seguem com força fraca em [[banco-mongo-relacoes]], sem constraint.

## O que esta nota não cobre

O aplicativo: não há tela de modelos de mensagem. O BFF por dentro; o elo é [[bff-preparado-e-ainda-nao-oferecido]], e os modelos seguem só preparados. O que os outros serviços fazem ao chamar este host. O texto de `DataTemplate`. Senha, connection string e identificador de empresa ou de aplicativo.

## Incertezas

A configuração deste projeto declara `NoSQLDB` como MongoDB, banco `Template` e coleção `Template`. No Windows e no Linux o Mongo só é preparado quando a variável `NoSQLDB` vale MongoDB; nos outros casos o arranque prepara Dynamo, que não é esta coleção, e nesse caminho a lista não separa modelo desligado. Se essa variável vier vazia, o registro do serviço ainda cai no Mongo por causa do arquivo, sem ter preenchido banco e coleção por esse caminho, enquanto o arranque daquele sistema já preparou o Dynamo. O nome de coleção lido no Windows e no Linux é a variável `TemplateStoreDatabasePhotosCollectionName`. Fora desses dois sistemas, a configuração pedida é a seção `PhotoStoreDatabase`, e este projeto declara `MongoDbStoreDatabase`. Por este repositório não dá para fechar qual armazenamento o host publicado está usando agora.

Este projeto não declara o host público. Os outros serviços apontam para `https://templateapimicroservice.bptsoftware.com.br/`, e alguns de desenvolvimento usam a porta 12443.

O cliente interno apaga em `/api/Template/Delete/{id}`. A porta só aceita `/api/Template/Delete/{empresa}/{sistema}/{id}`. Os dois não se encontram. A extração viu `NameTemplate`, `TemplateType`, `DataTemplate`, `IdEnterprise` e `IdSystem`. O modelo que esta porta grava também leva identificador, se está em uso, as duas datas e quem mudou.

A lacuna de sessão do BFF segue aberta: o arranque prepara a sessão e não a lê no caminho do pedido. Ver [[contradicoes-e-lacunas]], [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
