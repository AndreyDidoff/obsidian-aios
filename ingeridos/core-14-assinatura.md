> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Assinatura

## Onde isso mora

1. No app. Não há tela de assinatura de contrato. O cadastro recebe este serviço e não o chama. O vínculo na pessoa nasce vazio.
2. No BFF. A assinatura está só preparada ([[bff-preparado-e-ainda-nao-oferecido]]). O app fala com api.wecareu.app.
3. No projeto Br.Signature.API. Host https://signatureapimicroservice.bptsoftware.com.br/
4. No Mongo [[banco-mongo-signature]]. Banco Signature, coleção Signature, 0 documentos. Usuario.FkSignature está sem destino único em [[banco-sql-relacoes]] e não se amarra a esta coleção.

## O que isso é

É o serviço que guarda a assinatura ligada à conta. A coleção Signature estava vazia. Esta nota não descreve a forma dos campos e não descreve contrato assinado.

A lista devolve o que ainda está em uso. Abrir pede o identificador do documento. Gravar, substituir e desligar deixam trilha nomeando o banco Signature e a tabela Signature, com o aprovador vazio. O que a extração viu é a coleção Mongo desse mesmo nome. A trilha de gravar só nasce quando o pedido já traz identificador. A de substituir descreve edição. A de desligar descreve exclusão. O documento desligado fica na coleção e sai da lista.

## O que já se consegue fazer

Listar o que está em uso. Coleção vazia devolve lista vazia. O que foi desligado não volta.

Abrir pelo identificador. A resposta é uma lista de um item, também quando já está desligado. Sem documento, a lista traz um vazio e a chamada responde sucesso.

Incluir. Se o pedido já traz identificador, o serviço troca por um novo e deixa trilha antes de gravar. A trilha pede, nos cabeçalhos, quem fez, o nome, a empresa e o sistema. Se um desses cabeçalhos falta, a inclusão quebra e nada entra. Se a trilha só responde que não gravou, o serviço ainda inclui. Se o pedido chega sem identificador, não há trilha e o documento segue com identificador vazio. Se o pedido não passa na conferência de forma, nada é gravado e a resposta ainda diz que deu certo.

Substituir. O pedido manda o documento inteiro e essa versão toma o lugar daquele identificador. Identificador que não existe responde sucesso e não cria documento. A trilha descreve edição e nasce com identificador vazio. Se a trilha estoura, a troca não acontece. Se a trilha só responde que não gravou, o serviço ainda troca.

Desligar. O documento continua, sai de uso e some da lista. Ainda pode ser aberto pelo identificador. A trilha descreve exclusão. Sem documento com esse identificador, a chamada quebra e nada muda.

Antes de cada ação o serviço pergunta ao login se o acesso vale. A resposta é sim ou não. A recusa desta porta só aconteceria se a resposta viesse vazia. Ela não vem vazia. A ação segue com o acesso aceito e com o acesso recusado.

Ao entrar, se Usuario.FkSignature tem valor, a conta pede a abertura e devolve o identificador. Sem valor, não chama este serviço. A confirmação da sessão pela área de senha faz a mesma abertura e devolve o documento. Isso não amarra a coluna à coleção. Nenhum outro projeto deste repositório grava, troca, lista ou desliga por aqui. O cadastro não chama.

Se a chamada quebra, o ocorrido segue para a operação e a falha continua. O texto desse aviso fala em foto.

## Em que pé está

A coleção Signature está vazia: não há documento gravado para mostrar.

Listar o que está em uso e abrir pelo identificador: feito no caminho. Sem documento, a lista volta vazia e abrir devolve um vazio.

Incluir, substituir e desligar: feito no caminho do serviço, com trilha nomeando o banco Signature e a tabela Signature. Pela metade no fechamento: a inclusão sem identificador não deixa trilha e pode gravar identificador vazio; a inclusão pode responder sucesso sem gravar; a troca de um identificador ausente responde sucesso sem criar; desligar um identificador ausente quebra; e nenhum outro projeto deste repositório grava por aqui.

A porta de acesso: casca. A pergunta ao login acontece e não recusa.

Contrato assinado e tela no aplicativo: esta API não faz, e o cadastro não chama este serviço.

## O que esta nota não cobre

A tela de assinatura de contrato, que o app não tem. O miolo de [[bff-preparado-e-ainda-nao-oferecido]], além do lugar dessa porta na cadeia. O cadastro por dentro, além de constar que ele não chama este serviço. A entrada e a área de senha, além de constar que pedem a abertura quando FkSignature tem valor. A forma dos campos, porque a coleção tinha 0 documentos. Senha e endereço de conexão. Planos de assinatura, que são outra nota.

## Incertezas

O arquivo do projeto escolhe Mongo e escreve o banco Signature e a coleção Signature. No Windows e no Linux o Mongo só é preparado quando a variável NoSQLDB vale MongoDB; nos outros casos o arranque prepara Dynamo, que não é esta coleção. A variável que levaria o nome da coleção nesse caminho fala em fotos. O compose do serviço br.signature.api não define NoSQLDB nem o nome do banco. Se a variável vier vazia, o registro do serviço ainda cai no Mongo por causa do arquivo, sem ter preenchido banco e coleção por esse caminho. A extração viu a coleção Signature com 0 documentos.

Se a escolha de armazenamento não for Mongo, corre outra implementação. Nessa, a lista não tira o que já foi desligado, e a inclusão sempre gera identificador novo. A extração observada é a coleção Mongo vazia.

Este repositório declara o host em UrlsSignature. O endereço de Br.Signature.API fecha a cadeia pedida nesta extração.
