---
tipo: conceito
criado: 2026-10-21
atualizado: 2026-10-21
fontes: ["[[mapa-do-app-do-artista]]", "[[abertura-do-artista]]", "[[cadastro-do-artista]]", "[[entrar-senha-e-biometria-do-artista]]", "[[inicio-do-artista]]", "[[pedidos-do-artista]]", "[[agenda-do-artista]]", "[[planos-do-artista]]", "[[perfil-do-artista]]", "[[enderecos-do-artista]]", "[[avisos-ajuda-e-regras-do-artista]]", "[[o-que-ainda-nao-esta-no-app-do-artista]]", "[[cruzamento-como-ler]]", "[[cruzamento-o-que-so-um-app-tem]]", "[[cruzamento-bff-como-ler]]", "[[cruzamento-bff-conta]]", "[[cruzamento-bff-o-que-a-tela-le]]", "[[cruzamento-bff-o-que-ninguem-pede]]", "[[board-conta-e-acesso]]", "[[board-agendamentos-e-atendimento]]", "[[board-review]]", "[[board-estrutura-dos-apps]]"]
---

# App do artista

Retrato de 21/10 do repositório `ui_worker`. O nome na loja é **WeCareU - Artistas**, versão marcada **1.0.0**. Textos em português e inglês; se faltar tradução, mostra o inglês. As cascas de Pedidos, Agenda e Planos ficam em inglês ("Tab Orders", "Tab Schedules", "Tab Plans") mesmo com o aparelho em português. É o app de quem atende. O retrato de quem procura o serviço está em [[app-do-cliente]]. Esta página não o reescreve. Não é o alvo do [[mvp]], que mantém os dois apps em desenvolvimento. Se esta extração bater com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial. ([[mapa-do-app-do-artista]])

A extração do artista não cita `@wecareu/auth-flow`. A extração do artista não cita o kit visual. O cruzamento dos quatro repositórios, mais abaixo, diz que este app não instala nenhum dos dois. O percurso de entrar que o app mostra está em [[fluxo-de-entrada]].

## Como se entra

Não há uso sem conta. Abertura com seis slides, localização, notificações, **Cadastrar** e **Já tenho uma conta**. Se a pessoa negar a permissão, o app avisa e segue. ([[abertura-do-artista]])

**Com conta.** Barra Início, Pedidos, Agenda, Planos e Perfil. O Início abre primeiro. Clientes não está na barra. A conversa do agendamento não está na barra. ([[mapa-do-app-do-artista]])

A biometria é pedida no primeiro login com senha e liga e desliga no perfil. A abertura não dispara a biometria sozinha. ([[entrar-senha-e-biometria-do-artista]])

## Pé das áreas

| Área | Pé | Onde |
|---|---|---|
| Abertura | Construído. Recusar permissão avisa e segue. Agenda, preço, check-in e pagamento são promessa de cópia | [[abertura-do-artista]] |
| Cadastro | Parcial. Cinco etapas criam a conta; a tela não abre as abas nem avisa sucesso; CEP sem resultado não avisa nem trava | [[cadastro-do-artista]] |
| Entrar, senha e biometria | Construído. Senha errada cai na mensagem genérica. A biometria não entra sozinha na abertura | [[entrar-senha-e-biometria-do-artista]] |
| Início | Parcial. Olá, nome, foto e nota; se não houver nota, 5,0, fallback de tela; cartão de exemplo; "Vamos agendar?" não faz nada | [[inicio-do-artista]] |
| Pedidos | Casca. No centro, "Tab Orders" | [[pedidos-do-artista]] |
| Agenda | Casca. No centro, "Tab Schedules" | [[agenda-do-artista]] |
| Planos | Casca. No centro, "Tab Plans". Não implementa [[planos-de-assinatura]] | [[planos-do-artista]] |
| Perfil | Construído como menu; destinos mistos. Editar Perfil é "em breve" | [[perfil-do-artista]] |
| Endereços | Parcial. O endereço do cadastro vai com a conta. Gerenciar no perfil é "em breve" | [[enderecos-do-artista]] |
| Avisos, ajuda e regras | Parcial. A central de ajuda abre `https://wecareu.app/suporte`. Notificações gravadas no aparelho | [[avisos-ajuda-e-regras-do-artista]] |
| O que ainda não está | Não entregue | [[o-que-ainda-nao-esta-no-app-do-artista]] |

O 5,0 do Início, quando a conta não traz nota, é fallback de tela. O item 17 de [[contradicoes-e-lacunas]] trata de outra nota e não muda com este retrato.

## O que já é da conta e o que é exemplo

**Da conta:** entrar, sair e a sessão; criar a conta, com a entrada nas abas na próxima abertura se a sessão valer; recuperar e trocar a senha; biometria no primeiro login e no perfil; nome, apelido e foto no Início, quando a conta os tem; o endereço informado no cadastro; as preferências de notificação neste aparelho. Sair pede confirmação (**Sair da WeCareU**) e volta à abertura. ([[mapa-do-app-do-artista]], [[perfil-do-artista]])

