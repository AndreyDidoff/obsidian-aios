> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Organização

## Onde isso mora

1. No app: os apps de 21/10 não gerem esta organização numa tela.
2. No BFF: o retrato de 21/10 deixa dados da empresa só preparados ([[bff-preparado-e-ainda-nao-oferecido]]).
3. Projeto Br.Enterprise.API. Host https://enterpriseapimicroservice.bptsoftware.com.br/
4. Banco [[banco-sql-enterprise]], tabela Enterprise. Company de [[banco-sql-systemservice]] é a empresa do profissional, outra linha, outro banco.

## O que isso é

É a organização dona do aplicativo. A linha guarda razão social, nome fantasia, CNPJ, representante, tipo de negócio, segmento, site, CEP, cidade, complemento e número, o código de um plano, o código de um logo, se ainda está em uso, quando nasceu, quando mudou e quem mudou. Não há logradouro nem estado. E-mail e telefone não ficam nesta tabela: na leitura o serviço busca a foto do logo, os e-mails e os telefones e devolve junto. Lista e abertura só trazem organização ativa. A lista não olha a organização de quem chamou: devolve toda organização ativa.

## O que já se consegue fazer

Listar. Cada item traz a organização, a foto do logo, os e-mails e os telefones. Fora de uso não volta. Se a foto, o e-mail ou o telefone falhar no meio, a lista estoura, a falha vai para o registro de operação e a chamada estoura de novo.

Abrir pelo código. O mesmo conjunto, com os e-mails sob o nome mails; na lista o nome é emails. Sem organização ativa com aquele código, a chamada quebra ao pedir o logo.

Gravar. O pedido manda a organização inteira, os e-mails e os telefones. Sem código, nasce uma linha; com código, a foto substitui a que já existe. O serviço aceita o pedido como chegou: não confere CNPJ repetido, não tira máscara e não exige plano nem logo. Em seguida dispara só o e-mail e o telefone que ainda não têm código, sem esperar o fim e sem escrever neles o código da organização. O dono do contato é o que veio no pedido. Se o código da organização voltar vazio, a resposta é um pedido recusado no formato de tempo esgotado e não há trilha. Com código, a trilha nomeia o banco Enterprise e a tabela Enterprise, com verbo Post e motivo Inserting, sem foto anterior, e a resposta é esse código. A trilha exige no pedido quem fez, o nome, a empresa e o sistema. A linha já está gravada antes da trilha: se esses cabeçalhos faltarem, a trilha estoura e quem chamou não recebe o código.

Alterar. O serviço relê a organização, grava a foto nova e dispara todos os e-mails e telefones do pedido, de novo sem esperar. A resposta é se a trilha disse que gravou, não o código. Código vazio pula a trilha e a resposta ainda diz que deu certo. A trilha usa verbo Post, motivo Editing e código de trilha vazio. A foto anterior é só a organização, sem e-mail e sem telefone.

Desligar. A chamada chega como leitura. A linha permanece e sai de uso, então some da lista e da abertura. Antes disso o serviço dispara o apagamento dos e-mails e das configurações de e-mail usando o código da organização no lugar do código de cada e-mail, e dispara o apagamento de cada telefone pelo código do telefone, sem esperar. A trilha roda antes do desligamento no banco e grava o antes e o depois já fora de uso, porque as duas fotos são a mesma. Sem organização ativa, a chamada quebra nessa trilha e a linha segue ativa; as tentativas de e-mail e telefone já saíram. Se faltar quem fez, o nome, a empresa ou o sistema, a trilha estoura e a organização permanece ativa. Se a trilha só responder que não gravou, o desligamento ainda acontece.

A autenticação preparada na subida não entra no pedido. A trava é a checagem invertida: token que o login aceita vira recusa, e token que o login recusa deixa listar, abrir, gravar, alterar e desligar seguirem. O cabeçalho segue inteiro, e o login recebe a palavra Bearer duas vezes.

## Em que pé está

Dá para listar, abrir, gravar, alterar e desligar a organização ativa, sem tela nos apps de 21/10 e com os dados da empresa só preparados no BFF ([[bff-preparado-e-ainda-nao-oferecido]]), com a checagem de acesso invertida, com e-mail e telefone disparados sem espera e o desligar chegando como leitura, e com o cliente do repositório chamando caminhos que esta porta não publica; ServicePlanId e Logo estão sem destino único em [[banco-sql-relacoes]], não são constraint.

## O que esta nota não cobre

O aplicativo. O BFF por dentro; o elo é [[bff-preparado-e-ainda-nao-oferecido]]. A empresa do profissional e os colaboradores, Company e CompanyUsers em [[banco-sql-systemservice]]. O que a foto, o e-mail e o telefone fazem por dentro. O plano de serviço como cadastro. Senha, connection string e identificador.

## Incertezas

Este projeto não declara o host `enterpriseapimicroservice`. O cliente que o login usa aponta para Urls:Enterprise, https://enterpriseapimicroservice.bptsoftware.com.br/, com a barra final. Esse cliente, e o pacote 3.1 ao lado, chamam /api/Enterprise/Create, /api/Enterprise/Edit, /api/Enterprise/list, /api/Enterprise/get/{id} e POST /api/Enterprise/Delete/{id}, e esperam a organização crua ou um código solto. A porta publica api/Enterprise/Enterprise/List, api/Enterprise/Enterprise/{id}, api/Enterprise/Enterprise/Save, api/Enterprise/Enterprise/Edit e GET api/Enterprise/Enterprise/Delete/{id}, e devolve a organização embrulhada com logo e contatos, ou um objeto com o código. Quem chama por esse cliente não encontra estas ações.

No Windows e no Linux a subida lê a variável UserLogin e troca o marcador pelo catálogo Enterprise. Sem o marcador, o catálogo permanece o que já estava na variável. Fora desses dois sistemas a subida pede a conexão Address, e a configuração deste projeto declara a conexão Enterprise, com catálogo Enterprise, sem declarar Address. O compose do serviço br.enterprise.api nomeia Database como Enterprise; a subida no Linux não lê essa variável.
