---
tipo: extração
tema: Encontrar profissionais
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: Parcial. A tela está pronta e os artistas são dados de exemplo.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Encontrar profissionais

Volta para o [[Mapa do app do cliente]].

A lista é o lugar em que a pessoa vê artistas. Hoje ela está pronta para rolar, passar as fotos e, sem conta, seguir para o cadastro. Os nomes, as fotos, as notas, as distâncias, os preços e as descrições são dados de exemplo, fixos na tela. Não vêm de artistas reais. Visitante e quem tem conta veem a mesma lista. O que muda é o cartaz de cadastro, e o jeito de sair.

**Pé:** Parcial. A tela funciona. Os artistas continuam sendo exemplo, e tocar no card não abre um perfil.

## Dois caminhos, a mesma lista

**Sem conta.** Quem termina o endereço em [[Primeira entrada]] cai aqui como visitante. No topo há fechar. Fechar sai da visita e volta para a abertura.

**Com conta.** A lista é a segunda área da barra de baixo, com ícone de estrela. Ao selecionar, o nome que aparece é **Artistas**. A pessoa sai dessa área pelas outras: [[Início]], [[Agenda]] e [[Meu perfil]].

A distância que a pessoa vê é o número escrito em cada card. O endereço informado na primeira entrada não troca quem aparece nem esses quilômetros.

## O que cada card mostra

Cinco pessoas, sempre nesta ordem. Quando a lista pede mais, as mesmas cinco voltam.

1. Karen Watanabe
2. Maria Silva
3. Ana Santos
4. Juliana Oliveira
5. Patricia Lima

Em cada card:

- À esquerda, uma foto do trabalho. Se houver mais de uma, um contador no canto, no formato 1/3. Karen tem três fotos. Maria, Juliana e Patricia têm duas. Ana tem uma, e o contador não aparece.
- Uma foto pequena de perfil e o nome, em uma linha.
- Uma descrição, em uma linha. O texto está em inglês, fixo na tela, fora da tradução do app:
  - Karen: "Engaging professional profile description"
  - Maria: "Nail art and decorative nails specialist"
  - Ana: "Professional with over 10 years of experience"
  - Juliana: "Personalized service in a welcoming environment"
  - Patricia: "Nail extension specialist"
- Uma estrela e a nota com uma casa e ponto, como na tela: 4.5, 4.8, 4.2, 5.0 e 4.7.
- A distância, também com ponto: 5 km, 3.2 km, 7.5 km, 2.8 km e 4.1 km.
- A faixa de preço: dois números com "à" no meio e um ícone de dinheiro de cada lado. Na tela fica "10 à 150", "50 à 200", "30 à 180", "80 à 250" e "100 à 300". Não aparece "R$".

O nome **Artistas** da barra vem da tradução. Card e cartaz não: estão escritos direto na tela. O botão do cartaz e as três frases estão em português. As descrições dos cards estão em inglês.

## O que acontece ao tocar

Tocar no corpo do card não abre perfil, agenda nem conversa. Nada acontece.

Tocar na foto da esquerda passa para a próxima foto daquele card. Na última, volta para a primeira.

## Carregar mais

Ao abrir, a lista espera cerca de um segundo e mostra os cinco cards.

Perto do fim da rolagem, uma espera de cerca de um segundo e meio, e entram de novo os mesmos cinco, com as mesmas fotos, notas, distâncias e preços. Isso se repete. Não há uma última página.

Sem conta, a cada quatro cards entra um cartaz. Na primeira leva: quatro cards, o cartaz, e o quinto card. Nas levas seguintes o cartaz continua a cada quatro.

Com conta, só os cards. O cartaz não entra.

## Cartaz de cadastro

Só na visita sem conta. Um ícone pequeno fica acima do texto. Cada cartaz mostra uma das três frases, sorteada quando ele aparece:

- Cadastre-se no WeCareU agora mesmo e tenha acesso a todos os artistas da plataforma de forma 100% gratuita!
- Você sabia que a plataforma WeCareU é grátis até mesmo para o artista? Isso mesmo aqui todos são bem vindos.
- Na WeCareU você escolhe quem vai te atender! Sempre teremos um artista perfeito para você! Cadastre-se!

O botão **Cadastrar** abre [[Criar conta]].

## A tela de endereço que ninguém abre

O app tem uma tela "Qual é seu endereço?", com busca de endereço e o atalho **Entrar ou Cadastrar**. Ela não abre a partir desta lista. Nenhuma tela do app navega até ela. O endereço de quem visita sem conta é o do carrossel em [[Primeira entrada]]. Quem já tem conta cuida disso em [[Endereços]].

## O que a lista ainda não faz

- Não traz artistas reais. Os cinco nomes são fixos na tela e se repetem ao carregar mais.
- Não abre o perfil de ninguém ao tocar no card.
- Não tem busca, filtro nem mapa.
- Não usa o endereço da pessoa para mudar a ordem nem a distância.
- Não segue para um agendamento nem para a [[Conversa do agendamento]].
- Não traduz as descrições: ficam em inglês. O preço não traz moeda.
- Não abre a tela solta "Qual é seu endereço?". Ninguém navega até ela.
