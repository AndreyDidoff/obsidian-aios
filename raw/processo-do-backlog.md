# Processo do backlog — WeCareU

Fonte de trabalho, conversa de 2026-11-05. Ainda não ingerir: o dono vai completar este arquivo antes.

Os cards antigos não foram reescritos. Time, área e iterações da Release 1.0.0 foram criados. Este texto é a regra alvo.

Marcador: [DEFINIDO] = fechado nessa conversa.

## 1. Hierarquia

[DEFINIDO] A árvore de trabalho é:

```
Epic
  Feature
    User Story
      Task
```

[DEFINIDO] Release não é work item e não é pai de ninguém. Release é nível de iteração. Um Epic atravessa releases. A Feature cabe inteira numa release. O que entra na release é a Feature, não o Epic.

```
Release 1.0.0
  Sprint 1
  Sprint 2
```

| Item | Iteração |
|---|---|
| Epic | `WeCareU\Release 1.0.0` enquanto o backlog do time for essa release. Sobe para `WeCareU` quando existir outra release |
| Feature | o nó da release, ex.: `WeCareU\Release 1.0.0` |
| User Story | um sprint dentro dessa release |
| Task | o mesmo sprint da Story |

[DEFINIDO] Pai responde de qual resultado o item faz parte. Iteração responde em qual release ele entra. A consulta do conteúdo de uma release é Iteration Path Under essa release.

[DEFINIDO] Cada item tem um pai só. Por isso a release não aparece como pasta na grade do backlog. A grade continua Epic, Feature, User Story, Task. A release é o seletor no topo dessa grade, e a coluna Iteration Path mostra a release e o sprint de cada linha. O Epic aparece de novo em cada release em que tiver Feature.

[DEFINIDO] Story que não cabe na release muda de sprint para a release seguinte. A Feature deixa de caber inteira: ou a Feature inteira muda de release, ou o que ficou para trás vira Feature nova, no mesmo Epic, na release seguinte.

## 2. Bug e Issue

[DEFINIDO] O corte do Bug não é a idade do código. É se o comportamento já foi aceito.

- História ainda aberta que falha no próprio critério de aceite continua nessa Story. A correção é Task. Não abre Bug.
- Defeito em algo que já saiu da Story (sprint anterior, release anterior ou código já aceito) é Bug. A Feature pode seguir em desenvolvimento.
- Bug fica no mesmo nível da User Story, ligado à Feature, com Tasks embaixo.
- Issue fica fora da árvore. É bloqueio, ligado ao item afetado.

[DEFINIDO] `[BUG]` e `[FIX]` não entram no título. O tipo do item já é Bug. A correção da história aberta é Task `[FE]`, `[BE]` ou `[QA]`.

## 3. Nomes

[DEFINIDO] O título sozinho diz quem faz o quê. A release não entra no título.

| Tipo | Fórmula |
|---|---|
| Epic | o resultado, sem persona, sem tela, sem colchete |
| Feature | um colchete de onde + capacidade no infinitivo |
| User Story | um colchete de onde + comportamento no presente |
| Task | `[Camada] [Destino]` + trabalho técnico |
| Bug | um colchete de onde + o que falhou, observável |
| Issue | o bloqueio |

[DEFINIDO] A descrição da User Story leva: Como [persona], quero [ação], para [motivo]. Critério de aceite fica na Story. A Task não repete o valor da Story.

[DEFINIDO] A Story se divide pela persona. Cliente, Artista e o painel já são os apps e o painel. Não há um segundo corte por repositório. App e API do mesmo comportamento ficam na mesma Story. A Task de backend da segunda persona só existe se o serviço fizer algo a mais para esse papel. O mesmo endpoint não vira duas Tasks iguais.

## 4. Tags no título

[DEFINIDO] Grafia travada. `[CLIENTE]` se escreve `[CLIENT]`, no par de `[ARTIST]`.

Onde, um colchete só, em Feature, Story e Bug:

`[CLIENT]` `[ARTIST]` `[PAINEL]` `[WIKI]`

Camada, primeiro colchete da Task. O segundo é o destino.

`[DS]` `[FE]` `[BE]` `[QA]`

