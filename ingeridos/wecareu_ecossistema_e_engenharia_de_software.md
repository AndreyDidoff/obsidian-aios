> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um *snapshot* do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Ecossistema e Engenharia de Software

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Atuar como Single Source of Truth (SSoT) para a arquitetura de software, estrutura do monorepo, padrões estritos de código e esteira de automação (CI/CD/AI) do projeto WeCareU.

## 1. Arquitetura do Ecossistema (Aplicações)

O sistema opera sob uma arquitetura orientada a serviços com separação rigorosa por perfil de usuário. A stack padrão do Front-end é **Expo, React Native e TypeScript**, enquanto o Back-end utiliza **C# com .NET (8 e 10)**.

* **Ambientes de Cliente:**
  * `ui-client`: Aplicativo mobile principal para o consumidor final buscar, agendar e avaliar serviços.
  * `web-client`: Versão web equivalente ao app do cliente.
* **Ambientes de Artista:**
  * `ui-worker`: Aplicativo mobile focado na produtividade do profissional (agenda, métricas e portfólio).
  * `web-worker`: Versão web do painel do artista.
* **Ambientes de Locais (Empresas):**
  * `ui-business` / `web-business`: Aplicações (mobile e web) para gestão de salões, clínicas e múltiplos profissionais.
* **Ambientes Internos (Controle e Gestão):**
  * `web-admin`: Plataforma web para controle de acessos, senhas, feature flags, banimentos e aprovações de perfis.
  * `web-wiki`: Base de conhecimento interna, documentação de style guides e processos da empresa.
* **Back-end Central:**
  * `service_api`: API RESTful centralizada em .NET que alimenta todos os front-ends acima.

## 2. Estrutura do Monorepo e Hierarquia de Dependências

O código-fonte Front-end é orquestrado como um Monorepo utilizando **Turborepo (`turbo.json`)** e **pnpm workspaces**. A arquitetura exige um fluxo unilateral de dependências rígido para evitar acoplamento.

### Repositórios de Bibliotecas (Workspaces)
* **`library-design-system`:** Contém pacotes puramente visuais e tokens.
* **`library-components`:** Contém componentes de negócio complexos e fluxos reutilizáveis (ex: `@wecareu/auth-flow`).

### Fluxo de Dependência Obrigatório (Grafo)
Nenhum pacote pode importar itens de uma camada superior ou pular camadas da base:
1. `tokens` (Variáveis puras, sem dependências internas) $\rightarrow$
2. `theme` (Depende exclusivamente de tokens) $\rightarrow$
3. `componentes` (Dependem de theme/tokens) $\rightarrow$
4. `apps` (Consomem os componentes).

## 3. Padrões Estritos de Código (Regras `.mdc`)

Toda implementação humana ou via Inteligência Artificial deve obedecer aos contratos estabelecidos nos arquivos `.mdc`:

* **Padrões React e JSX Transform:** É proibido o uso de `import React from 'react'` apenas para JSX (o projeto usa React 17+ transform). A programação deve ser funcional e declarativa (classes são proibidas).
* **Idioma:** Variáveis, funções, caminhos, nomes de arquivos e comentários devem ser estritamente em **Inglês**. Textos visuais na interface utilizam internacionalização (`i18n`).
* **Design System First & Integração de Tema:** 
  * É **proibido** o uso de valores de cor (`hex`) ou espaçamento *hardcoded*.
  * O uso do hook `useTheme()` importado de `@wecareu/theme` é obrigatório.
* **Regras de Importação e Peer Dependencies:**
  * **Sempre** use imports absolutos via escopo npm (ex: `import { Icon } from '@wecareu/icons'`). É terminantemente proibido o uso de caminhos relativos entre pacotes (ex: `../../theme/src`).
  * Dependências compartilhadas (React, React Native, Expo, Theme) devem ser declaradas exclusivamente no bloco `peerDependencies` no `package.json` dos pacotes.

## 4. Automação Full-Cycle, Orquestração e IA

A WeCareU adota uma esteira de desenvolvimento orquestrada por IA com forte controle de concorrência e testes contínuos.

* **Azure DevOps como SSoT:** O Azure DevOps Boards é a única fonte da verdade para o gerenciamento de tarefas e status.
* **Orquestração com n8n (Docker):** O n8n gerencia webhooks do Azure, executa a triagem e dispara o Agente CLI (Aider + LLM) em background.
* **Grafo de Dependência (Dependency-Aware Locking):** O orquestrador aplica regras de bloqueio de concorrência. Se uma nova tarefa tentar alterar o mesmo escopo de domínio de uma tarefa já em progresso (*Doing*), o n8n a move para *Blocked* automaticamente.
* **Spec-Driven Development (SDD v3):** Antes de qualquer linha de código, a IA gera um contrato técnico rigoroso (SDD v3) definindo escopo, dependências e interfaces TypeScript, garantindo ausência de alucinações e foco em regras de negócio mapeadas.
* **Yalc / NPM Link:** Utilizado para *simlink* local, garantindo que alterações no Design System reflitam quase em tempo real nos aplicativos durante o desenvolvimento via IA.

## 5. Estratégia de Qualidade e Pirâmide de Testes

* **Testes Unitários e Lógicos (Jest):** Rodados de forma contínua para validar lógica de negócio, hooks e regras de submissão sem onerar a interface.
* **Testes E2E Emulados (Maestro + MCP Server):** A validação visual e de fluxo não substitui o Jest. O Maestro atua em camada superior, emulando a navegação real do usuário, sendo acionado pelo n8n via Model Context Protocol após a aprovação dos testes unitários.
* **Dívida Técnica Mapeada:** Migrar a validação visual do Storybook para o **Chromatic** integrado à esteira de CI/CD para testes de regressão automatizados.

## 6. Padrões de Git Flow

* **`main`**: App oficial de produção.
* **`develop`**: Ambiente base de integração contínua.
* **Feature Branches**: Obrigatoriamente vinculadas ao ID da tarefa do Azure (ex: `CLIENT-XXX` ou `WORKER-XXX`), geradas a partir da `develop`.