---
tipo: pendencia
superficie: app-cliente
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[encontrar-profissionais]]", "[[inicio]]", "[[enderecos]]"]
---

# Ajustes do app do cliente: descoberta

Esta página lista o que o app do cliente precisa mudar na descoberta para chegar ao alvo do MVP. Não é a especificação do produto.

### Listagem

- **Alvo:** A listagem abre sem conta, depois do welcome, com as quatro abas Início, Artistas, Agenda e Perfil. Sem conta, a barra aparece ao chegar na listagem; Início, Agenda e Perfil abrem a tela de bloqueio, com "Criar conta" e "Já tenho conta", e a aba Artistas fica livre. Quem entra pela tela de bloqueio volta para a listagem. No início não há filtro de data, categoria nem serviço: a lista é única, da região do endereço atual, e os grupos A e B só aparecem depois que o cliente escolhe uma data. O topo mostra o endereço atual pelo nome ou, sem nome, pela região, nunca o endereço completo. ("Navegação inferior do cliente", "M05 Filtros e tela", [[mvp-funcoes-e-telas]])
- **Hoje:** Quem termina o endereço da primeira entrada cai numa lista de cinco artistas de exemplo, a mesma para visitante e para quem tem conta. Não há busca, filtro nem mapa, e esse endereço não troca quem aparece nem a distância do card. Sem conta, fechar volta para a abertura e a barra não aparece; com conta, a barra é Início, Artistas, Agenda e Perfil. ([[encontrar-profissionais]], [[inicio]])
- **Ajuste:** Abrir a listagem sem conta, depois do welcome, com a barra visível também nesse caso: Início, Agenda e Perfil abrem a tela de bloqueio, e Artistas fica livre. Trocar a lista fixa de exemplo pela lista da região do endereço atual, sem filtro de data, categoria ou serviço ao chegar; a data e os grupos A e B só entram depois que o cliente escolhe uma data.

### Card da listagem

- **Alvo:** O card traz a foto de divulgação, a foto e o nome do artista, a descrição curta de no máximo 28 caracteres, estrelas e a faixa de preço que o artista digitou, sempre com "R$", no formato "R$ 10 a R$ 150", sem cálculo pela busca. Abaixo de 3 avaliações, o texto "Poucas avaliações", sem número, no lugar das estrelas. O card não mostra horários nem a data do grupo B, e o ofício não entra. Com uma foto só, a seta de galeria não aparece. Uma tag por card. ("M05 Card de artista na listagem", "M05/M02 Foto de divulgação", "M05/M02-F05 Perfil do artista visto pelo cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** Cada card de exemplo tem foto do trabalho com contador 1/3 quando há mais de uma, foto pequena e nome, descrição em inglês fixa, estrela e nota com ponto, distância e faixa com "à" no meio, sem "R$". Tocar no corpo não abre perfil; tocar na foto passa para a próxima. ([[encontrar-profissionais]])
- **Ajuste:** Tirar o número da nota, a distância, o contador de fotos e a descrição em inglês; mostrar estrelas, ou "Poucas avaliações" sem número quando forem menos de 3, a descrição curta de no máximo 28 caracteres e a faixa que o artista digitou, sempre com "R$", no formato "R$ 10 a R$ 150". Com uma foto só, a seta de galeria não aparece; o card não mostra horários, a data do grupo B nem o ofício, passa a ter uma única tag, e o toque no corpo abre o perfil.

### Pesquisar

- **Alvo:** A lupa da listagem abre a tela "Pesquisar", com campo de texto, chips de categoria e de serviço, data única e o botão "Aplicar filtros". Na tela, o agrupamento se chama categoria. O texto só destaca os chips; o filtro só existe ao tocar no chip, e a lista só muda em "Aplicar filtros". Sem filtros, a listagem não mostra a data nem a faixa de chips. ("M05 Filtros e tela", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve esta tela.
- **Ajuste:** O retrato não tem esta tela. Criar "Pesquisar", aberta pela lupa da listagem, em que o agrupamento se chama categoria: o cliente escolhe chips e uma data única, e a listagem só atualiza em "Aplicar filtros".

### Home

- **Alvo:** A home aparece quando o cliente entra logado e ao finalizar um agendamento. O cabeçalho tem logo, "Olá, <nome>!" e foto, sem nota do cliente. Na ordem: "Vamos agendar", "Avalie seu atendimento" e "Próximo agendamento"; seção sem itens fica oculta. O bloco "Vamos agendar" tem o campo de endereço, que abre o formulário, salva o endereço com nome, torna-o o atual e leva à listagem, mais a lista dos dois últimos endereços usados. ("Registro de detalhamento: Home do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** É a primeira aba de quem já entrou. A saudação usa apelido ou nome, e a nota do topo vem da conta ou cai em 5,0. "Próximos agendamentos" é texto fixo de exemplo, com data e serviços, e o botão "Vamos agendar?" não abre a listagem nem usa o endereço salvo. ([[inicio]])
- **Ajuste:** A home segue apenas para o cliente logado. Tirar a nota do topo e os cartões de exemplo; a saudação passa a "Olá, <nome>!", "Vamos agendar" passa a salvar ou escolher o endereço e abrir a listagem, e "Avalie seu atendimento" e "Próximo agendamento" só aparecem quando houver item.

### Endereço

- **Alvo:** Não existe endereço principal: o atual é o último escolhido e permanece ao reabrir o app. O cliente logado salva todo endereço novo, com nome. O deslogado começa com o endereço do welcome. Na troca pela listagem, o deslogado não salva: o formulário não tem nome nem lista, e o botão é "Usar este endereço". A pesquisa é por CEP. No topo aparece o nome ou, sem nome, a região, e o olho revela o endereço completo. ("Endereço de atendimento e troca pela listagem", [[mvp-funcoes-e-telas]])
- **Hoje:** "Gerenciar Endereços" avisa que em breve será possível gerenciar, sem lista, sem segundo endereço e sem apelido. A tela não lê a conta. Nenhuma tela da listagem abre "Qual é seu endereço?", e o endereço da primeira entrada não muda a lista. ([[enderecos]], [[encontrar-profissionais]])
- **Ajuste:** Tirar o aviso de "em breve" e gravar os endereços do cliente logado, todos, com nome, sem eleger um principal: vale o último escolhido. Na troca pela listagem, o deslogado começa com o endereço do welcome e o botão passa a ser "Usar este endereço", sem nome, sem lista e sem salvar; a pesquisa é por CEP, o topo mostra o nome ou a região, e o olho revela o endereço completo.

### Perfil do artista

- **Alvo:** O perfil só abre pela listagem. No topo: voltar, foto grande do artista, nome, estrelas ou "Poucas avaliações" sem número, descrição curta e o botão "Agendar agora". A foto de divulgação não aparece no MVP. Sem idade e sem "Compartilhar". Os serviços vêm agrupados por categoria, com "Ver mais"; na tela, o agrupamento se chama categoria. ("M05/M02-F05 Perfil do artista visto pelo cliente", "M05/M02 Foto de divulgação", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve esta tela.
- **Ajuste:** O retrato não tem esta tela. Criar o perfil aberto pelo card da listagem, sem foto de divulgação, sem idade e sem "Compartilhar", mostrando a foto do artista, o nome, estrelas ou "Poucas avaliações" sem número, e os serviços agrupados por categoria, com "Ver mais".
