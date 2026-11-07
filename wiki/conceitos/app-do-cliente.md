---
tipo: conceito
criado: 2026-10-21
atualizado: 2026-10-21
fontes: ["[[mapa-do-app-do-cliente]]", "[[decisoes-2026-10-21]]", "[[primeira-entrada]]", "[[criar-conta]]", "[[entrar-senha-e-biometria]]", "[[encontrar-profissionais]]", "[[inicio]]", "[[meu-perfil]]", "[[enderecos]]", "[[avisos-ajuda-e-regras]]", "[[agenda]]", "[[conversa-do-agendamento]]", "[[o-que-ainda-nao-esta-no-app]]", "[[cruzamento-como-ler]]", "[[cruzamento-o-que-so-um-app-tem]]", "[[cruzamento-bff-como-ler]]", "[[cruzamento-bff-conta]]", "[[cruzamento-bff-o-que-a-tela-le]]", "[[cruzamento-bff-o-que-ninguem-pede]]", "[[board-conta-e-acesso]]", "[[board-listagem]]", "[[board-inicio-do-cliente]]", "[[board-perfil]]", "[[board-favoritos]]", "[[board-agendamentos-e-atendimento]]", "[[board-review]]", "[[board-estrutura-dos-apps]]"]
---

# App do cliente

Retrato de 21/10 do repositório `ui_client`. O app se chama **WeCareU**, versão marcada **1.0.0**. Textos em português e inglês; se faltar tradução, mostra o inglês. Não descreve o app de quem atende. Não é o alvo do [[mvp]], que mantém os dois apps em desenvolvimento. Se esta extração bater com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial. ([[mapa-do-app-do-cliente]])

Nenhuma destas doze extrações cita os pacotes do [[kit-visual]] nem `@wecareu/auth-flow`. Quem instala o quê está no cruzamento, mais abaixo. O percurso de entrar que o app mostra está em [[fluxo-de-entrada]].

## Dois jeitos de usar

**Sem conta.** Abertura com "Vamos começar?" e "Já tenho uma conta". Carrossel: localização, notificações e endereço, com número obrigatório. Depois a pessoa visita a lista. Fechar a lista volta à abertura e sai do modo visitante. ([[primeira-entrada]], [[encontrar-profissionais]]) A listagem deslogada **é alvo do [[mvp]]**: cadastrar só na hora de agendar. ([[decisoes-2026-10-21]]) O retrato abaixo continua sendo o que a tela fazia em 21/10, não o estado depois do alinhamento.

**Com conta.** Barra Início, Artistas, Agenda e Perfil. O Início abre primeiro. ([[mapa-do-app-do-cliente]])

Quem já ativou digital ou rosto pode entrar por aí na abertura, se a credencial for válida. ([[primeira-entrada]], [[entrar-senha-e-biometria]])

## Pé das áreas

| Área                      | Pé                                                                                                | Onde                            |
| ------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------- |
| Primeira entrada          | Construído, com falha na permissão de localização                                                 | [[primeira-entrada]]            |
| Criar conta               | Construído, com falha quando o CEP não é encontrado                                               | [[criar-conta]]                 |
| Entrar, senha e biometria | Construído, com falha no aviso de senha errada, na lista da nova senha e na biometria já salva    | [[entrar-senha-e-biometria]]    |
| Encontrar profissionais   | Parcial. Lista de exemplo                                                                         | [[encontrar-profissionais]]     |
| Início                    | Parcial. Cabeçalho da conta; cartão de exemplo; "Vamos agendar?" não faz nada                     | [[inicio]]                      |
| Meu perfil                | Parcial. Menu inteiro. Editar dados é "em breve". Senha e biometria funcionam, com ressalvas      | [[meu-perfil]]                  |
| Endereços                 | Parcial. CEP e localização no cadastro e na visita. Gerenciar no perfil é "em breve"              | [[enderecos]]                   |
| Avisos, ajuda e regras    | Parcial. A central de ajuda abre `https://wecareu.app/suporte`. Termos e privacidade estão no app | [[avisos-ajuda-e-regras]]       |
| Agenda                    | Casca. No centro, "Tab Schedules"                                                                 | [[agenda]]                      |
| Conversa do agendamento   | Casca. No centro, "Tab ChatSchedules". Nenhuma aba abre. Nenhum botão aponta                      | [[conversa-do-agendamento]]     |
| O que ainda não está      | Não entregue                                                                                      | [[o-que-ainda-nao-esta-no-app]] |

## O que já é da conta e o que é exemplo

**Da conta:** entrar, sair e a sessão; criar a conta; recuperar e trocar a senha; biometria na abertura e no perfil; nome, apelido e foto no Início, quando a conta os tem. A nota do Início cai em 5,0 se a conta não trouxer uma: isso é fallback de tela. Endereço no cadastro e na visita. ([[mapa-do-app-do-cliente]], [[inicio]])

