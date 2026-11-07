---
tipo: cruzamento
tema: Como ler o cruzamento com o backend
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza os dois apps com o backend de apoio. Descreve onde a tela lê ou grava um dado, por que a pessoa precisa dele, e se essa porta existe no backend. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — como ler o backend

Esta nota é a porta das outras três. O backend de apoio está em [[01-o-que-e-este-backend]]. Ele não desenha tela. Os apps é que pedem. Os dois apps, o de quem procura e o de quem atende, falam com o mesmo backend.

O kit visual não lê dado de conta. O fluxo compartilhado de entrar, em [[library-components-o-que-entrega]], desenha tela e espera o app ligar o serviço. Esse fluxo não está instalado em nenhum dos dois apps. Quem fala com o backend, hoje, é o próprio app. Ver [[Cruzamento - entrar senha e biometria]].

## O que já conversa

| Momento | Por que | Onde a pessoa está | Porta no backend |
|---------|---------|--------------------|------------------|
| Abrir conta | Criar a pessoa no serviço da WeCareU | [[Criar conta]] e [[Cadastro do artista]] | Abrir conta de cliente, em [[04-cadastro]]. Os dois apps usam essa porta. A porta de profissional existe e o app do artista não a usa. |
| Entrar | Saber quem é e abrir as abas | [[Entrar, senha e biometria]] e [[Entrar, senha e biometria do artista]] | Entrar, em [[03-entrar-sair-e-senha]] |
| Reabrir o app | Não pedir a senha de novo se a sessão ainda vale | Abertura dos dois apps | O app pergunta se a sessão vale num caminho que este retrato do backend não publica. A porta publicada é outra. O detalhe está em [[Cruzamento - BFF conta]]. |
| Esqueci a senha e senha de quem já entrou | Recuperar o acesso | As mesmas notas de entrar, e [[Meu perfil]] e [[Perfil do artista]] | Pedir a troca, validar o código e trocar a senha, em [[03-entrar-sair-e-senha]] |
| Sair | Encerrar a sessão neste aparelho | Menu do perfil dos dois | Sair, em [[03-entrar-sair-e-senha]] |
| Início | Mostrar nome, foto e nota da conta | [[Início]] e [[Início do artista]] | O app pede a pessoa logada de novo. Esse pedido não está nas portas deste retrato. Ver [[Cruzamento - BFF o que a tela lê]]. |
| CEP no cadastro e na visita | Preencher rua e cidade antes de seguir | [[Criar conta]], [[Cadastro do artista]], [[Primeira entrada]] | Não é porta deste backend. É uma consulta ao mapa da Google, fora da WeCareU. O endereço da conta só viaja dentro do cadastro. |

## O que não conversa

O backend já publica serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação e o que a pessoa pode ver. Nenhum dos dois apps pede essas portas. Planos e cupons são porta sem ligação, e a aba Planos do artista nem chega a perguntar. A lista está em [[Cruzamento - BFF o que ninguém pede]].

Lista de artistas, agenda, conversa, pedidos e o cartão do próximo atendimento não leem este backend. O cartão é exemplo fixo. A lista de artistas é exemplo fixo. Ver [[Cruzamento - o que só um app tem]].

## As notas

| Nota | O que cruza |
|------|-------------|
| [[Cruzamento - BFF conta]] | Entrar, sessão, senha e cadastro. Onde o pedido do app e a porta do backend não têm o mesmo formato. |
| [[Cruzamento - BFF o que a tela lê]] | Nome, foto e nota do Início. CEP. Endereço que só vai junto da conta. O que fica no aparelho. |
| [[Cruzamento - BFF o que ninguém pede]] | Porta no ar sem tela, e pedido do app sem porta neste retrato. |
