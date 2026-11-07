---
tipo: fonte
arquivo: "ingeridos/Mapa do app do artista.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_worker; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Mapa do app do artista"]
---

# Mapa do app do artista

Porta desta leva. O app é o de quem atende. O nome na loja é **WeCareU - Artistas**. Versão marcada **1.0.0**. Textos em português e inglês; se faltar tradução, o app mostra o inglês. As cascas de Pedidos, Agenda e Planos estão em inglês mesmo com o aparelho em português. Com o aparelho em inglês, a barra passa a Home, Orders, Schedules, Plans e Profile.

A extração do artista não cita `@wecareu/auth-flow`. A extração do artista não cita o kit visual.

Pé, como esta extração define:

| Pé | Significado |
|---|---|
| Construído | A pessoa percorre o fluxo e ele faz o que a tela promete |
| Parcial | A tela existe e mostra alguma coisa, mas parte é exemplo fixo, o botão não leva a lugar nenhum, ou o destino só avisa "em breve" |
| Casca | A entrada existe. A tela só tem um título |
| Não entregue | O app cita a função, ou ela foi prevista, e não há tela em uso |

## Como se entra

Não há uso sem conta. Quem abre o app vê a [[abertura-do-artista]]: seis slides, pedido de localização, pedido de notificações, **Cadastrar** e **Já tenho uma conta**. Se a pessoa negar a permissão, o app avisa e segue.

O [[cadastro-do-artista]] tem cinco etapas: dados pessoais, foto, endereço, confirmação do endereço e acesso. Ao terminar, a conta é enviada e a sessão fica no aparelho. A tela não avisa sucesso e não abre as abas. Na próxima abertura, se a sessão ainda valer, a pessoa entra.

[[entrar-senha-e-biometria-do-artista]] pede e-mail e senha. O título é **Vamos entrar na sua conta:**. Quem já entrou cai nas abas. O Início abre primeiro. Sair pede confirmação (**Sair da WeCareU**) e volta para a abertura.

## A barra de baixo

Em português, nesta ordem: **Início**, **Pedidos**, **Agenda**, **Planos**, **Perfil**. Os ícones são casa, etiqueta, calendário, estrelas e pessoa.

Clientes não está na barra. A conversa do agendamento também não. As duas existem como tela e não têm caminho visível. Estão em [[o-que-ainda-nao-esta-no-app-do-artista]].

## As áreas

| Área | Pé |
|---|---|
| [[abertura-do-artista]] | Construído. Se a pessoa negar a permissão, o app avisa e segue |
| [[cadastro-do-artista]] | Parcial. A conta é enviada, mas a tela não abre as abas |
| [[entrar-senha-e-biometria-do-artista]] | Construído. A biometria também liga e desliga no perfil, se o aparelho tiver |
| [[inicio-do-artista]] | Parcial. O cartão é fixo (Karen Watanabe, 25 de Maio, 12h00). "Vamos agendar?" não faz nada |
| [[pedidos-do-artista]] | Casca. No centro, "Tab Orders" |
| [[agenda-do-artista]] | Casca. No centro, "Tab Schedules" |
| [[planos-do-artista]] | Casca. No centro, "Tab Plans" |
| [[perfil-do-artista]] | Construído. O menu está inteiro. "Editar Perfil" abre uma tela de "em breve". A nota do perfil precisa o pé: construído como menu, com destinos mistos |
| [[enderecos-do-artista]] | Parcial. No perfil, a tela diz que gerenciar endereços vem depois |
| [[avisos-ajuda-e-regras-do-artista]] | Parcial. A central de ajuda abre `https://wecareu.app/suporte` |
| [[o-que-ainda-nao-esta-no-app-do-artista]] | Não entregue |

## O que já é da conta e o que ainda é exemplo

**Já ligado à conta:** entrar, sair e manter a sessão; criar a conta (a entrada nas abas fica para a próxima abertura, ou para um login); recuperar a senha e trocar a senha no perfil; biometria na entrada e no perfil; no Início, "Olá" com apelido ou nome, foto e nota. Se a conta não trouxer nota, aparece 5,0. Sem foto, entra um avatar genérico. O endereço informado no cadastro vai com a conta. O perfil não o mostra de novo. As preferências de notificação ficam gravadas no aparelho. Sobre o app, termos de uso e política de privacidade estão na tela.

**Ainda exemplo, ou sem efeito:** o cartão **Próximos agendamentos** (Karen Watanabe, nota 4,5, 25 de Maio, Quarta, 12h00); os serviços desse cartão (Unha da Mão, Unha do Pé, Aplicação de pedra na unha, Botox, Unha Gel); o endereço "Rua B..., 504" e "Imirim - São Paulo, SP - BR", com olho fechado e menu que não respondem; **Vamos agendar?**; Pedidos, Agenda e Planos; editar perfil e gerenciar endereços, que só avisam "em breve".

A abertura promete perfil gratuito, sem comissão, clientes, agendamento automático, pagamento no app, escolha de horários e preços, check-in e check-out. Várias dessas telas não existem. A promessa fica na [[abertura-do-artista]] e em [[o-que-ainda-nao-esta-no-app-do-artista]]. É cópia do retrato. [[decisoes-2026-10-20]] prevalece.

Ver [[app-do-artista]].
