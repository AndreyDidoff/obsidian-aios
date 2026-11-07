> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um *snapshot* do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Spec-Driven Development (Metodologia SDD)

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Atuar como Single Source of Truth (SSoT) para a metodologia de desenvolvimento guiado por especificações otimizadas para Inteligência Artificial (SDD v3).

**⚠️ ESCOPO ESTRITO (ATENÇÃO):** As diretrizes a seguir representam **instruções estritas de engenharia de software, geração de código e orquestração de Agentes de IA** (como Cursor AI e Aider) para a manipulação do repositório. Este documento **não** é um manual de processos corporativos, regras de negócios da empresa ou fluxos de recursos humanos. Seu foco é 100% técnico e voltado à automação do ecossistema WeCareU.

## 1. O Conceito: SDD v3 (AI-Optimized)

O Spec-Driven Development (SDD) na WeCareU garante que nenhuma linha de código seja escrita — seja por humanos ou por IA — sem que exista um contrato arquitetural prévio aprovado. A versão 3 (v3) foi desenhada especificamente para economizar tokens de LLMs, reduzir alucinações e impor o uso do Design System.

O fluxo opera obrigatoriamente em dois modos:
*   **Modo 1 (Nova Funcionalidade):** Fluxo sequencial para novas features (Discovery $\rightarrow$ Spec $\rightarrow$ Código).
*   **Modo 2 (Reverse Spec / Geração Retroativa):** Quando o Agente de IA precisa mapear código legado existente para gerar a documentação baseando-se estritamente no comportamento observável do repositório, alimentando a base de especificações.

## 2. O Fluxo de Desenvolvimento em 5 Fases

O ciclo de vida da inteligência artificial operando no Monorepo é rigidamente dividido em 5 fases. Pular etapas é estritamente proibido pelas regras de sistema (`.mdc`).

*   **Fase 0 - Discovery:** O Agente de IA atua como um Arquiteto. Ele analisa o pedido, consulta o `inventory.md` (SSoT do que já existe no código) e levanta perguntas de integração e bloqueadores. **Regra:** É proibido gerar blocos de código nesta fase; o foco é estruturação lógica.
*   **Fase 1 - Especificação:** Criação do documento central (`specs/[nome-feature].md`). Consolida o objetivo, contexto e os requisitos funcionais e não-funcionais.
*   **Fase 2 - Planejamento Técnico:** Criação do plano (`specs/plans/[nome-feature]-plan.md`). Define as bibliotecas a serem instaladas, a árvore de componentes e a comunicação com a `service_api` (.NET).
*   **Fase 3 - Quebra de Tarefas:** Fragmentação do plano em um checklist atômico (`specs/tasks/[nome-feature]-tasks.md`). Divide-se obrigatoriamente em tarefas de Design System (se faltar um componente), tarefas de Instalação (App) e tarefas de Interface/Integração.
*   **Fase 4 - Implementação:** Apenas aqui o Agente de IA começa a codificar, seguindo estritamente as tarefas da Fase 3 e respeitando as restrições arquiteturais (ex: *Design System First*, Tipagem Estrita, Sem arquivos desnecessários).

## 3. Estrutura Obrigatória do Contrato (Draft SDD v3)

Ao finalizar a *Discovery* (Fase 0), o Agente de IA deve gerar um esboço (Draft) em Markdown contendo as seguintes seções obrigatórias:

1.  **Metadados e Escopo:** Identificação da tarefa (Azure DevOps ID), os aplicativos alvos (ex: `ui-client`, `ui-worker`) e o impacto no ecossistema (Monorepo).
2.  **Requisitos e Componentização (Design System First):** A instrução clara de uso de componentes mapeados no `inventory.md`. É **proibido** criar estilos *hardcoded* (hex, spacing) que já existam no tema `library-design-system`.
3.  **Contratos de Dados (Interfaces TypeScript):**
    *   Definição puramente descritiva (ou interfaces TS isoladas) do *Input* esperado e *Output* esperado. Não deve conter lógica de implementação inline.
4.  **Plano de Implementação Lógico:**
    *   Lista de caminhos relativos dos arquivos que serão criados ou alterados.
    *   Passo a passo lógico da regra de negócio (ex: "1. Criar validação com Zod; 2. Acionar endpoint de POST").
5.  **Quality Gates (Aprovação e Testes):**
    *   A implementação exige que a lógica de submissão/regras passe nos testes unitários com **Jest**.
    *   O fluxo visual (tela e navegação) deve ser mapeado para validação com emuladores via **Maestro**.
    *   A presença de *bloqueadores de negócio* (perguntas pendentes) no final do draft impede o avanço para as fases de planejamento e código.

## 4. O Papel do Inventário (`inventory.md`)

Para que os Agentes de IA operem sem "miopia de contexto", o arquivo `inventory.md` atua como a única fonte da verdade do estado atual dos repositórios. 

*   O Agente é instruído a ler o inventário antes de sugerir soluções.
*   Se a feature pedir um "Input" que já existe na `library-design-system`, o agente deve reusá-lo.
*   Se a feature pedir um "TextArea" que **não** existe, a primeira tarefa do SDD v3 deverá ser, obrigatoriamente, criar esse componente base na biblioteca antes de aplicá-lo ao aplicativo final.