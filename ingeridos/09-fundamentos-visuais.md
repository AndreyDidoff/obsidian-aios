> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 09 · Fundamentos visuais

Tags: #lyraui #tipografia #icones #cores #wcag #tokens

---

## 1. Status

- **LyraUI (alvo, em discovery, não implementada no código):** tudo abaixo é definição de design para a LyraUI. Nada disso está em produção.
- **WeCareU (app em produção):** o app atual usa os tokens, o tema e os ícones de `@wecareu/*`. Os valores atuais podem diferir dos definidos aqui. Inventário em [[06-catalogo-e-inventario-legado]].
- Este tema é o que alimenta os tokens. Cadeia em [[04-arquitetura-e-estrutura-do-ds]] e tema em [[05-sistema-de-tema]].

---

## 2. Tipografia

### Situação atual dos fundamentos

| Uso | Fonte | Situação |
|---|---|---|
| Títulos (headings) | **Livvic** | Estabelecida |
| Corpo e labels | A definir | Em análise |

### Pontos de decisão

- Livvic foi classificada como **fonte de display com x-height baixa**, portanto **inadequada para tamanhos pequenos**. Por isso ela fica restrita aos títulos.
- Para corpo e labels, foram identificadas duas opções compatíveis: **Plus Jakarta Sans** e **DM Sans**.
- Não há escolha final registrada entre as duas.

### Regras de uso

- Tipografia entra sempre via estilo de texto (`textStyleId`), nunca com fonte, tamanho e peso soltos. Ver [[08-regras-tecnicas-figma-api-mcp]].
- Convenção de nomes de estilo com hierarquia por barra. Exemplo: `headings/desktop/font-heading-sm`.
- Componente de texto: hoje `@wecareu/text-wcu`, alvo `@lyra-ui/text` (a confirmar). Nome no Figma: `Typography/Text`.

---

## 3. Ícones

### Direção do estilo

- Estilo identificado: **outline dominante, moderno**.

### Bibliotecas avaliadas

| Biblioteca | Situação | Observação |
|---|---|---|
| **Phosphor Icons** | **Candidata principal** | Qualidade estética, múltiplos pesos, suporte a React Native |
| Tabler | Alternativa | Citada como opção |
| Lucide | Alternativa | Citada como opção |

### Exceção fixa

- O ícone do **Pix** (meio de pagamento brasileiro) exige um **SVG avulso**, independentemente da biblioteca escolhida.

### Estado atual

- Hoje existe `@wecareu/icons` (sistema de ícones SVG). Alvo: `@lyra-ui/icons`. Nome no Figma: `Icon`.
- Não há decisão final registrada sobre a biblioteca. Phosphor é a recomendação, não uma decisão fechada.

---

## 4. Sistema de cores

### Paletas definidas

| Paleta | Valor-base | Observação |
|---|---|---|
| **Primary** | `#712FC1` (roxo) | |
| **Secondary** | `#D85A30` (coral) | Revisada: era violeta e foi trocada para coral para evitar conflito de matiz com a Primary |
| **Tertiary** | `#FF0098` (magenta) | |
| **Neutral** | Escala de 12 passos | Ancorada em quatro cores já existentes no app |

Token especial: o fundo do dark mode, `#0B0C13`, é tratado **fora da escala numerada**.

### Método de construção das escalas

- Escalas de **8 passos (100 a 800)**, ancoradas no **500**.
- Matiz e saturação HSL **constantes** ao longo da escala.
- Curva de luminosidade **proporcional**.
- Tema light/dark por **espelho simétrico**: 100↔800, 200↔700, 300↔600, 400↔500.

### Entregas já concluídas

- Grades de contraste **WCAG** para cada paleta.
- Mapeamentos light/dark espelhados.
- Documentação de tokens de cada paleta.

### Observações

- A Neutral tem 12 passos, enquanto as demais seguem o método de 8. Isso é coerente com a ancoragem em cores existentes, mas o mapeamento de espelho da Neutral não está descrito nas notas.
- Os valores hexadecimais dos demais passos de cada paleta e as grades de contraste **não estão nas fontes disponíveis**. Devem ser extraídos do Figma ou do ZeroHeight.

---

## 5. Como isso vira token

1. Os valores das paletas, tipografia e ícones são definidos aqui.
2. Viram **tokens** (`@lyra-ui/tokens`), sem dependência de nada.
3. O **theme** consome os tokens e entrega light e dark. Ver [[05-sistema-de-tema]].
4. No Figma, as variáveis têm os mesmos nomes dos tokens. Ver [[07-figma-padroes-e-tokens]].

Regra inegociável: nenhuma cor, espaçamento ou tipografia hardcoded.

---

## 6. Pontos em aberto

- Fonte de corpo e labels: Plus Jakarta Sans ou DM Sans.
- Biblioteca de ícones: confirmar Phosphor.
- Tabela completa de hex por passo e grades WCAG (não disponíveis nas fontes desta extração).
- Espelho light/dark da escala Neutral de 12 passos.
- Coerência com as cores já usadas no app em produção (as quatro cores âncora da Neutral).

---

## Links

Anterior: [[08-regras-tecnicas-figma-api-mcp]] · Próximos: [[10-voz-e-tons]] · [[11-escrita-e-ortografia]]
