---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-22
fontes: ["[[decisoes-2026-10-20]]", "[[ssot-ecossistema-engenharia]]", "[[pendencias]]", "[[bff-o-que-e-este-backend]]", "[[bff-cliente-e-profissional]]", "[[bff-preparado-e-ainda-nao-oferecido]]", "[[bff-entrar-sair-e-senha]]", "[[bff-cadastro]]", "[[bff-servicos]]", "[[bff-planos-e-cupons]]", "[[bff-bloqueio]]", "[[bff-enderecos]]", "[[bff-telefones]]", "[[bff-fotos]]", "[[bff-relatos]]", "[[bff-documentos-para-validacao]]", "[[bff-o-que-a-pessoa-pode-ver]]", "[[cruzamento-bff-como-ler]]", "[[cruzamento-bff-conta]]", "[[cruzamento-bff-o-que-a-tela-le]]", "[[cruzamento-bff-o-que-ninguem-pede]]", "[[board-conta-e-acesso]]", "[[banco-indice]]", "[[banco-sql-relacoes]]", "[[banco-mongo-relacoes]]", "[[core-00-o-que-e-este-nucleo]]", "[[core-01-conta]]", "[[core-07-bloqueio]]", "[[core-08-enderecos]]", "[[core-09-telefones]]", "[[core-02-servicos]]", "[[core-03-agenda]]", "[[core-04-empresa-e-colaboradores]]", "[[core-05-a-organizacao]]", "[[core-06-planos-cupons-e-cobranca]]", "[[core-10-emails]]", "[[core-17-idiomas]]", "[[core-11-fotos]]", "[[core-12-relatos]]", "[[core-13-documentos-para-validacao]]", "[[core-14-assinatura]]", "[[core-15-modelos-de-mensagem]]", "[[core-16-permissoes-grupos-e-telas]]", "[[core-18-rastro-e-falhas]]"]
---

# Beautiful.API

BFF que o app consome hoje. O repositório no Azure chama-se `service_api`. O CNAME público é `api.wecareu.app`, o mesmo host do Swagger provisório. ([[decisoes-2026-10-20]]) → [[mvp]], [[protecao-de-dados]]

O snapshot de engenharia citava `service_api` só como "API central". Esta página é o detalhe confirmado pelo usuário: é um BFF, e os dados vêm dos microserviços abaixo. ([[ssot-ecossistema-engenharia]] descreve o nome; [[decisoes-2026-10-20]] descreve o papel.)

## Microserviços

Chaves como estão na configuração. Todos em `https://*.bptsoftware.com.br/`.

| Chave | URL |
|---|---|
| UrlsAddress | https://addressapimicroservice.bptsoftware.com.br/ |
| UrlsAudit | https://auditapimicroservice.bptsoftware.com.br/ |
| UrlsAuth | https://loginapimicroservice.bptsoftware.com.br/ |
| UrlsBilling | https://billingapimicroservice.bptsoftware.com.br/ |
| UrlsBlock | https://blockapimicroservice.bptsoftware.com.br/ |
| UrlsEnterprise | https://enterpriseapimicroservice.bptsoftware.com.br/ |
| UrlsI18N | https://i18napimicroservice.bptsoftware.com.br/ |
| UrlsLogging | https://slacklogginapimicroservice.bptsoftware.com.br/ |
| UrlsLogin | https://loginapimicroservice.bptsoftware.com.br/ |
| UrlsMail | https://emailapimicroservice.bptsoftware.com.br/ |
| UrlsPhone | https://phoneapimicroservice.bptsoftware.com.br/ |
| UrlsPhotos | https://photosapimicroservice.bptsoftware.com.br/ |
| UrlsReport | https://reportapimicroservice.bptsoftware.com.br/ |
| UrlsService | https://serviceapimicroservice.bptsoftware.com.br/ |
| UrlsSignature | https://signatureapimicroservice.bptsoftware.com.br/ |
| UrlsSystems | https://systemsapimicroservice.bptsoftware.com.br/ |
| UrlsTemplate | https://templateapimicroservice.bptsoftware.com.br/ |
| UrlsValidation | https://validationapimicroservice.bptsoftware.com.br/ |

## Observações

