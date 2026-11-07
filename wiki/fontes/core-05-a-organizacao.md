---
tipo: fonte
arquivo: "ingeridos/core-05-a-organizacao.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Organização"]
---

# Organização

Retrato de 21/10 do projeto `Br.Enterprise.API`. Host `https://enterpriseapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-enterprise]], tabela `Enterprise`. É a organização dona do aplicativo.

`Company`, em [[banco-sql-systemservice]], é a empresa do profissional. São linhas e bancos diferentes. Ver [[core-04-empresa-e-colaboradores]].

Foto desse serviço. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

1. No app. Os apps de 21/10 não gerem esta organização numa tela.
2. No BFF. O retrato de 21/10 deixa dados da empresa só preparados ([[bff-preparado-e-ainda-nao-oferecido]]). Isso permanece só preparado.
3. Neste serviço: `Br.Enterprise.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

A linha guarda razão social, nome fantasia, CNPJ, representante, tipo de negócio, segmento, site, CEP, cidade, complemento e número, o código de um plano, o código de um logo, se ainda está em uso, quando nasceu, quando mudou e quem mudou. Sem logradouro e sem estado. E-mail e telefone não ficam na tabela: a leitura busca logo, e-mails e telefones. Lista e abertura só trazem organização ativa. A lista devolve toda organização ativa, não a de quem chamou.

## O que já se consegue fazer

Listar. Cada item traz a organização, a foto do logo, os e-mails e os telefones. Fora de uso não volta. Se a foto, o e-mail ou o telefone falhar no meio, a lista estoura, a falha vai para o registro de operação e a chamada estoura de novo.

Abrir pelo código. O mesmo conjunto, com os e-mails sob o nome `mails`; na lista o nome é `emails`. Sem organização ativa com aquele código, a chamada quebra ao pedir o logo.

Gravar. O pedido manda a organização inteira, os e-mails e os telefones. Sem código, nasce uma linha; com código, a foto substitui a que já existe. O serviço aceita o pedido como chegou: não confere CNPJ repetido, não tira máscara e não exige plano nem logo. Em seguida dispara só o e-mail e o telefone que ainda não têm código, sem esperar o fim e sem escrever neles o código da organização. O dono do contato é o que veio no pedido. Se o código da organização voltar vazio, a resposta é um pedido recusado no formato de tempo esgotado e não há trilha. Com código, a trilha nomeia o banco `Enterprise` e a tabela `Enterprise`, com verbo Post e motivo Inserting, sem foto anterior, e a resposta é esse código. A trilha exige no pedido quem fez, o nome, a empresa e o sistema. A linha já está gravada antes da trilha: se esses cabeçalhos faltarem, a trilha estoura e quem chamou não recebe o código.

Alterar. O serviço relê a organização, grava a foto nova e dispara todos os e-mails e telefones do pedido, de novo sem esperar. A resposta é se a trilha disse que gravou, não o código. Código vazio pula a trilha e a resposta ainda diz que deu certo. A trilha usa verbo Post, motivo Editing e código de trilha vazio. A foto anterior é só a organização, sem e-mail e sem telefone.

Desligar. A chamada chega como leitura. A linha permanece e sai de uso, então some da lista e da abertura. Antes disso o serviço dispara o apagamento dos e-mails e das configurações de e-mail usando o código da organização no lugar do código de cada e-mail, e dispara o apagamento de cada telefone pelo código do telefone, sem esperar. A trilha roda antes do desligamento no banco e grava o antes e o depois já fora de uso, porque as duas fotos são a mesma. Sem organização ativa, a chamada quebra nessa trilha e a linha segue ativa; as tentativas de e-mail e telefone já saíram. Se faltar quem fez, o nome, a empresa ou o sistema, a trilha estoura e a organização permanece ativa. Se a trilha só responder que não gravou, o desligamento ainda acontece.

A autenticação preparada na subida não entra no pedido. Checagem invertida: token que o login aceita vira recusa, e token que o login recusa deixa listar, abrir, gravar, alterar e desligar seguirem. O cabeçalho segue inteiro, e o login recebe a palavra Bearer duas vezes.

## Em que pé está

Dá para listar, abrir, gravar, alterar e desligar a organização ativa, sem tela nos apps de 21/10 e com os dados da empresa só preparados no BFF ([[bff-preparado-e-ainda-nao-oferecido]]). A checagem de acesso está invertida. E-mail e telefone são disparados sem espera e sem o código da organização escrito neles. Desligar chega como leitura. O cliente do repositório chama caminhos que esta porta não publica. `ServicePlanId` e `Logo` estão sem destino único em [[banco-sql-relacoes]]. Não são constraint.

## O que esta nota não cobre

O aplicativo. O BFF por dentro; o elo é [[bff-preparado-e-ainda-nao-oferecido]], e essa preparação segue aberta. A empresa do profissional e os colaboradores. O que a foto, o e-mail e o telefone fazem por dentro. O plano de serviço como cadastro. Senha, string de conexão e identificador.

## Incertezas

Este projeto não declara o host `enterpriseapimicroservice`. O cliente que o login usa aponta para `Urls:Enterprise`, `https://enterpriseapimicroservice.bptsoftware.com.br/`, com a barra final. Esse cliente, e o pacote 3.1 ao lado, chamam `/api/Enterprise/Create`, `/api/Enterprise/Edit`, `/api/Enterprise/list`, `/api/Enterprise/get/{id}` e POST `/api/Enterprise/Delete/{id}`. A porta publica `api/Enterprise/Enterprise/List`, `api/Enterprise/Enterprise/{id}`, `api/Enterprise/Enterprise/Save`, `api/Enterprise/Enterprise/Edit` e GET `api/Enterprise/Enterprise/Delete/{id}`. Quem chama por esse cliente não encontra estas ações.

No Windows e no Linux a subida lê a variável `UserLogin` e troca o marcador pelo catálogo `Enterprise`. Sem o marcador, o catálogo permanece o que já estava na variável. Fora desses dois sistemas a subida pede a conexão `Address`, e a configuração deste projeto declara a conexão `Enterprise`, com catálogo `Enterprise`, sem declarar `Address`. O compose do serviço `br.enterprise.api` nomeia `Database` como `Enterprise`; a subida no Linux não lê essa variável. Por este repositório não dá para fechar qual banco o host publicado está usando agora. O wikilink permanece [[banco-sql-enterprise]].

Ver [[bpt-core]].
