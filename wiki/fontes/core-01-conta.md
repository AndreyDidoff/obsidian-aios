---
tipo: fonte
arquivo: "ingeridos/core-01-conta.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Conta"]
---

# Conta

Retrato de 21/10 do projeto `Br.Login.API`. Host `https://loginapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-userlogin]], SQL `UserLogin`, tabelas `Usuario`, `Session`, `forgetpassword` e `GrupoUsuario`. `BlockUsers` fica de fora desta nota.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

1. No app: [[entrar-senha-e-biometria]], [[entrar-senha-e-biometria-do-artista]], [[criar-conta]], [[cadastro-do-artista]].
2. No BFF: o aplicativo fala com `api.wecareu.app`. [[bff-entrar-sair-e-senha]] e [[bff-cadastro]].
3. Neste serviço: `Br.Login.API`. O aplicativo não fala com ele. Fala com o BFF. A regra de entrar, sair e cadastrar mora aqui.

O que cruza de banco está em [[banco-sql-relacoes]] e não é constraint. O contexto destas quatro tabelas também não declara trava entre elas. O vínculo é pelo identificador da pessoa.

## O que isso é

A conta da pessoa neste núcleo: quem ela é, a sessão aberta, o pedido de senha nova e o grupo a que pertence. Cliente e profissional nascem os dois em `Usuario`. O profissional, além da pessoa, abre uma empresa e fica ligado a ela. Foto, endereço, telefone, assinatura e empresa não são tabelas deste banco. A conta guarda o vínculo e chama os outros serviços.

## O que já se consegue fazer

Entrar com e-mail e senha, se a conta estiver ativa e a senha bater. Se já houver sessão ativa ainda no prazo, a mesma sessão volta. Se não houver, abre outra: 48 horas de acesso e 7 dias para renovar. Junto vêm o identificador da pessoa e, quando existem, os de foto, assinatura, endereços e telefones. O grupo é lido nesse momento e não volta na resposta.

Sair da sessão que está em uso. Também dá para encerrar todas as sessões da pessoa de uma vez.

Perguntar se a sessão ainda vale e ver quem está dentro, com a ficha, a foto, os endereços e os telefones. Se o acesso venceu e a renovação ainda vale, o serviço grava outra sessão.

Pedir senha nova por e-mail. O código tem 4 horas de prazo no pedido. Se o e-mail não for de uma conta ativa, a resposta é a mesma. Dá para recusar o código, conferir se ele combina com o e-mail e gravar a senha nova. Quem pede pode encerrar as outras sessões nessa troca. Quem já está dentro também troca a própria senha, com a mesma opção.

Cadastrar o cliente: nome, gênero, apelido, documento, e-mail, senha, foto e endereço. Se o e-mail ou o documento já existem, o cadastro para. A conta nasce com cinco estrelas e nenhuma avaliação. A data de nascimento vem no pedido e não é gravada.

Cadastrar o profissional: a mesma pessoa, mais a empresa (razão social, nome fantasia e documento da empresa). A pessoa fica ligada a essa empresa, e a resposta devolve os dois. O mesmo conflito de e-mail ou documento impede o cadastro.

Antes de cadastrar, perguntar se o documento da pessoa já existe e, quando vem também o documento da empresa, se já há empresa ligada a essa pessoa.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito | Entrar, reaproveitar sessão viva, abrir sessão nova e sair desta sessão. Ver quem está dentro, com foto, endereço e telefone. Pedir o código, recusar, conferir e gravar a senha nova, e trocar a senha já dentro, no caminho. Cadastro de cliente e de profissional, com foto e endereço, e com empresa no profissional, no caminho feliz. Sair de todas as sessões, como ação própria |
| Pela metade | Na troca de senha, o pedido de sair de todos é disparado e a resposta não espera o encerramento. Renovar: a sessão nova é gravada e a resposta continua com a antiga. No fechamento da senha, o código continua ativo depois do uso, e a conferência não olha o prazo nem se ele ainda vale. Na pergunta solta de antes do cadastro, a consulta pelo documento responde; a consulta por e-mail e documento não espera o banco. A data de nascimento vem no pedido e não é gravada |
| Casca | O que a pessoa pode ver no sistema, no momento de entrar. O grupo é lido e o retorno disso está desligado. A confirmação pela área de senha ainda busca telas e permissões |
| Operação interna | Grupo da pessoa. `GrupoUsuario` é lido. Este serviço não coloca ninguém em grupo no cadastro. Falha ao entrar ou ao mexer na senha: o ocorrido é enviado para a operação |

A assinatura volta ao entrar e na confirmação da sessão pela área de senha. Não volta na consulta da ficha.

As cinco estrelas e nenhuma avaliação, ao nascer a conta, não são o fallback de tela 5,0 nem a decisão de avaliação obrigatória. O alvo do cadastro permanece em [[cadastro]]. A sessão e a senha permanecem em [[fluxo-de-entrada]].

## O que esta nota não cobre

O aplicativo, inclusive a biometria das notas de entrar. Aqui a entrada é e-mail e senha.

O BFF em si. O lugar dele na cadeia está em [[bff-entrar-sair-e-senha]] e [[bff-cadastro]].

O bloqueio de conta. `BlockUsers` não entra nesta nota. O miolo está em [[core-07-bloqueio]].

Pagamento e modalidade. Há um gancho no entrar e ele não roda.

O miolo de endereço e de telefone está em [[core-08-enderecos]] e [[core-09-telefones]]. Empresa está em [[core-04-empresa-e-colaboradores]]. Foto está em [[core-11-fotos]]. E-mail está em [[core-10-emails]]. Assinatura está em [[core-14-assinatura]]. Modelo da mensagem está em [[core-15-modelos-de-mensagem]]. Sistemas estão em [[core-16-permissoes-grupos-e-telas]]. Este serviço chama esses vizinhos e fica com o vínculo.

A forma como a senha é transformada antes de gravar.

## Incertezas

`UrlsLogin` não aparece em `Br.Login.API`. A chave deste projeto é `UrlsAuth` no ambiente e `Urls:Auth` na configuração. O valor configurado é `https://loginapimicroservice.bptsoftware.com.br`, sem a barra final. A linha `UrlsLogin` de [[beautiful-api]] permanece.

