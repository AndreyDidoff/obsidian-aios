> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Entrar, sair e senha

## O que isso é para o app

Isto é o que o aplicativo pede ao backend de apoio para a pessoa entrar, sair, saber se a sessão ainda vale e cuidar da senha. A tela fica no aplicativo. Aqui está o caminho `beautiful/api/Login`.

## O que a pessoa já consegue fazer por este backend

- **Entrar.** POST, sem sessão prévia.
- **Sair.** GET `logout`. Marcado como exigindo pessoa logada.
- **Saber se a sessão ainda vale.** GET `Valid`. Marcado como exigindo pessoa logada.
- **Pedir troca de senha a partir do e-mail.** GET `Password/Create/{Email}`, sem sessão.
- **Recusar a troca.** GET `Password/refuse/{Token}`, sem sessão.
- **Trocar a senha.** POST `Password/Change`, sem sessão.
- **Validar e-mail e token do pedido.** GET `Password/valid/{Email}/{Token}`, sem sessão.

Pedir a troca a partir do e-mail não faz este backend enviar o e-mail. O envio em si não é uma ação daqui. Ver [[14-preparado-e-ainda-nao-oferecido]].

## Quem pode

Entrar, pedir a troca, recusar a troca, trocar a senha e validar e-mail com token: o aplicativo pede sem sessão já aberta.

Sair e conferir a sessão estão marcados como exigindo pessoa logada. Se essa marca é aplicada na entrada fica em aberto, porque o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Ver [[01-o-que-e-este-backend]].

Estes pedidos não separam, neste backend, cliente e profissional (Artista). O que diferencia os dois papéis está em [[02-cliente-e-profissional]].

## Em que pé está

**No ar.** O serviço de login está ligado neste backend, e os sete pedidos acima estão publicados para o aplicativo.

Escala desta base: No ar / Porta sem ligação / Só preparado / Fora de uso.

## O que esta nota não cobre

- A tela de entrar, sair ou trocar senha.
- O texto do e-mail e o ato de enviá-lo.
- Abrir conta. Ver [[04-cadastro]].
- O que a pessoa passa a ver depois de entrar. Ver [[13-o-que-a-pessoa-pode-ver]].

## Ligações

- [[01-o-que-e-este-backend]]
- [[02-cliente-e-profissional]]
- [[04-cadastro]]
- [[13-o-que-a-pessoa-pode-ver]]
- [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

- O formato da senha não está neste repositório. O pedido de entrar e o pedido de trocar a senha seguem para um pacote de login; os campos desse pacote não estão aqui.
- A expiração do token do pedido de troca não está neste repositório.
- O texto do e-mail de troca de senha não está neste repositório. O envio do e-mail não é uma ação deste backend.
