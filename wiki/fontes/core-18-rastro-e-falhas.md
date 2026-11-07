---
tipo: fonte
arquivo: "ingeridos/core-18-rastro-e-falhas.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Rastro e falhas"]
---

# Rastro e falhas

Retrato de 21/10 de dois projetos de operação interna. O rastro é `Br.Audit.API`, host `https://auditapimicroservice.bptsoftware.com.br/`, banco [[banco-sql-audition]]: o banco se chama `Audition` e a tabela se chama `Audit`. As falhas são `Br.Error.Loggin.API`, host `https://slacklogginapimicroservice.bptsoftware.com.br/`, com a grafia `slackloggin` de um g só. Sem banco SQL e sem tabela.

Foto desses serviços. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. Os apps de 21/10 não pedem. No BFF a auditoria segue só preparada ([[bff-preparado-e-ainda-nao-oferecido]]). Esta página não fecha isso.

## Onde isso mora

Rastro:

1. No app. Os apps de 21/10 não pedem isto. Não há tela de rastro nesta extração.
2. No BFF. Auditoria fica só preparada ([[bff-preparado-e-ainda-nao-oferecido]]). O aplicativo fala com `api.wecareu.app`.
3. Neste serviço: `Br.Audit.API`. O aplicativo não fala com ele. Fala com o BFF.
4. O compose deste repositório (`Br.Login.API/docker-compose.yml`, serviço `br.audit.api`) declara `Database` `Audition`.

Falhas:

1. No app. Os apps de 21/10 não pedem isto. Não há tela de falha nesta extração. É operação interna.
2. `Br.Error.Loggin.API`, no host `https://slacklogginapimicroservice.bptsoftware.com.br/`.
3. Sem banco SQL nesta extração. O compose deste repositório (`Br.Login.API/docker-compose.yml`, serviço `br.error.loggin.api`) não declara `Database`. Não há tabela.

## O que isso é

O rastro é a linha de uma mudança. Junto vão o sistema, a empresa, a pessoa, quem mudou em texto, quem aprovou, o verbo, o motivo, o nome do banco e o nome da tabela que a mudança cita, o objeto de antes, o objeto de depois, quando a linha nasceu e quando mudou. Quem aprovou viaja em dois campos, com a grafia `Aproved`: um identificador e um texto. Os dois podem vir vazios.

`AprovedId` não tem destino único. `UserId` é força fraca para `Usuario`. `SystemId` e `EnterpriseId` são força forte. As amarrações estão em [[banco-sql-relacoes]] e não são constraint. O script da tabela não cria essas amarrações. Ao gravar, o serviço aceita os identificadores que vierem e não procura a pessoa, o sistema nem a empresa.

A falha é um texto que segue para um canal. Não fica em tabela. Não é tela e não é função do app.

## O que já se consegue fazer

Listar as linhas de uma empresa e de um sistema. O pedido leva esses dois identificadores. Volta tudo desse par: pessoa, verbo, tabela e período não filtram. A tabela não guarda linha fora de uso, então não há o que esconder.

Ler uma linha. O pedido leva a empresa, o sistema e o identificador da linha, nessa ordem. Linha de outro par não volta. Linha que não existe responde com corpo vazio.

Gravar a linha inteira. Sem identificador, abre linha nova e devolve o identificador que ficou na linha. Com identificador, essa foto substitui a linha e devolve o mesmo identificador. Identificador que não existe não abre linha nova, e a chamada ainda devolve esse identificador. Quem mudou, o verbo, o motivo, o banco, a tabela e o objeto de depois precisam vir na própria linha. O serviço não preenche isso com quem está na sessão. Não há conferência de tamanho, de vazio nem de identificador solto além do que a tabela recusar. Não há ação de apagar.

Antes de listar, ler e gravar, o serviço pergunta ao login se o acesso vale. A checagem está invertida: se o login aceita, a ação é recusada; se o login não aceita, a ação segue. A autenticação preparada na subida do serviço não entra no caminho do pedido. A única trava é essa checagem.

A subida do rastro registra o acesso à tabela, o login e o aviso de falha, e não entrega o miolo que lista, lê e grava. O pedido quebra antes de abrir a tabela.

