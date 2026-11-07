---
tipo: extração
tema: Identidade visual
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/tokens", "@wecareu/theme"]
pé: Parcial. Tokens 0.2.8 e tema 0.3.4 pintam a tela; não há teste automático nem demonstração da paleta.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Identidade visual

Volta para o [[Panorama do design system]].

A [[Identidade visual]] é a prateleira de cara do app: modo claro, modo escuro, cor, folga, canto e letra. Os tokens guardam os valores. O tema entrega esses valores para a tela, já separados por modo.

**Pé:** Parcial. Dá para usar numa tela. `@wecareu/tokens` está na versão **0.2.8**. `@wecareu/theme` está na versão **0.3.4** e aponta para esses tokens. Não há teste automático de nenhum dos dois. Não há demonstração da paleta. O código existir não basta para o pé Pronto.

## Dois modos

São dois modos: claro e escuro.

Na largada, quem monta a tela escolhe o modo. Se ninguém escolhe, abre no claro. A pessoa que usa o app não escolhe neste repositório. O interruptor do app do cliente não está aqui.

O kit permite alternar com a tela aberta: do claro para o escuro e de volta, ou direto para um dos dois. Quem consome o kit é que liga esse gesto a um controle, se quiser.

## Cores que uma tela pinta

A lista completa é maior. São **nove famílias**: cores de tela (claro e escuro), neutras, erro, sucesso, aviso, informação, degradê, transparência e sombra. Erro, sucesso, aviso e informação têm onze degraus cada, do mais claro ao mais escuro, mais um véu a 10% de opacidade. Abaixo estão os papéis que uma tela usa. O hex é o que o tema entrega.

Vários papéis dividem o mesmo hex. O comentário no arquivo diz que as cores de tela seguem o app principal. Isso não é um guia de marca.

### Fundo

| Papel | Claro | Escuro |
| --- | --- | --- |
| Página | #ecedf4 | #0b0c13 |
| Faixa secundária | #e4e5ec | #1e1d34 |
| Faixa terciária | #e6e3f2 | #13141b |
| Faixa mais fechada | #d7d7e8 | #100e1c |
| Cartão | #d4c7ea | #231639 |
| Elevado e modal | #cccbe2 | #181829 |
| Campo | #e6e3f2 | #1e1d34 |
| Cartão secundário | #e6e3f2 | #1e1d34 |
| Cabeçalho | #e4e5ec | #13141b |
| Barra de baixo | #d7d7e8 | #100e1c |
| Superfície desabilitada | #e4e5ec | #100e1c |
| Véu sobre a tela | preto a 50% | preto a 70% |

No claro, campo e cartão secundário são o mesmo #e6e3f2. No escuro, campo, cartão secundário e faixa secundária são o mesmo #1e1d34.

O arquivo de tokens ainda guarda, no escuro, uma superfície primária #1e1d34 e uma superfície elevada #231639. O tema não pinta a tela com esses dois valores. A superfície principal que a tela recebe é a do cartão. O elevado que a tela recebe é o fundo elevado da tabela.

### Texto

| Papel | Claro | Escuro |
| --- | --- | --- |
| Principal | #2a282b | #e8e5e9 |
| Apoio | #4b484c | #c8c5c9 |
| Discreto | #6b686c | #9b989c |
| Desabilitado | #adadb0 | #6f6c70 |
| Texto de exemplo no campo | #8b888c | #9b989c |
| Link | #712fc1 | #803ed0 |
| Inverso | #FFFFFF | #000000 |
| Selo | #ecedf4 | #0b0c13 |

Preto #000000 e branco #FFFFFF também ficam fixos, nos dois modos. O inverso é branco no modo claro e preto no modo escuro. Serve para texto sobre uma superfície do modo oposto.

Há uma rampa de cinzas, de #FAFAFA a #2A282B. A tela usa os papéis da tabela.

### Marca

A cor de marca é um roxo. O texto de instalação dos tokens ainda cita #2E6BE6 para a marca clara. O código usa os hex desta tabela.

| Papel | Claro | Escuro |
| --- | --- | --- |
| Ação principal | #712fc1 | #803ed0 |
| Ação principal, hover | #5f2399 | #9148e0 |
| Ação principal, pressionado | #4d1a7a | #6f34b8 |
| Ação principal, desabilitada | #b8b5bb | #333445 |
| Ação secundária | #817eb9 | #494681 |
| Ação secundária, hover | #6f6b9a | #5a5691 |
| Ação secundária, pressionado | #5d597b | #3a3669 |
| Acento | #a981d9 | #4d267e |
| Acento, hover | #9670c7 | #5e318e |
| Acento, pressionado | #835fa5 | #3c1c6e |

O degradê de botão é o mesmo nos dois modos: de #BC4CF7 a #7873EE. A versão desabilitada guarda #BC4CF760 e #7873EE60. Hover e pressionado estão no arquivo. O arquivo não diz em que gesto cada um entra. O comportamento do botão está em [[Ações]].

### Erro, sucesso, aviso e informação

Cada um tem quatro papéis na tela: fundo, borda, cor e texto. No escuro, o fundo é a cor padrão com 10% de opacidade.

