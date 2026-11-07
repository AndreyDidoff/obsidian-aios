---
tipo: cruzamento
tema: O que deveria ser uma peça só
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza o app do cliente, o app do artista, o kit visual e o fluxo compartilhado de entrar na conta. Descreve o que já está construído, em que pé está e onde a mesma experiência aparece mais de uma vez. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — o que deveria ser uma peça só

## Isto é uma direção, não uma decisão

O que está duplicado hoje deveria, no futuro, morar numa peça só e ser instalada nos dois apps. Hoje não está assim.

Esta nota registra uma direção de manutenção pedida neste retrato de 21/10/2026. A empresa não tomou essa decisão. Se o que está aqui conflitar com uma decisão oficial, vale a oficial.

Cada app conta a própria cópia de percursos que a pessoa reconhece como o mesmo: entrar, recuperar a senha, o cartão do início, o menu do perfil, a ajuda e os textos legais. O kit visual já existe, e só o app do cliente o usa. A casa dos percursos já tem uma peça de entrar na conta, e nenhum dos dois apps a instalou.

## Duas casas

A cara da tela e o percurso da pessoa não moram no mesmo lugar.

A cara é botão, campo, texto, ícone, cor, data, lista e espera. Essa casa é o kit visual, no repositório library-design-system. Já existe. O panorama está em [[Panorama do design system]]. O app do cliente instala as doze peças. O app do artista não instala nenhuma. Falta o artista passar a usar o kit. O fluxo compartilhado de entrar usa um pedaço dessa cara: texto, botões, campo, ícones, tema e fechar. Não usa data, lista nem máscara.

O percurso que é o mesmo nos dois apps — entrar, recuperar senha, início, menu do perfil, ajuda e textos legais — é peça de fluxo, no repositório library-components, para ser instalada nos dois. Hoje essa casa só tem o fluxo de entrar, o @wecareu/auth-flow na versão 0.1.0, e ele não está instalado no cliente nem no artista. O que essa peça entrega está em [[library-components-o-que-entrega]].

A coluna "casa certa" da tabela segue esta direção. Não é uma decisão já tomada.

## O que aparece mais de uma vez

| Experiência | Hoje | Casa certa | Por que ainda não é uma peça |
|-------------|------|------------|------------------------------|
| Kit visual no artista | O kit existe e o cliente já veste as telas com as doze peças. O artista não instala nenhuma. Entrar, cadastro, início e perfil desenham botão, campo e texto por conta própria. | Kit visual | A casa já existe. O app do artista ainda não passou a usá-la. Enquanto isso, a mesma cara nasce nos dois apps. |
| Entrar, senha e biometria | Cada app tem o próprio entrar, recuperar senha e biometria. Os dois usam o título "Vamos entrar na sua conta:" e, quando a senha nova dá certo, avisam "Senha alterada com sucesso! Faça login com sua nova senha." A peça compartilhada se chama "Entre na sua conta". O link de cadastro não faz nada. O sucesso da senha nova não aparece. Nenhum dos dois apps a instalou. Ver [[Entrar, senha e biometria]] e [[Entrar, senha e biometria do artista]]. | Peça de fluxo | Cliente e artista estão mais próximos entre si do que dessa peça. Ela ainda tem esses buracos. Colocá-la no lugar do que já está em uso mudaria títulos e esconderia o aviso de senha alterada. |
| Criar conta | Não é a mesma tela. O cliente faz três etapas, acesso, dados pessoais e endereço, e a foto entra nos dados pessoais. Ao concluir, abre o [[Início]]. O artista faz cinco etapas, dados pessoais, foto, endereço, confirmação do endereço e acesso, e não abre as abas. Ver [[Criar conta]] e [[Cadastro do artista]]. | Peça de fluxo, depois de alinhar os dois percursos | Candidata, não peça pronta. Unir agora congelaria duas jornadas. Primeiro os percursos precisam ser o mesmo. |
| Cartão do início | Os dois mostram o mesmo cartão fixo: Karen Watanabe, 25 de maio, 12h, unhas e botox. "Vamos agendar?" não faz nada. O topo, olá, foto e nota, vem da conta nos dois, e a nota cai em 5,0 quando a conta não traz uma. Ver [[Início]] e [[Início do artista]]. | Peça de fluxo, quando o cartão for um atendimento de verdade | O que se repete é um exemplo escrito na tela, não um horário da pessoa. A casa de fluxo ainda não tem início. Compartilhar o exemplo só espalharia o cartão falso. |
| Menu do perfil | A mesma lista nos dois: editar, senha, biometria, endereços, notificações, ajuda, sobre, termos, privacidade e sair. Editar dados e gerenciar endereços estão "em breve" nos dois. Sair pede a mesma confirmação, "Sair da WeCareU". Ver [[Meu perfil]] e [[Perfil do artista]]. | Peça de fluxo | A lista está copiada em cada app. A casa de fluxo não tem perfil. Dois destinos ainda não são tela de verdade, então o menu inteiro ainda não é um percurso fechado. |
| Ajuda, sobre, termos e privacidade | A ajuda abre https://wecareu.app/suporte nos dois. Sobre, termos e privacidade existem nos dois. Os textos legais trazem a data dezembro de 2024. O Sobre repete a mesma frase de apresentação e mostra o nome de cada app: WeCareU no cliente, WeCareU - Artistas no artista. As preferências de aviso também se repetem, cinco interruptores nos mesmos grupos, com a escolha guardada no aparelho. Um nome muda: no cliente, artistas que a pessoa segue; no artista, artistas favoritos. Ver [[Avisos, ajuda e regras]] e [[Avisos, ajuda e regras do artista]]. | Peça de fluxo | O texto e a ajuda estão escritos duas vezes, dentro de cada perfil. A casa de fluxo não tem essas telas. O nome no Sobre muda com o app. Isso é rótulo, não outro documento. |
| Agenda e conversa | Casca nos dois. A agenda é uma aba sem horário. A conversa do agendamento existe como tela e não tem caminho visível a partir das abas. O cartão do início não abre nenhuma das duas. | Peça de fluxo, quando houver percurso | Não há o que compartilhar. Uma casca repetida não é uma experiência. |
| Pedidos e planos | Só existem no artista, e são casca. O cliente não tem essas áreas. O artista não está atrás nelas: não há percurso correspondente no outro app. | Nenhuma casa compartilhada | Não é duplicata. Não há o que unir enquanto só um app tiver a área. |

