---
tipo: fonte
arquivo: "ingeridos/core-10-emails.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["E-mails"]
---

# E-mails

Retrato de 21/10 do projeto `Br.Email.API`. Host `https://emailapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-email]]. O servidor nomeia o banco `Email` e as tabelas `Emails` e `EmailOptions`. O compose do serviço `br.email.api` aponta `Database` para `Email`. O wikilink permanece o do servidor, [[banco-sql-email]].

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. Isto é envio e caixa de endereços. Não é a caixa de mensagens recebidas e não é o e-mail do cadastro da pessoa. Não fecha a lacuna do disparador nem o canal de e-mail do BFF, que segue fora de uso. Ver [[contradicoes-e-lacunas]].

## Onde isso mora

1. No app. Os apps de 21/10 não têm tela desta caixa. O e-mail que fica no cadastro da pessoa é outro dado. Esta nota não reescreve essa tela.
2. No BFF. [[bff-preparado-e-ainda-nao-oferecido]] deixa o canal de e-mail fora de uso. O aplicativo fala com `api.wecareu.app`. Esta nota não reescreve o miolo dessa porta.
3. Neste serviço: `Br.Email.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O serviço de envio e de caixa. A caixa guarda endereços e a configuração para enviar. Há três saídas fixas da empresa, só para disparo: login, suporte e não responder. A mensagem sai em HTML para o endereço do pedido, com o assunto e o texto do pedido, e o texto não fica gravado. O login se apresenta como Contact - BPT Software. O suporte se apresenta como Support - BPT Software. O não responder se apresenta como Não Responda - BPT Software. O remetente de cada uma vem da configuração do serviço, não das tabelas.

`Emails` guarda endereços de um dono: o endereço, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O dono vai em `OwnerIndentifier`, grafado como no servidor. A lista do dia a dia só devolve endereço que continua ativo. O pedido de lista chama esse dono de `Onwer`. A coluna continua `OwnerIndentifier`.

`EmailOptions` guarda a configuração de envio de uma caixa: servidor, porta, endereço, a senha dessa caixa, se ainda está em uso, as datas e quem mudou. A configuração guarda a senha da caixa. Esta nota não a copia. O campo `Owner` é gravado. A leitura pede o identificador da própria configuração, não o dono. `Owner` e `OwnerIndentifier` estão sem destino único em [[banco-sql-relacoes]]; não são constraint. O serviço aceita o dono que vier.

## O que já se consegue fazer

Disparar o e-mail de login. Esse pedido não pergunta se o acesso vale. Não grava o texto. Não consulta `Emails` nem `EmailOptions`.

Disparar o e-mail de suporte e o de não responder. Os dois perguntam ao login se o acesso vale. Se o login aceita, o disparo é recusado. Se o login não aceita, o disparo segue. Também não gravam o texto e não leem as tabelas.

Listar os endereços ativos de um dono. Endereço desligado não volta.

Incluir um endereço. Sem identificador, o serviço abre linha nova. Com identificador, regrava a linha. O endereço entra ativo quando o pedido não diz o contrário. Não há conferência de formato nem regra de um endereço só por dono. Antes de gravar há trilha. A trilha nomeia o banco `Email` e a tabela `Email`; o dado do endereço está em `Emails`. A trilha pede quem fez, o nome, a empresa e o sistema, e descreve a mudança como inclusão. Se a trilha estoura, a gravação não acontece. Se a trilha só responde que não gravou, o serviço ainda grava.

Editar um endereço. É o mesmo pedido da inclusão: identificador vazio vira linha nova; identificador preenchido substitui a linha. A trilha também descreve isso como inclusão e nomeia a tabela `Email`.

Apagar um endereço. A linha não sai da tabela: fica fora de uso e deixa de aparecer na lista. O pedido chega como uma consulta e leva só o identificador. A trilha que roda antes descreve isso como inclusão e nomeia a tabela `Email`. Se não houver linha com esse identificador, o desligamento quebra e o endereço permanece. Se a trilha estoura, o desligamento não acontece. Se a trilha só responde que não gravou, o serviço ainda desliga.

Ler uma configuração ativa pelo identificador dela. Não há lista de configurações de um dono. `Owner` não entra nessa busca. Configuração desligada não volta.

Incluir ou editar uma configuração. A regra do identificador é a mesma do endereço. Viajam juntos servidor, porta, endereço, senha da caixa, quem alterou e as datas. A senha segue no pedido; esta nota não a reproduz. A trilha de novo nomeia a tabela `Email` e descreve inclusão. A linha da configuração está em `EmailOptions`.

Apagar uma configuração. A linha fica fora de uso. Esse desligamento não passa por trilha. Sem configuração ativa com aquele identificador, a chamada quebra.

Enviar pela configuração. O pedido leva o identificador da configuração, o destino, o assunto e o texto. O remetente é o endereço da configuração, sem nome de exibição. O envio usa o servidor, a porta e a senha daquela configuração. Não olha a lista de endereços. Não grava a mensagem. Não pergunta se o acesso vale. Se não houver configuração ativa com aquele identificador, o envio quebra e nada sai.

Suporte, não responder, lista e gravação de endereço recusam o pedido quando o login aceita o acesso e seguem quando o login não aceita. O desligamento de endereço entra nessa mesma recusa. O disparo de login e o envio pela configuração nem fazem essa pergunta. A autenticação preparada na subida do serviço não entra no caminho do pedido.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Pela metade | As três saídas e a caixa de endereços com configuração estão escritas e respondem, sem tela no app e com o canal de e-mail fora de uso no BFF. Suporte, não responder, lista e gravação de endereço recusam quando o login aceita. O disparo de login e o envio pela configuração não perguntam se o acesso vale. A trilha nomeia a tabela `Email`; os endereços estão em `Emails` |
| Casca | No Windows e no Linux as três saídas da empresa sobem sem servidor, porta nem remetente, porque essa configuração só é ligada fora desses dois sistemas. A autenticação preparada na subida não entra no caminho do pedido |

Isto não é o disparador pendente de [[pendencias]] e não é o canal de e-mail fora de uso de [[bff-preparado-e-ainda-nao-oferecido]]. A lacuna continua aberta.

## O que esta nota não cobre

O aplicativo e o e-mail guardado no cadastro da pessoa. O BFF por dentro; o elo é [[bff-preparado-e-ainda-nao-oferecido]]. Caixa de entrada, anexo, template e o que os outros serviços disparam com esse host. Senha, connection string e identificador de empresa ou de aplicativo. A configuração guarda a senha da caixa; esta nota não a copia.

## Incertezas

O wikilink do banco permanece [[banco-sql-email]]: o script deste repositório cria o banco `Email` e as tabelas `Emails` e `EmailOptions`, sem chave estrangeira em `Owner` nem em `OwnerIndentifier`. O compose aponta `Database` para `Email`, e o código de Windows e Linux não lê essa variável: pega a conexão de login e força o catálogo `Email`. O compose não define essa conexão de login. Fora desses dois sistemas, o serviço pede uma conexão chamada `UserLogin`, e a configuração deste projeto declara a conexão `Email`, com catálogo `Email`, sem declarar `UserLogin`. O perfil de publicação aponta a conexão `Email` para o banco `Email`. Por este repositório não dá para fechar qual conexão o host publicado está usando agora. A trilha grava a tabela como `Email`, e as linhas moram em `Emails` e `EmailOptions`.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
