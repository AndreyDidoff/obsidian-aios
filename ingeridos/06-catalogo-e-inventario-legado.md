> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 06 · Catálogo e inventário legado

Tags: #wecareu #lyraui #legado #migracao #componentes #telas

---

## 1. Status e como ler

- **WeCareU (o que existe hoje):** este documento é o inventário do que **já existe** em `@wecareu/*`. É o **legado** que será migrado.
- **LyraUI (o que será):** em discovery, **não implementada no código**, construída em paralelo ao MVP. Ela ainda não tem catálogo próprio.
- Este catálogo é o **ponto de partida**, não o alvo. Usar como "o que temos para migrar", **nunca** como o catálogo final da LyraUI.
- Regras da migração: nomes de sufixo tendem a se manter, o escopo muda de `@wecareu/*` para `@lyra-ui/*`, e alguns nomes herdados da marca (ex.: `text-wcu`) podem ser revistos. Ver [[04-arquitetura-e-estrutura-do-ds]].

---

## 2. Componentes do Design System (atoms e sub-atomic)

| Componente atual | Alvo | O que é |
|---|---|---|
| `@wecareu/tokens` | `@lyra-ui/tokens` | Design tokens (cores, espaçamentos, raios, tipografia). Base de tudo |
| `@wecareu/theme` | `@lyra-ui/theme` | Sistema de temas. Consome os tokens e entrega o tema pronto |
| `@wecareu/icons` | `@lyra-ui/icons` | Sistema de ícones SVG |
| `@wecareu/text-wcu` | `@lyra-ui/text` (a confirmar) | Componente de texto customizado (tipografia) |
| `@wecareu/button-gradient` | `@lyra-ui/button-gradient` | Botão com gradiente |
| `@wecareu/button-link` | `@lyra-ui/button-link` | Botão em estilo link |
| `@wecareu/button-close` | `@lyra-ui/button-close` | Botão redondo de fechar |
| `@wecareu/loading` | `@lyra-ui/loading` | Overlay de loading com animação Lottie |
| `@wecareu/input-text` | `@lyra-ui/input-text` | Campo de texto controlado, com ícones e feedback de erro |
| `@wecareu/input-masked` | `@lyra-ui/input-masked` | Campo de texto com máscara dinâmica |
| `@wecareu/select` | `@lyra-ui/select` | Seleção com modal, busca e múltipla seleção |
| `@wecareu/date-picker` | `@lyra-ui/date-picker` | Seletor de data: única, range e múltiplas datas |
| `@wecareu/image-upload` | `@lyra-ui/image-upload` | Upload de imagem com preview e conversão para base64 |

Total: **13 pacotes** no design system atual. Os nomes dos componentes correspondentes no Figma estão em [[07-figma-padroes-e-tokens]].

---

## 3. Mapa de dependências

Base: `tokens → theme`. A partir daí, os demais compõem.

| Componente | Depende de |
|---|---|
| `theme` | `tokens` |
| `icons`, `text` e botões | `theme` (alguns também de `icons`) |
| `input-text` | `icons`, `theme`, `tokens` |
| `input-masked` | Construído sobre `input-text` |
| `select` | `icons`, `theme`, `tokens` |
| `date-picker` | `button-gradient`, `button-link`, `icons`, `text`, `theme`, `tokens`. **É o mais composto** |
| `image-upload` | `icons`, `loading`, `theme`, `tokens` |

Leitura: quanto mais "para baixo" na cadeia (tokens, theme, icons), mais reutilizado o item e **maior o impacto de mudá-lo**.

Implicações práticas, derivadas do mapa (leitura de apoio, não oficial):
- Mexer em `tokens` ou `theme` afeta todos os 13 pacotes.
- `icons` impacta quase tudo. A troca da biblioteca de ícones (ver [[09-fundamentos-visuais]]) é mudança de alto impacto.
- `input-masked` herda qualquer mudança de `input-text`.
- `date-picker` é o melhor candidato a teste de regressão da migração, por reunir mais dependências.

---

## 4. Biblioteca de componentes (molecules e organisms)

