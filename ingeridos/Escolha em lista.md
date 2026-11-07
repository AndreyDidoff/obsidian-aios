---
tipo: extração
tema: Escolha em lista
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/select"]
pé: Parcial. Escolha 0.2.7 usável, com demonstração e teste. Busca vazia sem frase. Textos prontos em inglês.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Escolha em lista

Volta para o [[Panorama do design system]].

Quando a resposta é uma opção, e não um texto livre. Texto livre é [[Campos de formulário]].

Isto não é a lista de artistas do app. É o controle de escolha: a tela manda as opções, a pessoa escolhe uma ou várias, e a lista abre numa folha que sobe de baixo.

**Pé:** Parcial. `@wecareu/select` está na versão **0.2.7**, usável, com demonstração e teste. A busca sem resultado não diz nada. A tela troca a ajuda do campo e o erro de obrigatório. As falas do leitor de tela ficam em inglês.

## Uma opção

O campo parece o campo livre: borda arredondada na cor da marca, texto no centro. Cores em [[Identidade visual]].

Vazio, mostra a ajuda que a tela escreveu. Se a tela não escrever, a frase pronta é **Select...**. Com uma opção escolhida, o campo mostra o nome dela.

A lista sobe de baixo, o fundo escurece, e o conteúdo rola se for longo. Tocar fora fecha. Escolher uma opção fecha. A seta da direita abre a lista. Com a lista aberta a seta vira para cima e o nome falado diz fechar, mas o toque nela não fecha.

Sem nenhuma opção, a escolha não aparece.

## Várias opções

O campo mostra etiquetas, lado a lado. Se não couberem, a faixa rola na horizontal. Cada etiqueta traz o nome e um X. Nome longo pode ser cortado.

O X tira só aquela. Na lista, tocar de novo numa opção já marcada também tira. A folha continua aberta, para escolher mais. Na linha, várias opções usam uma caixa de marcação. Uma opção só usa um visto.

## Busca

A busca é da tela pedir, para lista longa. No topo da folha entram um ícone de busca, do [[Vocabulário visual]], e um campo sem frase dentro. O nome falado desse campo é **Search options**.

A lista filtra pelo nome da opção, sem diferenciar maiúscula, e espera um instante curto antes de filtrar. A segunda linha da opção não entra na busca. Abrir a folha limpa a busca anterior.

Não existe frase de "nada encontrado". Se nada combina, a lista fica em branco.

## Opção desligada, campo desligado, somente leitura, erro e limpar

Uma opção desligada aparece esmaecida e o toque não escolhe. Na demonstração, **Away** e **Banned** estão assim.

Campo desligado e somente leitura ficam com o mesmo visual apagado, e os dois recusam abrir a lista. A diferença: no desligado, o X de cada etiqueta some. No somente leitura, o X continua na etiqueta, e o código não trava esse toque.

O erro balança, como em [[Campos de formulário]]. A borda vai para a cor de erro e a frase fica embaixo. A tela pode ligar o erro na hora. Na demonstração, a frase é **This field is required**.

Se a escolha é obrigatória e ainda está vazia, o erro entra quando a pessoa abre a lista. A frase pronta, em inglês, é **This field is required**. A tela pode trocar essa frase, e também a ajuda do campo. As falas do leitor de tela não trocam.

Limpar é a tela pedir. Com algo escolhido, o X da direita toma o lugar da seta. O nome falado é **Clear selection**. Uma opção volta a nada. Várias voltam a nenhuma. Para abrir de novo, o toque é no campo, não nesse X.

## Ícone, bandeira e cor da linha

Cada opção pode trazer um ícone ou uma bandeira, do [[Vocabulário visual]]. Se os dois vierem, a bandeira fica. Pode haver uma segunda linha, menor, embaixo do nome.

A linha pode ter cor de fundo própria, e o nome pode ter cor própria. Sem isso, a opção escolhida usa o fundo suave e o nome na cor da marca. Na demonstração, países levam bandeira e a região na segunda linha. Situação leva ícone e cor no nome. Papel leva cor na linha inteira. Esses textos da demonstração estão em inglês.

## Frases prontas

Ligadas a [[Textos da interface]]. A peça não tem português embutido. A tela escreve, no idioma que quiser, a ajuda do campo e o nome de cada opção.

O que se lê, se a tela não mandar outra coisa:

- **Select...** quando nada foi escolhido.
- **This field is required** quando a escolha obrigatória segue vazia depois de aberta.

O que o leitor de tela fala, sempre em inglês:

- **Select option**, se não houver nome escolhido nem ajuda.
- **Clear selection**, no X que zera.
- **Open options** e **Close options**, na seta.
- **Close dropdown**, no fundo escuro.
- **Search options**, no campo de busca.
- **Remove** seguido do nome, no X da etiqueta.

Não há frase para busca sem resultado.

## Demonstração e teste

A revisão visual está em [[Como o time revisa a interface]].

A demonstração cobre uma opção, opção já escolhida, bandeiras com busca, ícone e cor do nome, cor da linha, várias etiquetas, etiquetas já preenchidas, várias com busca, opção desligada, limpar, erro, campo desligado, somente leitura, e um painel com esses estados juntos.

Os testes cobrem a ajuda, o nome escolhido, abrir a lista, escolher, opção desligada que não responde, campo desligado, somente leitura, a frase de erro, limpar uma e limpar várias, a obrigatória vazia, a busca que esconde o que não combina, a segunda linha, a etiqueta, tirar pelo X e tirar tocando de novo na opção.