| Camada | Destino |
|---|---|
| `[FE]` | `[CLIENT]`, `[ARTIST]` ou `[PAINEL]` |
| `[BE]` | o nome da API, sempre o mesmo, ex.: `[UserLogin]` |
| `[DS]` | `[CLIENT]`, `[ARTIST]`, `[PAINEL]` ou `[WIKI]` |
| `[QA]` | `[CLIENT]`, `[ARTIST]`, `[PAINEL]` ou o nome da API |

[DEFINIDO] `[DS]` é desenho no Figma. Código do design system é `[FE]`. Epic não leva colchete.

Descrição da Story usa a palavra Cliente, Artista ou Operação. O colchete do painel é `[PAINEL]`.

## 5. Fluxo do board

[DEFINIDO] O card que anda neste fluxo é a Story, e também o Bug quando o defeito é de algo já aceito. Feature e Epic não entram na coluna FIX. Task vai de Desenvolvimento a Done. Review e QA são da Story.

Caminho feliz, da esquerda para a direita:

```
New → Desenvolvimento → Code Review → Ready for QA → QA Approved → Ready for Deploy → Done
```

[DEFINIDO] FIX não é passo do caminho feliz. É a coluna para onde a Story volta quando o QA recusa o critério de aceite. Fica ao lado de Desenvolvimento, porque o próximo a agir é quem desenvolve. De FIX a Story refaz Desenvolvimento, Code Review e Ready for QA. Não pula o code review.

| Coluna | Quem coloca o card | Saída |
|---|---|---|
| New | planejamento | Desenvolvimento |
| Desenvolvimento | quem desenvolve | Code Review |
| Code Review | quem desenvolve | Ready for QA, ou de volta a Desenvolvimento se o review falhar |
| Ready for QA | quem aprovou o review | QA Approved, ou FIX |
| FIX | QA, quando o critério de aceite falha | Desenvolvimento |
| QA Approved | QA, quando o critério passa | Ready for Deploy |
| Ready for Deploy | QA | Done, quando entra na release |
| Done | release | — |

[DEFINIDO] Code review reprovado volta para Desenvolvimento, não para FIX.

[DEFINIDO] QA recusa a Story aberta: move para FIX e comenta a falha. Não abre Bug. QA vê defeito fora do critério de aceite, em algo já aceito: a Story segue para QA Approved e abre um Bug. Esse Bug anda no mesmo fluxo.

## 6. Epics

[DEFINIDO] Sete, e só estes.

1. Acesso à conta
2. Encontrar um Artista
3. Oferta do Artista
4. Realizar o atendimento
5. Confiança no atendimento
6. Operar a praça
7. Receita — existe pelas releases seguintes; na Release 1.0.0 não tem Feature

[DEFINIDO] Ranking não é Epic. É comportamento da Feature de lista.

O board antigo, lido em 2026-11-05, usava módulo e tela como Epic. O destino de cada nome:

| Nome antigo | Destino |
|---|---|
| Sistema de cadastro de usuário, Sistema de login, Sistema de perfil, Configurações do app | Features e Stories de Acesso à conta |
| Sistema de listagem, Tela de início do Cliente | Features de Encontrar um Artista. Início é Task |
| Sistema de cadastro de serviços | Feature de Oferta do Artista |
| Sistema de agendamentos, Sistema de check-in e check-out | Features de Realizar o atendimento |
| Sistema de review, Sistema de denúncia, Sistema de bloqueio | Features de Confiança no atendimento |
| Sistema de planos, Sistema de Assinaturas | Epic Receita. Nenhuma Feature na Release 1.0.0 |
| Sistema de favoritos | Feature futura de Encontrar um Artista. Fora da Release 1.0.0 |
| Estrutura dos Apps | Some. Logo e nome do app são Tasks da Story que abre o app |

## 7. Features da Release 1.0.0

[DEFINIDO] Iteração de todas: `Release 1.0.0`. Nomes na gramática da seção 4. O conjunto segue o MVP já fechado. Detalhe de tela do Artista que ainda não chegou não ganha Story neste arquivo.

**Acesso à conta**

- [CLIENT] Criar a conta
- [CLIENT] Entrar com e-mail e senha
- [CLIENT] Recuperar a senha
- [CLIENT] Editar a conta e excluir
- [ARTIST] Criar a conta
- [ARTIST] Entrar com e-mail e senha
- [ARTIST] Editar perfil e foto

