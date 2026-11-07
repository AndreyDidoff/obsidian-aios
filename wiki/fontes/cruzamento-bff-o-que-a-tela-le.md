---
tipo: fonte
arquivo: "ingeridos/Cruzamento - BFF o que a tela lê.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 que cruza ui_client, ui_worker e service_api; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cruzamento — o que a tela lê"]
---

# Cruzamento — o que a tela lê

A porta é [[cruzamento-bff-como-ler]].

Depois da conta, quase tudo que a pessoa vê ou é exemplo, ou mora no aparelho, ou viaja uma vez dentro do cadastro.

## Nome, foto e nota no Início

A saudação tem de ser da pessoa, não de um exemplo. O topo de [[inicio]] e de [[inicio-do-artista]] mostra apelido ou nome, foto e nota. Se a conta não traz nota, a tela mostra 5,0. Se faltam apelido e nome, fica **Olá, !**.

Ao abrir o Início, os dois apps pedem de novo a pessoa logada. O caminho é `login/user/logged`. Este retrato do backend não publica essa porta. [[bff-entrar-sair-e-senha]] publica entrar, sair, saber se a sessão vale, e o fluxo de senha. Não publica esta leitura.

O que o app espera receber, se a resposta vier, é o nome, o apelido, a foto, a nota, o e-mail, o documento e um telefone. A tela do Início usa nome, apelido, foto e nota. O resto não aparece no Início.

O cartão **Próximos agendamentos**, com Karen Watanabe, não vem dessa leitura. É texto fixo nos dois apps. **Vamos agendar?** não pede nada. Ver [[cruzamento-dentro-da-conta]].

## Endereço

Há três endereços. Só um conversa com a WeCareU, e não pela porta de endereços.

O do cadastro diz onde a conta mora e cria a conta com esse local, em [[criar-conta]] e [[cadastro-do-artista]]. A rua e a cidade vêm da consulta de CEP, fora deste backend. O conjunto vai dentro do pedido de abrir conta, em [[bff-cadastro]]. Não passa por [[bff-enderecos]].

O da visita sem conta libera a lista de artistas, em [[primeira-entrada]], só no app do cliente. É a mesma consulta de CEP. Não grava conta. Não pede [[bff-enderecos]].

O do perfil é a pessoa a gerir os locais depois de entrar, em [[enderecos]] e [[enderecos-do-artista]]. Não lê nem grava. As duas telas dizem que em breve dá para gerenciar. A porta [[bff-enderecos]] está no ar e nenhum app a pede.

A pessoa informa o CEP para a tela completar rua e cidade. Os dois apps perguntam ao mapa da Google, não ao backend de apoio. Se o CEP não é encontrado, o cliente trava o fim do cadastro e o artista segue. Isso é comportamento da tela, não de [[bff-enderecos]]. Ver [[cruzamento-criar-conta]].

O endereço "Rua B..., 504" do cartão do Início também não é esta porta. É o exemplo fixo.

## O que fica no aparelho

O rascunho do cadastro fica no aparelho quando a pessoa sai no meio, nos dois cadastros. A senha e a foto não entram no rascunho. O backend não entra.

A sessão, para reabrir sem senha, é gravação local nos dois apps. A pergunta se ainda vale está em [[cruzamento-bff-conta]].

A biometria, para entrar com digital ou rosto, tem o reconhecimento no aparelho. A entrada, se segue, é a porta de entrar.

A preferência de notificação fica neste aparelho, em [[avisos-ajuda-e-regras]] e [[avisos-ajuda-e-regras-do-artista]]. Sair da conta, no cliente, não apaga. A nota do artista não diz se sair apaga.

## O que a tela mostra e não lê

Não há pedido ao backend.

- Lista de artistas, em [[encontrar-profissionais]]. Cinco nomes fixos. O endereço da visita não muda quem aparece.
- Agenda, nos dois. Só o título.
- Conversa do agendamento, nos dois. Sem caminho.
- Pedidos e Planos, só no artista. Casca. A porta de planos existe e não está ligada, em [[bff-planos-e-cupons]]. A aba nem pergunta.
- Editar perfil, nos dois. Aviso de em breve. Não lê a conta de volta para um formulário.
- Sobre, termos e privacidade. Texto escrito na tela, data dezembro de 2024.
- Central de ajuda. Abre o site, fora do app.

Ver [[beautiful-api]], [[app-do-cliente]], [[app-do-artista]].
