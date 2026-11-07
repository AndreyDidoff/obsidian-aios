---
tipo: extração
tema: Mapa do app do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: Retrato das áreas de quem atende.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Mapa do app do artista

Este app é o de quem atende: artista de beleza e bem-estar. O nome na loja é **WeCareU - Artistas**. O de quem procura o serviço é outra extração: [[Mapa do app do cliente]].

A abertura promete perfil gratuito, sem comissão, clientes, agendamento automático, pagamento no app, escolha de horários e preços, e check-in e check-out. O percurso dos slides está em [[Abertura do artista]].

## Como ler o pé

| Pé | Significado |
|----|-------------|
| Construído | A pessoa percorre o fluxo e ele faz o que a tela promete. |
| Parcial | A tela existe e mostra alguma coisa, mas parte é exemplo fixo, botão sem ação, ou o destino é só um aviso de "em breve". |
| Casca | A entrada existe e a tela só tem um título. |
| Não entregue | O app cita a função, ou ela foi prevista, e não há tela em uso. |

## Como se entra

Não há uso sem conta. Quem abre o app vê a [[Abertura do artista]]: seis slides, pedido de localização, pedido de notificações e o botão "Cadastrar". O link "Já tenho uma conta" fica na mesma tela e abre o login.

O [[Cadastro do artista]] tem cinco etapas: dados pessoais, foto, endereço, confirmação do endereço e acesso. Dá para voltar. O rascunho dos dados pessoais e do endereço fica no aparelho. Foto, e-mail e senha não entram nesse rascunho. Ao terminar, a conta é enviada e a sessão fica guardada. A tela não avisa sucesso e não abre as abas. Na próxima abertura, se a sessão ainda valer, a pessoa entra. Também dá para entrar pelo login.

[[Entrar, senha e biometria do artista]] pede e-mail e senha ("Vamos entrar na sua conta:"). "Esqueci minha senha" segue para o código e para uma senha nova, e devolve a pessoa ao login com "Senha alterada com sucesso! Faça login com sua nova senha." Se a biometria já estiver ligada e a credencial valer, aparece "Entrar com Biometria". No primeiro login com senha, o app pode pedir para ligar isso.

Quem já entrou cai nas abas. O Início abre primeiro. Sair pede confirmação ("Sair da WeCareU") e volta para a abertura.

## A barra de baixo

Em português, nesta ordem: **Início**, **Pedidos**, **Agenda**, **Planos**, **Perfil**. Os ícones são casa, etiqueta, calendário, estrelas e pessoa.

Clientes não aparece na barra. A conversa do agendamento também não. As duas existem como tela e não têm caminho visível. Estão em [[O que ainda não está no app do artista]].

Se o aparelho estiver em inglês, os nomes da barra passam a Home, Orders, Schedules, Plans e Profile.

## As áreas

| Área | O que a pessoa vê | Pé | Nota |
|------|-------------------|----|------|
| [[Abertura do artista]] | Seis slides, permissão de localização, permissão de notificações, "Cadastrar" e "Já tenho uma conta" | Construído | Se a pessoa negar a permissão, o app avisa e segue |
| [[Cadastro do artista]] | Cadastro em cinco etapas. O rascunho parcial fica no aparelho | Parcial | A conta é enviada, mas a tela não abre as abas |
| [[Entrar, senha e biometria do artista]] | Login, esqueci a senha, código, nova senha, digital ou rosto | Construído | A biometria também liga e desliga no perfil, se o aparelho tiver |
| [[Início do artista]] | "Olá" com o nome da conta, foto e nota, e o cartão do próximo atendimento | Parcial | O cartão é fixo (Karen Watanabe, 25 de Maio, 12h00). "Vamos agendar?" não faz nada |
| [[Pedidos do artista]] | Aba Pedidos | Casca | No centro está "Tab Orders" |
| [[Agenda do artista]] | Aba Agenda | Casca | No centro está "Tab Schedules" |
| [[Planos do artista]] | Aba Planos | Casca | No centro está "Tab Plans" |
| [[Perfil do artista]] | Menu: editar perfil, senha, biometria, endereços, notificações, ajuda, sobre, termos, privacidade e sair | Construído | O menu está inteiro. "Editar Perfil" abre uma tela de "em breve" |
| [[Endereços do artista]] | No perfil, "Gerenciar Endereços". No cadastro, um endereço é informado | Parcial | A tela do perfil diz "Em breve você poderá gerenciar seus endereços aqui." |
| [[Avisos, ajuda e regras do artista]] | Preferências de notificação, central de ajuda, sobre o app, termos e privacidade | Parcial | Notificações, sobre, termos e privacidade estão na tela. A central de ajuda abre `https://wecareu.app/suporte` |
| [[O que ainda não está no app do artista]] | Funções citadas ou previstas e não entregues | Não entregue | Lista na outra nota |

## O que já é da conta e o que ainda é exemplo

**Já ligado à conta da pessoa**

- Entrar, sair e manter a sessão
- Criar a conta (a entrada nas abas fica para a próxima abertura, ou para um login)
- Recuperar a senha e trocar a senha no perfil
- Entrar com biometria e ligar ou desligar isso no perfil
- No Início, "Olá" com apelido ou nome, foto e nota. Se a conta não trouxer nota, aparece 5,0. Sem foto, entra um avatar genérico
- O endereço informado no cadastro vai com a conta. O perfil não o mostra de novo: Gerenciar Endereços só avisa que vem depois
- As preferências de notificação, gravadas no aparelho
- Sobre o app, termos de uso e política de privacidade

**Ainda exemplo, ou sem efeito**

- O cartão **Próximos agendamentos**: Karen Watanabe, nota 4,5, 25 de Maio, Quarta, 12h00
- Os serviços desse cartão: Unha da Mão, Unha do Pé, Aplicação de pedra na unha, Botox, Unha Gel
- O endereço "Rua B..., 504" e "Imirim - São Paulo, SP - BR", e os ícones de olho fechado e de menu ao lado, que não fazem nada
- O botão "Vamos agendar?"
- Pedidos, Agenda e Planos
- Editar perfil e gerenciar endereços, que só avisam "em breve"

## O que esta extração não cobre

O que o app cita ou prevê e a pessoa não encontra em uso está em [[O que ainda não está no app do artista]]. Esta nota não percorre campo a campo o cadastro, a senha nem cada tela do perfil.

## Versão e idiomas

Versão marcada no app: **1.0.0**. O nome exibido é **WeCareU - Artistas**. Textos em **português** e **inglês**, conforme o idioma do aparelho. Se uma frase não tiver tradução, o app mostra o inglês. As cascas de Pedidos, Agenda e Planos estão em inglês mesmo com o aparelho em português.

[[Mapa do app do artista]] [[Abertura do artista]] [[Cadastro do artista]] [[Entrar, senha e biometria do artista]] [[Início do artista]] [[Pedidos do artista]] [[Agenda do artista]] [[Planos do artista]] [[Perfil do artista]] [[Endereços do artista]] [[Avisos, ajuda e regras do artista]] [[O que ainda não está no app do artista]]