Camada acima do design system: fluxos reutilizados entre apps. Também migra para `@lyra-ui/*`.

| Componente atual | Alvo | O que inclui |
|---|---|---|
| `@wecareu/auth-flow` | `@lyra-ui/auth-flow` | Fluxo de autenticação centralizado: Login, Register, ForgotPassword, BiometricAuth e TokenManager. Apoia-se em botões, input, loading, texto e tema |

Observação: `auth-flow` é o **único** item desta camada no inventário atual.

---

## 5. Telas do app CLIENT (cliente)

**Tema: light mode.** Ver [[05-sistema-de-tema]].

| Grupo | Telas |
|---|---|
| Autenticação e entrada | Welcome, GetPermissions, SignIn, Register (3 etapas), SecondStage, ForgotPassword, ResetPassword, LoggedOutAddressSelection |
| Núcleo (logado) | Home, Listing (listagem de Artistas), Schedules, Profile, ChatSchedules |
| Perfil e configurações | PersonalData, ChangePassword, ManageAddresses, NotificationSettings, AboutApp, TermsOfUse, PrivacyPolicy |

---

## 6. Telas do app WORKER (Artista)

**Tema: dark mode.**

| Grupo | Telas |
|---|---|
| Autenticação e entrada | Welcome, SignIn, Register, ForgotPassword, ResetPassword, SecondStage |
| Núcleo (logado) | Home (condicional, dirigida por máquina de estados), Orders (pedidos e agenda unificada), Schedules, Plans (premium), Profile, ChatSchedules |
| Perfil e configurações | PersonalData, ChangePassword, ManageAddresses, NotificationSettings, AboutApp, TermsOfUse, PrivacyPolicy |

---

## 7. Comparativo CLIENT x WORKER

| Tela | CLIENT | WORKER |
|---|---|---|
| Welcome, SignIn, ForgotPassword, ResetPassword, SecondStage | ✅ | ✅ |
| Register | ✅ (3 etapas) | ✅ |
| GetPermissions, LoggedOutAddressSelection | ✅ | ❌ |
| Home | ✅ | ✅ (condicional, máquina de estados) |
| Listing | ✅ | ❌ |
| Orders | ❌ | ✅ |
| Plans (premium) | ❌ | ✅ |
| Schedules, Profile, ChatSchedules | ✅ | ✅ |
| Perfil e configurações (7 telas) | ✅ | ✅ |

---

## 8. Observações de design

- CLIENT e WORKER compartilham muitas telas de perfil e configuração **com a mesma estrutura**, em temas opostos (light x dark).
- Essas telas são **candidatas a templates/pages universais** em `@wecareu/*` na nova arquitetura. Ver [[04-arquitetura-e-estrutura-do-ds]].
- A diferença de tema entre apps é **intencional** e é traço de identidade de cada produto.
- Telas novas que não estão neste inventário recebem o prefixo `[NEW]` no Figma. Ver [[07-figma-padroes-e-tokens]].

---

## 9. Divergências e pontos em aberto

- **`ChatSchedules`:** existe nos dois apps, mas o produto não tem chat hoje. Confirmar o que a tela faz. Ver [[03-estado-atual-do-produto]].
- **`@wecareu/text-wcu`:** destino `@lyra-ui/text` ainda a confirmar.
- **Menos de 20 itens no inventário atual** (13 pacotes de DS e 1 de biblioteca). O Figma tem mais de 30 páginas, incluindo moléculas e utilitários. Não há mapeamento entre as moléculas do Figma e os pacotes de código. Ver [[08-regras-tecnicas-figma-api-mcp]].
- **Quais telas viram templates universais:** o catálogo só as aponta como candidatas.
- **Telas de salão e Empresas:** inexistentes. Ver [[02-contexto-wecareu]].
- **Ordem e critério da migração:** não definidos nas fontes. A seção 3 apenas indica onde o impacto é maior.

---

## Links

Anterior: [[03-estado-atual-do-produto]] · Próximos: [[12-principios-de-design]] · [[13-glossario]]
