> Aviso de versionamento (extração via IA — Azure DevOps): Este documento é um retrato dos épicos, histórias e tarefas do board WeCareU no momento da extração. Conserva o título original de cada item, inclusive os que só têm nome. Não é decisão de produto e não preenche o que o board deixou vazio. Pode estar à frente ou atrás da base de conhecimento. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Conta e acesso

Extração em 2026-10-21. Organização piresbno1992, projeto WeCareU.

## Épico 329 — Sistema de login

**Tipo:** Epic
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/329
**Tags:** nenhuma

**Descrição:** ausente

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-01T18:19:01.060Z

```
Paired with WECAREU-1 - https://wecareu.atlassian.net/browse/WECAREU-1

 [###getint.io:1|t4df7c9de]
```

### História 343 — Integração com Login

**Tipo:** User Story
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Bruno Pires de Almeida
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/343
**Tags:** nenhuma

**sem descrição**

#### Tarefa 350 — [BE] Implementar Endpoint de login do Cliente 

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Bruno Pires de Almeida
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/350
**Tags:** nenhuma

**Descrição:**

Alterar endpoint existente de login para buscar informações do cliente 

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/2db99143-5b8b-40e7-9602-9f484e06fa6a?fileName=image.png)

de forma abuscar as informações adicionais se necessarias nos passos subsequentes antes do return 

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 351 — [BE] Implementar Endpoint de login do Artista

**Tipo:** Task
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Bruno Pires de Almeida
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/351
**Tags:** nenhuma

**Descrição:**

Implementar variação no login por intermedio do app ou front que está requerindo o login ( pegar diferenciação pelo HttpRequest da aplicação ) 

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/07114a5f-6876-4dac-b569-54aa9c926dd5?fileName=image.png)

dessa forma buscar os dado exclusivos do artista em função de seu usuario e/ou empresa 

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 455 — [FE] Fazer logout automático

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/455
**Tags:** nenhuma

**Descrição:**

Criar e colocar sistema de logout automático se o usuário estiver a x tempo sem acessar o app, ou trocar a senha fora do app, ou seus tokens expirarem.

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-03T21:49:05.907Z

```
Completing Pull Request 167 and the associated work items.
```

### História 421 — Criar telas de login

**Tipo:** User Story
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/421
**Tags:** nenhuma

**sem descrição**

#### Tarefa 422 — [FE] Tela de Esqueci minha senha

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/422
**Tags:** nenhuma

**Descrição:**

Descrição:

Vamos criar uma tela para o usuário preencher o seu email de login com um botão "Enviar e-mail" e um botão "Cancelar" para voltar para o login:

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/caf022aa-b686-4d7f-a5c8-bfb877dde758?fileName=image.png)

O botão voltar enviará para a tela anterior de onde ele partiu. Facilitando assim o cancelamento do login ou cadastro caso tenha clicado no lugar errado.

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 423 — [FE] Tela de código do esqueci minha senha

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/423
**Tags:** nenhuma

**Descrição:**

Descrição:

Vamos criar uma tela para o usuário preencher o código que foi enviado para seu email, deverá apresentar um erro caso o código seja inválido, deverá mostrar um contador de 5 minutos para inserir o código, ao acabar o timer, deverá aparecer um erro de tempo expirado, e o botão de enviar novamente, e um botão "Cancelar" para voltar para o login:

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/504471f6-891d-4585-9ac8-5317fa1e6040?fileName=image.png)

O botão voltar enviará para a tela anterior de onde ele partiu. Facilitando assim o cancelamento do login ou cadastro caso tenha clicado no lugar errado.

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-03-24T00:46:26.833Z

```
Tarefa bloqueada aguardando login e senha funcionarem no back-end
```

- Andrey Didoff do Nascimento — 2025-04-02T23:32:14.083Z

```
Completing Pull Request 149 and the associated work items.
```

#### Tarefa 424 — [FE] Tela de criação de nova senha

**Tipo:** Task
**Estado:** Blocked
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/424
**Tags:** nenhuma

**Descrição:**

Descrição:

Vamos criar uma tela para o usuário preencher a sua nova senha e repeti-la, a senha deverá seguir as regras descritas na imagem, as regras devem mudar o icone conforme forem sendo validadas:

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/12b96671-d636-4fed-baf8-73dfe4e07752?fileName=image.png)

