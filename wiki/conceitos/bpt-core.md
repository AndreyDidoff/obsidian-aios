---
tipo: conceito
criado: 2026-10-22
atualizado: 2026-10-22
fontes: ["[[core-00-o-que-e-este-nucleo]]", "[[core-01-conta]]", "[[core-19-o-que-nao-saiu-do-papel]]", "[[core-07-bloqueio]]", "[[core-08-enderecos]]", "[[core-09-telefones]]", "[[core-02-servicos]]", "[[core-03-agenda]]", "[[core-04-empresa-e-colaboradores]]", "[[core-05-a-organizacao]]", "[[core-06-planos-cupons-e-cobranca]]", "[[core-10-emails]]", "[[core-17-idiomas]]", "[[core-11-fotos]]", "[[core-12-relatos]]", "[[core-13-documentos-para-validacao]]", "[[core-14-assinatura]]", "[[core-15-modelos-de-mensagem]]", "[[core-16-permissoes-grupos-e-telas]]", "[[core-18-rastro-e-falhas]]"]
---

# Núcleo BPT-Core

O aplicativo fala com `api.wecareu.app`. Esse endereço é o BFF, [[beautiful-api]]. A regra de negócio mora aqui, nos projetos `Br.*.API`, nos hosts `*.bptsoftware.com.br` e nos bancos lidos em 21/10. Esta página reúne as ondas 1, 2, 3, 4 e 5 desse retrato. Não é o aplicativo e não é o BFF. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. ([[core-00-o-que-e-este-nucleo]])

Onze bancos SQL e quatro Mongo, no host `server.wecareu.app`. O mapa está em [[banco-indice]]. Não há chave estrangeira. Os pares pelo nome da coluna estão em [[banco-sql-relacoes]] e [[banco-mongo-relacoes]]. Ligação pelo nome da coluna não é constraint. ([[core-00-o-que-e-este-nucleo]])

`Br.PaymentPlan.API` não tem host na lista dos 18 nem neste repositório. Cobrança tem host e não tem ação, e não tem tabela nos onze bancos. Ticket não tem API, host nem tabela. ([[core-00-o-que-e-este-nucleo]], [[core-19-o-que-nao-saiu-do-papel]], [[core-06-planos-cupons-e-cobranca]])

Em vários projetos, o código que sobe no Windows e no Linux força um catálogo diferente do compose. O wikilink do banco continua o do servidor, em [[banco-indice]]. ([[core-00-o-que-e-este-nucleo]])

## Pé desta porta

O miolo de cada tema fica na nota correspondente. Nesta porta, o recorte é este. ([[core-00-o-que-e-este-nucleo]])

| Pé | O que esta porta recorta |
|---|---|
| Feito com ressalva | conta ([[core-01-conta]]), bloqueio ([[core-07-bloqueio]]), endereço ([[core-08-enderecos]]), telefone ([[core-09-telefones]]), foto ([[core-11-fotos]]), catálogo de serviços ([[core-02-servicos]]) |
| Pela metade | agenda ([[core-03-agenda]]), empresa do profissional ([[core-04-empresa-e-colaboradores]]), organização ([[core-05-a-organizacao]]), planos ([[core-06-planos-cupons-e-cobranca]]), e-mail ([[core-10-emails]]), idiomas ([[core-17-idiomas]]), relato ([[core-12-relatos]]), documento ([[core-13-documentos-para-validacao]]), permissão ([[core-16-permissoes-grupos-e-telas]]), modelo ([[core-15-modelos-de-mensagem]]) |
| Casca | cobrança ([[core-06-planos-cupons-e-cobranca]]), assinatura ([[core-14-assinatura]]), ticket ([[core-19-o-que-nao-saiu-do-papel]]), consola Vue ([[core-19-o-que-nao-saiu-do-papel]]) |
| Operação interna | rastro e falha ([[core-18-rastro-e-falhas]]) |

A conta está em [[core-01-conta]]. Bloqueio está em [[core-07-bloqueio]]. Endereço está em [[core-08-enderecos]]. Telefone está em [[core-09-telefones]]. Serviços estão em [[core-02-servicos]]. Agenda está em [[core-03-agenda]], no mesmo projeto, host e banco de serviços. Empresa do profissional está em [[core-04-empresa-e-colaboradores]], nesse mesmo projeto; `Company` e a organização são linhas e bancos diferentes. Organização está em [[core-05-a-organizacao]]. Planos, cupons e cobrança estão em [[core-06-planos-cupons-e-cobranca]]. E-mail está em [[core-10-emails]]. Idiomas estão em [[core-17-idiomas]]. Fotos estão em [[core-11-fotos]]. Relatos estão em [[core-12-relatos]]. Documentos estão em [[core-13-documentos-para-validacao]]: `Br.Validation.API`, coleção `Documents` vazia; não é o documento do cadastro do artista, não aprova e não recusa, e a pergunta ao login não recusa. Assinatura está em [[core-14-assinatura]]: coleção vazia, o cadastro recebe o serviço e não o chama, `Usuario.FkSignature` segue sem destino único, e no BFF segue só preparada. Modelos estão em [[core-15-modelos-de-mensagem]]: a lista ignora o tipo do endereço; listar e desligar recusam quando o login não aceita, e esta checagem não está invertida; no BFF seguem só preparados. Permissões estão em [[core-16-permissoes-grupos-e-telas]]: seis tabelas, `Screens` não é tela de aplicativo, a checagem não recusa ninguém, e o BFF continua [[bff-o-que-a-pessoa-pode-ver]]. Rastro e falhas estão em [[core-18-rastro-e-falhas]]: operação interna, checagem invertida no rastro, e o canal de falha não fecha o destino do host publicado. O que não saiu do papel está em [[core-19-o-que-nao-saiu-do-papel]]. A porta é [[core-00-o-que-e-este-nucleo]]. Nenhuma nota do núcleo segue sem página.

Nesta onda há duas checagens, ao lado da das fotos, já escrita. Documentos, assinatura e permissões perguntam ao login e não recusam: sim ou não deixam seguir. O rastro inverte: o login aceita e a ação é recusada. Nos modelos, listar e desligar recusam quando o login não aceita. A lacuna de que o BFF prepara a sessão e não a lê no pedido continua. Ver [[contradicoes-e-lacunas]].

Cliente e profissional nascem os dois em `Usuario`. O profissional abre uma empresa e fica ligado a ela. O que o serviço grava no cadastro está em [[cadastro]]. Sessão de 48 horas e 7 dias para renovar, e o código de senha, estão em [[fluxo-de-entrada]]. As cinco estrelas e nenhuma avaliação, ao nascer a conta, estão em [[avaliacoes]]. ([[core-01-conta]])

`Br.Ticket.Nuget` é classe vazia, sem API, sem host e sem tabela. A consola Vue em `Br.Login.API/Br.Login.Front` é casca. O `package.json` diz `client-app` e isso não a torna o aplicativo. Não é o app do cliente, nem o do artista, nem microserviço do BFF. ([[core-19-o-que-nao-saiu-do-papel]])

Ver [[contradicoes-e-lacunas]].
