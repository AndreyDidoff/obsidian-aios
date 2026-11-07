---
tipo: fonte
arquivo: "ingeridos/board-conta-e-acesso.md"
origem: "extração via IA (Cursor) do board Azure DevOps da organização piresbno1992, projeto WeCareU, em 2026-10-21; retrato de trabalho, não decisão de produto; em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Conta e acesso", "Sistema de login", "Sistema de cadastro de usuário"]
---

# Conta e acesso

Porta: [[board-indice]]. Extração em 2026-10-21. Organização `piresbno1992`, projeto WeCareU. Área WeCareU\GLOBAL em todos os itens deste bruto. Retrato de trabalho, não decisão de produto. Em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Estado no board não é pé do produto. New, Active, Blocked ou Completed não significa entregue no app nem no [[mvp]].

Nenhum item deste bruto traz critério de aceite.

## O que este tema pede

O board pede um sistema de login e um sistema de cadastro de usuário. No login: endpoint de cliente, endpoint de artista, logout automático e telas de esqueci a senha, de código, de nova senha, de formulário e de login usando digital. No cadastro: cliente e artista, inclusive tela em forma de chat. Três histórias não têm pai no board.

## Épico 329 — Sistema de login

Estado no board: Active. Responsável: Andrey Didoff do Nascimento ([[Andrey Didoff]]). Descrição ausente.

Comentário de Andrey Didoff do Nascimento em 2025-08-01: o épico está pareado com WECAREU-1, em `https://wecareu.atlassian.net/browse/WECAREU-1`, e traz um marcador getint.io. O comentário não descreve o login.

### História 343 — Integração com Login

Estado no board: Active. Responsável: Bruno Pires de Almeida ([[bruno]]). Sem descrição.

#### Tarefa 350 — **[BE] Implementar Endpoint de login do Cliente**

Estado no board: Completed. Responsável: Bruno Pires de Almeida.

Pede alterar o endpoint existente de login para buscar informações do cliente. Há um anexo. O texto não descreve a imagem. Em seguida pede, nas palavras do board, "de forma abuscar as informações adicionais se necessarias nos passos subsequentes antes do return".

#### Tarefa 351 — **[BE] Implementar Endpoint de login do Artista**

Estado no board: Active. Responsável: Bruno Pires de Almeida.

Pede implementar variação no login pelo app ou front que está requerendo o login, com a diferenciação pelo HttpRequest da aplicação. Há um anexo. O texto não descreve a imagem. Em seguida pede buscar "os dado exclusivos do artista em função de seu usuario e/ou empresa".

#### Tarefa 455 — **[FE] Fazer logout automático**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede criar logout automático se o usuário estiver a x tempo sem acessar o app, ou trocar a senha fora do app, ou os tokens expirarem. O texto não diz qual é o x.

### História 421 — Criar telas de login

Estado no board: Active. Responsável: Andrey Didoff do Nascimento. Sem descrição. O texto não diz de qual app são as telas.

#### Tarefa 422 — **[FE] Tela de Esqueci minha senha**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede uma tela para preencher o e-mail de login, com botão "Enviar e-mail" e botão "Cancelar" para voltar ao login. Há um anexo. O texto não descreve a imagem. O botão voltar envia para a tela anterior, para cancelar o login ou o cadastro se a pessoa clicou no lugar errado.

#### Tarefa 423 — **[FE] Tela de código do esqueci minha senha**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede uma tela para preencher o código enviado ao e-mail. Erro se o código for inválido. Contador de 5 minutos. Ao acabar o timer, erro de tempo expirado, botão de enviar novamente e botão "Cancelar" para voltar ao login. Há um anexo. O texto não descreve a imagem. O botão voltar envia para a tela anterior.

Comentário de 2025-03-24: a tarefa estava bloqueada, aguardando login e senha funcionarem no back-end. Comentário de 2025-04-02 registra o fechamento do Pull Request 149. O estado neste retrato é Completed.

#### Tarefa 424 — **[FE] Tela de criação de nova senha**

Estado no board: Blocked. Responsável: Andrey Didoff do Nascimento.

Pede uma tela para preencher a nova senha e repeti-la. A senha deve seguir as regras descritas na imagem, e as regras devem mudar o ícone conforme forem validadas. Há um anexo. O texto não transcreve as regras e não descreve a imagem. O botão voltar envia para a tela anterior.

Comentário de 2025-08-03: a tarefa está bloqueada e depende da tela de configurações do usuário.

#### Tarefa 425 — **[FE] Tela com formulário de login**

Estado no board: Completed. Responsável: nenhum.