O botão voltar enviará para a tela anterior de onde ele partiu. Facilitando assim o cancelamento do login ou cadastro caso tenha clicado no lugar errado.

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-03T17:56:04.227Z

```
Tarefa bloqueada, depende de tela de configurações do usuário.
```

#### Tarefa 425 — [FE] Tela com formulário de login

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** nenhum
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/425
**Tags:** nenhuma

**Descrição:**

Descrição:

Vamos criar uma tela para o usuário preencher os dados de login, esqueci minha senha, ou se cadastrar na plataforma:

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/c71c8486-b11f-4b96-a554-bfd1859a01b6?fileName=image.png)

O botão voltar enviará para a tela anterior de onde ele partiu. Facilitando assim o cancelamento do login ou cadastro caso tenha clicado no lugar errado.

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 462 — [FE] Colocar opção de login usando digital

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/462
**Tags:** nenhuma

**sem descrição**

#### Tarefa 466 — [FE] Remove console log and comments

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/466
**Tags:** nenhuma

**Descrição:** ausente

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-03T18:38:57.997Z

```
Completing Pull Request 165 and the associated work items.
```

## Épico 337 — Sistema de cadastro de usuário

**Tipo:** Epic
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/337
**Tags:** nenhuma

**sem descrição**

### História 357 — Cadastro de Cliente 

**Tipo:** User Story
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/357
**Tags:** nenhuma

**sem descrição**

#### Tarefa 358 — [BE] Cadastro do cliente no WeCareU.API

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** bruno.pires@wecareu.app
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/358
**Tags:** nenhuma

**Descrição:**

Criar Endpoint com modelo que contemple os dados do usuario CPF, com foto e ou foto padrão que deve ser inserida no sistema para não deixar a informação vazia. 

O valor da foto padrão deve ser inserido no AppSetting usando o padrão do json

"Pattern": { 
        "Photo":"GUID" 
} 

Qualquer outra informação padrão deve ficar dentro desse objeto e se carregado por injeção de dependência. 

Este endpoin vai se comunicar sem Autenticação padrão, Contudo, vamos validar as chaves de sistema e de empresa na chamada com utlização de um token combinado dos dois utilizando hash ( a validação da frente disso pode ser feita diretamente pelo token de login )  

Esse hash deve ficar no widowns secrets e se gerado unicamente para produção 

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 411 — [FE] Criação de Tela de cadastro cliente em forma de chat

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/411
**Tags:** nenhuma

**Descrição:**

Precisamos criar a tela de cadastro conforme disponível no figma e suas respectivas modais.

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/24c07a71-49eb-4351-9063-4a04a4020b3b?fileName=image.png)

- A tela deverá conter no canto superior esquerdo a logo da empresa We Care U.
- No canto superior direito teremos um botão de fechar que cancelará o cadastro de usuário.
- Teremos mensagens automáticas a esquerda contendo um icone de bot e um balão de mensagens.
- Teremos mensagens de resposta do cliente a direita seguindo as seguintes regras:
  - Imagem:
    - Icone de usuário para aquele cliente que ainda não subiu uma foto
    - Foto do usuário para aquele cliente que já subiu a foto
  - Mensagens:
    - Mensagem de escolha como por exemplo "Sim" ou "Não"
    - Mensagens de resposta com conteúdo oculto afim de proteger a privacidade do usuário. Sendo que:
      - Por padrão o texto virá escondido
      - Teremos um botão a direita com icone de olho, sendo:
        - Olho com risco: Indicando que está oculto, ao clicar deverá deixar as informações daquela mensagem visíveis 
        - Olho aberto: Indicando que está visível, ao clicar deverá deixar as informações daquela mensagem ocultadas 
    - Mensagens de resposta comuns sem ocultação
- Teremos validações de informações como:
  - CPF = Se já existe um cadastro no sistema, impedimos a continuação do cadastro.
  - E-mail = Se já existe um cadastro no sistema, impedimos a continuação do cadastro.
- Teremos modais para alertar o cliente ou auxiliar no envio das informações, sendo:
  - Modal de upload de imagem de perfil
  - Modal de aviso sobre CPF já cadastrado
  - Modal de aviso sobre E-mail já cadastrado