- `UrlsAuth` e `UrlsLogin` apontam para o mesmo host, `loginapimicroservice`.
- O host de logging está grafado `slacklogginapimicroservice`, com um "g" só. Registrado como está na configuração.
- Já existe `UrlsMail`, enquanto o disparador de e-mails segue como pendência. ([[pendencias]]) O serviço de e-mail do núcleo ([[core-10-emails]]) não é esse disparador nem o canal fora de uso. A lacuna continua aberta. Ver [[contradicoes-e-lacunas]].
- Já existe `UrlsEnterprise`, e o app de [[estabelecimento]] está fora do [[mvp]].

## Núcleo por trás deste BFF

O aplicativo fala com este BFF. A regra de negócio mora no núcleo [[bpt-core]], nos projetos `Br.*.API`, nos hosts `*.bptsoftware.com.br` e nos bancos. A foto de 21/10 dessa camada está na onda 1, e a onda 2 cobre bloqueio, endereço, telefone e serviços ([[core-07-bloqueio]], [[core-08-enderecos]], [[core-09-telefones]], [[core-02-servicos]]). A tabela dos 18 microserviços permanece. A onda 3 cobre agenda, empresa do profissional, organização e planos ([[core-03-agenda]], [[core-04-empresa-e-colaboradores]], [[core-05-a-organizacao]], [[core-06-planos-cupons-e-cobranca]]); `Br.PaymentPlan.API` segue sem URL nesta tabela. A onda 4 cobre e-mail ([[core-10-emails]]), idiomas ([[core-17-idiomas]]), fotos ([[core-11-fotos]]) e relatos ([[core-12-relatos]]). A tabela dos 18 microserviços permanece. Idiomas, neste BFF, seguem só preparados. A onda 5 cobre documentos ([[core-13-documentos-para-validacao]]), assinatura ([[core-14-assinatura]]), modelos ([[core-15-modelos-de-mensagem]]), permissões ([[core-16-permissoes-grupos-e-telas]]) e rastro ([[core-18-rastro-e-falhas]]), e a tabela dos 18 microserviços permanece. ([[core-00-o-que-e-este-nucleo]])

No projeto de conta, `UrlsLogin` não aparece. A chave é `UrlsAuth`, e o valor configurado não tem a barra final. ([[core-01-conta]])

## Retrato de 21/10

