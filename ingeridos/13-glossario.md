> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 13 · Glossário

Tags: #lyraui #wecareu #glossario #termos

---

## 1. Status e como ler

- **WeCareU:** o glossário oficial pertence à WeCareU e lista os principais termos usados pela equipe e seus significados.
- **LyraUI (em discovery, não implementada no código):** o glossário oficial **não traz** os termos específicos da LyraUI (virada de chave, `@lyra-ui/*`, legado x alvo). Eles estão na seção 3, extraídos dos demais documentos, e **não fazem parte do glossário oficial**.
- Contexto em [[01-visao-geral-lyraui]].
- Edição: corrigi erros de digitação e espaçamento da fonte (por exemplo, trechos colados em "Product Manager" e "Product Owner") sem alterar o sentido.
- Sugestão de termo novo ou dúvida: **ux@wecareu.app**.

---

## 2. Glossário oficial (ordem alfabética)

### A

**Aspect ratio**
Proporção dimensional usada como referência para redimensionar o mesmo elemento.

**Assets**
Elementos que compõem o conteúdo dos produtos digitais: folhas de estilo, scripts, fontes, imagens e outros recursos.

### B

**Backlog**
Lista de todas as tarefas necessárias para criar um produto ou desenvolver um projeto. Ajuda a organizar as sprints: a sprint seleciona tarefas do backlog e as distribui por período.

**Base Components**
Componentes elementares e indivisíveis, como ícones, botões e campos de texto. Ver [[04-arquitetura-e-estrutura-do-ds]].

**Biblioteca core**
Biblioteca principal de tokens (estilos) e componentes de design, onde as atualizações são centralizadas. Administrada pelo time responsável pelo Design System, que detém o poder de edição.

**Biblioteca de time**
Cópia ou versão da biblioteca core, que pode conter elementos específicos para uma equipe ou squad. Nela é possível sugerir adaptações e customizações. Se as atualizações fizerem sentido para o negócio, são absorvidas pela biblioteca core.

### C

**Call-to-action (CTA)**
Qualquer chamada, visual ou textual, que leve a pessoa a realizar uma ação. Muito usada em marketing digital para gerar interação com campanhas.

**Code Snippets**
Pequenos blocos de código reutilizáveis, que podem ser copiados e inseridos em um arquivo. Ajudam na produtividade e na padronização do código.

**Components**
Componentes mais complexos, que reúnem Base Components e Tokens. Exemplos: headers, cards, carrosséis.

**Core**
Derivado do inglês: aquilo que é essencial ou principal. Exemplo: a biblioteca core é a principal e a referência.

### D

**(Estado) Default**
Estado padrão, usado quando não ocorre nenhuma ação com o componente.

**Design Principles (princípios de design)**
Conjunto de definições que guia e minimiza a subjetividade da tomada de decisão em design. São valores que guiam as decisões. Cada princípio pode ser traduzido por uma palavra ou frase curta, com explicação clara e tangível. Ver [[12-principios-de-design]].

**Dev.**
Abreviação de "desenvolvedor" ou "desenvolvedora": pessoa ou time que desenvolve, programa e codifica softwares.

**Dev. Back-end**
Pessoa desenvolvedora focada na organização e dinamização de informações que não são visíveis às pessoas usuárias.

**Dev. Front-end**
Profissional que atua na aplicação visível e que interage diretamente com as pessoas usuárias, também chamada de interface.

**Dev. Full-stack**
Profissional que atua em front-end e back-end, capaz de entender e entregar um projeto completo, com todas as etapas do desenvolvimento.

**DS**
Abreviação de Design System.

### G

**Guidelines**
Diretrizes, ou um conjunto de regras.

### H

**Handoff**
Qualquer ponto de um processo em que o trabalho ou a informação passa de uma função para outra. É marcado quando o trabalho de UX/UI termina e é entregue ao time de desenvolvimento. O arquivo de handoff costuma trazer especificações e apontamentos para facilitar o entendimento de quem vai usá-lo.

**Helpers**
Biblioteca só para a equipe de design, que reúne todos os assets em um documento para facilitar a composição de páginas e estruturas do dia a dia. É o nosso **UI KIT**.

### L

**Label**
Título, legenda ou texto que acompanha ou faz parte do componente. Exemplos: o texto de um botão, ou o texto junto aos ícones de checkbox e radio button.

**Lib**
Abreviação de *library* (biblioteca, em inglês).

**Lightbox ou (Modal) Overlay**
Sobreposição de modal usada para carregar e exibir informações importantes sem sair da página atual. Casos de uso:
- Coletar dados dos usuários.
- Lembrar ou avisar algo aos usuários.
- Carregar diálogos que exigem a entrada da pessoa antes de avançar.
- Carregar tarefas que exigem atenção total do usuário.

### P

**Placeholder**
Frase ou palavra curta que ajuda a entender como preencher um campo, com texto contextual. Exemplo: em um campo de e-mail, `exemplo@email.com`.

**Product Manager (PM)**
Papel estratégico: gerir o produto e estar atento às oportunidades de mercado para aumentar o desempenho. Significa buscar formas de melhorar o produto constantemente, alinhando boas práticas de design, experiência, negócio e tecnologia.