Pede uma tela para preencher os dados de login, esqueci minha senha, ou se cadastrar na plataforma. Há um anexo. O texto não descreve a imagem e não lista os campos. O botão voltar envia para a tela anterior.

#### Tarefa 462 — **[FE] Colocar opção de login usando digital**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

#### Tarefa 466 — **[FE] Remove console log and comments**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

## Épico 337 — Sistema de cadastro de usuário

Estado no board: Active. Responsável: Andrey Didoff do Nascimento. Sem descrição.

### História 357 — Cadastro de Cliente

Estado no board: Active. Responsável: Andrey Didoff do Nascimento. Sem descrição.

#### Tarefa 358 — **[BE] Cadastro do cliente no WeCareU.API**

Estado no board: Completed. Responsável: bruno.pires@wecareu.app.

O título cita WeCareU.API. Isso é o nome que o board usa. Não confirma a arquitetura.

Pede criar endpoint com modelo que contemple os dados do usuário CPF, com foto e ou foto padrão, para não deixar a informação vazia. A foto padrão entra no AppSetting, no objeto JSON `Pattern`, campo `Photo` com valor `GUID`. Qualquer outra informação padrão fica nesse objeto e se carrega por injeção de dependência. O texto diz que este "endpoin" se comunica sem autenticação padrão e que as chaves de sistema e de empresa são validadas na chamada, com um token combinado dos dois, usando hash. A validação "da frente disso" pode ser feita pelo token de login. O hash fica no "widowns secrets" e é gerado unicamente para produção.

#### Tarefa 411 — **[FE] Criação de Tela de cadastro cliente em forma de chat**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede a tela de cadastro conforme o Figma e as modais. Há um anexo. O texto não descreve a imagem. O que o texto escreve:

- Logo We Care U no canto superior esquerdo. Botão de fechar no canto superior direito, que cancela o cadastro.
- Mensagens automáticas à esquerda, com ícone de bot e balão. Respostas do cliente à direita. Sem foto, ícone de usuário. Com foto, a foto.
- Escolhas como "Sim" ou "Não". Respostas com conteúdo oculto, escondido por padrão, com botão de olho à direita. Olho com risco indica oculto e o clique mostra. Olho aberto indica visível e o clique oculta. Há respostas comuns sem ocultação.
- CPF já cadastrado impede continuar. E-mail já cadastrado impede continuar.
- Modais: upload de imagem de perfil, aviso de CPF já cadastrado, aviso de e-mail já cadastrado.
- Campos de texto aparecem conforme a sequência de perguntas. Campo de CPF: válido e não cadastrado. Campo de e-mail: validador de e-mail e não cadastrado. Campo de senha: regras descritas no Figma. O texto não transcreve essas regras.
- O botão final leva à listagem, se o cadastro veio da listagem; ao agendamento, se a pessoa começou um agendamento; ao perfil, se o cadastro começou pela tela inicial do app.

O Figma citado: `https://www.figma.com/file/MSEibBfdtigMN0qxOJcrL5/WeCareU-App?type=design&node-id=143%3A5913&mode=design&t=0GvMOUdIwHey6El7-1`.

Comentário de 2023-08-30: a tarefa aguardava a tarefa 440, porque faltava uma tela para chegar até esta. Comentário de 2025-01-24: continua após ajustes da 440. Comentário de 2025-03-11: fechamento do Pull Request 140. O estado neste retrato é Completed.

#### Tarefa 412 — **[DS] Aviso de CPF Inválido**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

O texto diz: em vez de uma modal de CPF inválido, a mensagem de inválido fica no campo de escrita, e o mesmo vale para CPF, CNPJ e e-mail.

#### Tarefa 413 — **[DS] Aviso de E-mail inválido**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

O texto diz que a tarefa será concluída automaticamente com a tarefa 412.

#### Tarefa 414 — **[DS] Inclusão de botão de finalização de cadastro**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

O comentário de 2023-08-29 é só um anexo. O texto não descreve a imagem.

#### Tarefa 440 — **[FE] Criar tela de login ou cadastro do App**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição.

#### Tarefa 450 — **[DS-FE] Criação de tela incentivando o cadastro para o menu**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede uma tela de chamada para cadastro quando o usuário está deslogado e clica para acessar as telas home, favoritos, agendamentos e perfil. Há um anexo. O texto não descreve a imagem.

#### Tarefa 467 — **[FE] Ajustar código do registro conforme regras novas**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. O texto não diz quais são as regras novas.

### História 360 — Cadastro de Artista

