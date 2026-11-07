> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# E-mails

## Onde isso mora

1. No app. Os apps de 21/10 não têm tela desta caixa. O e-mail que fica no cadastro da pessoa é outro dado. Esta nota não reescreve essa tela.
2. No BFF. [[bff-preparado-e-ainda-nao-oferecido]] deixa o canal de e-mail fora de uso. O app fala com api.wecareu.app.
3. No projeto Br.Email.API, no host https://emailapimicroservice.bptsoftware.com.br/
4. No banco [[banco-sql-email]]. O servidor nomeia o banco Email e as tabelas Emails e EmailOptions. A grafia OwnerIndentifier fica como no servidor. Owner e OwnerIndentifier estão sem destino único em [[banco-sql-relacoes]]; não são constraint.

## O que isso é

É o serviço de envio e de caixa. A caixa guarda endereços e a configuração para enviar. Não é a caixa de entrada de mensagens recebidas e não é o e-mail do cadastro da pessoa.

Há três saídas fixas da empresa, só para disparo: login, suporte e não responder. A mensagem sai em HTML para o endereço do pedido, com o assunto e o texto do pedido, e não fica gravada. O login se apresenta como Contact - BPT Software. O suporte se apresenta como Support - BPT Software. O não responder se apresenta como Não Responda - BPT Software. O remetente de cada uma vem da configuração do serviço, não das tabelas.

À parte, Emails guarda endereços de um dono: o endereço, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O dono vai em OwnerIndentifier. A lista do dia a dia só devolve endereço que continua ativo.

EmailOptions guarda a configuração de envio de uma caixa: servidor, porta, endereço, a senha dessa caixa, se ainda está em uso, as datas e quem mudou. O campo Owner é gravado. A leitura pede o identificador da própria configuração, não o dono.

## O que já se consegue fazer

Disparar o e-mail de login. Esse pedido não pergunta se o acesso vale. Não grava o texto. Não consulta Emails nem EmailOptions.

Disparar o e-mail de suporte e o de não responder. Os dois perguntam ao login se o acesso vale. Se o login aceita, o disparo é recusado. Se o login não aceita, o disparo segue. Também não gravam o texto e não leem as tabelas.

Listar os endereços ativos de um dono. O pedido chama esse dono de Onwer. A coluna continua OwnerIndentifier. Endereço desligado não volta.

Incluir um endereço. Sem identificador, o serviço abre linha nova. Com identificador, regrava a linha. O endereço entra ativo quando o pedido não diz o contrário. Não há conferência de formato nem regra de um endereço só por dono. Antes de gravar há trilha. A trilha nomeia o banco Email e a tabela Email, pede quem fez, o nome, a empresa e o sistema, e descreve a mudança como inclusão. Se a trilha estoura, a gravação não acontece. Se a trilha só responde que não gravou, o serviço ainda grava.

Editar um endereço. É o mesmo pedido da inclusão: identificador vazio vira linha nova; identificador preenchido substitui a linha. A trilha também descreve isso como inclusão.

Apagar um endereço. A linha não sai da tabela: fica fora de uso e deixa de aparecer na lista. O pedido chega como uma consulta e leva só o identificador. A trilha que roda antes descreve isso como inclusão e nomeia a tabela Email. Se não houver linha com esse identificador, o desligamento quebra e o endereço permanece. Se a trilha estoura, o desligamento não acontece. Se a trilha só responde que não gravou, o serviço ainda desliga.

Ler uma configuração ativa pelo identificador dela. Não há lista de configurações de um dono. Owner não entra nessa busca. Configuração desligada não volta.

Incluir ou editar uma configuração. A regra do identificador é a mesma do endereço. Viajam juntos servidor, porta, endereço, senha da caixa, quem alterou e as datas. A trilha de novo nomeia a tabela Email e descreve inclusão. A senha segue no pedido; esta nota não a reproduz.

Apagar uma configuração. A linha fica fora de uso. Esse desligamento não passa por trilha. Sem configuração ativa com aquele identificador, a chamada quebra.

Enviar pela configuração. O pedido leva o identificador da configuração, o destino, o assunto e o texto. O remetente é o endereço da configuração, sem nome de exibição. O envio usa o servidor, a porta e a senha daquela configuração. Não olha a lista de endereços. Não grava a mensagem. Não pergunta se o acesso vale. Se não houver configuração ativa com aquele identificador, o envio quebra e nada sai.

## Em que pé está

As saídas de login, suporte e não responder e a caixa de endereços com configuração estão escritas e respondem, sem tela no app e com o canal de e-mail fora de uso no BFF. Lista, gravação e desligamento recusam o pedido quando o login aceita o acesso e seguem quando o login não aceita. O disparo de login e o envio pela configuração nem fazem essa pergunta. A autenticação preparada na subida do serviço não entra no caminho do pedido. No Windows e no Linux as três saídas da empresa sobem sem servidor, porta nem remetente, porque essa configuração só é ligada fora desses dois sistemas. Owner e OwnerIndentifier seguem sem constraint, e o serviço aceita o dono que vier.

## O que esta nota não cobre

Não cobre o aplicativo nem o e-mail guardado no cadastro da pessoa. Não cobre o BFF por dentro; o elo é [[bff-preparado-e-ainda-nao-oferecido]]. Não cobre caixa de entrada, anexo, template nem o que os outros serviços disparam com esse host. Não reproduz senha, connection string nem identificador de empresa ou aplicativo.

## Incertezas

O wikilink do banco permanece [[banco-sql-email]]: o script deste repositório cria o banco Email e as tabelas Emails e EmailOptions, sem chave estrangeira em Owner nem em OwnerIndentifier. O compose do serviço br.email.api aponta Database para Email, e o código de Windows e Linux não lê essa variável: pega a conexão de login e força o catálogo Email. O compose não define essa conexão de login. Fora desses dois sistemas, o serviço pede uma conexão chamada UserLogin, e a configuração deste projeto declara a conexão Email, com catálogo Email, sem declarar UserLogin. O perfil de publicação aponta a conexão Email para o banco Email. Por este repositório não dá para fechar qual conexão o host publicado está usando agora. A trilha grava a tabela como Email, e as linhas moram em Emails e EmailOptions.