**Encontrar um Artista**

- [CLIENT] Ver a lista sem ter conta
- [CLIENT] Filtrar por categoria, serviço, data e região
- [CLIENT] Abrir o perfil do Artista

**Oferta do Artista**

- [ARTIST] Publicar ofício, serviços e duração
- [ARTIST] Definir onde e quando atende

**Realizar o atendimento**

- [CLIENT] Reservar na hora
- [CLIENT] Consultar e cancelar até o início
- [CLIENT] Receber o lembrete do atendimento
- [CLIENT] Reagendar
- [ARTIST] Ver a agenda e os dados do dia
- [ARTIST] Fazer check-in e check-out
- [ARTIST] Registrar reserva manual
- [ARTIST] Receber aviso de nova reserva

**Confiança no atendimento**

- [CLIENT] Avaliar o atendimento
- [CLIENT] Denunciar
- [CLIENT] Bloquear
- [ARTIST] Ver as avaliações

**Operar a praça**

- [PAINEL] Aprovar o Artista
- [PAINEL] Tratar denúncia e bloquear

**Receita**

- Nenhuma Feature na Release 1.0.0

## 8. Exemplo fechado

Feature [CLIENT] Entrar com e-mail e senha, iteração `Release 1.0.0`.

```
Epic     Acesso à conta
  Feature  [CLIENT] Entrar com e-mail e senha
    Story  [CLIENT] Entra e chega na área logada
      Task [DS] [CLIENT] Desenhar a tela de login
      Task [FE] [CLIENT] Construir a tela de login
      Task [BE] [UserLogin] Autenticar e-mail e senha
      Task [QA] [CLIENT] Cobrir o fluxo feliz
    Story  [CLIENT] Vê erro único quando a senha falha
      Task [FE] [CLIENT] Mostrar o estado de erro
      Task [BE] [UserLogin] Responder sem dizer qual campo falhou
```

Descrição da primeira Story: Como Cliente, quero entrar com e-mail e senha, para acessar minha conta.

```
Feature  [ARTIST] Entrar com e-mail e senha
  Story   [ARTIST] Entra e chega na área logada
    Task  [FE] [ARTIST] Construir a tela de login
    Task  [BE] [UserLogin] Aceitar a sessão do Artista
    Task  [QA] [ARTIST] Cobrir o fluxo feliz
```

A Task `[BE] [UserLogin] Aceitar a sessão do Artista` só existe porque o serviço trata esse papel. Se fosse o mesmo endpoint da Story do Cliente, ela não se repetiria.

Bug de comportamento já aceito:

```
Bug   [CLIENT] Login com senha certa volta erro
  Task [BE] [UserLogin] Devolver o código certo
  Task [QA] [CLIENT] Reproduzir o fluxo
```

Story ainda aberta, critério falhou no QA: o card vai para FIX. A correção é Task nova nessa Story, por exemplo `[FE] [CLIENT] Corrigir o botão que não envia`. Não abre Bug.

## 9. Time e área

[DEFINIDO] O backlog novo é do time **WeCareU - App**. O time GLOBAL fica com o board antigo.

[DEFINIDO] Área desse time: só `WeCareU\WeCareU - App`, e essa é a área padrão. `WeCareU\GLOBAL` não entra neste time. Item antigo em GLOBAL não aparece no backlog novo.

[DEFINIDO] Em Team configuration, Iterations:

- Backlog iteration: `WeCareU\Release 1.0.0`. Este time enxerga a Release 1.0.0 e o que estiver abaixo.
- Default iteration: `WeCareU\Release 1.0.0`. Card novo nasce na release. O sprint é escolha de planejamento, não o lugar onde o card nasce.
- Sprint 1 selecionado na lista do time. Sem isso o sprint não aparece no Sprints hub. Datas do Sprint 1 dentro das datas da Release 1.0.0.

[DEFINIDO] Backlog navigation levels: Epics, Features e Stories marcados.

[DEFINIDO] Working with bugs: **Bugs are managed with requirements**. O Bug fica no mesmo nível da User Story. A opção "managed with tasks" coloca o Bug no lugar da Task e quebra essa regra. A correção de Story ainda aberta continua sendo Task, não Bug.
