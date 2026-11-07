---
tipo: fonte
arquivo: ingeridos/wecareu_spec_driven_development_sdd.md
origem: extração via IA (Gemini), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# SSoT de Spec-Driven Development

O próprio arquivo limita o escopo: é instrução para agentes de código (Cursor, Aider), não regra de negócio nem de RH.

## Pontos principais

- Dois modos: funcionalidade nova (Discovery → Spec → código) e reverse spec (documentar legado pelo comportamento observável).
- Cinco fases, sem pular: Discovery (sem código; lê `inventory.md`), Especificação, Plano técnico, Quebra de tarefas, Implementação.
- Draft obrigatório: metadados e Azure ID, componentes do inventário, interfaces de entrada e saída sem lógica, lista de arquivos, quality gates (Jest e Maestro).
- Bloqueador de negócio no draft impede avançar.
- Se o componente não existe no inventário, a primeira tarefa é criá-lo na biblioteca.

Ver [[engenharia-de-software]].
