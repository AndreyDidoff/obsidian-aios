> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Conta

## Onde isso mora

1. No app: [[entrar-senha-e-biometria]], [[entrar-senha-e-biometria-do-artista]], [[criar-conta]], [[cadastro-do-artista]].
2. No BFF: o app fala com api.wecareu.app. [[bff-entrar-sair-e-senha]] e [[bff-cadastro]].
3. Projeto: Br.Login.API (grafia da pasta). Host: https://loginapimicroservice.bptsoftware.com.br/ (UrlsLogin e UrlsAuth).
4. Banco: [[banco-sql-userlogin]], SQL UserLogin, tabelas Usuario, Session, forgetpassword e GrupoUsuario. BlockUsers fica de fora desta nota (é o bloqueio).

## O que isso é

É a conta da pessoa no BPT-Core: quem ela é, a sessão aberta, o pedido de senha nova e o grupo a que pertence. O aplicativo não fala com este serviço. Fala com o BFF, e a regra de entrar, sair e cadastrar mora aqui.

Cliente e profissional nascem os dois em Usuario. O profissional, além da pessoa, abre uma empresa e fica ligado a ela. Foto, endereço, telefone, assinatura e empresa não são tabelas deste banco: a conta guarda o vínculo e chama os outros serviços. O que cruza de banco está em [[banco-sql-relacoes]] e não é constraint. O contexto destas quatro tabelas também não declara trava entre elas; o vínculo é pelo identificador da pessoa.

## O que já se consegue fazer

Entrar com e-mail e senha, se a conta estiver ativa e a senha bater. Se já houver sessão ativa ainda no prazo, a mesma sessão volta. Se não houver, abre outra: 48 horas de acesso e 7 dias para renovar. Junto vêm o identificador da pessoa e, quando existem, os de foto, assinatura, endereços e telefones. O grupo é lido nesse momento e não volta na resposta.

Sair da sessão que está em uso. Também dá para encerrar todas as sessões da pessoa de uma vez.

Perguntar se a sessão ainda vale e ver quem está dentro, com a ficha, a foto, os endereços e os telefones. Se o acesso venceu e a renovação ainda vale, o serviço grava outra sessão.

Pedir senha nova por e-mail. Chega um código com 4 horas de prazo. Se o e-mail não for de uma conta ativa, a resposta é a mesma, para não revelar se a conta existe. Dá para recusar o código, conferir se ele combina com o e-mail e gravar a senha nova. Quem pede pode encerrar as outras sessões nessa troca. Quem já está dentro também troca a própria senha, com a mesma opção.

Cadastrar o cliente: nome, gênero, apelido, documento, e-mail, senha, foto e endereço. Se o e-mail ou o documento já existem, o cadastro para. A conta nasce com cinco estrelas e nenhuma avaliação.

Cadastrar o profissional: a mesma pessoa, mais a empresa (razão social, nome fantasia e documento da empresa). A pessoa fica ligada a essa empresa, e a resposta devolve os dois. O mesmo conflito de e-mail ou documento impede o cadastro.

Antes de cadastrar, perguntar se o documento da pessoa já existe e, quando vem também o documento da empresa, se já há empresa ligada a essa pessoa.

## Em que pé está

Entrar, reaproveitar sessão viva, abrir sessão nova e sair desta sessão: feito.

Sair de todas as sessões, como ação própria: feito. Na troca de senha, o pedido de sair de todos é disparado e a resposta não espera o encerramento: pela metade.

Ver quem está dentro, com foto, endereço e telefone: feito. A assinatura volta ao entrar e na confirmação da sessão pela área de senha; não volta nessa consulta da ficha.

Renovar quando o acesso venceu e a janela de 7 dias ainda vale: pela metade. A sessão nova é gravada e a resposta continua com a antiga.

O que a pessoa pode ver no sistema, no momento de entrar: casca. O grupo é lido e o retorno disso está desligado. A confirmação pela área de senha ainda busca telas e permissões.

Pedir o código, recusar, conferir e gravar a senha nova, e trocar a senha já dentro: feito no caminho. Pela metade no fechamento: o código continua ativo depois do uso, e a conferência não olha o prazo nem se ele ainda vale.

Cadastro de cliente e de profissional, com foto e endereço, e com empresa no profissional: feito no caminho feliz. A data de nascimento vem no pedido e não é gravada.

Saber se e-mail ou documento já existem, na pergunta solta de antes do cadastro: pela metade. A consulta pelo documento responde. A consulta por e-mail e documento não espera o banco.

Grupo da pessoa: operação interna. GrupoUsuario é lido; este serviço não coloca ninguém em grupo no cadastro.

Falha ao entrar ou ao mexer na senha: operação interna. O ocorrido é enviado para a operação.

## O que esta nota não cobre

O aplicativo, inclusive a biometria das notas de entrar. Aqui a entrada é e-mail e senha.

O BFF em si. O lugar dele na cadeia está em [[bff-entrar-sair-e-senha]] e [[bff-cadastro]].

O bloqueio de conta. BlockUsers não entra nesta nota.

Pagamento e modalidade. Há um gancho no entrar e ele não roda.

O miolo de foto, endereço, telefone, assinatura, e-mail, modelo da mensagem, sistemas e empresa. Este serviço chama esses vizinhos e fica com o vínculo.

A forma como a senha é transformada antes de gravar.

## Incertezas

UrlsLogin não aparece em Br.Login.API. A chave deste projeto é UrlsAuth no ambiente e Urls:Auth na configuração. O valor configurado é https://loginapimicroservice.bptsoftware.com.br, sem a barra final do briefing.

O e-mail de senha nova não usa esse host. O texto leva um endereço fixo no código: https://bptsoftwareloginservice.azurewebsites.net.

O contexto expõe forgetpassword e GrupoUsuario com outros nomes de coleção. As tabelas mapeadas são forgetpassword e GrupoUsuario. Vale a tabela. O identificador de GrupoUsuario está mapeado na coluna idsession.

A sessão marca o sistema como obrigatório e o entrar não preenche esse campo.

E-mail ou senha que não batem recusam a entrada. A busca, quando ninguém coincide, estoura erro em vez de seguir a mensagem de senha errada escrita logo abaixo. O efeito para a pessoa continua sendo recusa, com outro texto. Uma falha no meio do entrar também devolve o texto do erro.

No profissional, empresa e sistema chegam no pedido e não são usados para gravar a pessoa. O campo de empresa da pessoa recebe a empresa recém-criada. No cliente, esse mesmo campo recebe a empresa que veio no pedido. A empresa do profissional é gravada por outro serviço, o de sistemas, e não em Usuario. O cruzamento está em [[banco-sql-relacoes]] e não é constraint.

Cliente e profissional saem com o mesmo tipo de pessoa. O que o código separa é a empresa e o vínculo com ela.

A data de nascimento entra no cadastro e não é copiada para Usuario.

O documento é gravado sem pontuação. A conferência de duplicidade compara o texto como chegou. Um documento com máscara pode não achar o que já está gravado sem máscara, e o cadastro pode seguir mesmo assim.

Recusar o código não confere se o e-mail é o daquela conta. Código inexistente na troca de senha estoura erro; o ramo que recusaria em silêncio não chega a rodar.

A checagem do papel de acesso não confere emissor nem audiência. O que corta o acesso é a linha ativa em Session e o prazo.

Foto, endereço, telefone, assinatura e empresa são passos em outros serviços. Se um deles falha no meio, a conta pode ficar pela metade: empresa sem pessoa, ou pessoa sem endereço.