## Onde o artista está atrás

Só onde o mesmo percurso existe e o cliente já andou mais. Não vale para o app inteiro.

A cara das telas. O cliente já usa o kit visual. O artista ainda não. O mesmo tipo de tela, entrar, cadastro, início e perfil, não veste o kit.

O fim do cadastro. Os dois criam a conta no serviço da WeCareU. No cliente, a pessoa entra e o app abre o Início. No artista, a sessão fica guardada, a tela não avisa sucesso e não abre as abas. A entrada fica para a próxima abertura, se a sessão ainda valer. Se a criação falha, o cliente mostra um aviso. O artista não mostra frase.

O CEP que não é encontrado, no mesmo cadastro. No cliente, a conta não se conclui. No artista, a etapa segue, e a conta pode nascer com rua e cidade em branco. O cliente ainda não explica isso: a frase está escrita e não aparece. O que o cliente já faz a mais, aqui, é não concluir.

Na troca de senha de quem já entrou, não há esse atraso. Os dois percursos existem. Nesse ponto o cliente ainda deixa um rótulo cru no aviso de sucesso e não preenche os segundos da espera para reenviar o código.

## Onde não é atraso

Pedidos e Planos. Só o artista tem essas abas, e as duas são casca. O cliente não as tem. Não existe, no cliente, um percurso em que ele tenha avançado e o artista tenha ficado para trás.

A etapa de foto do cadastro. O artista separa a foto numa etapa. O cliente pede a foto dentro dos dados pessoais. Os dois exigem a foto, e nos dois ela vem da galeria. A etapa a mais não é o cliente ter passado na frente.

A abertura em slides. O artista abre com seis slides, pede localização e notificações, e não tem uso sem conta. O cliente tem outra porta, com visita sem conta. São entradas diferentes. A biometria que tenta entrar sozinha ao abrir também é da porta do cliente. No artista, a pessoa vê os slides, toca "Já tenho uma conta" e só então encontra "Entrar com Biometria".

## Notas ligadas

[[Mapa do app do cliente]] [[Mapa do app do artista]] [[Panorama do design system]] [[library-components-o-que-entrega]]

[[Criar conta]] [[Cadastro do artista]] [[Entrar, senha e biometria]] [[Entrar, senha e biometria do artista]] [[Início]] [[Início do artista]] [[Meu perfil]] [[Perfil do artista]] [[Avisos, ajuda e regras]] [[Avisos, ajuda e regras do artista]]
