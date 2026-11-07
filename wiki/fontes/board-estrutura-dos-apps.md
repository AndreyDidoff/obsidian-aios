---
tipo: fonte
arquivo: "ingeridos/board-estrutura-dos-apps.md"
origem: "extração via IA (Cursor) do board Azure DevOps da organização piresbno1992, projeto WeCareU, em 2026-10-21; retrato de trabalho, não decisão de produto; em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Estrutura dos apps", "Estrutura dos Apps"]
---

# Estrutura dos apps

Porta: [[board-indice]]. Extração em 2026-10-21. Organização `piresbno1992`, projeto WeCareU. Área WeCareU\GLOBAL em todos os itens deste bruto. Retrato de trabalho, não decisão de produto. Em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Estado no board não é pé do produto. New, Active, Blocked ou Completed não significa entregue no app nem no [[mvp]]. Removed é estado do work item.

## O que este tema pede

O board pede a estrutura dos dois apps. O épico 417, Estrutura dos Apps, está Active. Debaixo dele cabem o início dos dois apps, as telas de start app, a reestruturação do client, dados de logo e nome, uma wiki interna, biblioteca de componentes, a reestruturação do worker, ajustes finos no client e biblioteca de design system. O épico 441, Create App using Expo, está Completed e pede os dois apps com Expo. Fora dos dois épicos ficam histórias sem pai: consulta de exemplo ao back-end, troca de nome Beautiful, estrutura em flutter, telas de start app do client, localização dos apps, stories da sprint e um teste. Flutter aparece só nesse bloco sem pai.

## Épico 417 — Estrutura dos Apps

Estado no board: Active. Responsável: Andrey Didoff do Nascimento ([[Andrey Didoff]]). Sem descrição.

### Início dos dois apps

- História 418, Criar a tela de Início do App. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 419, [FE] Criar tela de Início no App client. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 420, [FE] Criar tela de Início no App worker. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

### Start app

- História 426, Criar telas de Start App. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição diz: criar as telas de Start App.
- Tarefa 429, [FE] Criar tela de seleção de Tipo de atendimento. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição pede a tela de seleção de atendimento para quem ainda não está logado. Há anexo. O comentário diz que a tarefa era legada do Pedro e se resolveu sozinha na tarefa 431.
- Tarefa 430, [FE] Criar tela de seleção de Localidade. Estado: Removed. Responsável: Andrey Didoff do Nascimento. A descrição pede a tela de seleção de localidade do cliente para apresentar os prestadores mais próximos. Há anexo.

### Reestruturação

- História 427, Reestruturação do App Cliente. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição diz: promover a reestruturação do App Client.
- Tarefa 431, [FE] Reestruturar o App Client para no novo padrão de código. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- História 476, Reestruturação do App Worker. Estado: New. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 477, [FE] Reestruturar o App Worker para no novo padrão de código. Estado: Blocked. Responsável: Andrey Didoff do Nascimento. Sem descrição.

### Logos e nomes

- História 428, Configurar dados dos Apps. Estado: New. Responsável: Andrey Didoff do Nascimento. A descrição pede adicionar Nome do App, Icone do App e False screen loading.
- Tarefa 432, [FE] Implementar logo do App no App Client. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 433, [FE] Implementar logo do App no App Worker. Estado: New. Sem responsável. Sem descrição.
- Tarefa 434, [DS] Criar logos dos Apps. Estado: Removed. Sem responsável. Sem descrição.
- Tarefa 435, [FE] Colocar o nome do App no ui_client. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 436, [FE] Colocar o nome do App no ui_worker. Estado: New. Sem responsável. Sem descrição.
- Tarefa 437, [FE] Colocar o false screen do App do client. Estado: Removed. Sem responsável. Sem descrição.
- Tarefa 438, [FE] Colocar o false screen do App do worker. Estado: Removed. Sem responsável. Sem descrição.
- Tarefa 439, [DS] Criar false screen apra os Apps. Estado: Removed. Sem responsável. Sem descrição.

### Wiki interna

- História 456, Criar Wiki interna. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 457, [DV] Criar repositórios e subir primeiro commit. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição diz: criar wiki para uso interno da empresa.
- Tarefa 458, [FE] Definir wiki como produção. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição diz: definir wiki como produção.
- Tarefa 459, [FE] Subir itens faltantes. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

Pedido do board. Não é esta base.

### Bibliotecas

