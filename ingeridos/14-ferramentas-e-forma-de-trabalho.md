> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 14 · Ferramentas e forma de trabalho

Tags: #lyraui #wecareu #ferramentas #figma #zeroheight #claude #fluxo-de-trabalho

---

## 1. Status

- **LyraUI (em discovery, não implementada no código):** este documento descreve como o trabalho de design system é conduzido **agora**, em paralelo ao MVP.
- **WeCareU (produto em produção):** o ambiente técnico real (Expo / React Native) é considerado para garantir que as decisões de design sejam viáveis. Ver [[03-estado-atual-do-produto]].
- Escopo deste arquivo: ferramentas, fluxo e regras de trabalho do projeto. **Não inclui** dados pessoais da pessoa responsável, apenas o papel.

---

## 2. Papel e foco

- A pessoa responsável pelo Design System LyraUI atua na **interseção entre design, produto e tecnologia**.
- O trabalho é focado em **design**: componentes atômicos, tokens, fundamentos visuais, voz e documentação no ZeroHeight.
- O trabalho considera o ambiente técnico real (Expo / React Native) para garantir viabilidade.

---

## 3. Ferramentas

| Ferramenta | Papel | Observação |
|---|---|---|
| **Figma** | Ambiente de **criação e aplicação** | Arquivo sendo refeito para os novos padrões. Ver [[07-figma-padroes-e-tokens]] e [[08-regras-tecnicas-figma-api-mcp]] |
| **ZeroHeight** | **Fonte de verdade de design** e documentação | Prevista para a virada de chave |
| **Expo / React Native** | Ambiente técnico dos apps | Define a viabilidade das decisões. Ver [[04-arquitetura-e-estrutura-do-ds]] |
| **Cursor** | Ambiente de código com integração MCP com o Figma | Regras de nomes via `.cursorrules`. Ver [[08-regras-tecnicas-figma-api-mcp]] |
| **Storybook** | Vitrine técnica dos componentes, web e on-device | Existe hoje. Relação com ZeroHeight em aberto |
| **FigJam** | Diagramas de fluxo de navegação | Citado como apoio para fluxos |
| **Claude (Projects)** | Apoio ao trabalho de design system, com instruções e arquivos de contexto do projeto | Ver seção 6 |
| **Obsidian** | Base de conhecimento pessoal alimentada por esta extração, com método Karpathy | Ver seção 8 |

**Figma e ZeroHeight se retroalimentam.** O Figma cria e aplica. O ZeroHeight documenta e é a fonte de verdade de design.

---

## 4. Regras de trabalho no Figma

Resumo operacional. Detalhes em [[07-figma-padroes-e-tokens]] e [[08-regras-tecnicas-figma-api-mcp]].

1. **Nada hardcoded.** Cores, espaçamentos, bordas, opacidade e tipografia sempre vinculados a variáveis ou estilos.
2. **Sem variável, sinalizar antes.** Valor que não existe nos tokens é levado ao TL antes de entregar. Vira decisão de criar (ou não) um token novo.
3. **Nome antes de entregar.** Componente novo segue `Categoria/NomeDoComponente`.
4. **Telas novas** entram em `Screens` do app correspondente, com prefixo `[NEW]` se não existirem no inventário.
5. **Alteração em componente existente** é registrada no `Changelog`.
6. **Identificar por node-id**, não só por nome, sobretudo durante o rebrand.

---

## 5. Princípios de comunicação no dia a dia

- Trabalho e documentação em **português**.
- Respostas **curtas e diretas** quando a pergunta for direta, sem texto de preenchimento.
- Linguagem profissional e clara, **acessível também a pessoas não técnicas**. Jargão só com explicação.
- Quando houver risco de decisão inviável tecnicamente ou inconsistente com as diretrizes da LyraUI/WeCareU, **apontar antes de continuar**.
- Preferência por **ouvir um "não"** e corrigir o rumo do que receber concordância que mantém a decisão no lugar errado.
- **Não repetir contexto** já estabelecido.
- Ao dar opções, **indicar a melhor e explicar o porquê**, sem devolver a decisão sem opinião.
- **Sem suposições:** se faltar informação para uma resposta precisa, perguntar antes.
- Explicações com **narrativa única** e construção de entendimento conceitual, em vez de listas soltas de exemplos ou definições rasas.

---

## 6. Trabalho com o agente de IA (Claudinho)

### Persona e instruções do projeto

- O agente do projeto se chama **Claudinho**.
- As instruções do projeto ficam em Claude Projects, junto dos documentos de contexto.
- O agente **não edita** as instruções do projeto diretamente. Para ajustá-las, a frase combinada é: "Quer que eu te envie as instruções corrigidas do projeto agora".

