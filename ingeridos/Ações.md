---
tipo: extração
tema: Ações
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/button-gradient", "@wecareu/button-link", "@wecareu/button-close"]
pé: Pronto. Três botões usáveis, com demonstração e teste.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Ações

Volta para o [[Panorama do design system]].

**Pé:** Parcial. Os três botões estão usáveis e cada um tem teste. A demonstração do degradê ainda usa o texto e os exemplos do link, inclusive uma história chamada de sublinhado que não sublinha. O rito de olhar a interface está em [[Como o time revisa a interface]].

São três papéis. O degradê é a ação principal. O link é a ação secundária, com cara de link. O fechar só dispensa. Os ícones que eles podem mostrar vêm do [[Vocabulário visual]]. As cores vêm da [[Identidade visual]].

O texto do degradê e o do link são os que a tela escrever. A peça não traz frase pronta. O fechar não mostra palavra; o leitor de tela é que ouve **Fechar**. Frases fixas da interface estão em [[Textos da interface]].

Quem usa a peça diz o que acontece no toque. Estas peças não decidem para onde o app vai.

Nenhum dos três mostra espera. Isso fica em [[Espera e carregamento]].

## Botão em degradê

`@wecareu/button-gradient`, versão **0.3.3**. Demonstração: sim. Teste: sim. O teste confere o texto, o toque e o toque que não responde quando desabilitado.

O fundo atravessa o botão, do canto de cima à esquerda até o canto de baixo à direita. As cores são as do botão na [[Identidade visual]]: roxo #BC4CF7 até azul #7873EE. O par é o mesmo no tema claro e no escuro.

O texto é branco. Os cantos são bem arredondados. Por padrão o botão ocupa a largura da área e o conteúdo fica no centro.

O ícone pode ficar antes do texto, depois, ou dos dois lados. Dá para aumentar esse ícone e trocar a cor dele. Sem ícone, fica só o texto.

Dá para o botão acompanhar só a largura do conteúdo. Dá para alinhar o conteúdo à esquerda.

Este botão não sublinha.

No toque, ligado, ele encolhe um pouco e fica mais transparente.

Desabilitado, o mesmo roxo e o mesmo azul ficam lavados, e o botão inteiro fica semitransparente. O texto continua branco. Se houver ícone, o ícone passa para a cor de texto desabilitado. O toque não responde.

O leitor de tela escuta o texto visível, o papel de botão e, quando for o caso, o estado desabilitado. O nome é o próprio texto.

## Botão link

`@wecareu/button-link`, versão **0.3.4**. Demonstração: sim. Teste: sim. O teste confere o texto, o toque, o toque que não responde quando desabilitado, e que o sublinhado começa desligado.

Sem fundo e sem borda. O texto usa a cor secundária da [[Identidade visual]]: lilás no tema claro.

Por padrão ocupa a largura e centraliza. Pode ficar só na largura do texto e alinhado à esquerda.

Ícone antes, depois ou os dois. Tamanho e cor do ícone podem mudar.

O sublinhado começa desligado. Quando a tela pede, o texto fica sublinhado.

No toque, fica mais transparente. Desabilitado, o texto passa para a cor de texto desabilitado, o botão fica semitransparente e o toque não responde.

O leitor de tela escuta o texto visível, o papel de botão e o estado desabilitado quando for o caso.

## Botão fechar

`@wecareu/button-close`, versão **0.2.4**. Demonstração: sim. Teste: sim. O teste confere os três tamanhos, o toque, o toque que não responde quando desabilitado, e que o leitor de tela ouve **Fechar** com papel de botão.

É um círculo com um X. Três tamanhos:

- Pequeno: círculo de 32, X de 16.
- Médio: círculo de 40, X de 20. É o padrão.
- Grande: círculo de 48, X de 24.

No tema claro o círculo é claro e o X é escuro. No tema escuro o círculo escurece e o X clareia.

Desabilitado, o fundo vira o da superfície desabilitada, o X esmaece, o círculo fica semitransparente e o toque não responde.

O desenho das demonstrações é o X. A peça aceita outro ícone no lugar; nenhuma demonstração mostra outro.

O leitor de tela escuta **Fechar** e o papel de botão, mesmo sem texto na tela. O estado desabilitado vai junto.

## O que a demonstração do degradê troca

A demonstração chamada de sublinhado não sublinha. Sublinhado é do link.

A faixa que junta quatro degradês repete o mesmo botão. Largura e alinhamento estão nas demonstrações separadas, e essas aplicam a diferença.

O texto de instalação do degradê descreve tamanhos pequeno, médio e grande, um degradê cinza no desabilitado e um toque que só baixa a opacidade. A peça não tem esses tamanhos. Desabilitada, continua roxa e azul, mais transparente. No toque ela encolhe e fica mais transparente.
