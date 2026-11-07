---
tipo: cruzamento
tema: O que a tela lê no backend
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza os dois apps com o backend de apoio. Descreve onde a tela lê ou grava um dado, por que a pessoa precisa dele, e se essa porta existe no backend. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — o que a tela lê

Depois da conta, quase tudo que a pessoa vê ou é exemplo, ou mora no aparelho, ou viaja uma vez dentro do cadastro. Esta nota separa esses casos.

## Nome, foto e nota no Início

**Por que.** A saudação tem de ser da pessoa, não de um exemplo.

**Onde.** O topo de [[Início]] e de [[Início do artista]]. Apelido ou nome, foto e nota. Se a conta não traz nota, a tela mostra 5,0. Se faltam apelido e nome, fica **Olá, !**.

**Como.** Ao abrir o Início, os dois apps pedem de novo a pessoa logada. O caminho é `login/user/logged`. Este retrato do backend não publica essa porta. [[03-entrar-sair-e-senha]] publica entrar, sair, saber se a sessão vale, e o fluxo de senha. Não publica esta leitura.

O que o app espera receber, se a resposta vier, é o nome, o apelido, a foto, a nota, o e-mail, o documento e um telefone. A tela do Início usa nome, apelido, foto e nota. O resto não aparece no Início.

O cartão **Próximos agendamentos**, com Karen Watanabe, não vem dessa leitura. É texto fixo nos dois apps. **Vamos agendar?** não pede nada. Ver [[Cruzamento - dentro da conta]].

## Endereço

Há três endereços diferentes. Só um conversa com a WeCareU, e não pela porta de endereços.

| Endereço | Por que | Onde | De onde vem |
|----------|---------|------|-------------|
| O do cadastro | Dizer onde a conta mora, e criar a conta com esse local | [[Criar conta]] e [[Cadastro do artista]] | A rua e a cidade vêm da consulta de CEP, fora deste backend. O conjunto vai dentro do pedido de abrir conta, em [[04-cadastro]]. Não passa por [[08-enderecos]]. |
| O da visita sem conta | Liberar a lista de artistas | [[Primeira entrada]], só no app do cliente | A mesma consulta de CEP. Não grava conta. Não pede [[08-enderecos]]. |
| O do perfil | A pessoa gerir os locais depois de entrar | [[Endereços]] e [[Endereços do artista]] | Não lê nem grava. As duas telas dizem que em breve dá para gerenciar. A porta [[08-enderecos]] está no ar e nenhum app a pede. |

**CEP.** A pessoa informa o CEP para a tela completar rua e cidade. Os dois apps perguntam ao mapa da Google, não ao backend de apoio. Se o CEP não é encontrado, o cliente trava o fim do cadastro e o artista segue. Isso é comportamento da tela, não de [[08-enderecos]]. Ver [[Cruzamento - criar conta]].

O endereço "Rua B..., 504" do cartão do Início também não é esta porta. É o exemplo fixo.

## O que fica no aparelho

**Por que.** A tela precisa lembrar sem perguntar de novo ao backend.

| Dado | Por que está no aparelho | Onde | O backend entra? |
|------|--------------------------|------|------------------|
| Rascunho do cadastro | A pessoa saiu no meio | Os dois cadastros | Não. A senha e a foto não entram no rascunho. |
| Sessão | Reabrir sem senha | Os dois apps | A gravação é local. A pergunta se ainda vale está em [[Cruzamento - BFF conta]]. |
| Biometria | Entrar com digital ou rosto | Perfil e abertura | O reconhecimento é do aparelho. A entrada, se segue, é a porta de entrar. |
| Preferência de notificação | A pessoa ligou ou desligou um aviso | [[Avisos, ajuda e regras]] e [[Avisos, ajuda e regras do artista]] | Não. Fica neste aparelho. Sair da conta, no cliente, não apaga. A nota do artista não diz se sair apaga. |

## O que a tela mostra e não lê

Não há pedido ao backend. O motivo de cada uma está na nota da área.

- Lista de artistas, em [[Encontrar profissionais]]. Cinco nomes fixos. O endereço da visita não muda quem aparece.
- Agenda, nos dois. Só o título.
- Conversa do agendamento, nos dois. Sem caminho.
- Pedidos e Planos, só no artista. Casca. A porta de planos existe e não está ligada, em [[06-planos-e-cupons]]. A aba nem pergunta.
- Editar perfil, nos dois. Aviso de em breve. Não lê a conta de volta para um formulário.
- Sobre, termos e privacidade. Texto escrito na tela, data dezembro de 2024.
- Central de ajuda. Abre o site, fora do app.

## Notas

- [[03-entrar-sair-e-senha]]
- [[04-cadastro]]
- [[06-planos-e-cupons]]
- [[08-enderecos]]
- [[Início]]
- [[Início do artista]]
- [[Criar conta]]
- [[Cadastro do artista]]
- [[Primeira entrada]]
- [[Endereços]]
- [[Endereços do artista]]
- [[Encontrar profissionais]]
- [[Avisos, ajuda e regras]]
- [[Avisos, ajuda e regras do artista]]
- [[Cruzamento - BFF conta]]
- [[Cruzamento - dentro da conta]]
- [[Cruzamento - criar conta]]
