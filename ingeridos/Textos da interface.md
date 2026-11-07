---
tipo: extração
tema: Textos da interface
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/text-wcu"]
pé: Parcial. TextWcu 0.2.4 tem demonstração e teste; o teste não confere cor, tamanho nem peso.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Textos da interface

Volta para o [[Panorama do design system]].

[[Textos da interface]] é a peça TextWcu: o texto padronizado de uma tela. Ela pede à [[Identidade visual]] a família Livvic, o tamanho, o peso, a altura da linha e a cor do modo atual.

**Pé:** Parcial. A peça existe, entra numa tela, tem demonstração e tem teste automático. O nome npm é `@wecareu/text-wcu`, versão **0.2.4**. O teste confere se a frase aparece. Não confere se a cor, o tamanho e o peso pedidos são os da identidade. Por isso o pé não é Pronto.

## O que a tela pode pedir

Quatro papéis. Se a tela não escolher, o papel é corpo e a cor é a principal. O alinhamento de partida é à esquerda.

Cada papel usa uma receita do meio da identidade, não a escala inteira. O título desta peça é o título médio (18), não o título de 20 em negrito nem o de impacto de 32.

| Papel na tela | Pontos | Peso | Altura da linha | Família |
| --- | --- | --- | --- | --- |
| Título | 18 | seminegrito (600) | 25 | LivvicSemiBold |
| Rótulo | 14 | seminegrito (600) | 20 | LivvicSemiBold |
| Corpo | 16 | regular (400) | 22 | Livvic |
| Legenda | 12 | regular (400) | 17 | Livvic |

O rótulo aqui é só o texto. O campo está em [[Campos de formulário]].

A identidade ainda tem corpo grande e pequeno, títulos de 32, 24 e 20, rótulo grande e pequeno, e receitas de botão. Esta peça não oferece esses papéis pelo nome. O botão está em [[Ações]].

## Cores

A cor acompanha o modo claro ou escuro. Os hex são os do tema. Ver [[Identidade visual]].

| Pedido | Claro | Escuro |
| --- | --- | --- |
| Principal | #2a282b | #e8e5e9 |
| Apoio | #4b484c | #c8c5c9 |
| Discreta | #6b686c | #9b989c |
| Desabilitada | #adadb0 | #6f6c70 |
| Link | #712fc1 | #803ed0 |
| Inversa | #FFFFFF | #000000 |

A cor de link é a marca. A peça não sublinha. A demonstração do link sublinha por fora.

A cor inversa é branca no modo claro e preta no modo escuro. O texto de instalação diz que ela serve a fundo escuro. No código, ela é a tinta oposta ao modo atual. Num kit já escuro, a inversa é preta.

A cor desabilitada muda a tinta. A peça não bloqueia toque e não anuncia estado desabilitado.

## Tamanho e peso por cima

A tela pode trocar o tamanho sem trocar o papel. Entram 12, 14, 16, 18, 20, 24 ou 32 pontos. Muda o número. A altura da linha continua a do papel.

A tela pode trocar o peso: regular (400), médio (500), seminegrito (600) ou negrito (700). Muda o peso. A família do papel continua. O peso médio não tem arquivo de fonte na identidade. Ver [[Identidade visual]].

## Estilo por fora e texto longo

A tela pode mandar estilo por fora, por duas entradas. As duas cobrem o visual da peça. Se as duas mandarem na mesma coisa, vale a que entra por último.

A peça aceita corte de linhas quando a tela pede. Sozinha, ela não corta e não limita largura.

A demonstração de texto longo pede quatro linhas, reticências no fim, largura máxima de 400 e altura de linha 24. Esse 24 está escrito na demonstração. A altura do corpo na identidade é 22.

Um toque pode ser ligado no texto, porque a peça repassa ao texto nativo o que a tela pedir. Ela não vira botão por isso.

## Demonstração e teste

A demonstração mostra o corpo padrão, o título ("Título Principal"), o rótulo ("Label de Campo"), a legenda, um exemplo de cor, um de tamanho e um de peso (um de cada vez, no controle), um estilo vindo de fora e o texto longo.

Há também um painel com título, apoio, texto discreto, link, desabilitado e inversa. Os cartões desse painel usam cinzas e cores escritas na própria demonstração: #fafafa, #1a1a1a, #4CAF50, #FF9800 e #9E9E9E. Não são lidos da [[Identidade visual]]. O fundo escuro desse painel está pintado na demonstração. A inversa só fica clara enquanto o kit está no modo claro.

O teste automático sobe a frase e confere se ela está na tela. Cobre papel, cor, tamanho, peso, identificador de teste, estilo por fora e corte de linhas nesse sentido: a frase continua visível. Não lê a cor aplicada, nem o tamanho, nem o peso, nem a altura da linha.

O tema simulado no teste diverge da identidade. Altura de linha no teste: corpo 20, legenda 16, título 22, rótulo 18. Na identidade: 22, 17, 25 e 20. A cor principal simulada é #4b484c, que na identidade clara é a cor de apoio, não a principal #2a282b.

## O que esta nota não cobre

As frases das telas do app não moram aqui. "Olá", "Vamos começar" e qualquer outro texto escrito ficam no app que consome o kit.

Esta nota não cobre botão, campo, lista, data nem espera. A peça não traz essas coisas.
