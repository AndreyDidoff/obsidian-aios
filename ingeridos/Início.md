---
tipo: extração
tema: Início
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: Parcial. Cabeçalho da conta; próximo atendimento de exemplo; botão de agendar sem ação.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Início

Volta para o [[Mapa do app do cliente]].

O [[Início]] é a primeira aba de quem já entrou. A barra de baixo tem quatro áreas, nesta ordem: Início, Artistas ([[Encontrar profissionais]]), Agenda e Perfil. Quem ainda não entrou não vê esta barra. Fica na [[Primeira entrada]], no [[Criar conta|cadastro]] ou no [[Entrar, senha e biometria|login]].

**Pé:** Parcial. A saudação, a foto e a nota do topo vêm da conta. A nota cai em **5,0** quando a conta não traz uma. O cartão de próximos agendamentos está escrito fixo na tela, igual para qualquer pessoa. O botão **Vamos agendar?** não faz nada.

## O que é da conta

No topo, a frase é **Olá, {apelido ou nome}!** O apelido vem primeiro. Sem apelido, entra o nome.

Sem os dois, a frase fica **Olá, !**. O app pede a conta de novo e mostra carregamento. Se essa busca falhar, o carregamento acaba e a tela não explica: a saudação continua **Olá, !**.

A foto é a da conta. Sem foto, aparece a imagem de perfil que o app reserva para esse caso.

A nota, ao lado de uma estrela, é a da conta. Se a conta não trouxer nota, ou a nota vier vazia, a tela mostra **5,0**. Esse 5,0 ocupa o lugar. Não é uma avaliação que a pessoa tenha recebido.

Nome, apelido, foto e nota vêm da conta. A tela de [[Meu perfil]] não os mostra: lá o menu não traz esses dados.

## O que é exemplo

O título **Próximos agendamentos** fica abaixo da saudação. Em seguida vêm dois cartões. O texto é o mesmo para qualquer conta. Não é um horário marcado de verdade. A aba [[Agenda]] é outra nota e não preenche este cartão.

### Profissional, data e serviços

Um ícone de pessoa, o nome **Karen Watanabe** e a nota **4,5**. Essa 4,5 é do exemplo. A nota da pessoa logada continua no topo.

O cartão escreve, um embaixo do outro:

- **Data:** 25 de Maio
- **Quarta**
- **12h00**

**Quarta** está escrito na tela. A data não tem ano, e o dia da semana não é calculado.

**Serviços**, cada um numa etiqueta, nesta ordem:

- Unha da Mão
- Unha do Pé
- Aplicação de pedra na unha
- Botox
- Unha Gel

Não há foto da profissional, preço, duração nem situação do horário.

### Endereço e o botão

O segundo cartão abre com **Endereço:** e um ícone de casa. As duas linhas são:

- Rua B..., 504
- Imirim - São Paulo, SP - BR

A rua já chega cortada, "Rua B...". Ao lado aparecem um olho fechado e um menu. Os dois estão na tela e não respondem ao toque. Este texto não é um item de [[Endereços]].

O botão **Vamos agendar?** ocupa a largura do cartão. O toque não abre a lista de artistas, não abre a [[Agenda]] e não abre a [[Conversa do agendamento]].

## O que o Início ainda não faz

- Não mostra um atendimento da pessoa. O cartão de Karen Watanabe permanece, tenha ela horário ou não.
- Não agenda. A ação do botão está vazia.
- Não troca o endereço pelo que a pessoa salvou.
- Não esconde nem revela a rua. O corte "Rua B..." já está escrito, e o olho fechado não muda isso.
- Não separa "a conta não tem nota" de "a nota é 5,0".
- Não avisa quando a busca do nome falha.
- Não abre ajuda, avisos nem regras ([[Avisos, ajuda e regras]]). O que o app cita e ainda não entrega está em [[O que ainda não está no app]].