### Sugestões contextuais de ferramentas

O agente sugere um próximo passo **só quando o gatilho é evidente**, ao final da resposta, separado por uma linha, no formato:

> 🛠️ Posso ajudar com mais um passo — [descrição do que pode ser feito e por quê agrega valor agora]

| Gatilho | Sugestão |
|---|---|
| Tokens ou cores sendo definidos | Revisão de acessibilidade (contraste e legibilidade) |
| Componente especificado ou fechado | Arquivo de especificações técnicas para o dev, ou levar o componente ao Figma |
| Microcopy ou texto de interface indefinido | Apoio na escrita alinhada à voz e aos tons. Ver [[10-voz-e-tons]] |
| Fluxo de navegação ou estrutura de telas descrita | Diagrama visual do fluxo no FigJam |
| Componente ou tela pronto para documentar | Rascunho de documentação estruturado para o ZeroHeight |
| Decisão de design que impacta o Figma | Aplicação direta no Figma via integração |
| Elemento existente no Figma que embasaria uma decisão | Leitura do Figma para trazer o contexto real |
| Novo padrão, componente ou diretriz sendo criado | Auditoria de consistência com o design system existente |
| Entrega ou fechamento de ciclo | Atualização de status para comunicar o avanço ao time |

### Alerta de salvar contexto

O agente avisa, ao final da resposta e de forma discreta, no formato:

> 💾 Hora de salvar contexto — [motivo em uma linha]

Condições para avisar:
- Uma decisão de design relevante foi tomada e fechada (token, componente, padrão, estrutura).
- Uma etapa do DS foi concluída ou gerou um output.
- Um documento importante foi criado ou definido (diretriz, especificação, fluxo).
- A conversa acumulou definições que, se perdidas, causariam retrabalho significativo.

Não avisar a cada resposta: só quando algo precisa ser preservado fora do histórico do chat.

---

## 7. Recursos do Claude explorados

Foram explorados as diferenças entre **Chat, Projects, Artifacts, Cowork e Dispatch**. Projects é o recurso em uso ativo neste trabalho, por reunir instruções e arquivos de contexto fixos.

---

## 8. Esta base de conhecimento (Obsidian)

- Base montada com o **método Karpathy**, alimentada por extração do projeto dividida em **14 temas**, um arquivo por tema.
- Todo arquivo começa com o **aviso de versionamento (extração via IA - Claude)**: é um snapshot, pode divergir do repositório oficial e as diretrizes arquiteturais devem ser validadas em caso de conflito.
- Os arquivos usam links `[[...]]` entre si. Se renomear algum, ajustar os links.

Mapa:

| # | Arquivo |
|---|---|
| 01 | [[01-visao-geral-lyraui]] |
| 02 | [[02-contexto-wecareu]] |
| 03 | [[03-estado-atual-do-produto]] |
| 04 | [[04-arquitetura-e-estrutura-do-ds]] |
| 05 | [[05-sistema-de-tema]] |
| 06 | [[06-catalogo-e-inventario-legado]] |
| 07 | [[07-figma-padroes-e-tokens]] |
| 08 | [[08-regras-tecnicas-figma-api-mcp]] |
| 09 | [[09-fundamentos-visuais]] |
| 10 | [[10-voz-e-tons]] |
| 11 | [[11-escrita-e-ortografia]] |
| 12 | [[12-principios-de-design]] |
| 13 | [[13-glossario]] |
| 14 | [[14-ferramentas-e-forma-de-trabalho]] |

---

## 9. Divergências e pontos em aberto

- **Fonte de verdade.** Dois documentos usam o termo de formas diferentes: a LyraUI se descreve como Única Fonte da Verdade (SSoT) de diretrizes, tokens e padrões de código. As instruções do projeto tratam o **ZeroHeight** como fonte de verdade de design. Definir o que cada uma cobre.
- **Storybook x ZeroHeight.** Relação ainda em decisão aberta. Não assumir como definida. Ver [[04-arquitetura-e-estrutura-do-ds]].
- **Preferências gerais x instruções do projeto.** As preferências gerais da conta usam critérios genéricos para o alerta de salvar contexto (banco, schema, arquitetura). As instruções do projeto são específicas de design (token, componente, padrão). Dentro deste projeto, vale a versão do projeto.
- **Handoff e documentação.** O fluxo de entrega ao desenvolvimento (especificação técnica) é sugerido pelo agente, mas não há processo formal descrito nos documentos.
- **Integração Figma MCP.** A regra de transformar nomes com barra em objetos aninhados ainda não tem texto definido. Ver [[08-regras-tecnicas-figma-api-mcp]].

---

## Links

Anterior: [[13-glossario]] · Início: [[01-visao-geral-lyraui]]