- Teremos campos de texto que aparecerão conforme a sequência de perguntas
- Teremos campo de CPF que validará se o CPF é válido e se não temos cadastrado
- Teremos campo de email que deverá conter um validador de email e se não temos cadastrado
- Teremos campo de senha que precisarão seguir as regras de senha descritas no figma
- E por fim um botão levando o usuário para:
  - Listagem = Caso ele apenas tenha feito um cadastro pela listagem
  - Agendamento = Caso ele tenha iniciado o processo de agendamento
  - Perfil = Caso ele tenha iniciado o processo de cadastro pela tela inicial do app

Figma:
https://www.figma.com/file/MSEibBfdtigMN0qxOJcrL5/WeCareU-App?type=design&node-id=143%3A5913&mode=design&t=0GvMOUdIwHey6El7-1

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2023-08-30T00:43:59.140Z

```
No processo de criação desta tarefa verificamos que havia a necessidade de criação de uma tela adicional para conseguirmos chegar até essa tela, 
Sendo assim essa tarefa está aguardando Tarefa 440 para continuar.
```

- Andrey Didoff do Nascimento — 2025-01-24T05:19:27.910Z

```
Tarefa continua após ajustes da tarefa 440
```

- Andrey Didoff do Nascimento — 2025-03-11T00:07:26.717Z

```
Completing Pull Request 140 and the associated work items.
```

#### Tarefa 412 — [DS] Aviso de CPF Inválido

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/412
**Tags:** nenhuma

**Descrição:**

Ao invés de criarmos uma modal de aviso de CPF inválido colocamos a mensagem de inválido diretamente no campo de escrita, o Mesmo valerá para CPF, CNPJ, email. 

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 413 — [DS] Aviso de E-mail inválido

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/413
**Tags:** nenhuma

**Descrição:**

Essa tarefa será concluída automaticamente com a tarefa 412 

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 414 — [DS] Inclusão de botão de finalização de cadastro

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/414
**Tags:** nenhuma

**Descrição:** ausente

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2023-08-29T00:19:12.870Z

```
![image.png](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/20fe2d59-0eee-48c1-94a5-8c28f0f8eb3e?fileName=image.png) 
```

#### Tarefa 440 — [FE] Criar tela de login ou cadastro do App

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/440
**Tags:** nenhuma

**sem descrição**

#### Tarefa 450 — [DS-FE] Criação de tela incentivando o cadastro para o menu

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/450
**Tags:** nenhuma

**Descrição:**

Criar uma tela de chamada para cadastro do usuário para quando o usuário está deslogado e clica para acessar as telas home, favoritos, agendamentos, e perfil. 

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/8a60a578-7aff-4676-b8c9-5c0f0f161c43?fileName=image.png)

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-04-02T23:40:36.997Z

```
Completing Pull Request 150 and the associated work items.
```

#### Tarefa 467 — [FE] Ajustar código do registro conforme regras novas

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/467
**Tags:** nenhuma

**Descrição:** ausente

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-03T20:03:17.577Z

```
Completing Pull Request 166 and the associated work items.
```

### História 360 — Cadastro de Artista

**Tipo:** User Story
**Estado:** Blocked
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/360
**Tags:** nenhuma

**Descrição:** ausente

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-01-24T05:39:04.103Z

```
Aguardando termino do app de cliente
```

#### Tarefa 361 — [BE] Cadastro do Artista no WeCareU.API

**Tipo:** Task
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** bruno.pires@wecareu.app
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/361
**Tags:** nenhuma

**Descrição:**

Criação do Artista pode ser feita em duas tabelas 

Se for uma empresa , cadastraremos o CNPJ e e o grupo, vincularemos o usuario pelo CPF do criador como usuario principal dele , que permitirá fazer os cadastros. 

O vinculo de Usuario empresa é dado pelas permissões 

Precisamremos repensar como usaremos a parte de empresa para o resto do pacote. de informações em um segundo momento 

o sistema de cadastro a partir do momento que cadastramos o usuario do artista , segue o fluxo comum, 

Ao menos 1 artista é obrigatório no cadastro do CNPJ 

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 415 — [DS] Criação de modal de CNPJ inválido

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/415
**Tags:** nenhuma

**Descrição:**

Essa tarefa será concluída automaticamente com a tarefa 412

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 416 — [FE] Criação de Tela de cadastro artista em forma de chat

**Tipo:** Task
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/416
**Tags:** nenhuma