Estado no board: Blocked. Responsável: Andrey Didoff do Nascimento. Descrição ausente.

Comentário de 2025-01-24: "Aguardando termino do app de cliente".

#### Tarefa 361 — **[BE] Cadastro do Artista no WeCareU.API**

Estado no board: New. Responsável: bruno.pires@wecareu.app.

O título cita WeCareU.API. Isso é o nome que o board usa. Não confirma a arquitetura.

O texto diz que a criação do artista pode ser feita em duas tabelas. Não nomeia as tabelas. Se for uma empresa, cadastram o CNPJ e o grupo e vinculam o usuário pelo CPF do criador, como usuário principal, que poderá fazer os cadastros. O vínculo de usuário e empresa é dado pelas permissões. Pede repensar, em um segundo momento, como usar a parte de empresa para o resto do pacote de informações. A partir do cadastro do usuário do artista, segue o fluxo comum. O texto não define esse fluxo. Ao menos 1 artista é obrigatório no cadastro do CNPJ.

#### Tarefa 415 — **[DS] Criação de modal de CNPJ inválido**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

O texto diz que a tarefa será concluída automaticamente com a tarefa 412.

#### Tarefa 416 — **[FE] Criação de Tela de cadastro artista em forma de chat**

Estado no board: New. Responsável: Andrey Didoff do Nascimento.

Pede a tela de cadastro conforme o Figma e as modais. Há um anexo. O texto não descreve a imagem. O link do Figma é o mesmo da tarefa 411. A estrutura escrita repete a da 411, com o que o texto muda:

- As respostas são do artista.
- CPF, CNPJ ou e-mail já cadastrado impedem continuar.
- Modais: upload de imagem de perfil, aviso de CPF já cadastrado, aviso de CNPJ já cadastrado, aviso de e-mail já cadastrado.
- Há campo de CNPJ, válido e não cadastrado, além do CPF e do e-mail.
- A senha segue as regras descritas no Figma. O texto não as transcreve.
- O botão final leva ao perfil, para continuar o cadastro das informações enquanto o cadastro é aprovado.

## Itens sem pai no board

### História 223 — **Tela de Cadastro do Artistas**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem pai no board.

#### Tarefa 224 — **[DS] Criar tela de cadastro do Artista no figma**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem pai no board.

### História 225 — Criar modais necessárias no cadastro de cliente e artista

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem pai no board.

#### Tarefa 226 — **[DS] Criação de modais do cadastro para cliente**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem pai no board.

#### Tarefa 227 — **[DS] Criação de modais do cadastro para artista**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento. Sem descrição. Sem pai no board.

### História 246 — **[FE] Fluxo de Login**

Estado no board: Completed. Responsável: Pedro Rosa. Sem descrição. Sem pai no board.

#### Tarefa 247 — **[FE] Tela de seleção de login ou cadastro**

Estado no board: Completed. Responsável: Pedro Rosa. Sem pai no board.

Pede uma tela para a pessoa selecionar se quer se cadastrar ou fazer login. Há um anexo. O texto não descreve a imagem. O botão voltar envia para a tela anterior.

## O que isto não decide

Não decide 2FA. A tarefa 462 pede login usando digital e não tem descrição. Isso não é o 2FA do [[mvp]]. O alvo permanece em [[decisoes-2026-10-21]]. O item 15 de [[contradicoes-e-lacunas]] segue resolvido para o alvo.

Não decide que o app usa POST Artist. Pedir login de artista (351) e cadastro de artista (360, 361, 416) não apaga o retrato em que os dois apps abrem conta por POST User. Ver [[bff-cadastro]]. O item 28 segue aberto no código.

Não decide que o chat do board substitui as duas etapas. As tarefas 411 e 416 pedem tela em forma de chat. O alvo continua duas etapas, cada uma um fluxo do chatbot. Ver [[cadastro]] e [[decisoes-2026-10-20]]. O item 25 segue encaminhado.

Não decide o momento do cadastro no cliente. A tarefa 411 prevê fim de cadastro vindo da listagem, do agendamento ou da tela inicial do app. A tarefa 450 pede chamada de cadastro em home, favoritos, agendamentos e perfil. O alvo permanece: no cliente, cadastro na hora de agendar, não na porta. Ver [[decisoes-2026-10-21]].

Não decide que a tela pedida está no app de 21/10. Estado Completed no board não é a tela do retrato. Telas de login pedidas aqui não instalam `@wecareu/auth-flow`. Ver [[fluxo-de-entrada]] e [[bff-entrar-sair-e-senha]]. O item 24 segue aberto como retrato.