**Exemplo, ou sem efeito:** os cinco artistas da lista, com foto, nota, distância e faixa de preço; o cartão de Karen Watanabe (25 de Maio, Quarta, 12h00, unhas e botox) e o endereço "Rua B..., 504, Imirim"; o botão **Vamos agendar?**; a Agenda; a conversa. ([[encontrar-profissionais]], [[inicio]], [[agenda]], [[conversa-do-agendamento]])

A lista não implementa o [[ranking]]. A fórmula definida continua fora dela.

## O que o código faz e o alvo não é

O [[cadastro]] do cliente é um chatbot, com os campos fechados em 05/11. Neste app, em 21/10, são três etapas de formulário (Acesso, Dados pessoais, Endereço), com gênero e sem telefone. ([[cadastro]], [[criar-conta]])

O [[agendamento]] do MVP continua chatbot sem texto livre. Aqui a agenda e a conversa são casca, e o botão do cartão não faz nada. ([[agenda]], [[conversa-do-agendamento]], [[inicio]])

Ainda não entregue, entre o que o app cita: a tela antiga de visitante ("Agende, siga e descubra talentos agora mesmo"); alterar e-mail (o texto existe, sem entrada no menu); central de ajuda dentro do app; escolher tipo de serviço ("Ir até você", "Ir ao local", "Para:"); o cadastro antigo SignUp, que não é o cadastro em uso. ([[o-que-ainda-nao-esta-no-app]])

## O que o cruzamento acrescenta

O cliente instala as doze peças do [[kit-visual]] e não instala o fluxo compartilhado. O artista não instala o kit nem o fluxo. O cliente está à frente só na cara das telas e no fim do cadastro: aqui a conta abre o Início; no artista a conta nasce e as abas não abrem nessa hora. No mesmo ponto estão editar dados e gerenciar endereços, "em breve" nos dois, o cartão de Karen Watanabe, e a agenda e a conversa, casca nos dois. Pedidos e Planos não existem neste app. O que só este app tem, neste retrato, é a visita sem conta e a lista de artistas. ([[cruzamento-como-ler]], [[cruzamento-o-que-so-um-app-tem]])

## O que este app pede ao backend

Pede a conta no mesmo backend do artista: abrir pela porta de cliente (POST `User`), entrar, as três portas de senha e sair. Ao reabrir, pergunta se a sessão vale em `login/user/valid`, caminho que este retrato do backend não publica. No Início, pede de novo a pessoa logada em `login/user/logged`, leitura que este retrato também não publica. O CEP do cadastro e da visita é consulta ao mapa da Google. O endereço da conta viaja dentro do cadastro. ([[cruzamento-bff-como-ler]], [[cruzamento-bff-conta]], [[cruzamento-bff-o-que-a-tela-le]])

Não pede serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação nem o que a pessoa pode ver. Essas portas estão no ar. Não tem aba de planos. Lista de artistas, agenda, conversa e o cartão do próximo atendimento não leem este backend. ([[cruzamento-bff-o-que-ninguem-pede]], [[cruzamento-bff-como-ler]])

Cabe no [[ecossistema-de-produtos]]. Conflitos com a decisão: [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

Do lado do cliente, o board pede o endpoint de login do cliente (350) e o cadastro de cliente (357), inclusive a tela em forma de chat (411) e a chamada de cadastro quando a pessoa deslogada toca home, favoritos, agendamentos ou perfil (450). As telas da história 421 não dizem de qual app são. Isso não descreve o retrato de 21/10 acima. ([[board-conta-e-acesso]])

O board também pede a listagem, a tela de início, o perfil e os favoritos. A história 145 pede carregar artistas por endereço para quem não está logado. Isso encontra a lista sem login, e o alvo permanece. A lista deste retrato continua exemplo. A integração pedida no board está New. O pedido da tela de início convive com o cartão de exemplo e com o botão que não faz nada. Consultar perfil no board convive com editar dados em breve. O sistema de [[favoritos]] está no board. A chamada de cadastro para quem está deslogado continua a da tarefa 450, e a lista sem login permanece. ([[board-listagem]], [[board-inicio-do-cliente]], [[board-perfil]], [[board-favoritos]])

O board pede a tela de agendamento do cliente (372), sem chat livre, e o check-in do atendimento residencial (épico 339). Agenda e conversa continuam casca. O alvo continua chatbot. ([[board-agendamentos-e-atendimento]]) Pede também review de atendimento e médias. Isso não fecha os detalhes da avaliação. ([[board-review]])

O board pede, em [[board-estrutura-dos-apps]], o início dos dois apps, o logo e o nome no client, e a reestruturação do App Client. A história 418 está Completed. As tarefas 419, 432 e 435 estão Completed. A história 427 está Completed. A história 428, configurar dados dos apps, está New. Agenda e conversa continuam casca. O cartão de exemplo permanece. O POST User permanece.
