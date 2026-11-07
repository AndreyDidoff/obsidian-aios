---
tipo: fonte
arquivo: "ingeridos/core-07-bloqueio.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Bloqueio"]
---

# Bloqueio

Retrato de 21/10 do projeto `Br.Block.API`. Host `https://blockapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-userlogin]], SQL `UserLogin`, tabela `BlockUsers`. Não existe tabela `blocks`.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

1. No app. Os apps de 21/10 não desenham o efeito do bloqueio. Não há tela de bloqueio no app de cliente nem no de profissional. [[board-bloqueio]] entra só como pedido de trabalho, não como tela pronta.
2. No BFF. O aplicativo fala com `api.wecareu.app`. A porta dessa camada está em [[bff-bloqueio]]. Esta nota não reescreve o miolo dessa porta.
3. Neste serviço: `Br.Block.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O registro de uma pessoa que bloqueia outra. Um lado é quem bloqueia. O outro é quem fica bloqueado. Os dois são identificadores soltos: ao gravar, o serviço não procura a pessoa em `Usuario` e não cria constraint. Não impede bloquear a si mesmo nem repetir o mesmo par. A amarração desses dois campos com `Usuario` está inferida em [[banco-sql-relacoes]], com força fraca. O código não diverge dessa leitura.

O registro guarda se o bloqueio ainda está em efeito, quando nasceu, quando mudou e quem mudou. Não guarda motivo nem prazo. Quem mudou precisa vir no próprio pedido. O serviço não preenche isso com quem está na sessão.

A lista devolve só os bloqueios em efeito em que a pessoa consultada é quem bloqueia. Não devolve quem bloqueou essa pessoa. Não devolve o que já foi desfeito.

Nenhum outro serviço deste repositório lê `BlockUsers` para esconder perfil, conversa ou agenda.

## O que já se consegue fazer

Ver a lista de bloqueios em efeito de uma pessoa.

Registrar um bloqueio novo. A ação abre linha nova e deixa o banco dar o identificador. Não confere se as duas pessoas existem. Quem bloqueia e quem é bloqueado vêm no pedido. O serviço não troca esses dois pela pessoa da sessão. Registrar não deixa rastro.

Alterar um bloqueio que já tem identificador. O serviço regrava o que veio no pedido. Sem identificador, a alteração vira um registro novo.

Desfazer. A linha fica. O bloqueio sai de efeito e some da lista. Desfazer um identificador que não existe não completa.

Alterar e desfazer deixam rastro. A mudança acontece antes do rastro. O rastro descreve a mudança como inclusão e nomeia a tabela `Block`, que não existe. O dado continua em `BlockUsers`. Se o rastro não fecha, a mudança pode ter ficado e a chamada ainda assim falha.

Antes de cada ação o serviço pergunta ao login se o acesso vale. Se o login aceita, a ação é recusada. Se o login não aceita, a ação segue.

O cliente interno que os outros serviços usam para falar com este consegue ver e registrar. O desfazer desse cliente aponta para um caminho com o nome cortado (`Bloc`) e não chega na ação que tira o bloqueio de efeito.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito com ressalva | Ver, registrar, alterar e desfazer em `BlockUsers`, sem tela e sem efeito no restante do produto. A checagem está invertida: login que aceita recusa a ação; login que não aceita deixa seguir |
| Pela metade | O rastro de alterar e desfazer nomeia a tabela `Block`, que não existe, e a mudança fica gravada antes do rastro |
| Casca | O desfazer do cliente interno. O caminho se chama `Bloc` e não chega na ação |

## O que esta nota não cobre

Telas. Relatos. O miolo de [[bff-bloqueio]], além do lugar dessa porta na cadeia. O conteúdo das linhas já gravadas. O efeito em perfil, conversa ou agenda fica no fato acima: nenhum outro serviço deste repositório lê `BlockUsers` para esconder ou impedir.

## Incertezas

A pergunta ao login reenvia o acesso já apresentado, e o login apresenta de novo. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler esta porta como fechada para quem não está logado.

Em registrar, alterar e desfazer, a chamada pode responder que deu certo mesmo quando nenhuma linha mudou, desde que não estoure erro. Na alteração, a resposta de sucesso é a do rastro, não a da gravação. No desfazer, o antes e o depois do rastro saem iguais, já com o bloqueio fora de efeito.

O desfazer do cliente interno usa envio. O serviço só desfaz numa consulta com o identificador do bloqueio.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
