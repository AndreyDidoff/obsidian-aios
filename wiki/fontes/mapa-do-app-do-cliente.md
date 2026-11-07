---
tipo: fonte
arquivo: "ingeridos/Mapa do app do cliente.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_client; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Mapa do app do cliente"]
---

# Mapa do app do cliente

Porta desta leva. O app se chama **WeCareU**. Versão marcada **1.0.0**. Textos em português e inglês; se faltar tradução, o app mostra o inglês. Esta nota cobre só quem procura o serviço. Não descreve o app de quem atende.

Pé, como esta extração define:

| Pé | Significado |
|---|---|
| Construído | A pessoa percorre o fluxo. A conta, a senha e o endereço conversam com o serviço da WeCareU |
| Parcial | A tela existe e mostra alguma coisa, mas parte é exemplo fixo ou o botão não leva a lugar nenhum |
| Casca | A entrada existe. A tela só tem um título |
| Não entregue | O app cita a função, ou ela foi prevista, e não há tela em uso |

## Dois jeitos de usar

**Sem conta.** Na abertura, "Vamos começar?" e "Já tenho uma conta". Quem começa passa pelo carrossel: localização, notificações e endereço (o número é obrigatório). Só então visita a lista. Fechar a lista volta à abertura e sai do modo visitante.

**Com conta.** A barra de baixo tem Início, Artistas, Agenda e Perfil. O Início abre primeiro.

Quem já ativou digital ou reconhecimento facial pode entrar por aí na abertura, se o aparelho tiver o recurso e a credencial ainda for válida. Se falhar, o app manda para o login.

## As áreas

| Área | Pé |
|---|---|
| [[primeira-entrada]] | Construído |
| [[criar-conta]] | Construído |
| [[entrar-senha-e-biometria]] | Construído |
| [[encontrar-profissionais]] | Parcial. A lista é de exemplo. Não vem dos artistas de verdade |
| [[inicio]] | Parcial. O cartão é fixo (Karen Watanabe, 25 de maio, 12h, unhas e botox). "Vamos agendar?" não faz nada |
| [[agenda]] | Casca. Só o título |
| [[conversa-do-agendamento]] | Casca. Só o título. Não há caminho visível a partir das abas |
| [[meu-perfil]] | Parcial. O menu está inteiro. Editar dados é "em breve". Senha e biometria funcionam, com ressalvas na nota |
| [[enderecos]] | Parcial. CEP e localização funcionam no cadastro e na visita. Gerenciar no perfil é "em breve" |
| [[avisos-ajuda-e-regras]] | Parcial. A central de ajuda abre `https://wecareu.app/suporte`. Não é uma tela de dentro do app |
| [[o-que-ainda-nao-esta-no-app]] | Não entregue |

## O que já é da conta e o que ainda é exemplo

**Já ligado à conta:** entrar, sair e manter a sessão; criar a conta; recuperar e trocar a senha; biometria na entrada e no perfil; nome, apelido e foto no Início, quando a conta os tem. A nota mostrada cai em 5,0 se a conta não trouxer uma. Endereço no cadastro e na visita. A gestão no perfil ainda não lista nem edita nada.

**Ainda exemplo, ou sem efeito:** os artistas da lista; o próximo atendimento do Início, o endereço "Rua B..., 504, Imirim" e os serviços desse cartão; o botão de agendar; a Agenda; a conversa do agendamento.

## O que esta extração não cobre

App de quem presta o serviço. Regras comerciais, preços reais, pagamento e cancelamento. Catálogo oficial de serviços: o que aparece (unha da mão, unha do pé, pedra na unha, botox, unha gel) está escrito na tela de início como exemplo. Escolher o tipo de serviço está previsto e não tem tela. Alterar o e-mail: o texto existe, e não há entrada no menu. Uma tela antiga de visitante ("Agende, siga e descubra talentos agora mesmo") não entra em nenhum fluxo. O cadastro com o nome antigo "SignUp" não é o cadastro em uso.

Ver [[app-do-cliente]].
