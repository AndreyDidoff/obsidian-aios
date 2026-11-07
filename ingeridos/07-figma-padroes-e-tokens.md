> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 07 · Figma: padrões e tokens

Tags: #lyraui #figma #tokens #nomenclatura #changelog

---

## 1. Status

- **LyraUI (alvo, em discovery, não implementada no código):** estes padrões descrevem o Figma **como ele deve ficar** na virada de chave. O Figma está sendo refeito para esta padronização.
- **WeCareU (app em produção):** os pacotes ainda se chamam `@wecareu/*`. As tabelas abaixo usam o escopo alvo `@lyra-ui/*`.
- Contexto em [[01-visao-geral-lyraui]]. Regras técnicas de execução (API/MCP) em [[08-regras-tecnicas-figma-api-mcp]].

---

## 2. Por que padronizar

Sem padrão, Figma e código divergem:
- O mesmo componente vira coisas diferentes.
- Valores entram "na mão".
- Não há rastro de qual peça do Figma corresponde a qual componente.

A padronização mantém Figma e design system "falando a mesma língua". Esta é uma das regras que a entidade LyraUI detém.

---

## 3. Nomenclatura de componentes

Convenção: `Categoria/NomeDoComponente`. Cada nome mapeia direto para um pacote.

| Nome no Figma | Pacote (alvo) |
|---|---|
| `Button/Gradient` | `@lyra-ui/button-gradient` |
| `Button/Link` | `@lyra-ui/button-link` |
| `Button/Close` | `@lyra-ui/button-close` |
| `Input/Text` | `@lyra-ui/input-text` |
| `Input/Masked` | `@lyra-ui/input-masked` |
| `Input/Select` | `@lyra-ui/select` |
| `Input/DatePicker` | `@lyra-ui/date-picker` |
| `Media/ImageUpload` | `@lyra-ui/image-upload` |
| `Feedback/Loading` | `@lyra-ui/loading` |
| `Typography/Text` | `@lyra-ui/text` (hoje `text-wcu`, nome candidato a revisão no rebrand) |
| `Icon` | `@lyra-ui/icons` |
| `Foundation/Theme` | `@lyra-ui/theme` |
| `Foundation/Tokens` | `@lyra-ui/tokens` |

**Regra:** ao criar um componente novo no Figma, aplicar o nome seguindo a convenção **antes** de entregar a demanda.

---

## 4. Estrutura de páginas

```
📁 Design System
   └── Components       ← componentes do DS, com variantes
   └── Tokens           ← paleta de cores, espaçamentos, tipografia

📁 [Nome do App] (CLIENT / WORKER / WEB_ADMIN)
   └── Screens          ← telas completas
   └── Flows            ← fluxos de navegação
   └── Archive          ← telas antigas / descartadas
```

**Regras:**
- Telas novas sempre entram em `Screens` do app correspondente.
- `Archive` é histórico. **Não é fonte de verdade.**

> **Divergência a validar.** O arquivo Figma atual tem mais de 30 páginas organizadas por fundamentos, componentes base, moléculas e utilitários (ver [[08-regras-tecnicas-figma-api-mcp]]). Essa organização não é igual à estrutura-alvo acima. Como o Figma está sendo refeito, tratar a estrutura acima como alvo e confirmar se a reorganização já foi feita antes de usá-la como referência.

---

## 5. Variáveis do Figma alinhadas aos tokens

As variáveis de design do Figma usam **os mesmos nomes** dos tokens do pacote de tokens. Isso mantém Figma e código sincronizados e elimina valores soltos.

| Token (código) | Variável (Figma) |
|---|---|
| `theme.colors.primary` | `colors/primary` |
| `theme.spacing.md` | `spacing/md` |
| `theme.radius.xxl` | `radius/xxl` |

**Regras:**
- Todo componente novo usa variáveis, **nunca valores hardcoded**.
- Valor necessário que não existe nos tokens é sinalizado ao TL **antes** de entregar. Vira decisão de criar (ou não) um token novo.

Mapeamento por propriedade, usado no trabalho diário com o Figma:

| Propriedade | Como vincular |
|---|---|
| Cores | Variável de cor, via `setBoundVariableForPaint` |
| Espaçamentos (padding, gap) | Variáveis da coleção de spacings, via `setBoundVariable` |
| Bordas (raio e espessura) | Variáveis da coleção de borders, via `setBoundVariable` |
| Opacidade | Variáveis da coleção de opacity, via `setBoundVariable` |
| Tipografia | Estilo de texto, via `textStyleId` |

Se a propriedade não tiver variável correspondente no arquivo, **sinalizar antes** de usar valor fixo. IDs das coleções e detalhes de API em [[08-regras-tecnicas-figma-api-mcp]].

> **Divergência a validar.** Nos exemplos acima as variáveis aparecem no singular (`spacing/md`, `radius/xxl`), mas as coleções usadas no arquivo atual chamam-se **spacings**, **paddings** e **borders**. Confirmar o nome oficial antes de padronizar, porque o alinhamento nome a nome entre Figma e código depende disso.

---

## 6. Telas novas x existentes

- Telas recebem o **mesmo nome** do inventário. Exemplos: `Profile`, `PersonalData`, `NotificationSettings`. Inventário em [[06-catalogo-e-inventario-legado]].
- Tela nova que ainda não existe no inventário recebe o prefixo `[NEW]`:

```
[NEW] SecurityCenter
[NEW] ReviewScreen
```

---

## 7. Changelog de componentes

Toda alteração em componente existente é registrada em uma página `Changelog` no Figma.

Formato:

```
[DATA] | [COMPONENTE] | [TIPO DE ALTERAÇÃO] | [DESCRIÇÃO]
Ex: 2026-05-07 | Button/Gradient | Layout | Padding interno aumentado de 12 para 16px
```

Serve para:
- Dar rastreabilidade do que mudou e quando.
- Sinalizar que o componente correspondente no código precisa ser atualizado.

---

## 8. Identificador estável de componente

- Cada componente no Figma tem um **ID de nó único** (`node-id` na URL ao copiar o link).
- Esse ID **não muda quando o componente é renomeado**.
- É a forma mais confiável de identificar um componente, mais que o nome.
- Útil sobretudo durante o rebrand, quando os nomes vão mudar.

---

## 9. Checklist antes de entregar uma demanda

1. Nome do componente segue `Categoria/NomeDoComponente`.
2. Nenhum valor hardcoded: cores, espaçamentos, bordas, opacidade e tipografia vinculados.
3. Valores sem token foram sinalizados ao TL.
4. Tela nova está em `Screens` do app correto, com prefixo `[NEW]` se não existir no inventário.
5. Alteração em componente existente foi registrada no `Changelog`.

---

## 10. Pontos em aberto

- Nome final de `Typography/Text` (`text-wcu` → `@lyra-ui/text`).
- Singular x plural no nome das coleções e variáveis.
- Estado real da reorganização de páginas do arquivo Figma.
- Nomes `WEB_ADMIN` e demais apps web na estrutura de páginas: hoje só CLIENT e WORKER existem como apps.

---

## Links

Anterior: [[05-sistema-de-tema]] · Próximos: [[08-regras-tecnicas-figma-api-mcp]] · [[09-fundamentos-visuais]]