**Descrição:**

Precisamos criar a tela de cadastro conforme disponível no figma e suas respectivas modais.

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/1dd43d2a-cbe1-4d72-8975-2ab4176fb1f1?fileName=image.png)

- A tela deverá conter no canto superior esquerdo a logo da empresa We Care U.
- No canto superior direito teremos um botão de fechar que cancelará o cadastro de usuário.
- Teremos mensagens automáticas a esquerda contendo um icone de bot e um balão de mensagens.
- Teremos mensagens de resposta do artista a direita seguindo as seguintes regras:
  - Imagem:
    - Icone de usuário para aquele artista que ainda não subiu uma foto
    - Foto do usuário para aquele artista que já subiu a foto
  - Mensagens:
    - Mensagem de escolha como por exemplo "Sim" ou "Não"
    - Mensagens de resposta com conteúdo oculto afim de proteger a privacidade do usuário. Sendo que:
      - Por padrão o texto virá escondido
      - Teremos um botão a direita com icone de olho, sendo:
        - Olho com risco: Indicando que está oculto, ao clicar deverá deixar as informações daquela mensagem visíveis 
        - Olho aberto: Indicando que está visível, ao clicar deverá deixar as informações daquela mensagem ocultadas 
    - Mensagens de resposta comuns sem ocultação
- Teremos validações de informações como:
  - CPF = Se já existe um cadastro no sistema, impedimos a continuação do cadastro.
  - CNPJ = Se já existe um cadastro no sistema, impedimos a continuação do cadastro.
  - E-mail = Se já existe um cadastro no sistema, impedimos a continuação do cadastro.
- Teremos modais para alertar o artista ou auxiliar no envio das informações, sendo:
  - Modal de upload de imagem de perfil
  - Modal de aviso sobre CPF já cadastrado
    Modal de aviso sobre CNPJ já cadastrado
  - Modal de aviso sobre E-mail já cadastrado
- Teremos campos de texto que aparecerão conforme a sequência de perguntas
- Teremos campo de CPF que validará se o CPF é válido e se não temos cadastrado
  Teremos campo de CNPJ que validará se o CNPJ é válido e se não temos cadastrado
- Teremos campo de email que deverá conter um validador de email e se não temos cadastrado
- Teremos campo de senha que precisarão seguir as regras de senha descritas no figma
- E por fim um botão levando o usuário para:
  - Perfil = Para continuar o cadastro das informações enquanto seu cadastro é aprovado

Figma:
https://www.figma.com/file/MSEibBfdtigMN0qxOJcrL5/WeCareU-App?type=design&node-id=143%3A5913&mode=design&t=0GvMOUdIwHey6El7-1

**Critério de aceite:** ausente

**Comentários:** ausente

## Itens sem pai no board

### História sem pai 223 — Tela de Cadastro do Artistas

**Tipo:** User Story
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/223
**Tags:** nenhuma

**sem descrição**

#### Tarefa 224 — [DS] Criar tela de cadastro do Artista no figma

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/224
**Tags:** nenhuma

**sem descrição**

### História sem pai 225 — Criar modais necessárias no cadastro de cliente e artista

**Tipo:** User Story
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/225
**Tags:** nenhuma

**sem descrição**

#### Tarefa 226 — [DS] Criação de modais do cadastro para cliente

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/226
**Tags:** nenhuma

**sem descrição**

#### Tarefa 227 — [DS] Criação de modais do cadastro para artista

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/227
**Tags:** nenhuma

**sem descrição**

### História sem pai 246 — [FE] Fluxo de Login

**Tipo:** User Story
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Pedro Rosa
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/246
**Tags:** nenhuma

**sem descrição**

#### Tarefa 247 — [FE] Tela de seleção de login ou cadastro

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Pedro Rosa
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/247
**Tags:** nenhuma

**Descrição:**

Descrição:

Vamos criar uma tela para o usuário selecionar se ele quer se cadastrar ou fazer login na plataforma:

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/52ca8590-a94b-4314-979a-8e6d4d112202?fileName=image.png)

O botão voltar enviará para a tela anterior de onde ele partiu. Facilitando assim o cancelamento do login ou cadastro caso tenha clicado no lugar errado.

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2023-08-08T21:40:10.690Z

```
Completing Pull Request 26 and the associated work items.
```
