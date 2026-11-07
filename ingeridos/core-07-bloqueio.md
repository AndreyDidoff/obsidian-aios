> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Bloqueio

## Onde isso mora

1. No app. Os apps de 21/10 não desenham o efeito do bloqueio. Nesta extração não há tela de bloqueio no app de cliente nem no app de profissional. [[board-bloqueio]] entra só como pedido de trabalho, não como tela pronta.
2. No BFF. O app fala com api.wecareu.app. A porta de bloqueio dessa camada está em [[bff-bloqueio]].
3. No projeto Br.Block.API. Host https://blockapimicroservice.bptsoftware.com.br/
4. No banco [[banco-sql-userlogin]], SQL UserLogin, tabela BlockUsers. Não existe tabela blocks.

## O que isso é

É o registro de uma pessoa que bloqueia outra. Um lado é quem bloqueia. O outro é quem fica bloqueado. Os dois são identificadores soltos: ao gravar, o serviço não procura a pessoa em Usuario e não cria constraint. A amarração desses dois campos com Usuario está inferida em [[banco-sql-relacoes]], com força fraca. O código não diverge dessa leitura.

O registro guarda se o bloqueio ainda está em efeito, quando nasceu, quando mudou e quem mudou. Não guarda motivo nem prazo. Quem mudou precisa vir no próprio pedido. O serviço não preenche isso com quem está na sessão. Sem esse texto, a gravação não completa.

Ver devolve só os bloqueios em efeito em que a pessoa consultada é quem bloqueia. Não devolve quem bloqueou essa pessoa. Não devolve o que já foi desfeito.

## O que já se consegue fazer

- Ver a lista de bloqueios em efeito de uma pessoa.
- Registrar um bloqueio novo. A ação abre linha nova e deixa o banco dar o identificador. Não confere se as duas pessoas existem, não impede bloquear a si mesmo e não impede repetir o mesmo par. Quem bloqueia e quem é bloqueado vêm no pedido. O serviço não troca esses dois pela pessoa da sessão. Registrar não deixa rastro.
- Alterar um bloqueio que já tem identificador. O serviço regrava o que veio no pedido. Sem identificador, a alteração vira um registro novo.
- Desfazer. A linha fica. O bloqueio sai de efeito e some da lista. Desfazer um identificador que não existe não completa.

Alterar e desfazer deixam rastro. Esse rastro descreve a mudança como inclusão e nomeia a tabela como Block. Essa tabela não existe. O dado continua em BlockUsers. A mudança do bloqueio acontece antes do rastro. Se o rastro não fecha, a mudança pode ter ficado e a chamada ainda assim falha.

Antes de cada ação o serviço pergunta ao login se o acesso vale. Se o login aceita, a ação é recusada. Se o login não aceita, a ação segue.

O cliente interno que os outros serviços usam para falar com este consegue ver e registrar. O desfazer desse cliente não chega na ação que tira o bloqueio de efeito.

## Em que pé está

Já se vê, registra, altera e desfaz o bloqueio em BlockUsers, sem tela e sem efeito no restante do produto, e a ação é recusada quando o login aceita o acesso.

## O que esta nota não cobre

O que o bloqueio muda em perfil, conversa ou agenda. Nenhum outro serviço deste repositório lê BlockUsers para esconder ou impedir alguma coisa. Telas. Relatos. O miolo de [[bff-bloqueio]], além do lugar dessa porta na cadeia. O conteúdo das linhas já gravadas.

## Incertezas

A pergunta ao login reenvia o acesso já apresentado como acesso, e o login apresenta de novo. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler a porta como fechada para quem não está logado.

Na alteração, a resposta de sucesso é a do rastro, não a da gravação do bloqueio. Em registrar, alterar e desfazer, a chamada pode responder que deu certo mesmo quando nenhuma linha mudou, desde que não estoure erro.

No desfazer, o antes e o depois do rastro saem iguais, já com o bloqueio fora de efeito. O rastro não mostra o estado anterior.

O desfazer do cliente interno aponta para um caminho com o nome cortado (Bloc em vez de Block) e usa envio. O serviço só desfaz numa consulta com o identificador do bloqueio.

Este repositório não declara o host público. O endereço de Br.Block.API fecha a cadeia pedida nesta extração.
