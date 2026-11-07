> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Documentos para validação

## Onde isso mora

1. No app. O documento que o artista envia no cadastro não é, por este código, esta coleção. Este serviço não lê esse cadastro e não tem ação de aprovar nem de recusar.
2. No BFF. O app fala com api.wecareu.app. A porta desta camada está em [[bff-documentos-para-validacao]]. O serviço daqui não aprova e não recusa, então esta nota não atribui essa decisão à porta.
3. No projeto Br.Validation.API. Host https://validationapimicroservice.bptsoftware.com.br/
4. No banco [[banco-mongo-validation]], Mongo, banco Validation, coleção Documents. Na extração havia 0 documentos. A forma dos campos não foi observada.

## O que isso é

É o registro de validação de uma empresa e de um sistema. A lista traz o que ainda está em efeito nessa empresa e nesse sistema. Abrir um registro pede também a pessoa e o identificador.

Gravar, substituir e desligar não decidem o documento. A trilha deixa o aprovador vazio, nomeia o banco Validation e a tabela Validation, e descreve as três mudanças como inclusão. A coleção observada chama-se Documents e estava vazia. Esta nota não descreve a forma dos campos.

## O que já se consegue fazer

Ver a lista do que ainda está em efeito para uma empresa e um sistema. O que já foi desligado não volta. A lista não separa por pessoa.

Abrir um registro. O pedido leva empresa, sistema, pessoa e identificador. A resposta é uma lista de um item. Se não houver registro, essa lista traz um vazio.

Registrar. O serviço troca o identificador por um novo e inclui o pedido. Antes há trilha. A trilha pede, nos cabeçalhos, quem fez, o nome, a empresa e o sistema. Nomeia o banco Validation e a tabela Validation. O dado, quando o armazenamento é Mongo, segue para a coleção configurada. A trilha descreve inclusão e não preenche aprovador. Se a trilha estoura, a inclusão não acontece. Se a trilha só responde que não gravou, o serviço ainda inclui. Se o pedido não passa na conferência de forma, nada é gravado e a resposta ainda diz que deu certo. O identificador novo nasce depois da trilha: o rastro pode mostrar outro identificador.

Alterar. O serviço substitui o registro daquele identificador pelo que veio no pedido. Identificador que não existe não vira registro novo, e a chamada ainda responde sucesso. A trilha de novo descreve inclusão, nomeia a tabela Validation e deixa o aprovador vazio. Se a trilha estoura, a troca não acontece. Se a trilha só responde que não gravou, o serviço ainda troca.

Desligar. O registro fica. Sai de efeito e some da lista. A trilha descreve inclusão. Sem registro com aquele identificador, empresa, sistema e pessoa, a chamada quebra e nada muda. Se a trilha estoura, o desligamento não acontece. Se a trilha só responde que não gravou, o serviço ainda desliga.

Antes de cada ação o serviço pergunta ao login se o acesso vale. A resposta é sim ou não. A recusa desta porta só aconteceria se a resposta viesse vazia. Ela não vem vazia. A ação segue com o acesso aceito e com o acesso recusado.

O cliente interno pede a lista e abre um registro nos caminhos que este serviço tem. Registrar, nesse cliente, aponta para um caminho Save que este serviço não tem. Alterar e desligar apontam para fotos, não para este serviço. Nenhum outro projeto deste repositório chama esse cliente.

Se a chamada quebra, o ocorrido segue para a operação e a falha continua.

## Em que pé está

A coleção Documents está vazia: não há documento gravado para mostrar.

Listar o que está em efeito e abrir um registro: feito no caminho. Sem registro, a lista volta vazia e abrir devolve um vazio.

Registrar, alterar e desligar: feito no caminho do serviço, com a trilha nomeando a tabela Validation e descrevendo inclusão. Pela metade no fechamento: a inclusão pode responder sucesso sem gravar, a alteração de um identificador ausente responde sucesso sem criar, e o cliente interno não alcança essas três ações.

Aprovar ou recusar: esta API não faz.

A porta de acesso: casca. A pergunta ao login acontece e não recusa.

## O que esta nota não cobre

O cadastro do artista no aplicativo. O miolo de [[bff-documentos-para-validacao]], além do lugar dessa porta na cadeia. A forma dos campos, porque a coleção tinha 0 documentos. Senha e endereço de conexão. O conteúdo de uma validação já gravada: não havia nenhuma.

## Incertezas

O arquivo do projeto escolhe Mongo e escreve o banco Validation e a coleção Documents numa seção que a subida no servidor não lê. No servidor, o nome do banco e o da coleção vêm do ambiente, e o nome da variável da coleção fala em fotos. O caminho sem sistema operacional procura a seção PhotoStoreDatabase, que este arquivo não tem. A extração viu a coleção Documents com 0 documentos. O controlador não fixa esse nome.

Se a escolha de armazenamento não for Mongo, corre outra implementação. Nessa, a lista não tira o que já foi desligado. A extração observada é a coleção Mongo vazia.

Este repositório não declara o host público. O endereço de Br.Validation.API fecha a cadeia pedida nesta extração.