**Exemplo, ou sem efeito:** o cartão de Karen Watanabe (25 de Maio, Quarta, 12h00, unhas e botox) e o endereço "Rua B..., 504, Imirim"; **Vamos agendar?**; Pedidos; Agenda; Planos; editar perfil e gerenciar endereços. ([[inicio-do-artista]], [[pedidos-do-artista]], [[agenda-do-artista]], [[planos-do-artista]])

## Promessas da abertura que não têm tela

A abertura promete perfil gratuito, sem comissão, clientes, agendamento automático, pagamento no app, escolha de horários e preços, check-in e check-out. ([[abertura-do-artista]])

Não há tela de clientes na barra (existe uma casca "Tab Clients", sem caminho). Não há tela de horário, preço, check-in, check-out, pagamento nem mapa. A conversa existe como casca: o centro diz "Tab ChatSchedules" e nenhum botão a abre. [[conversa-do-agendamento]] não descreve este app. ([[o-que-ainda-nao-esta-no-app-do-artista]], [[agenda-do-artista]])

Nenhum pagamento está construído. Ícone ou slide não é cobrança. A aba Planos não é [[planos-de-assinatura]]. A promessa na tela é fato do retrato. A decisão permanece: MVP gratuito, sem pagamento no lançamento. ([[decisoes-2026-10-20]], [[pagamentos]])

O detalhe de tela do cadastro do artista não chegou. Neste app, em 21/10, são cinco etapas de formulário (dados pessoais, foto, endereço, confirmação, acesso), com gênero e sem telefone. ([[cadastro-do-artista]])

O [[agendamento]] do MVP continua chatbot sem texto livre. Aqui a agenda é casca, a conversa não tem caminho, e o botão do cartão não faz nada.

## O que o cruzamento acrescenta

Este app não instala o [[kit-visual]] nem o fluxo compartilhado. Campos, botões e textos nascem aqui. Está atrás só onde o mesmo percurso já andou no cliente: a cara das telas, e o fim do cadastro, em que a conta é criada e as abas não abrem nessa hora. No mesmo ponto estão o "em breve" de editar dados e de endereços, o cartão de Karen Watanabe, e a agenda e a conversa, casca nos dois. Pedidos e Planos existem só aqui, e ainda são casca. Não há visita sem conta. ([[cruzamento-como-ler]], [[cruzamento-o-que-so-um-app-tem]])

## O que este app pede ao backend

Pede as mesmas ações de conta que o cliente, no mesmo backend, e também pela porta de cliente: POST `User`. A porta de profissional, POST `Artist`, existe e este app não a pede. O vínculo de empresa e aplicativo não entra no pedido. Ao criar a conta, a sessão fica guardada e esta tela não marca a pessoa como dentro. Entrar, as três portas de senha e sair mapeiam para [[bff-entrar-sair-e-senha]]. Ao reabrir, pergunta a sessão em `login/user/valid`. No Início, pede a pessoa logada em `login/user/logged`. Nenhum desses dois caminhos está nas portas deste retrato. O CEP do cadastro é consulta ao mapa da Google. ([[cruzamento-bff-como-ler]], [[cruzamento-bff-conta]], [[cruzamento-bff-o-que-a-tela-le]])

Não pede serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação nem o que a pessoa pode ver. A aba Planos nem chega a perguntar a porta de planos e cupons, que existe sem ligação. Pedidos, agenda e o cartão do próximo atendimento não leem este backend. ([[cruzamento-bff-o-que-ninguem-pede]], [[cruzamento-bff-como-ler]])

Cabe no [[ecossistema-de-produtos]], ao lado de [[app-do-cliente]]. O profissional está em [[artista]]. Conflitos com a decisão: [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

Do lado do artista, o board pede o endpoint de login do artista (351) e o cadastro de artista (360), inclusive a tela em forma de chat (416) e o endpoint no nome WeCareU.API (361). A história 360 está Blocked no board. O comentário diz que aguarda o término do app de cliente. Há história sem pai de tela de cadastro do artista (223). Isso não mostra que este app usa POST Artist. O retrato de 21/10 acima permanece. ([[board-conta-e-acesso]])

O board pede a tela de agendamento do artista (375), aceitar ou recusar (379) e importar agendamentos de outras plataformas (380). Agenda continua casca. A conversa continua sem caminho. O alvo continua chatbot. Importar é pedido do board, não decisão de integração. O épico 339 pede check-in e check-out. Não há tela de check-in neste retrato. ([[board-agendamentos-e-atendimento]]) Pede a média geral do artista (390). A nota 5,0 do Início, quando a conta não traz nota, continua fallback de tela. ([[board-review]])

O board pede, em [[board-estrutura-dos-apps]], o início no worker, o logo, o nome e a reestruturação. A tarefa 420 está Completed. A tarefa 433, logo no App Worker, está New e sem responsável. A tarefa 436, nome no ui_worker, está New e sem responsável. A história 476 está New. A tarefa 477 está Blocked. Pedidos, Agenda e Planos continuam casca. O app segue em POST User.
