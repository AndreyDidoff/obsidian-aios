---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-final]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[spec-busca-e-ranqueamento]]", "[[brainstorming-wecareu]]", "[[planos-para-o-futuro]]", "[[encontrar-profissionais]]", "[[board-listagem]]"]
---

# Busca e filtros

Como o cliente encontra Artistas. ([[brainstorming-wecareu]])

## Alvo do cliente

A listagem abre sem conta. Ao chegar, não há filtro de data, categoria nem serviço: a lista é única, por faixas de ranqueamento, sem grupos A e B e sem checagem de agenda. Grupos A e B só existem depois que o cliente escolhe uma data. Não há filtro de horário. O card não mostra horários nem a data do grupo B. A faixa de preço do card é a que o artista digitou. A região vem do endereço de atendimento atual, que é o bairro do CEP. Só aparecem categorias e serviços com pelo menos um artista aprovado nessa região. A busca vazia não promete aviso. ([[mvp-alteracoes-pos-congelamento]], [[mvp-final]])

O cliente logado salva todo endereço novo e escolhe o de atendimento. Não existe endereço principal. O deslogado começa com o endereço do welcome. Na troca pela listagem, o deslogado não salva. ([[mvp-funcoes-e-telas]])

Na interface, o agrupamento se chama categoria, não ofício. ([[mvp-copys-cliente]])

O retrato de 21/10, abaixo, é estado atual.

## Raio

- Cidades grandes: bairro e bairros vizinhos (ex.: 10 km).
- Cidades pequenas: inclui cidades próximas, para haver mais Artistas.
- A busca parte do endereço já cadastrado; a localização atual é capturada só para avisar que não bate com o endereço, sem impedir o pedido.

## Ordenação e filtros

- Ordem por filtros, regras internas e planos, não por proximidade. → [[ranking]]
- Depois do MVP: bloco de pagantes primeiro, com cards destacados (cor, tamanho, imagens), e depois os não pagantes, todos pela mesma regra. ([[decisoes-2026-10-20]])
- Filtros combinados com E: "unhas" + "pé" traz só quem faz os dois. Com menos de 10 resultados, o app sugere ampliar a busca.
- Filtro por especialidade e por datas (até 3 dias, ex.: "próximos 3 sábados").
- A listagem mostra os filtros escolhidos; no perfil do Artista há busca para adicionar outros serviços dele.

## Ideias futuras ([[planos-para-o-futuro]])

- Categorias de serviço com nomes profissionais ("Estética Capilar", "Estética de Unhas").
- Busca por tags de avaliação ("manicure no meu bairro com a tag 'Mão Leve'"). → [[avaliacoes]]
- "Filtros sombra" por marca ou atributo de produto, para medir demanda. → [[publicidade-e-marcas]]
- Micro-copys de urgência nos cards ("Restam apenas 2 horários para hoje").

## O que a lista do cliente mostra em 21/10

A lista é exemplo, fixa na tela. Visitante e quem tem conta veem os mesmos cinco nomes. Não há busca, filtro nem mapa. O endereço da pessoa não troca quem aparece nem a distância. Tocar no card não abre perfil. Isso não é a busca descrita acima. A fórmula de [[ranking]] também não está nesta lista. ([[encontrar-profissionais]])

## O que o board pede em 21/10

A história 145 pede carregar artistas por endereço, sem cadastro. A descrição pede trazer a lista de artistas para o usuário não logado ([[board-listagem]]). Isso encontra a lista sem login. O alvo permanece ([[decisoes-2026-10-21]]).

A tarefa 449 pede filtros de listagem para mudar a ordem. Não nomeia os filtros nem outra fórmula. A ordem definida continua em [[ranking]]. A tarefa 451 pede um campo de troca de endereço no topo da listagem e não tem descrição. A tarefa 448 pede integrar os cards ao backend, respeitando a ordenação, e está New. A lista do app em 21/10, acima, continua exemplo.