| Papel | Claro | Escuro |
| --- | --- | --- |
| Erro | #EF4444 | #F87171 |
| Fundo de erro | #FEE2E2 | #EF4444 a 10% |
| Texto de erro | #991B1B | #FECACA |
| Sucesso | #22C55E | #4ADE80 |
| Fundo de sucesso | #DCFCE7 | #22C55E a 10% |
| Texto de sucesso | #166534 | #BBF7D0 |
| Aviso | #F59E0B | #FBBF24 |
| Informação | #3B82F6 | #60A5FA |

Há um segundo uso, chamado de status, que não muda com o modo: erro #EF4444, sucesso #22C55E, aviso #F59E0B, informação #3B82F6. No escuro, esse status e a cor da tabela acima não são o mesmo hex.

Situação e estrela também estão guardadas. O arquivo não diz quando cada uma vale.

| Papel | Claro | Escuro |
| --- | --- | --- |
| Disponível | #a981d9 | #4d267e |
| Ocupado | #FF9800 | #FFB74D |
| Online | #4CAF50 | #81C784 |
| Offline | #adadb0 | #6f6c70 |
| Estrela | #FFD700 | #FFB000 |

### Borda

| Papel | Claro | Escuro |
| --- | --- | --- |
| Secundária | #d7d7e8 | #292a39 |
| Leve | #e6e3f2 | — |
| Desabilitada | #e4e5ec | #333445 |
| Erro | #FECACA | #B91C1C |
| Foco | #712fc1 | #803ed0 |
| Primária, translúcida | rgba(75, 72, 76, 0.2) | rgba(182, 179, 183, 0.3) |

A borda leve só existe no claro. Cabeçalho e barra usam essa leve no claro. No escuro, usam a secundária #292a39.

Sombra de cartão, sombra média e sombra forte (na cor da marca) estão no tema. O arquivo não diz quando usar cada uma.

## Folga, canto e letra

Folga, do menor para o maior:

| Nome na tela | Pontos |
| --- | --- |
| Mínima | 4 |
| Pequena | 8 |
| Média | 12 |
| Grande | 16 |
| Maior | 24 |
| Bem maior | 32 |
| Máxima | 48 |

A tela em si usa folga grande (16). A área segura usa folga média (12). A altura do cabeçalho é 56. A barra de baixo é 80. O texto de instalação lista a folga só até 32 e omite 4 no canto. O código inclui a escala inteira abaixo.

Canto:

| Nome na tela | Pontos |
| --- | --- |
| Mínimo | 4 |
| Pequeno | 6 |
| Médio | 8 |
| Grande | 12 |
| Maior | 16 |
| Bem maior | 24 |
| Pílula | 9999 |

A letra é Livvic. O pacote de tokens traz três arquivos: regular, seminegrito e negrito. Os nomes que a tela pede são Livvic, LivvicSemiBold e LivvicBold.

| Peso | Número |
| --- | --- |
| Regular | 400 |
| Médio | 500 |
| Seminegrito | 600 |
| Negrito | 700 |

O peso médio é só o número 500. Não há arquivo de fonte para ele.

Tamanhos que se repetem com nomes diferentes: 12, 14, 16, 18, 20, 24 e 32 pontos. O tema monta catorze receitas. A peça de texto da interface usa quatro delas. Ver [[Textos da interface]].

| Receita | Pontos | Peso | Altura da linha | Família |
| --- | --- | --- | --- | --- |
| Corpo grande | 18 | regular | 29 | Livvic |
| Corpo | 16 | regular | 22 | Livvic |
| Corpo pequeno | 14 | regular | 20 | Livvic |
| Título de impacto | 32 | negrito | 38 | LivvicBold |
| Título de impacto médio | 24 | negrito | 29 | LivvicBold |
| Título | 20 | negrito | 28 | LivvicBold |
| Título médio | 18 | seminegrito | 25 | LivvicSemiBold |
| Título pequeno | 16 | seminegrito | 22 | LivvicSemiBold |
| Rótulo grande | 16 | seminegrito | 22 | LivvicSemiBold |
| Rótulo | 14 | seminegrito | 20 | LivvicSemiBold |
| Rótulo pequeno | 12 | regular | 17 | Livvic |
| Legenda | 12 | regular | 17 | Livvic |
| Botão grande | 16 | seminegrito | 22 | LivvicSemiBold |
| Botão | 14 | seminegrito | 20 | LivvicSemiBold |

O tema também deixa medidas prontas para peças: botão com canto médio (8) e folga grande na horizontal (16); campo com canto médio (8); cartão com canto grande (12) e folga média (12); modal com canto maior (16). O comportamento dessas peças está em [[Ações]] e [[Campos de formulário]].

## O que o arquivo não decide

Um hex guardado não é regra de marca. Este repositório não diz o que a marca permite, proíbe ou significa.

- Hover, pressionado e desabilitado são tintas. Não há regra de gesto.
- Disponível, ocupado, online, offline e estrela são tintas. Não há regra de quando a pessoa está disponível, nem do que a estrela mede.
- As escalas de erro, sucesso, aviso e informação comentam no arquivo que seguem uma rampa pronta de mercado. Isso não é uma decisão de marca escrita aqui.
- O resumo curto de cores (poucos papéis, para compatibilidade) diverge do tema que a tela lê. No escuro, a superfície desse resumo é #1e1d34. A superfície que o tema entrega é a do cartão, #231639.
- Não há teste automático segurando esses valores. Uma mudança de hex não quebra um teste destes pacotes, porque o teste não existe.