- História 460, Biblioteca de componentes. Estado: New. Responsável: Andrey Didoff do Nascimento. A descrição pede uma biblioteca de componentes para facilitar a manutenção do código.
- Tarefa 461, Desenvolver biblioteca inicial. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição diz: criar um biblioteca inicial.
- Tarefa 490, [FE] Integrar bibliotecas no app client. Estado: Removed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 495, [FE] Instalação do pipeline e rpmrc. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição pede migrar pacotes npm de um Design System React Native, hoje publicados publicamente no npmjs.com no escopo `@wecareu/*`, para um feed privado no Azure Artifacts, mantendo a instalação e trocando a origem do registro. Cita `@wecareu/button-gradient` e `@wecareu/input-text`. A instalação citada é via yarn.
- História 488, Biblioteca de Design System. Estado: New. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 489, [FE] Desenvolver biblioteca inicial. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 493, [FE] Instalação do pipeline e rpmrc. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição repete a da tarefa 495.
- Tarefa 494, [FE] Migrar pacotes npms para o Azure Artifacts. Estado: Completed. Responsável: Andrey Didoff do Nascimento. A descrição repete a da tarefa 495.

### Ajustes finos no cliente

- História 478, Ajustes Finos no App do Cliente. Estado: New. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 479, [FE] Ajuste na tabbar. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 480, [FE] Ajustar camelCase do projeto. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 497, [FE] Adicionar consumo de azure artefatos. Estado: New. Responsável: Andrey Didoff do Nascimento. Sem descrição.

## Épico 441 — Create App using Expo

Estado no board: Completed. Sem responsável. Sem descrição.

- História 442, Create App ui_client using Expo. Estado: Completed. Sem responsável. Sem descrição.
- Tarefa 444, Create new structure. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- História 443, Create App ui_worker using Expo. Estado: Completed. Sem responsável. Sem descrição.
- Tarefa 445, Create new structure. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

Pedido de fila. Expo neste épico não resolve o monorepo. Não é a stack do [[mvp]] por causa do estado Completed.

## Sem pai no board

- História 189, [FE] Colocar exemplo de consulta axios para o back-end. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem tarefas. O comentário cita o par WECAREU-10.
- História 213, [FE] Trocar nome Beautiful para WeCareU em toda plataforma. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem tarefas.
- História 214, Criar estrutura app cliente em flutter. Estado: Completed. Responsável: Pedro Rosa. Sem descrição. Sem pai no board.
- Tarefa 222, [FE] Criar estrutura app cliente em flutter. Estado: Completed. Responsável: Pedro Rosa. Sem descrição. Sem pai no board.
- História 217, Criar telas start app Client. Estado: Completed. Responsável: Pedro Rosa. A descrição pede duas telas em flutter, com a logo da empresa e um link para a futura tela de login. A primeira traz o texto "Escolha seu Atendimento" e as opções "Para: Vir até você" e "Para: Ir até o local". As duas opções levam à tela seguinte. A segunda pede a escolha do endereço, o do atendimento ou o de onde a pessoa está, para achar o local mais próximo. Há anexo. Cita um arquivo no Figma.
- Tarefa 221, [FE] Criar telas start app Client. Estado: Completed. Responsável: Pedro Rosa. A descrição repete a da história 217. Há anexo. Cita um arquivo no Figma.
- História 321, [FE] Localização dos apps. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 322, [FE] Localização do app ui_client. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 323, [FE] localização do app ui_worker. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- História 408, Criar todas as stories da próxima sprint. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 409, Criar stories de front-end. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 410, Criar stories de design. Estado: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- História 491, Testes. Estado: New. Responsável: Andrey Didoff do Nascimento. Sem descrição.
- Tarefa 492, [FE] Teste de criação de Task [CLIENT]. Estado: Active. Responsável: Andrey Didoff do Nascimento. A descrição pede um botão na tela welcome, abaixo de já tenho uma conta, com o texto "teste n8n", que ao clicar alerta a frase "Teste de n8n".

Flutter fica neste bloco. A história 214 e a tarefa 222 são item do board. Não são a stack do [[mvp]].

## O que isto não decide

Não é a stack do [[mvp]]. Expo no épico 441 e Flutter na história 214 são fila de trabalho. O retrato de 21/10 dos repositórios permanece. Ver [[engenharia-de-software]] e [[ecossistema-de-produtos]].

Não é esta base. A história 456 e a tarefa 457 pedem wiki para uso interno da empresa. A tarefa 458, definir wiki como produção, está Completed. Isso não confirma lançamento. O item 12 de [[contradicoes-e-lacunas]] segue aberto, com prevalência.

Não preenche cascas dos apps. Início, logo, nome e reestruturação pedidos aqui não apagam agenda, conversa, pedidos nem planos do retrato de 21/10. O POST User permanece. Ver [[app-do-cliente]] e [[app-do-artista]].

Não resolve o monorepo. O item 18 segue aberto. Expo no board não o fecha.

Não renomeia o BFF. A história 213 pede trocar Beautiful por WeCareU em toda plataforma. O retrato continua `service_api` / Beautiful. Ver [[beautiful-api]].

Não instala `@wecareu/auth-flow`. Biblioteca de componentes e biblioteca de design system são pedido do board. O cliente continua instalando as doze. O artista continua sem instalar o kit. O item 24 segue aberto como retrato. Ver [[kit-visual]] e [[lyraui]].
