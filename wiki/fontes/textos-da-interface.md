---
tipo: fonte
arquivo: "ingeridos/Textos da interface.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Textos da interface"]
---

# Textos da interface

Volta para [[panorama-do-design-system]]. Peça TextWcu: o texto padronizado de uma tela. Pede à [[identidade-visual]] a Livvic, o tamanho, o peso, a altura da linha e a cor do modo.

**Pé:** Parcial. `@wecareu/text-wcu` **0.2.4**. Existe, entra numa tela, tem demonstração e teste. O teste confere se a frase aparece. Não confere cor, tamanho nem peso. Por isso não é Pronto.

## O que a pessoa vê

Quatro papéis. Sem escolha, o papel é corpo e a cor é a principal. O alinhamento parte à esquerda.

| Papel | Pontos | Peso | Família |
|---|---|---|---|
| Título | 18 | seminegrito | LivvicSemiBold |
| Rótulo | 14 | seminegrito | LivvicSemiBold |
| Corpo | 16 | regular | Livvic |
| Legenda | 12 | regular | Livvic |

O título desta peça é o título médio (18), não o de 20 nem o de impacto de 32. A escala maior (display e os outros títulos) fica só na identidade. O rótulo aqui é só o texto. O campo está em [[campos-de-formulario]]. O botão está em [[acoes]].

A cor acompanha claro e escuro. A de link é a marca (`#712fc1` / `#803ed0`) e a peça não sublinha. A inversa é a tinta oposta ao modo: branca no claro, preta no escuro. A cor desabilitada muda a tinta e não bloqueia toque.

A tela pode trocar o tamanho (12, 14, 16, 18, 20, 24 ou 32) sem trocar o papel. A altura da linha continua a do papel. O peso médio (500) não tem arquivo de fonte.

## O que falta

O teste sobe a frase e para aí. O tema simulado nele diverge da identidade: a altura de linha não bate, e a cor principal simulada é `#4b484c`, que no claro é a cor de apoio, não a principal `#2a282b`. Um painel da demonstração pinta cinzas e cores na própria página (`#fafafa`, `#1a1a1a` e outras), sem ler a identidade.

As frases das telas do app não moram aqui. Esta nota não cobre botão, campo, lista, data nem espera.

Ver [[voz-e-escrita]], [[kit-visual]].
