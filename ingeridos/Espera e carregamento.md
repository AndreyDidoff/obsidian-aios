---
tipo: extração
tema: Espera e carregamento
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/loading"]
pé: Pronto
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Espera e carregamento

Volta para o [[Panorama do design system]].

Isto é a peça pronta para quando uma tela precisar esperar. Não é o carregamento de uma tela específica do app.

## O que a pessoa vê

Os dois ao mesmo tempo: uma cortina por cima da tela inteira e, no centro, a animação de pontos do [[Vocabulário visual]] (dots).

A cortina acompanha o tema. No claro, um véu preto pela metade. No escuro, o mesmo preto, mais fechado. Ver [[Identidade visual]].

Os pontos são brancos, grandes, começam sozinhos e ficam repetindo. Não há frase, título nem botão de cancelar.

Enquanto a cortina está no ar, o toque fica nela. O que está por baixo não recebe o toque.

## De onde se liga

O guarda-chuva precisa estar por cima das telas. Qualquer tela dentro dele liga e desliga a espera. Uma tela de fora não consegue.

A espera começa desligada. Ligar e desligar são pedidos separados. Pedir para mostrar de novo não apaga. Quem mostrou é que precisa pedir para esconder.

## Celular e navegador

A pessoa vê a mesma espera nos dois: cortina inteira, pontos brancos no centro, mesmo tamanho, em repetição. Cada lado lê o véu por um nome diferente no tema, e os dois nomes apontam para o mesmo tom.

## Versão, demonstração, teste, pé

Versão marcada de `@wecareu/loading`: **0.4.4**.

A demonstração é a variante do navegador. Um botão liga a espera, e ela se apaga sozinha depois de três segundos.

O teste é a variante do celular. Confirma três coisas: o conteúdo da tela continua lá, a cortina aparece quando a espera liga, e uma tela fora do guarda-chuva não controla a espera. A demonstração é que mostra o desligar.

| Peça | Demonstração | Teste | Pé |
|------|--------------|-------|----|
| Espera | Sim, no navegador | Sim, no celular | Pronto |

## Como ler o pé

| Pé | Significado |
|----|-------------|
| Pronto | Existe, usável numa tela, com demonstração e teste. |
| Parcial | Existe com buraco. |
| Previsto | Não construído. |
