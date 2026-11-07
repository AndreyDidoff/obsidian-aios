> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 04 · Arquitetura e estrutura do Design System

Tags: #lyraui #arquitetura #atomic-design #tokens #definition-of-done

---

## 1. Status

- **LyraUI** (este documento): em discovery, **não implementada no código**. Construída em paralelo ao MVP, entra como versão futura do app. Tudo abaixo descreve o **alvo** da "virada de chave".
- **WeCareU** (app em produção): hoje os componentes vivem em `@wecareu/*`. Esse é o **legado** a ser migrado. Inventário em [[06-catalogo-e-inventario-legado]].
- Contexto geral em [[01-visao-geral-lyraui]].

---

## 2. A virada de chave: escopos de pacote

A virada de chave combina três mudanças: rebrand de escopo, novo Atomic Design e novos repositórios.

| Escopo | Contém | Status |
|---|---|---|
| `@lyra-ui/*` | Design System e Biblioteca de componentes (sub-atomic, atoms, molecules, organisms) | Alvo, em migração a partir de `@wecareu/*` |
| `@wecareu/*` | Templates e pages universais (compartilhados entre apps) e tudo que **não** é design system nem biblioteca de componentes | Permanece, com escopo reduzido |

- Hoje: todos os componentes estão em `@wecareu/*`.
- Na virada: tudo que for design system e biblioteca de componentes passa para `@lyra-ui/*`.
- Os sufixos tendem a se manter 1:1. Exemplo: `@wecareu/button-gradient` → `@lyra-ui/button-gradient`.
- Alguns nomes herdados da marca antiga podem ser revistos. Exemplo: `text-wcu`.

---

## 3. Atomic Design: novo mapeamento em 4 camadas

| Camada Atomic | Pertence a | Escopo | Portável entre apps? |
|---|---|---|---|
| Sub-atomic, Atoms | LyraUI, Design System | `@lyra-ui/*` | Sim |
| Molecules, Organisms | LyraUI, Biblioteca de Componentes | `@lyra-ui/*` | Sim |
| Templates, Pages universais | WeCareU compartilhado | `@wecareu/*` | Sim (todos os apps) |
| Atomic Design do app (qualquer nível, específico) | Dentro do próprio app | Não se aplica | **Nunca** portado para outro app |

Leitura:
- A LyraUI cobre do sub-atomic até organisms.
- Acima disso, o que serve a todos os apps é WeCareU universal.
- O que é específico de um app fica no app e nunca sai dele.

Definições relacionadas (ver [[13-glossario]]):
- **Base Components:** componentes elementares e indivisíveis, como ícones, botões e campos de texto.
- **Components:** componentes mais complexos que reúnem Base Components e tokens, como headers, cards e carrosséis.

---

## 4. Hierarquia de dependências

A base é hierárquica: nada de baixo depende do que está acima.

```
tokens → theme → componentes (atoms → organisms) → templates/pages → apps
```

| Nível | O que é |
|---|---|
| **tokens** | Valores brutos de design (cores, espaçamentos, raios, tipografia). Não dependem de nada |
| **theme** | Consome tokens e entrega o tema pronto |
| **componentes** | Consomem theme e tokens |
| **templates/pages universais** | Compõem componentes |
| **apps** | Consomem tudo acima e têm seu próprio atomic design interno |

Implicação prática: quanto mais abaixo na cadeia (tokens, theme, icons), mais reutilizado o item e **maior o impacto de mudá-lo**. O mapa de dependências dos componentes atuais está em [[06-catalogo-e-inventario-legado]].

---

## 5. Sistema de tema (resumo)

- Tema centralizado no pacote de tema da LyraUI.
- Existem light e dark, mas o tema **não é exposto** à pessoa usuária.
- CLIENT usa somente light. WORKER usa somente dark. É decisão de design intencional.
- Regra inegociável: **nunca** cor, espaçamento ou tipografia hardcoded. Sempre via tokens do tema.

Detalhes em [[05-sistema-de-tema]].

---

## 6. Convenções de nomenclatura

| Elemento | Convenção | Exemplo |
|---|---|---|
| Componente | PascalCase | `ButtonGradient` |
| Pacote / diretório | camelCase | `button-gradient` |
| Interface de props | PascalCase + `Props` | `ButtonGradientProps` |
| Variável booleana | Verbo auxiliar | `isLoading`, `hasError` |
| Textos visíveis ao usuário | Sempre via i18n | Não se aplica |

> **Inconsistência a validar.** A fonte diz "camelCase" para pacote/diretório, mas o exemplo (`button-gradient`) está em **kebab-case**, assim como todos os pacotes do catálogo. Provável erro de rótulo na fonte. Confirmar com o TL antes de tratar como regra.

Nomenclatura dos componentes no Figma: ver [[07-figma-padroes-e-tokens]].

---

## 7. Definition of Done de um componente

Um componente só é "pronto" quando atende a **todos** os itens:

1. Integrado ao tema, sem cor ou espaçamento hardcoded.
2. Tipagem completa, com documentação nas props públicas.
3. Stories cobrindo estado padrão, variantes e estados (disabled, loading, error).
4. Testes com no mínimo **80% de cobertura**.
5. Acessibilidade implementada (role, label e estado acessível).
6. Documentação com exemplos de uso.
7. Exports públicos corretos: só o componente e seus tipos, sem helpers internos vazando.

Todo componente novo também entra na vitrine com seus estados e variantes. Isso faz parte do "pronto".

---

## 8. Vitrine e documentação

| Item | Situação |
|---|---|
| Storybook (web e on-device, dentro de um app de playground) | Vitrine dos componentes **hoje** |
| ZeroHeight | Documentação de design prevista para a virada |
| Relação Storybook x ZeroHeight | **Decisão aberta.** Não assumir como definida |

---

## 9. Pontos em aberto

- Relação entre Storybook e ZeroHeight.
- Nome final do componente de texto (`text-wcu` → `@lyra-ui/text`, a confirmar).
- Convenção real de nome de pacote/diretório (camelCase ou kebab-case).
- Quais telas de perfil e configuração viram templates/pages universais em `@wecareu/*` (o catálogo as aponta como candidatas).
- Data e critério da virada de chave.

---

## Links

Anterior: [[01-visao-geral-lyraui]] · Próximos: [[05-sistema-de-tema]] · [[06-catalogo-e-inventario-legado]] · [[07-figma-padroes-e-tokens]]
