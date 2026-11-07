---
tipo: fonte
arquivo: "ingeridos/Cruzamento - BFF como ler.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 que cruza ui_client, ui_worker e service_api; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cruzamento — como ler o backend"]
---

# Cruzamento — como ler o backend

Porta das outras três. O backend de apoio está em [[bff-o-que-e-este-backend]]. Ele não desenha tela. Os apps é que pedem. O app de quem procura e o de quem atende falam com o mesmo backend.

O [[kit-visual]] não lê dado de conta. O fluxo compartilhado de entrar, em [[library-components-o-que-entrega]], desenha tela e espera o app ligar o serviço. Esse fluxo não está instalado em nenhum dos dois apps. Quem fala com o backend, hoje, é o próprio app. Ver [[cruzamento-entrar-senha-e-biometria]].

## O que já conversa

| Momento | Onde a pessoa está | Porta |
|---|---|---|
| Abrir conta | [[criar-conta]] e [[cadastro-do-artista]] | Abrir conta de cliente, em [[bff-cadastro]]. Os dois apps usam essa porta. A porta de profissional existe e o app do artista não a usa |
| Entrar | [[entrar-senha-e-biometria]] e [[entrar-senha-e-biometria-do-artista]] | Entrar, em [[bff-entrar-sair-e-senha]] |
| Reabrir o app | Abertura dos dois apps | O app pergunta se a sessão vale num caminho que este retrato do backend não publica. A porta publicada é outra. O detalhe está em [[cruzamento-bff-conta]] |
| Esqueci a senha e senha de quem já entrou | As mesmas notas de entrar, e [[meu-perfil]] e [[perfil-do-artista]] | Pedir a troca, validar o código e trocar a senha, em [[bff-entrar-sair-e-senha]] |
| Sair | Menu do perfil dos dois | Sair, em [[bff-entrar-sair-e-senha]] |
| Início | [[inicio]] e [[inicio-do-artista]] | O app pede a pessoa logada de novo. Esse pedido não está nas portas deste retrato. Ver [[cruzamento-bff-o-que-a-tela-le]] |
| CEP no cadastro e na visita | [[criar-conta]], [[cadastro-do-artista]], [[primeira-entrada]] | Não é porta deste backend. É uma consulta ao mapa da Google, fora da WeCareU. O endereço da conta só viaja dentro do cadastro |

## O que não conversa

O backend já publica serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação e o que a pessoa pode ver. Nenhum dos dois apps pede essas portas. Planos e cupons são porta sem ligação, e a aba Planos do artista nem chega a perguntar. A lista está em [[cruzamento-bff-o-que-ninguem-pede]].

Lista de artistas, agenda, conversa, pedidos e o cartão do próximo atendimento não leem este backend. O cartão é exemplo fixo. A lista de artistas é exemplo fixo. Ver [[cruzamento-o-que-so-um-app-tem]].

## As outras notas

| Nota | O que cruza |
|---|---|
| [[cruzamento-bff-conta]] | Entrar, sessão, senha e cadastro. Onde o pedido do app e a porta do backend não têm o mesmo formato |
| [[cruzamento-bff-o-que-a-tela-le]] | Nome, foto e nota do Início. CEP. Endereço que só vai junto da conta. O que fica no aparelho |
| [[cruzamento-bff-o-que-ninguem-pede]] | Porta no ar sem tela, e pedido do app sem porta neste retrato |

Ver [[beautiful-api]], [[fluxo-de-entrada]], [[cadastro]], [[app-do-cliente]], [[app-do-artista]], [[contradicoes-e-lacunas]].
