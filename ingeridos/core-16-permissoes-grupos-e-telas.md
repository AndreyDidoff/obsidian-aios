> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Permissões, grupos e registros de tela

## Onde isso mora

1. No app. Menu e permissão de tela do celular não são esta tabela. O celular, nesta extração, não lê estes registros para montar o que a pessoa vê.
2. No BFF. A porta dessa camada está em [[bff-o-que-a-pessoa-pode-ver]].
3. No projeto Br.Systems.API. Host https://systemsapimicroservice.bptsoftware.com.br/
4. No banco [[banco-sql-systemsdata]], SQL SystemsData. Seis tabelas: EnterpriseSystems, Groups, GroupsPermissions, Permissions, Screens, Systems.

## O que isso é

É o cadastro, neste núcleo, de sistema, de registro de tela, de permissão, de grupo e do vínculo da empresa com um sistema. Screens é registro deste núcleo. Não é a tela do aplicativo.

Um sistema guarda nome, endereço, o código de uma foto, se ainda está em uso, quando nasceu, quando mudou e quem mudou. Systems.PhotoId aponta com força fraca para Photos.photos em [[banco-mongo-relacoes]]. Não é constraint.

EnterpriseSystems liga uma empresa a um sistema. Os dois códigos são identificadores soltos.

Screens guarda o nome do registro, o sistema, se está em uso, as datas e quem mudou. Não guarda a empresa.

Permissions guarda nome, nome de exibição, o sistema, um registro de tela, se está em uso, as datas e quem mudou.

Groups guarda nome, sistema, registro de tela, empresa, se está em uso, as datas e quem mudou.

GroupsPermissions liga um grupo a uma permissão e guarda um tipo: nenhum, ver, auditado, editar ou apagar. Também guarda se a ligação está em uso, as datas e quem mudou. A leitura do grupo com as permissões não devolve esse tipo.

Os pares internos estão em [[banco-sql-relacoes]]. Não são constraint. Gravar um grupo não procura empresa, sistema nem registro de tela.

O código mapeia um complemento: o modelo chama UserComplement e o contexto expõe o conjunto como SystemComplement. O servidor de 21/10 não tem essa tabela. Ela fica fora das seis.

## O que já se consegue fazer

- Ver os grupos em uso de uma empresa e de um sistema. Grupo fora de uso não volta.
- Gravar ou alterar um grupo na mesma ação. Sem identificador, nasce uma linha com o identificador zerado que veio no pedido: o serviço não pede código novo ao banco e não deixa rastro. Com identificador, regrava o grupo inteiro como veio. Não confere se empresa, sistema ou registro de tela existem. Quem mudou é o texto do pedido, não a pessoa da sessão. O rastro só existe nessa alteração, roda antes da gravação, nomeia o banco como System e a tabela Groups, com verbo Post e motivo Editing, e sem o estado anterior. Se faltar no cabeçalho quem fez, o nome, a empresa ou o sistema, o rastro estoura e o grupo não muda. A resposta é se a gravação do grupo mexeu em alguma linha. O cliente interno diz que deu certo sempre que a chamada volta sem erro, mesmo quando nenhuma linha mudou.
- Ver os registros de tela em uso de um sistema. A empresa que vai no endereço não entra na consulta.
- Ver as permissões em uso de um sistema. A empresa não entra. Cada permissão traz um registro de tela, e a lista não filtra por ele.
- Pedir o pacote de uma empresa: os sistemas ligados a ela, a foto de cada um e os registros de tela em uso, mais os grupos enviados no pedido com as permissões em uso. A ligação empresa-sistema e o próprio sistema entram mesmo fora de uso. A ligação grupo-permissão fora de uso ainda puxa a permissão. Grupo fora de uso, se o código veio no pedido, ainda volta. O sistema do cabeçalho é lido e não entra na consulta. Sem esse cabeçalho a chamada quebra antes. A foto entra dentro da consulta que o banco teria de executar, então o pacote não completa, e as permissões do grupo, que viriam em seguida, não são lidas.
- Há uma ação de complemento. Ela tenta ler o mapeamento que o servidor de 21/10 não tem. Se a leitura passasse, a resposta seria sucesso sem corpo, porque o que foi lido é descartado. No servidor de 21/10 a leitura não passa.

Antes de cada ação o serviço pergunta ao login se o acesso vale. A resposta é sim ou não, e a trava compara isso com vazio. Sim ou não, a ação segue. Se a pergunta estourar, a falha vai para o registro de operação e a chamada estoura de novo. O mesmo caminho vale para as outras falhas destas ações.

Nesta porta não se grava sistema, registro de tela, permissão, ligação empresa-sistema nem ligação grupo-permissão. Não há desligar separado. O grupo some da lista de ativos quando a alteração o manda para fora de uso.

No login, a entrada deixa esta chamada comentada. A validação de um acesso que o login já aceitou pede o pacote com os grupos da pessoa. Esse cliente não manda o sistema no cabeçalho, e esta porta quebra ao ler esse cabeçalho. Esses grupos nascem no login. A montagem procura Groups por esses códigos.

## Em que pé está

Já se lista grupo em uso, registro de tela em uso e permissão em uso, e já se grava ou altera grupo, sem menu no celular e com a porta no BFF em [[bff-o-que-a-pessoa-pode-ver]], sem a checagem de acesso recusar ninguém e sem constraint entre as seis tabelas, enquanto o pacote da empresa com foto e permissões do grupo não completa e o complemento mapeado no código não existe no servidor de 21/10.

## O que esta nota não cobre

O menu e a permissão de tela do celular. O miolo de [[bff-o-que-a-pessoa-pode-ver]], além do lugar dessa porta na cadeia. O que a foto faz por dentro. O conteúdo das linhas já gravadas. Senha e connection string. O complemento como cadastro: o servidor de 21/10 não tem essa tabela, e esta nota não descreve as colunas dela.

## Incertezas

Este projeto não declara o host público. Os clientes dos outros serviços apontam para https://systemsapimicroservice.bptsoftware.com.br/ , e alguns de desenvolvimento usam a porta 12443. O HSTS deste projeto exclui `systemsapimicroservice.bptsoftware.com`, sem `.br`.

O cliente do complemento chama a ação em leitura, em `/api/system/Complement/{sistema}`. A porta só aceita envio nesse caminho. Os dois não se encontram. O pacote 3.1 ao lado chama os mesmos caminhos de lista, grupo, registro de tela e permissão, sem o cabeçalho de sessão.

O rastro da alteração nomeia o banco System. O dado continua em SystemsData. A segunda inclusão com identificador zerado pode colidir com a primeira.

Se o código de grupo que o login manda não for o de Groups, o pacote não acha grupo.
