> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 08 · Regras técnicas do Figma (API e MCP)

Tags: #lyraui #figma #api #mcp #cursor #use_figma

---

## 1. Status

- **LyraUI (alvo, em discovery, não implementada no código):** este documento trata do arquivo Figma onde a LyraUI está sendo desenhada. O arquivo está sendo refeito para seguir os padrões de [[07-figma-padroes-e-tokens]].
- **WeCareU (app em produção):** o código dos apps ainda usa `@wecareu/*`. O Figma é o ambiente de criação, não o código.
- Este é o tema com mais conhecimento "caro de reaprender". Os IDs abaixo são do arquivo atual e **podem mudar** com a refação do Figma. Validar antes de reutilizar.

---

## 2. Arquivo Figma

| Item | Valor |
|---|---|
| File key | `cgiDSTP8mJptixfc06ErRt` |
| Página Readme | `0:1` |
| Frame principal | `35:2` |
| Tamanho | Mais de 30 páginas: fundamentos, componentes base, moléculas e utilitários |

---

## 3. Regra central: nada hardcoded

Todo valor aplicado via `use_figma` deve ser **vinculado** à variável correspondente. Nunca usar valor fixo.

| Propriedade | Como vincular |
|---|---|
| Cores | `figma.variables.setBoundVariableForPaint` |
| Padding e gap (`itemSpacing`) | `node.setBoundVariable(prop, variable)` com variáveis da coleção **spacings** |
| `cornerRadius` e espessura de borda | `node.setBoundVariable(prop, variable)` com variáveis da coleção **borders** |
| Opacidade | `node.setBoundVariable(prop, variable)` com variáveis da coleção **opacity** |
| Tipografia | `node.textStyleId` |

Se a propriedade não tiver variável correspondente no arquivo, **sinalizar antes** de usar valor fixo. Isso segue a regra de [[05-sistema-de-tema]]: valor sem token vira decisão de criar (ou não) um token novo, tomada com o TL.

---

## 4. Regras de API que custaram caro

1. **Listar páginas:** usar `figma.root.children` dentro de `use_figma`. O `get_metadata` com `node-id` retorna só o contexto do nó indicado, **não** o arquivo inteiro.
2. **Fontes:** carregar com `figma.loadFontAsync` **antes** de criar qualquer nó de texto.
3. **Valores numéricos:** nunca fixos. Sempre via variável (seção 3).
4. **Tipografia:** sempre via estilo de texto (`textStyleId`), nunca definindo fonte, tamanho e peso soltos.

---

## 5. IDs das coleções de variáveis

| Coleção | Faixa | ID de referência |
|---|---|---|
| Spacings | `quark` (4px) até `titan` (200px) | `quark`: `VariableID:14:35` |
| Paddings | `quark` (4px) até `md` (40px) | `quark`: `VariableID:14:53` · `md`: `VariableID:14:62` |
| Borders (radius) | `xxs` (4px) até `xl` | `xxs`: `VariableID:15:64` |

Limites desta tabela:
- Só tenho os IDs de ponta das faixas. Os intermediários (por exemplo, `xs`, `sm` de spacings) **não estão registrados** nas notas e devem ser lidos do arquivo.
- A coleção **opacity** é citada na regra de binding, mas **não tenho IDs** dela.
- Os nomes das coleções aparecem no plural (spacings, paddings, borders), enquanto o padrão de variáveis em [[07-figma-padroes-e-tokens]] usa o singular. Divergência em aberto.

---

## 6. Integração Figma → Cursor via MCP

- Os nomes de estilo em hierarquia com barra são **preservados** pelo MCP. Exemplo: `headings/desktop/font-heading-sm`.
- Para esses nomes virarem **objetos aninhados** no código, é preciso instruir explicitamente: no prompt ou em um arquivo `.cursorrules`. Sem a instrução, a transformação não sai correta.

Consequência prática: a convenção de nomes com barra no Figma só rende no código se houver uma regra de transformação escrita no projeto. Vale registrar essa regra junto da documentação de tokens.

---

## 7. Checklist antes de rodar um script no Figma

1. Carreguei as fontes com `loadFontAsync`?
2. Cada cor, espaçamento, borda, opacidade e texto está vinculado a variável ou estilo?
3. Existe variável para o que preciso? Se não, sinalizei ao TL antes?
4. Para listar páginas, usei `figma.root.children`?
5. Os IDs de variável que estou usando ainda existem no arquivo refeito?

---

## 8. Pontos em aberto

- IDs completos de todas as coleções, inclusive opacity.
- Conteúdo da regra `.cursorrules` para transformar nomes com barra em objetos aninhados.
- Efeito da refação do Figma sobre os IDs listados.
- Singular x plural no nome das coleções e variáveis.

---

## Links

Anterior: [[07-figma-padroes-e-tokens]] · Próximos: [[09-fundamentos-visuais]] · [[10-voz-e-tons]]
