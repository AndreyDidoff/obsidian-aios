---
tipo: fonte
arquivo: "ingeridos/03-entrar-sair-e-senha.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Entrar, sair e senha"]
---

# Entrar, sair e senha

O que este backend publica para entrar, sair, saber se a sessão ainda vale e cuidar da senha. Caminho `beautiful/api/Login`. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela.

## O que está publicado

O serviço de login está ligado. Sete pedidos:

- **Entrar.** POST, sem sessão prévia.
- **Sair.** GET `logout`. Marcado como exigindo pessoa logada.
- **Saber se a sessão ainda vale.** GET `Valid`. Marcado como exigindo pessoa logada.
- **Pedir troca de senha a partir do e-mail.** GET `Password/Create/{Email}`, sem sessão. Este backend não envia o e-mail. O envio não é uma ação daqui. Ver [[bff-preparado-e-ainda-nao-oferecido]].
- **Recusar a troca.** GET `Password/refuse/{Token}`, sem sessão.
- **Trocar a senha.** POST `Password/Change`, sem sessão.
- **Validar e-mail e token do pedido.** GET `Password/valid/{Email}/{Token}`, sem sessão.

## Quem pode

Entrar, pedir a troca, recusar a troca, trocar a senha e validar e-mail com token: publicados sem sessão já aberta.

Sair e conferir a sessão estão marcados como exigindo pessoa logada. Essa marca pode não ser aplicada, porque o arranque prepara a sessão e a leitura dela não entra no caminho do pedido. Ver [[bff-o-que-e-este-backend]] e [[contradicoes-e-lacunas]].

Estes pedidos não separam cliente e profissional (Artista). O que diferencia os dois papéis está em [[bff-cliente-e-profissional]].

## Em que pé está

No ar. O serviço de login está ligado, e os sete pedidos estão publicados.

## O que esta nota não cobre

A tela de entrar, sair ou trocar senha. O texto do e-mail e o ato de enviá-lo. Abrir conta: [[bff-cadastro]]. O que a pessoa passa a ver depois de entrar está em [[bff-o-que-a-pessoa-pode-ver]].

Esta nota não menciona 2FA e não publica porta de 2FA. O alvo do [[mvp]] continua precisando de 2FA nos apps. ([[decisoes-2026-10-21]]) O item 15 de [[contradicoes-e-lacunas]] permanece resolvido no alvo.

## Incertezas

O formato da senha não está neste repositório. Entrar e trocar a senha seguem para um pacote de login; os campos desse pacote não estão aqui.

A expiração do token do pedido de troca não está neste repositório.

O texto do e-mail de troca de senha não está neste repositório. O envio do e-mail não é uma ação deste backend.

Ver [[beautiful-api]], [[fluxo-de-entrada]].

O board pede alterar o endpoint existente de login do cliente para buscar informações do cliente (tarefa 350, estado Completed no board) e uma variação de login do artista pela aplicação que pede, via HttpRequest (tarefa 351, estado Active), buscando dados exclusivos do artista. Também pede logout automático (455). Completed no board não diz que a alteração está nesta porta. Esta porta publica um entrar só e não separa cliente de profissional. O pedido do board não muda esse retrato. ([[board-conta-e-acesso]])

O board pede 401 quando o login falha (tarefa 465, estado Completed). A descrição no board diz que o endpoint `https://api.wecareu.app/beautiful/api/Login`, quando o login falha, dá um erro 500, e o esperado é 401. Este retrato do backend não diz o código de resposta. Completed no board não diz que o conserto está neste código. ([[board-bugs]])
