---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-22
fontes: ["[[decisoes-2026-10-20]]", "[[ssot-ecossistema-engenharia]]", "[[ssot-automacao]]", "[[ssot-sdd]]", "[[ssot-backlog]]", "[[divisao-atomic-design]]", "[[lyraui-04-arquitetura]]", "[[panorama-do-design-system]]", "[[como-o-time-revisa-a-interface]]", "[[bff-o-que-e-este-backend]]", "[[board-indice]]", "[[board-conta-e-acesso]]", "[[board-estrutura-dos-apps]]", "[[board-design-no-figma]]", "[[board-bugs]]", "[[banco-indice]]", "[[banco-sql-relacoes]]", "[[banco-mongo-relacoes]]", "[[banco-sql-userlogin]]", "[[banco-sql-systemservice]]", "[[banco-sql-systemsdata]]", "[[banco-sql-address]]", "[[banco-sql-phone]]", "[[banco-sql-email]]", "[[banco-sql-enterprise]]", "[[banco-sql-i18n]]", "[[banco-sql-paymentplans]]", "[[banco-sql-report]]", "[[banco-sql-audition]]", "[[banco-mongo-photos]]", "[[banco-mongo-signature]]", "[[banco-mongo-template]]", "[[banco-mongo-validation]]"]
---

# Engenharia de software

Como o código da [[wecareu]] é organizado e como a IA é autorizada a mexer nele. O BFF abaixo foi confirmado pelo usuário. O restante desta página vem de snapshots Gemini/Claude e ainda não foi conferido no repositório.

## Stack e repositórios

- Front: Expo, React Native, TypeScript. Back: C# .NET 8 e 10. ([[ssot-ecossistema-engenharia]])
- O back que o app consome hoje é o BFF [[beautiful-api]]: repositório Azure `service_api`, CNAME `api.wecareu.app`, dados vindos dos microserviços `*.bptsoftware.com.br`. ([[decisoes-2026-10-20]])
- Apps nomeados: `ui-client`, `ui-worker`, `ui-business` e as versões web, mais `web-admin` e `web-wiki`. → [[ecossistema-de-produtos]]
- Código e comentários em inglês. Texto de tela via i18n. Sem classe, sem `import React` só por causa do JSX, sem hex hardcoded, `useTheme()` obrigatório, import só por escopo `@wecareu/...`. ([[ssot-ecossistema-engenharia]])

## Um monorepo ou dois

| Fonte | Forma |
|---|---|
| [[ssot-ecossistema-engenharia]] | um monorepo Turborepo + pnpm, com workspaces `library-design-system` e `library-components` |
| [[divisao-atomic-design]] | dois monorepos separados, o primeiro como fundação da [[lyraui]] |
| [[lyraui-04-arquitetura]] | alvo `@lyra-ui/*` até organisms e `@wecareu/*` para templates; não usa esses nomes de repositório |

A cadeia de dependência, essa sim comum às três: tokens → theme → componentes → apps. Ver [[contradicoes-e-lacunas]].

## Retrato de 21/10

A extração do [[kit-visual]] olhou só o repositório `library-design-system`. Não cita `library-components` e não fecha o item 18. Dentro dele existem `playground` (versão 1.0.0) e `storybook-web` (porta 6006). Nenhum dos dois usa o escopo `@wecareu`. ([[panorama-do-design-system]], [[como-o-time-revisa-a-interface]])

O retrato de 21/10 do repositório `service_api` confirma o papel de encaminhar: este backend não desenha tela, e a regra de negócio mora nos serviços. O item 18 continua aberto. ([[bff-o-que-e-este-backend]])

A estrutura lida em 21/10 tem onze bancos SQL e quatro Mongo, no host `server.wecareu.app`. Não há chave estrangeira declarada. Os pares pelo nome da coluna estão em [[banco-sql-relacoes]] e [[banco-mongo-relacoes]] e não são constraint. Isto não é decisão de produto. ([[banco-indice]]) Quem acessa está em [[banco-sql-userlogin]] (`Usuario`, `Session`, `forgetpassword`, `GrupoUsuario`, `BlockUsers`; não há `Bilings`). Serviço, agenda e empresa do profissional estão em [[banco-sql-systemservice]]. Permissões, grupos e a tabela `Screens` estão em [[banco-sql-systemsdata]]; não há `SystemComplement`. Endereço: [[banco-sql-address]], tabela `address`. Telefone: [[banco-sql-phone]], banco `Phone`, tabela `Telefones`. E-mail: [[banco-sql-email]]. Organização: [[banco-sql-enterprise]], distinta de `Company`. Idiomas: [[banco-sql-i18n]]. Planos: [[banco-sql-paymentplans]], banco `PaymentPlans`. Relatos: [[banco-sql-report]], tabelas `Report` e `ReportFotos`. Auditoria: [[banco-sql-audition]], tabela `Audit`. Fotos, modelos, assinatura e documentos de validação não são SQL: [[banco-mongo-photos]], [[banco-mongo-template]], [[banco-mongo-signature]] e [[banco-mongo-validation]]. As duas últimas coleções estão vazias.

## SDD v3

Nenhuma linha, humana ou de IA, sem contrato. Fases: Discovery (lê `inventory.md`, sem código), especificação, plano, tarefas, implementação. Bloqueador de negócio no draft impede codar. Componente que não existe nasce primeiro na biblioteca. ([[ssot-sdd]])

## Esteira

Azure DevOps é a fonte da verdade das tarefas. Colunas: Backlog, ToDo, Doing, Blocked, Ready for QA, Fix, Ready for Deploy, Done. O n8n dispara o Aider. Antes de Doing, `madge` olha o grafo; se o escopo cruza outra tarefa em Doing, a nova vai para Blocked. ([[ssot-automacao]])

Git: `main` é produção, `develop` é integração, branch `CLIENT-XXX` ou `WORKER-XXX` sai de `develop` e volta para ela em Ready for Deploy. ([[ssot-automacao]])

## O que o board pede em 21/10

Entraram o mapa ([[board-indice]]) e a conta e acesso ([[board-conta-e-acesso]]). Conta, listagem, início, perfil, favoritos, agendamentos, review, bloqueio, denúncia, serviços, planos e configurações têm fonte. Estrutura tem fonte ([[board-estrutura-dos-apps]]). Design no Figma tem fonte ([[board-design-no-figma]]). Bugs têm fonte ([[board-bugs]]). Os 15 temas têm fonte. Nenhum tema do board segue em `raw/`. Esta onda pede biblioteca de componentes, biblioteca de design system, pipeline para feed privado e os dois apps com Expo. Flutter está em história sem pai. Expo no board não resolve o monorepo. O item 18 segue aberto. A história 213 pede trocar Beautiful por WeCareU. O retrato do BFF continua `service_api` / Beautiful. A história 456 pede wiki interna. Não é esta base. O board é fila de trabalho, não stack. Estado de work item não é pé do produto. O alvo continua o [[mvp]], via [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Testes

Jest valida lógica e não pode ser trocado pelo Maestro. Essa troca chegou a ser discutida e foi rejeitada como dívida. Maestro entra só no E2E, via MCP, depois do Jest. Yalc publica o pacote local antes do teste no app. Chromatic no lugar da regressão visual do Storybook ainda é dívida. ([[ssot-backlog]], [[ssot-automacao]])

Ver [[lyraui]], [[kit-visual]].