O cliente interno que os outros serviços deste repositório usam para deixar rastro grava num caminho de criação. O serviço só grava num caminho de salvamento. A criação não alcança a ação, então o rastro deixado pelos outros serviços não é linha já gravada em `Audit`. A lista desse cliente junta empresa e sistema no endereço sem a separação que a ação espera, e também não alcança. A leitura que tira empresa e sistema da sessão usa a ordem que a ação publica. A leitura que recebe sistema e empresa em separado inverte os dois no caminho. O cliente trata a chamada como feita quando o host responde e não olha o identificador devolvido. Pessoa, nome, empresa e sistema que ele manda à parte não entram na linha: o serviço não os lê.

Lista e leitura, quando falham, saem com aviso de carregamento de endereço. A gravação, quando falha, sai com aviso de salvamento de auditoria. Os três seguem para o canal marcado como Discord. Se esse aviso também falha, a chamada quebra no aviso.

No serviço de falhas dá para encaminhar um texto ao Slack e um texto ao Discord. O destino de cada um sai do ambiente da máquina, não do pedido, e não está neste repositório. Não dá para fechar se o host publicado tem para onde enviar. O texto do Slack viaja como veio. O texto do Discord viaja como veio, com o nome `SystemError`. Texto com aspa quebra o envio ao Discord. O cliente interno manda o texto: se o alvo é a palavra Discord, cai no Discord; qualquer outro alvo cai no Slack. Quando uma ação dos outros serviços deste repositório quebra, o aviso pede Discord. As duas ações não perguntam ao login se o acesso vale. Não há lista nem releitura. Quando o envio falha, fica um registro local com a grafia `mendagem` e a chamada quebra. Nada disso vai para tabela.

## Em que pé está

Operação interna. Os apps de 21/10 não pedem rastro nem falha, e o BFF deixa a auditoria só preparada. No rastro já existem lista, leitura e gravação na tabela `Audit`. O miolo dessas ações não é entregue na subida: o pedido quebra antes de abrir a tabela. A gravação do cliente interno não alcança a ação. A checagem do rastro está invertida. O modelo pede `DtCreated` e o script da tabela não cria essa coluna. Nas falhas já se encaminha um texto ao Slack ou ao Discord, sem banco, sem pergunta ao login e sem linha em tabela.

## O que esta nota não cobre

Telas. O miolo do que o BFF ainda não oferece; o elo de auditoria é [[bff-preparado-e-ainda-nao-oferecido]], e a auditoria segue só preparada. O verbo, o banco e a tabela que cada outro serviço cita ao deixar rastro; isso fica na nota daquele serviço. Senha, connection string e o endereço do canal. Quem lê o canal. O conteúdo das linhas já gravadas e o das mensagens já enviadas.

## Incertezas

O modelo que o serviço lê chama a data de criação de `DtCreated`. O script que cria a tabela `Audit`, e o backup deste repositório, não têm essa coluna. A data de mudança fecha nos dois, como `DtChange`. Contra esse script, listar, ler e gravar quebram ao tocar a linha. Não dá para fechar, por este repositório, se o banco do host publicado já ganhou `DtCreated`.

Sem identificador, a inclusão devolve o identificador que ficou na linha depois da gravação. Não dá para fechar, só com este código, se o banco troca um identificador vazio pelo dele ou se a linha nasce vazia.

No Windows e no Linux o serviço pega a conexão `UserLogin` e força o catálogo `Audition`. O compose do serviço `br.audit.api` declara `Database` `Audition` e não declara `UserLogin`. Fora desses dois sistemas, usa a conexão `UserLogin` da configuração, que já nomeia o catálogo `Audition`. O wikilink permanece [[banco-sql-audition]].

A pergunta ao login reenvia o acesso já apresentado como acesso. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler a porta como fechada para quem não está logado.

A gravação do cliente interno vai para um caminho de criação que o serviço não publica. A lista desse cliente não separa o endereço como a ação espera. A leitura com sistema e empresa em argumentos separados troca os dois. Não dá para tratar o rastro deixado pelos outros serviços como linha gravada em `Audit`.

O destino do Slack e o do Discord não estão neste repositório. O compose de `br.error.loggin.api` não os declara. Não dá para fechar se o host publicado tem para onde enviar. Sem isso, o aviso quebra e nada fica guardado.

A lacuna de sessão do BFF segue aberta: o arranque prepara a sessão e não a lê no caminho do pedido. Ver [[contradicoes-e-lacunas]], [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