O e-mail de senha nova não usa esse host. O texto leva um endereço fixo no código: `https://bptsoftwareloginservice.azurewebsites.net`.

O contexto expõe `forgetpassword` e `GrupoUsuario` com outros nomes de coleção. As tabelas mapeadas são `forgetpassword` e `GrupoUsuario`. Vale a tabela. O identificador de `GrupoUsuario` está mapeado na coluna `idsession`.

A sessão marca o sistema como obrigatório e o entrar não preenche esse campo.

E-mail ou senha que não batem recusam a entrada. A busca, quando ninguém coincide, estoura erro em vez de seguir a mensagem de senha errada escrita logo abaixo. O efeito para a pessoa continua sendo recusa, com outro texto. Uma falha no meio do entrar também devolve o texto do erro.

No profissional, empresa e sistema chegam no pedido e não são usados para gravar a pessoa. O campo de empresa da pessoa recebe a empresa recém-criada. No cliente, esse mesmo campo recebe a empresa que veio no pedido. A empresa do profissional é gravada por outro serviço, o de sistemas, e não em `Usuario`. O cruzamento está em [[banco-sql-relacoes]] e não é constraint. Cliente e profissional saem com o mesmo tipo de pessoa. O que o código separa é a empresa e o vínculo com ela.

A data de nascimento entra no cadastro e não é copiada para `Usuario`.

O documento é gravado sem pontuação. A conferência de duplicidade compara o texto como chegou. Um documento com máscara pode não achar o que já está gravado sem máscara, e o cadastro pode seguir mesmo assim.

Recusar o código não confere se o e-mail é o daquela conta. Código inexistente na troca de senha estoura erro. O ramo que recusaria em silêncio não chega a rodar.

A checagem do papel de acesso não confere emissor nem audiência. O que corta o acesso é a linha ativa em `Session` e o prazo.

Foto, endereço, telefone, assinatura e empresa são passos em outros serviços. Se um deles falha no meio, a conta pode ficar pela metade: empresa sem pessoa, ou pessoa sem endereço.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
