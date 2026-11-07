> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um *snapshot* do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Automação Full-Cycle e Orquestração de IA

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Atuar como Single Source of Truth (SSoT) para os fluxos de automação, gestão de concorrência, testes e versionamento contínuo geridos por inteligência artificial no ecossistema WeCareU.

## 1. Gestão de Tarefas e SDD v3 (AI-Optimized)

O fluxo de desenvolvimento da WeCareU é guiado pelo conceito de **Spec-Driven Development (SDD)**. Nenhuma linha de código deve ser escrita sem um contrato prévio estruturado para leitura eficiente por IAs (otimização de tokens).

*   **Azure DevOps Boards como SSoT:** O Azure DevOps é a única fonte da verdade para o estado das tarefas. O fluxo Kanban obrigatório é: `Backlog` $\rightarrow$ `ToDo` $\rightarrow$ `Doing` $\rightarrow$ `Blocked` $\rightarrow$ `Ready for QA` $\rightarrow$ `Fix` $\rightarrow$ `Ready for Deploy` $\rightarrow$ `Done`.
*   **Estrutura do SDD v3:** Cada tarefa enviada para o Azure deve conter um documento com metadados estritos:
    *   **Escopo de Domínio:** Identificação do raio de impacto (ex: `pkg:button-close`, `screen:login`).
    *   **Contratos TypeScript:** Definição prévia das interfaces de *Input* e *Output*.
    *   **Plano de Implementação:** Lista de arquivos exatos que serão editados e as regras de negócio associadas.

## 2. Fluxo Git (Git Flow e Branching)

O ciclo de vida do código obedece a um padrão hierárquico rígido para garantir estabilidade e rastreabilidade:

*   **`main`:** Código de produção (estável e homologado).
*   **`develop`:** Ambiente base de integração contínua e testes.
*   **Feature Branches (`CLIENT-XXX` ou `WORKER-XXX`):** Para cada nova tarefa assumida (em `Doing`), deve-se criar uma ramificação (fork) a partir da `develop`. O prefixo deve corresponder ao ID da tarefa no Azure DevOps (ex: `CLIENT-142` para uma tarefa do app `ui-client`).
*   **Merge Strategy:** Quando a tarefa atinge o status `Ready for Deploy`, o código da Feature Branch deve ser mergeado na `develop`. O deploy oficial para produção ocorre da `develop` para a `main`.

## 3. Gestão de Concorrência e Bloqueios Lógicos

Para evitar *race conditions* quando múltiplos agentes de IA estiverem atuando no monorepo, utilizamos **Análise de Grafo de Dependências (File-Level Locking)**.

*   A abordagem simplista de comparar nomes de arquivos é proibida.
*   Antes de uma tarefa sair de `ToDo` para `Doing`, executa-se uma análise estática (via ferramentas como `madge`) da árvore de dependências do escopo da tarefa (definido no SDD v3).
*   **Semáforo de Domínio:** Se a nova tarefa exigir alterações em pacotes ou componentes que já estão sendo modificados por outra tarefa em `Doing` (ex: atualizar um botão central no `library-design-system` que afetará o `ui-client`), a nova tarefa deve ser movida **obrigatoriamente** para a coluna `Blocked` até que o conflito seja resolvido (merge da branch corrente).

## 4. Resolução de Simlink/Path no Ambiente Windows (Yalc)

Dado que a arquitetura front-end é um monorepo distribuído (`library-design-system`, `library-components`, `ui-client`), as alterações em pacotes internos precisam refletir instantaneamente nos aplicativos durante o desenvolvimento automatizado.

*   **O Problema do Path Local:** IAs têm dificuldade em validar bibliotecas consumidas em tempo real se não houver um proxy NPM ou um link consistente.
*   **A Solução (Simlink Automatizado):** O fluxo adota o uso do **Yalc** ou **npm link** para o ambiente Windows.
    1.  Ao finalizar uma alteração no pacote base (ex: `library-design-system`), o agente deve publicar a versão semanticamente (ex: `1.0.1`) e rodar `yalc publish`.
    2.  No app consumidor (ex: `ui-client`), o fluxo deve rodar `yalc add @wecareu/[pacote]` para injetar o código real na pasta do projeto.
    3.  Somente após esse *simlink*, a IA testa o fluxo completo no aplicativo final.

## 5. Pirâmide de Testes Automatizados (Rigor Arquitetural)

A validação do código gerado por IA segue uma esteira em duas camadas. **A regra de ouro é: O Maestro nunca substitui o Jest.**

*   **Camada 1: Testes Unitários e Lógicos (Jest)**
    *   Executados em *loop* contínuo durante a escrita do código (TDD local).
    *   Foco em validar regras de negócio, hooks customizados e submissão de dados sem onerar emuladores.
    *   Falhas aqui geram recusa imediata do código antes de avançar de coluna.
*   **Camada 2: Validação Visual e de Fluxo (Maestro via MCP)**
    *   Acionado apenas quando a tarefa atinge seu fim estrutural e passa no Jest.
    *   O Maestro emula a navegação do usuário final no dispositivo, operando via Model Context Protocol (MCP Server).

*Dívida Técnica Mapeada:* No futuro, substituir ou integrar a validação visual (atualmente dependente do Storybook) pelo **Chromatic** integrado à esteira de CI/CD para detecção automatizada de regressões de interface.