> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Modelos de mensagem

## Onde isso mora

1. No app. Não há tela de modelos de mensagem.
2. No BFF. Os modelos estão só preparados em [[bff-preparado-e-ainda-nao-oferecido]].
3. No projeto Br.Template.API, no host https://templateapimicroservice.bptsoftware.com.br/
4. No Mongo [[banco-mongo-template]]. O banco se chama Template e a coleção se chama Template. IdEnterprise aponta com força fraca para Enterprise.Enterprise. IdSystem aponta com força fraca para Systems.Systems. Os dois estão em [[banco-mongo-relacoes]]. Não é constraint.

## O que isso é

É o cadastro do texto pronto de um modelo, separado por empresa e por sistema. Cada documento guarda o nome em NameTemplate, o tipo em TemplateType e o texto em DataTemplate. Também guarda o identificador, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O texto de DataTemplate fica no documento; esta nota não o reproduz.

O pacote ao lado nomeia três tipos: e-mail, contrato e termo de uso. Esta porta não lê esse número. O tipo que permanece é o texto que veio no pedido. Empresa e sistema são códigos soltos: gravar não procura a empresa nem o sistema.

A lista do dia a dia devolve o modelo que continua em uso daquela empresa e daquele sistema. O tipo que vai no endereço dessa lista não entra na consulta.

## O que já se consegue fazer

Listar os modelos em uso de uma empresa e de um sistema. O endereço ainda pede um tipo, e esse tipo é ignorado. Modelo desligado não volta. O pedido pergunta ao login se o acesso vale. Se o login não aceita, a lista é recusada. Se aceita, voltam os documentos ativos daquele par, sem separar por tipo.

Abrir um modelo pelo identificador, dentro daquela empresa e daquele sistema. A resposta é uma lista com esse documento, inclusive quando já está desligado. Se não houver documento com esse trio, a lista vem com um vazio e a chamada ainda responde sucesso. Não pergunta se o acesso vale.

Incluir um modelo. O serviço gera um identificador novo e ignora o identificador que veio no pedido. O resto entra como veio: nome, tipo, texto, empresa, sistema, se está em uso, datas e quem mudou. Quando o pedido não marca o contrário, o modelo nasce em uso, com a data de agora. Não pergunta se o acesso vale. Não confere se a empresa ou o sistema existem, se o tipo é um dos três nomeados nem o que está escrito em DataTemplate. Não deixa trilha. Se o pedido não fecha como documento, a resposta ainda é sucesso e nada é gravado.

Editar um modelo. O pedido manda o documento inteiro e essa versão substitui a daquele identificador. A troca procura só o identificador: empresa e sistema que vierem no pedido passam a ser os do documento. O serviço lê o documento anterior e não usa essa leitura. Não pergunta se o acesso vale. As datas e quem mudou são as do pedido; o serviço não carimba a alteração. Identificador que não existe responde sucesso e não cria documento. Não deixa trilha.

Apagar um modelo. O documento continua na coleção, fica fora de uso e deixa de aparecer na lista. Ainda pode ser aberto pelo identificador. O pedido pergunta ao login se o acesso vale. A trilha dessa ação está comentada e não roda. Se não houver documento com esse trio, a chamada ainda responde que apagou.

A autenticação preparada na subida do serviço não entra no caminho do pedido. Só a lista e o desligamento perguntam ao login. Se essa pergunta estourar, o aviso da falha sai para o Discord e a chamada estoura de novo. O mesmo caminho vale para as outras falhas destas ações.

## Em que pé está

Listar, abrir, gravar, substituir e desligar estão escritos e respondem sobre a coleção Template do banco Template, sem tela no app e com os modelos só preparados em [[bff-preparado-e-ainda-nao-oferecido]], enquanto a lista ignora o tipo que o endereço pede e devolve todo modelo em uso daquela empresa e daquele sistema, abrir, gravar e substituir não perguntam se o acesso vale, listar e desligar recusam o pedido quando o login não aceita, o desligamento deixa o documento na coleção sem trilha, e IdEnterprise e IdSystem seguem com força fraca em [[banco-mongo-relacoes]], sem constraint.

## O que esta nota não cobre

Não cobre o aplicativo: não há tela de modelos de mensagem. Não cobre o BFF por dentro; o elo é [[bff-preparado-e-ainda-nao-oferecido]]. Não cobre o que os outros serviços fazem ao chamar este host. Não reproduz o texto de DataTemplate, senha, connection string nem identificador de empresa ou aplicativo.

## Incertezas

A configuração deste projeto declara NoSQLDB como MongoDB, banco Template e coleção Template. No Windows e no Linux o Mongo só é preparado quando a variável NoSQLDB vale MongoDB; nos outros casos o arranque prepara Dynamo, que não é esta coleção, e nesse caminho a lista não separa modelo desligado. Se essa variável vier vazia, o registro do serviço ainda cai no Mongo por causa do arquivo, sem ter preenchido banco e coleção por esse caminho, enquanto o arranque daquele sistema já preparou o Dynamo. O nome de coleção lido no Windows e no Linux é a variável TemplateStoreDatabasePhotosCollectionName. Fora desses dois sistemas, a configuração pedida é a seção PhotoStoreDatabase, e este projeto declara MongoDbStoreDatabase. Por este repositório não dá para fechar qual armazenamento o host publicado está usando agora.

Este projeto não declara o host público. Os outros serviços apontam para https://templateapimicroservice.bptsoftware.com.br/ , e alguns de desenvolvimento usam a porta 12443.

O cliente interno apaga em `/api/Template/Delete/{id}`. A porta só aceita `/api/Template/Delete/{empresa}/{sistema}/{id}`. Os dois não se encontram. A extração viu NameTemplate, TemplateType, DataTemplate, IdEnterprise e IdSystem. O modelo que esta porta grava também leva identificador, se está em uso, as duas datas e quem mudou.
