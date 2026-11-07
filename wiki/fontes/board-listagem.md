---
tipo: fonte
arquivo: "ingeridos/board-listagem.md"
origem: "extração via IA (Cursor) do board Azure DevOps da organização piresbno1992, projeto WeCareU, em 2026-10-21; retrato de trabalho, não decisão de produto; em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Listagem", "Sistema de listagem"]
---

# Listagem

Porta: [[board-indice]]. Extração em 2026-10-21. Organização `piresbno1992`, projeto WeCareU. Retrato de trabalho, não decisão de produto. Em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Estado no board não é pé do produto. New, Active ou Completed não significa entregue no app nem no [[mvp]].

Área WeCareU\GLOBAL, salvo a história 145, que está em WeCareU\ARTIST.

Nenhum item deste bruto traz critério de aceite.

## O que este tema pede

O board pede um sistema de listagem. Uma história pede carregar artistas por endereço, sem cadastro. A outra pede listagem de delivery, com card gratuito, tag de propaganda, integração, filtros e um campo de troca de endereço.

## Épico 330 — Sistema de listagem

Estado no board: New. Responsável: nenhum. Descrição ausente.

Comentário de Andrey Didoff do Nascimento em 2025-08-01: o épico está pareado com WECAREU-2, em `https://wecareu.atlassian.net/browse/WECAREU-2`, e traz um marcador getint.io. O comentário não descreve a listagem.

### História 145 — Criar Carregamento de Artistas por endereço, sem cadastro

Estado no board: New. Área: WeCareU\ARTIST. Responsável: Bruno Pires de Almeida ([[bruno]]). Sem tarefas.

A descrição pede trazer a lista de artistas para o usuário não logado.

Isso encontra a lista sem login. O alvo permanece em [[decisoes-2026-10-21]].

Comentário de Andrey Didoff do Nascimento em 2025-08-01: a história está pareada com WECAREU-7, em `https://wecareu.atlassian.net/browse/WECAREU-7`, e traz um marcador getint.io. O comentário não descreve o carregamento.

### História 359 — Listagem de delivery

Estado no board: Active. Responsável: Andrey Didoff do Nascimento ([[Andrey Didoff]]). Sem descrição.

#### Tarefa 362 — **[BE] Listagem de serviços dinâmico**

Estado no board: New. Responsável: nenhum.

Pede usar o mesmo endpoint com variáveis para gerar a lista de atendentes por tipo de atendimento. Pede pesquisar pelo cadastro de serviços do usuário e subir isso de forma invertida, usando left join para agrupar em ordem. Nomeia UserService, Address, User, Enterprise e Forma de Pagamento. São nomes do board. Não confirmam a arquitetura.

#### Tarefa 446 — **[FE] Criação do card de listagem gratuito**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede a criação do card de listagem gratuito desenvolvido no Figma. O texto diz que, neste momento, farão somente cards de listagem gratuita. Há um anexo. O texto não descreve a imagem.

Comentário de 2025-04-02 registra o fechamento do Pull Request 144. O estado neste retrato é Completed.

#### Tarefa 447 — **[FE] Criação de tag propaganda para se cadastrar**

Estado no board: Completed. Responsável: Andrey Didoff do Nascimento.

Pede uma tag a cada 4 cards, com chamada para o cliente se cadastrar na plataforma. No início, três frases, randômicas entre elas. Há anexos. O texto não descreve as imagens.

Comentário de 2025-04-02 registra o fechamento do Pull Request 145. O estado neste retrato é Completed.

#### Tarefa 448 — **[FE] Integração dos cards de listagem com back-end**

Estado no board: New. Responsável: Andrey Didoff do Nascimento.

Pede integração com o back-end: consumir os dados via API e exibir em tela, respeitando a ordenação da listagem.

#### Tarefa 449 — **[FE] Criação dos filtros de listagem**

Estado no board: New. Responsável: Andrey Didoff do Nascimento.

Pede criar os filtros de listagem a serem aplicados para mudar a ordem da listagem. Não nomeia os filtros.

#### Tarefa 451 — **[FE] Criar campo de troca de endereço no topo da listagem**

Estado no board: New. Responsável: Andrey Didoff do Nascimento. Sem descrição.

## O que isto não decide

Não decide que a lista do app de 21/10 lê o backend. A tarefa 448 pede a integração e está New. Completed nas tarefas 446 e 447 é o estado do work item. A lista do retrato continua exemplo. Ver [[busca-e-filtros]] e [[encontrar-profissionais]].

Não muda o alvo de lista sem login. A história 145 pede artistas por endereço, sem cadastro, para usuário não logado. O alvo permanece. O item 29 de [[contradicoes-e-lacunas]] não foi reaberto.

Não muda a fórmula do [[ranking]]. Card gratuito, tag de propaganda, filtros e a menção a ordenação não reabrem o item 19. A tag da tarefa 447 não é o rótulo de patrocinado. O rótulo continua em aberto.

Não decide quando o endereço aparece para o Artista. A história 145 pede carregamento por endereço. A tarefa 451 pede um campo de troca no topo. O item 16 permanece aberto.
