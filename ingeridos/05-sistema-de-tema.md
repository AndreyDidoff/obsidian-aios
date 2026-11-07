> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 05 · Sistema de tema

Tags: #lyraui #tema #light-mode #dark-mode #tokens

---

## 1. Status

- **WeCareU (app em produção):** já existe `@wecareu/theme`, que consome `@wecareu/tokens` e entrega o tema pronto. CLIENT roda em light e WORKER em dark.
- **LyraUI (alvo, em discovery, não implementada no código):** o tema passa a ser centralizado no pacote `@lyra-ui/theme`, com os tokens redefinidos pelo novo sistema de cores. Ver [[09-fundamentos-visuais]].
- Contexto em [[01-visao-geral-lyraui]] e posição do tema na hierarquia em [[04-arquitetura-e-estrutura-do-ds]].

---

## 2. Decisão de produto

| Regra | Detalhe |
|---|---|
| Temas existentes | **Light** e **dark** |
| Exposição ao usuário | O tema **não é exposto**. A pessoa usuária não escolhe |
| CLIENT | Usa **exclusivamente light mode** |
| WORKER | Usa **exclusivamente dark mode** |
| Motivo | Diferença **intencional**: separa visualmente os dois apps. É traço de identidade de cada produto, não acaso técnico |

Consequência de design: não existe "alternar tema" nas configurações. Cada app é desenhado e validado em um único tema.

---

## 3. Regra inegociável

**Nunca** usar cor, espaçamento ou tipografia hardcoded. Tudo vem dos tokens, via tema.

Aplicação no Figma (ver [[07-figma-padroes-e-tokens]] e [[08-regras-tecnicas-figma-api-mcp]]):
- Todo componente novo usa variáveis, nunca valores fixos.
- Valor necessário que não existe nos tokens é sinalizado ao TL **antes** de entregar. Vira decisão de criar (ou não) um token novo.

Aplicação no código (Definition of Done): o componente só é "pronto" se estiver integrado ao tema. Ver [[04-arquitetura-e-estrutura-do-ds]].

---

## 4. Como o tema se encaixa na cadeia

```
tokens → theme → componentes → templates/pages → apps
```

- `theme` depende de `tokens`.
- Ícones, texto e botões dependem de `theme`.
- Mudar o tema afeta toda a cadeia acima dele, então tem alto impacto.

Mapa completo de dependências em [[06-catalogo-e-inventario-legado]].

---

## 5. Relação com o sistema de cores (resumo)

Detalhes completos em [[09-fundamentos-visuais]]. O que impacta o tema:

- Escalas de 8 passos (100 a 800), ancoradas no 500, com matiz e saturação HSL constantes e curva de luminosidade proporcional.
- O tema light/dark usa **espelho simétrico**: 100↔800, 200↔700, e assim por diante.
- O fundo do dark mode (`#0B0C13`) é tratado como **token especial**, fora da escala numerada.
- Cada paleta tem grade de contraste WCAG e mapeamento light/dark documentados.

---

## 6. Telas por tema

| App | Tema | Telas (catálogo atual, legado) |
|---|---|---|
| CLIENT (cliente) | Light | Welcome, SignIn, Register, Home, Listing, Schedules, Profile e outras |
| WORKER (Artista) | Dark | Welcome, SignIn, Register, Home, Orders, Schedules, Plans (premium), Profile e outras |

CLIENT e WORKER compartilham muitas telas de perfil e configuração com a mesma estrutura, em temas opostos. Por isso são candidatas a templates/pages universais em `@wecareu/*`, já que o tema muda a aparência sem mudar a estrutura. Lista completa em [[06-catalogo-e-inventario-legado]].

---

## 7. Pontos em aberto

- Como o tema trata um possível futuro app de Empresas (`ui-business`) ou de salões: sem decisão registrada. Hoje só existem CLIENT e WORKER.
- Se cada app terá paleta/tema próprio no novo `@lyra-ui/theme` ou se a diferença será apenas light x dark: não detalhado nas fontes.
- Revisão de contraste do dark mode para o WORKER, usado durante o expediente do Artista, quando a leitura é rápida (ver [[11-escrita-e-ortografia]] sobre leitura dinâmica).

---

## Links

Anterior: [[04-arquitetura-e-estrutura-do-ds]] · Próximos: [[06-catalogo-e-inventario-legado]] · [[07-figma-padroes-e-tokens]]