**Product Owner (PO)**
Pessoa responsável pela condução, gerenciamento e priorização das tarefas com o time. É o "guardião do backlog", alinhado às expectativas e necessidades do cliente, e define o que priorizar na execução.

### S

**Sprint**
Processo, baseado em período de tempo e etapas, para organizar o desenvolvimento de um produto ou projeto. Permite gerenciar em partes as atividades necessárias para a entrega final. Cada sprint é uma fase do projeto, com duração definida.

**Style Guide (guia de estilo)**
Também conhecido como *Style Tiles*. Guia visual que mantém a equipe alinhada e oferece um ponto de partida flexível para definir como um estilo visual será aplicado nas interfaces.

### T

**Tecnologia Assistiva**
Conjunto de recursos que amplia a mobilidade, a comunicação e o aprendizado das pessoas com deficiência. Ajuda na participação, inclusão social, autonomia, qualidade de vida e independência de pessoas com incapacidades, transtornos e mobilidade reduzida.

**(Global) Tokens**
Estilos compartilhados entre as frentes de missão. Definições compartilhadas e mantidas iguais em cada uma das marcas.

**(Brand) Tokens**
Estilos específicos da marca: próprios, exclusivos e personalizados de cada marca.

---

## 3. Termos adicionais (não fazem parte do glossário oficial)

Extraídos dos outros documentos desta base, para o Obsidian resolver os links. **Validar antes de oficializar.**

### Negócio e produto (WeCareU)

| Termo | Significado | Onde ver |
|---|---|---|
| **Artista** | Profissional de beleza cadastrado na plataforma | [[02-contexto-wecareu]] |
| **CLIENT** | App mobile do cliente final (tema light) | [[02-contexto-wecareu]] |
| **WORKER** | App mobile do Artista, prestador de serviço (tema dark) | [[02-contexto-wecareu]] |
| **Home service** | Modelo em que o Artista se desloca até o cliente | [[02-contexto-wecareu]] |
| **MVP** | Versão em produção do produto, em paralelo à qual a LyraUI é construída | [[03-estado-atual-do-produto]] |
| **Na esteira** | Funcionalidade priorizada, em fila de desenvolvimento | [[03-estado-atual-do-produto]] |
| **Check-in / Check-out** | Registro de chegada e saída do Artista no atendimento | [[03-estado-atual-do-produto]] |
| **LGPD** | Lei Geral de Proteção de Dados (Lei nº 13.709/2018) | [[02-contexto-wecareu]] |

### Design system (LyraUI)

| Termo | Significado | Onde ver |
|---|---|---|
| **LyraUI** | Design System oficial e exclusivo da WeCareU, também uma persona. Em discovery | [[01-visao-geral-lyraui]] |
| **SSoT** | *Single Source of Truth*, Única Fonte da Verdade | [[01-visao-geral-lyraui]] |
| **Virada de chave** | Migração de `@wecareu/*` para `@lyra-ui/*`, com rebrand de escopo, novo Atomic Design e novos repositórios | [[04-arquitetura-e-estrutura-do-ds]] |
| **Legado** | O que existe hoje em `@wecareu/*` e será migrado | [[06-catalogo-e-inventario-legado]] |
| **Alvo** | O estado desejado após a virada de chave | [[04-arquitetura-e-estrutura-do-ds]] |
| **Sub-atomic** | Camada abaixo dos atoms (tokens, tema, ícones) | [[04-arquitetura-e-estrutura-do-ds]] |
| **Atomic Design** | Organização em sub-atomic, atoms, molecules, organisms, templates e pages | [[04-arquitetura-e-estrutura-do-ds]] |
| **Definition of Done (DoD)** | Critérios para um componente ser considerado pronto | [[04-arquitetura-e-estrutura-do-ds]] |
| **Storybook** | Vitrine técnica dos componentes (web e on-device) | [[04-arquitetura-e-estrutura-do-ds]] |
| **ZeroHeight** | Documentação de design e fonte de verdade | [[01-visao-geral-lyraui]] |
| **TL** | Tech Lead, para quem se sinaliza valor sem token | [[07-figma-padroes-e-tokens]] |
| **node-id** | ID único e estável de um componente no Figma | [[07-figma-padroes-e-tokens]] |
| **Care** | Conceito de cuidado, base da voz acolhedora | [[10-voz-e-tons]] |

---

## 4. Divergências e pontos em aberto

- **Tokens (Global e Brand).** A definição cita "frentes de missão" e "cada uma de nossas marcas". Não está claro como isso se aplica a um ecossistema com uma marca (WeCareU) e um design system. Revisar.
- **Helpers (UI KIT).** Descreve uma biblioteca só de design. Não aparece na estrutura de páginas do Figma de [[07-figma-padroes-e-tokens]]. Confirmar se existe.
- **Biblioteca core x de time.** O modelo de governança está descrito, mas não há registro de que existam bibliotecas de time hoje.
- **Termos da LyraUI ausentes do glossário oficial.** A seção 3 sugere o que acrescentar.

---

## Links

Anterior: [[12-principios-de-design]] · Próximo: [[14-ferramentas-e-forma-de-trabalho]]