Foto do repositório `service_api`. O nome interno é Beautiful. O título do catálogo é "We Care U Service". Os pedidos entram pelo prefixo `beautiful/api/`. Não é alvo do [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. ([[bff-o-que-e-este-backend]], [[bff-cliente-e-profissional]], [[bff-preparado-e-ainda-nao-oferecido]], [[bff-entrar-sair-e-senha]], [[bff-cadastro]], [[bff-servicos]], [[bff-planos-e-cupons]], [[bff-bloqueio]], [[bff-enderecos]], [[bff-telefones]], [[bff-fotos]], [[bff-relatos]], [[bff-documentos-para-validacao]], [[bff-o-que-a-pessoa-pode-ver]])

Não desenha tela. Encaminha aos serviços; a regra de negócio mora neles. Está amarrado a uma empresa e a um aplicativo, no dado interno CompanyData. Os identificadores ficam na configuração e não entram na nota. O banco local sobe no arranque e não mapeia informação de negócio.

A estrutura lida em 21/10, separada deste BFF, está em [[banco-indice]]: onze bancos SQL e quatro Mongo. Não há chave estrangeira declarada. Os pares estão em [[banco-sql-relacoes]] e [[banco-mongo-relacoes]]. Os hosts desta página não mudam.

No cadastro há dois papéis: cliente (User) e profissional (Artist). O profissional recebe, neste backend, a empresa e o aplicativo. Fora do cadastro, as portas tratam a pessoa da sessão e não escolhem o caminho pelo papel.

| Pé | O que este retrato mostra |
|---|---|
| No ar | entrar e sair, senha ([[bff-entrar-sair-e-senha]]); cadastro ([[bff-cadastro]]); serviços, com ressalva ([[bff-servicos]]); bloqueio ([[bff-bloqueio]]); endereços ([[bff-enderecos]]); telefones ([[bff-telefones]]); fotos ([[bff-fotos]]); relatos ([[bff-relatos]]); documentos de validação ([[bff-documentos-para-validacao]]); permissões e grupos ([[bff-o-que-a-pessoa-pode-ver]]) |
| Porta sem ligação | planos e cupons ([[bff-planos-e-cupons]]). A porta existe, exige sessão, o serviço de planos não entra na ligação quando o backend sobe, e a configuração não tem endereço de planos |
| Só preparado | auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem, e o cliente de e-mail (ligado no arranque, sem ação para o aplicativo) |
| Fora de uso | o canal de e-mail. Há código de porta, vazio, desligado da compilação. O construtor pede dois identificadores soltos, incompatíveis com CompanyData |

A tabela dos 18 microserviços acima permanece a lista confirmada em 20/10. Este bruto não traz as URLs. Onde ele não nomeia um microserviço, a linha fica como está.

"Dados da empresa", no pé só preparado, é o serviço de empresa conhecido no arranque, sem porta. CompanyData é o vínculo que já sobe com o backend e entra no cadastro do profissional. "Assinatura" é o nome do serviço no arranque; o repositório não diz se é aceite de documento ou outro tipo.

O canal de e-mail deste retrato está fora da compilação. O cliente de e-mail está ligado, sem ação exposta. A lacuna com o disparador de [[pendencias]] continua aberta: não está dito se são a mesma entrega. O serviço de e-mail do núcleo ([[core-10-emails]]) é envio e caixa de endereços. Não é esse disparador nem este canal fora de uso. A lacuna continua aberta. Ver [[contradicoes-e-lacunas]].

O arranque prepara a sessão, e a leitura da sessão não entra no caminho do pedido. Portas que declaram sessão podem receber o pedido sem a pessoa preenchida. Várias portas recebem cliente de auditoria e de autenticação e não os chamam. A configuração nomeia um serviço de registro de falhas e o arranque não liga esse cliente. Fica em aberto. Ver [[contradicoes-e-lacunas]].

## O que os apps pedem

Foto do cruzamento de 21/10 entre os dois apps e este backend. O alvo do [[mvp]] permanece. ([[cruzamento-bff-como-ler]], [[cruzamento-bff-conta]], [[cruzamento-bff-o-que-a-tela-le]], [[cruzamento-bff-o-que-ninguem-pede]])

Os dois apps falam com este mesmo backend. Quem pede, hoje, é o próprio app. O que já conversa é a conta.

- Abrir conta: os dois pedem a porta de cliente, POST `User`, em [[bff-cadastro]]. A porta de profissional, POST `Artist`, está no ar e o app do artista não a pede. O vínculo de empresa e aplicativo, que só essa porta recebe, não entra no pedido.
- Entrar, esqueci a senha, senha de quem já entrou e sair pedem [[bff-entrar-sair-e-senha]]. Os dois pedem as três portas de senha que estão no ar. A de recusar a troca está no ar e nenhum app a pede.
- Reabrir: o app pergunta se a sessão vale em `login/user/valid`. Este retrato não publica esse caminho. A porta publicada é GET `Valid`.
- Início: ao abrir, os dois pedem de novo a pessoa logada em `login/user/logged`. Este retrato não publica essa leitura. Entrar devolve a sessão.
- CEP no cadastro e na visita é consulta ao mapa da Google, fora deste backend. O endereço da conta viaja dentro do pedido de abrir conta e não passa por [[bff-enderecos]].

No ar, e nenhum dos dois apps pede: serviços ([[bff-servicos]]), bloqueio ([[bff-bloqueio]]), endereços ([[bff-enderecos]]), telefones ([[bff-telefones]]), fotos ([[bff-fotos]]), relatos ([[bff-relatos]]), documentos de validação ([[bff-documentos-para-validacao]]) e o que a pessoa pode ver ([[bff-o-que-a-pessoa-pode-ver]]). Planos e cupons ([[bff-planos-e-cupons]]) são porta sem ligação, e a aba Planos do artista nem chega a perguntar.

Lista de artistas, agenda, conversa, pedidos e o cartão do próximo atendimento não leem este backend. Continuam exemplo ou casca.

Há ainda um pedido preparado de invalidar todas as sessões, `auth/revoke-all-sessions`. Nenhuma tela o chama, e este retrato não publica esse caminho. Outro pedido preparado troca a senha informando a senha antiga; nenhuma tela o dispara, e este bruto não nomeia o caminho.

Esta página não cobre telas, chave de sessão, identificadores nem endereço dos serviços. Os campos moram em pacotes fora deste repositório.

## O que o board pede em 21/10

O board pede endpoint de login do cliente (350), endpoint de login do artista (351) e cadastro de cliente e de artista. Os títulos 358 e 361 usam o nome WeCareU.API. Isso é pedido do board, não confirmação desta arquitetura. Estado Completed no board não diz que o pedido está nesta porta. A tabela de pé e os 18 microserviços acima não mudam. ([[board-conta-e-acesso]])
