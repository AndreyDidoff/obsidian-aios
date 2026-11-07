---
tipo: extração
tema: Mapa do app do cliente
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Mapa do app do cliente

O app se chama **WeCareU**. Esta nota cobre só o aplicativo de quem procura o serviço (o cliente). Não descreve o app de quem atende, nem a missão da empresa: isso não está neste repositório.

O que o app deixa ver: a pessoa descobre **artistas** perto de um endereço, olha foto, nota, distância e faixa de preço, e a intenção do produto é **agendar**. Os exemplos fixos na tela de início são de unha e de botox. Isso sugere beleza e cuidado, mas o catálogo de serviços ainda não existe como lista de verdade.

Versão marcada no app: **1.0.0**. Textos em **português** e **inglês**. Se uma frase não tiver tradução, o app mostra o inglês.

## Como ler o pé de cada área

| Pé | Significado |
|----|-------------|
| Construído | A pessoa consegue percorrer o fluxo. A conta, a senha e o endereço conversam com o serviço da WeCareU. |
| Parcial | A tela existe e mostra alguma coisa, mas parte é exemplo fixo ou o botão não leva a lugar nenhum. |
| Casca | A entrada existe. A tela só tem um título. |
| Não entregue | O app cita a função, ou ela foi prevista, e não há tela em uso. |

## Dois jeitos de usar

**Sem conta.** Na abertura há duas saídas: "Vamos começar?" e "Já tenho uma conta". Quem começa passa por um carrossel: permitir localização, permitir notificações e informar o endereço (o número é obrigatório). Só então entra como visitante na lista de artistas. Fechar essa lista volta para a abertura e sai do modo visitante.

**Com conta.** Depois de entrar, a barra de baixo tem quatro áreas: Início, Artistas, Agenda e Perfil. O Início abre primeiro. Do perfil saem as telas de dados, senha, endereços, notificações, sobre, termos e privacidade.

Quem já ativou digital ou reconhecimento facial pode entrar por aí na abertura, se o aparelho tiver isso e a credencial ainda for válida. Se falhar, o app manda para o login.

## As áreas

| Área | O que a pessoa vê | Pé | Nota |
|------|-------------------|----|------|
| [[Primeira entrada]] | Abertura, carrossel de localização, notificações e endereço, e o uso sem conta | Construído | É a porta de quem ainda não entrou |
| [[Criar conta]] | Cadastro em três passos: acesso, dados pessoais e endereço. O rascunho fica no aparelho | Construído | Dá para voltar e avançar entre os passos |
| [[Entrar, senha e biometria]] | Login, esqueci a senha, código, nova senha, digital ou rosto | Construído | A biometria também liga e desliga no perfil |
| [[Encontrar profissionais]] | Lista de artistas: foto, nota, distância, faixa de preço e convite para criar conta | Parcial | A lista é de exemplo. Não vem dos artistas de verdade |
| [[Início]] | Nome e foto da conta, nota e o cartão do próximo atendimento | Parcial | O cartão é fixo (Karen Watanabe, 25 de maio, 12h, unhas e botox). O botão "Vamos agendar?" não faz nada |
| [[Agenda]] | Aba Agenda | Casca | Só o título |
| [[Conversa do agendamento]] | Uma tela prevista para falar de um horário | Casca | Só o título. Não há caminho visível a partir das abas |
| [[Meu perfil]] | Editar dados, senha, biometria, endereços, notificações, ajuda, sobre, termos, privacidade e sair | Parcial | O menu está inteiro. Editar dados é só o aviso "em breve". Senha e biometria funcionam, com ressalvas na nota |
| [[Endereços]] | Onde o atendimento acontece no cadastro e na visita, e a gestão no perfil | Parcial | CEP e localização funcionam no cadastro e na visita. Gerenciar no perfil é só o aviso "em breve" |
| [[Avisos, ajuda e regras]] | Preferências de notificação, central de ajuda, sobre o app, termos e privacidade | Parcial | A central de ajuda abre o site `https://wecareu.app/suporte`. Não é uma tela de dentro do app |
| [[O que ainda não está no app]] | Funções citadas e não entregues | Não entregue | Ver a lista abaixo |

## O que já é da conta e o que ainda é exemplo

**Já ligado à conta da pessoa**

- Entrar, sair e manter a sessão
- Criar a conta
- Recuperar e trocar a senha
- Entrar com biometria e ligar ou desligar isso no perfil
- Nome, apelido e foto no Início, quando a conta os tem. A nota mostrada cai em 5,0 se a conta não trouxer uma
- Endereço no cadastro e na entrada de visitante. A gestão no perfil ainda não lista nem edita nada

**Ainda exemplo, ou sem efeito**

- Os artistas da lista (nomes, fotos, notas, distâncias e preços)
- O próximo atendimento do Início, o endereço "Rua B..., 504, Imirim" e os serviços escritos nesse cartão
- O botão de agendar nesse cartão
- A Agenda
- A conversa do agendamento

## O que esta extração não cobre

- App de quem presta o serviço
- Regras comerciais, preços reais, pagamento e cancelamento
- Catálogo oficial de serviços. O que aparece (unha da mão, unha do pé, pedra na unha, botox, unha gel) está escrito na tela de início como exemplo
- Escolher o tipo de serviço. Está previsto e não tem tela
- Alterar o e-mail. O texto existe, e não há entrada no menu
- Uma tela antiga de visitante ("Agende, siga e descubra talentos agora mesmo") que não entra em nenhum fluxo
- Cadastro com o nome antigo "SignUp". O cadastro em uso é outro

## Ordem sugerida para as próximas notas

1. [[Primeira entrada]]
2. [[Criar conta]]
3. [[Entrar, senha e biometria]]
4. [[Encontrar profissionais]]
5. [[Início]]
6. [[Meu perfil]]
7. [[Endereços]]
8. [[Avisos, ajuda e regras]]
9. [[Agenda]]
10. [[Conversa do agendamento]]
11. [[O que ainda não está no app]]
