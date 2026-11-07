---
tipo: fonte
arquivo: "ingeridos/core-12-relatos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Relatos"]
---

# Relatos

Retrato de 21/10 do projeto `Br.Report.API`. Host `https://reportapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-report]]. As tabelas são `Report` e `ReportFotos`.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. Isto não é [[board-denuncia]] e não há tela de relato em uso. O retrato [[bff-relatos]] diz que a porta do BFF não declara texto, motivo nem sobre quem. Esta nota não reescreve essa página fonte. As duas camadas ficam: o núcleo tem a descrição e os dois identificadores; o BFF, no retrato dele, não declara esses campos.

## Onde isso mora

1. No app. Não há tela de relato em uso. [[board-denuncia]] é pedido de denúncia e não é esta tabela.
2. No BFF. [[bff-relatos]]. O aplicativo fala com `api.wecareu.app`. O miolo dessa porta fica na página dela.
3. Neste serviço: `Br.Report.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O registro de um relato dentro de uma empresa e de um sistema. Quem relata vai em `UserId`. Quem é relatado vai em `ReportedUserId`. Os dois são identificadores soltos: ao gravar, o serviço não procura a pessoa em `Usuario` e não cria constraint. `UserId` e `ReportedUserId` apontam com força fraca para `Usuario`. Não é constraint.

O item relatado, `ReportedItemId`, pode vir vazio e não tem destino único. O nome de tabela que viaja junto, `ReportedTable`, é texto livre. A descrição vai em `ReportDescription`. O registro marca se ainda está ativo, quando nasceu, quando mudou e quem mudou.

A foto do relato fica em `ReportFotos`: empresa, sistema, o relato e `PhotoId`. `PhotoId` aponta com força fraca para `Photos.photos` em [[banco-mongo-relacoes]]. Não é constraint. O serviço guarda o identificador e não abre a foto. O rastro da foto nomeia `ReportPhoto`. A linha está em `ReportFotos`.

A lista devolve só o relato ativo de quem relatou, naquela empresa e naquele sistema, com as fotos ativas de cada um. Não devolve o que foi relatado sobre essa pessoa. A leitura de um relato só existe para alimentar o desligar. Não esconde perfil, conversa nem agenda.

## O que já se consegue fazer

Listar os relatos ativos da pessoa do caminho, com as fotos ativas. A pessoa da lista é quem relatou.

Gravar um relato. O pedido traz o relato inteiro: quem relata, quem é relatado, o item, o nome de tabela, a descrição e as fotos. O serviço não troca essas pessoas pela pessoa da sessão. Identificador preenchido tenta incluir a linha. Identificador vazio tenta substituir. Cada foto que vier junto recebe o identificador do relato e segue pelo gravar de foto, sem a chamada esperar o fim. Se a gravação do relato diz que entrou, a resposta passa a ser a do rastro: inclusão, banco `Report`, tabela `Report`, e um rastro por foto nomeando a tabela `ReportPhoto`. Se a gravação do relato diz que não entrou, a resposta continua sucesso e o rastro do relato não é escrito. A foto pode ter sido tentada mesmo assim.

Alterar um relato. Cai na mesma gravação. Com a gravação dizendo que entrou, o rastro descreve edição. Sem identificador, a alteração tenta substituir. Com identificador, tenta incluir.

Gravar uma foto e alterar uma foto. As duas caem na mesma gravação de `ReportFotos`. Identificador preenchido tenta incluir; vazio tenta substituir. O rastro nomeia a tabela `ReportPhoto`. Na alteração, o motivo do rastro é edição. A linha continua em `ReportFotos`.

Desligar um relato. Chega como leitura. O serviço marca o relato inativo e marca inativas as fotos ativas daquele relato. As linhas ficam e somem da lista. O rastro descreve inclusão e só é escrito se a empresa do caminho não vier vazia. O antes e o depois saem do mesmo objeto, já inativo. O desligar lê um trecho do caminho que não entra na busca.

Desligar uma foto. Também é leitura. A linha fica, fora de uso. O rastro descreve inclusão e nomeia a tabela `ReportPhoto`.

A checagem de acesso está invertida. Em todas essas ações a pergunta ao login vem antes. Se o login aceita o acesso, a ação é recusada. Se o login não aceita, a ação segue. A autenticação preparada na subida do serviço não entra no caminho do pedido.

O cliente deste repositório chama `api/Report` e, no apagar da foto, `api/Service`. Lista e grava em `api/Report`, altera em `api/Report/User/Edit` e apaga a foto em `api/Service/Delete/photo/`. São caminhos que esta porta não publica. Esta porta publica lista, gravar, alterar, gravar foto, alterar foto, desligar e desligar foto sem o prefixo `api/Report`. O alterar dela não tem o trecho `User`.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Pela metade | Já se lista o relato ativo de quem relatou. Gravar, alterar e desligar relato e foto estão escritos sobre `Report` e `ReportFotos`, sem tela em uso. A checagem está invertida. Identificador preenchido tenta incluir; identificador vazio tenta substituir. O rastro da foto nomeia `ReportPhoto`; a linha está em `ReportFotos`. O cliente chama caminhos que esta porta não publica |
| Casca | Não há tela de relato em uso. Isto não é [[board-denuncia]]. Não esconde perfil, conversa nem agenda |

## O que esta nota não cobre

A tela do app, que não está em uso, e o pedido [[board-denuncia]]. O miolo de [[bff-relatos]], além das duas camadas: o núcleo tem `ReportDescription`, `UserId` e `ReportedUserId`; o retrato do BFF não declara texto, motivo nem sobre quem. Senha, string de conexão e identificador de empresa ou de aplicativo. O desenho do banco além do necessário para fechar a cadeia: o detalhe fica em [[banco-sql-report]] e [[banco-mongo-relacoes]].

## Incertezas

A pergunta ao login reenvia o acesso já apresentado como acesso, e o login apresenta de novo. Uma sessão no formato usual pode falhar nessa pergunta. Quando falha, a ação segue. Quando o login aceita, a ação é recusada.

O desligar do relato publica o último trecho do caminho com nome de endereço. A busca usa o identificador do relato, e esse trecho não o preenche. Sem relato ativo para o identificador que sobra, a chamada quebra e nada é desligado. O aviso dessa falha fala em deleção de endereço. O aviso de falha ao listar ou gravar fala em denúncia. O texto de abertura do serviço ainda se apresenta como serviço de endereço. O registro gravado continua o relato em `Report` e `ReportFotos`.

O rastro da foto nomeia a tabela `ReportPhoto`. A linha continua em `ReportFotos`.

No gravar e no alterar, a resposta de sucesso, quando a gravação diz que entrou, é a do rastro. A linha pode já ter mudado se o rastro quebrar. Se a gravação diz que não entrou, a chamada responde sucesso sem rastro do relato. Sem a lista de fotos, a gravação quebra depois que o relato pode já ter sido escrito. O gravar de cada foto não segura a resposta.

No desligar, o antes e o depois do rastro saem iguais, já inativos. Empresa vazia no caminho responde sucesso sem rastro.

No Windows e no Linux o serviço força o catálogo `Report` a partir da conexão de login. O compose deste repositório aponta `Database` para `Report`, em variáveis que esse código não lê. Fora do Windows e do Linux, o código pede uma conexão chamada `Address`, e a configuração deste projeto declara a conexão `Report`, sem declarar `Address`. Por este repositório não dá para fechar qual catálogo o host publicado está usando agora. As tabelas do modelo seguem `Report` e `ReportFotos`.

`ReportedTable` é texto. Não dá para fechar quais itens um relato pode apontar.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
