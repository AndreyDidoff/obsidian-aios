---
tipo: extração
tema: Início do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: Parcial. Cabeçalho da conta; cartão de agendamento de exemplo; botão de agendar sem ação.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Início do artista

Volta para [[Mapa do app do artista]].

**Pé:** Parcial. Cabeçalho da conta; cartão de agendamento de exemplo; botão de agendar sem ação.

O [[Início do artista]] é a primeira aba de quem já entrou. A barra de baixo tem cinco áreas, nesta ordem: Início, Pedidos, Agenda, Planos e Perfil. Os ícones, na mesma ordem, são casa, etiqueta, calendário, estrelas e pessoa. Quem ainda não entrou não vê esta barra.

## O que é da conta

No topo, a frase é **Olá, {apelido ou nome}!** O apelido é o nome curto que a conta guarda para a pessoa, quando traz um. Sem apelido, entra o nome da pessoa na conta.

Sem os dois, a frase fica **Olá, !**. O app pede a conta de novo e mostra carregamento. Se essa busca falhar, o carregamento acaba e a tela não explica: a saudação continua **Olá, !**.

A foto é a da conta. Sem foto, aparece a imagem de perfil que o app reserva para esse caso.

A nota, ao lado de uma estrela, é a que a conta traz. Se a conta não trouxer nota, ou a nota vier vazia, a tela mostra **5,0**. Esse 5,0 ocupa o lugar. Não é uma avaliação que a pessoa tenha recebido.

## O que é exemplo

O título **Próximos agendamentos** fica abaixo da saudação. Em seguida vêm dois cartões. O texto é o mesmo para qualquer conta. Não é um horário marcado de verdade. A aba [[Agenda do artista]] é outra nota e não preenche este cartão.

### Nome, data e serviços

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

Não há foto, preço, duração nem situação do horário.

### Endereço e o botão

O segundo cartão abre com **Endereço:** e um ícone de casa. As duas linhas são:

- Rua B..., 504
- Imirim - São Paulo, SP - BR

A rua já chega cortada, "Rua B...". Ao lado aparecem um olho fechado e um menu. Os dois estão na tela e não respondem ao toque. Este texto está escrito na tela. Não é um endereço que a pessoa tenha salvo.

O botão **Vamos agendar?** ocupa a largura do cartão. O toque não faz nada: não abre a [[Agenda do artista]] e não abre a conversa do agendamento.

## O que o Início ainda não faz

- Não mostra um horário da pessoa. O cartão de Karen Watanabe permanece, tenha ela horário ou não.
- Não agenda. O toque em **Vamos agendar?** está vazio.
- Não troca o endereço pelo que a pessoa salvou.
- Não esconde nem revela a rua. O corte "Rua B..." já está escrito, e o olho fechado não muda isso.
- Não separa "a conta não tem nota" de "a nota é 5,0".
- Não avisa quando a busca do nome falha.

A [[Abertura do artista]] promete gerir horários; esta tela ainda não faz isso ([[O que ainda não está no app do artista]]).
