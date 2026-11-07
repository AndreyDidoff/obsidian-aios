# Índice

Catálogo de todas as páginas da wiki: link, resumo de uma linha, número de fontes. Lido primeiro em toda query; atualizado em todo ingest.

Ponto de partida: [[visao-geral]].

## Sínteses

| Página | Resumo | Fontes |
|---|---|---|
| [[visao-geral]] | O que é a WeCareU, a aposta, o MVP do cliente fechado em 05/11, o mesmo backend nos dois apps; teste local até 31/12/2026 | 39 |
| [[contradicoes-e-lacunas]] | Índice por tema; do MVP: conta, agendamento, busca, avaliação e escopo | 116 |
| [[contradicoes-conta]] | Do MVP. Conta, cadastro, sessão, SMS e 2FA. Itens 2, 14, 15, 25, 28, 29, 34 | 1 |
| [[contradicoes-agendamento]] | Do MVP. Contato, chat, endereço e lembretes. Itens 4, 13, 16, 33 | 1 |
| [[contradicoes-busca]] | Do MVP. Ranking e card. Itens 9, 19, 31 | 1 |
| [[contradicoes-avaliacao]] | Do MVP. Avaliação, sanção e denúncia. Itens 17, 32, 35 | 1 |
| [[contradicoes-escopo]] | Do MVP. O que entra, o que fica fora e o que precisa estar pronto antes. Itens 1, 3, 5, 10, 11, 12, 26, 30 | 1 |
| [[contradicoes-negocio]] | Fora do produto do MVP. Capital, redação e missão. Itens 6, 7, 8 | 1 |
| [[contradicoes-kit]] | Fora do produto do MVP. Kit visual. Itens 20, 21, 22, 23, 24, 27 | 1 |
| [[contradicoes-engenharia]] | Fora do produto do MVP. Monorepo, código, e-mail, sessão, board e bancos. Item 18 | 1 |

## Entidades

| Página | Resumo | Fontes |
|---|---|---|
| [[wecareu]] | A empresa: marketplace de beleza em MVP, sem comissão, pede R$ 1M | 7 |
| [[Andrey Didoff]] | Cofundador; responsável por quase todas as pendências; no board, épico 329 | 3 |
| [[bruno]] | Cofundador; divide e-mails e criptografia; no board, história 343 | 3 |

## Conceitos

| Página | Resumo | Fontes |
|---|---|---|
| [[mvp]] | Alvo do cliente fechado em 05/11; teste local dos dois apps até 31/12/2026; lançamento em São Paulo em 01/01/2027; ajustes em `wiki/pendencias/` | 28 |
| [[artista]] | O profissional; app WeCareU - Artistas 1.0.0; a abertura promete o que a tela ainda não faz | 8 |
| [[estabelecimento]] | Salões e locais de beleza: gestão web, atendimento imediato do dia | 5 |
| [[missao-e-posicionamento]] | Três versões da missão; comunidade em vez de agenda | 3 |
| [[modelo-de-receita]] | Zero comissão; planos premium (20%) e publicidade; R$ 1M e ROI de 12–24 meses; cobrança do board fica fora do lançamento | 8 |
| [[ranking]] | Spec v0.3.1 permanece; no cliente o card não mostra horário nem a data do grupo B | 18 |
| [[planos-de-assinatura]] | Planos definidos, fora do lançamento gratuito; a porta existe e o serviço não está ligado; sem host de planos no núcleo; a aba continua casca; o board não traz preço | 9 |
| [[atendimento-imediato]] | Janela de 1–2 h para preencher furos; trava de agenda, check-in, penalidade | 4 |
| [[programa-de-pontos]] | Gamificação estilo Waze/Shopee, VIP, validade de 12 meses, missões de marca | 4 |
| [[busca-e-filtros]] | Lista sem conta; ao chegar, sem data, categoria nem serviço; card sem horário | 12 |
| [[favoritos]] | O board pede gerir favoritos; a tarefa 450 trata deslogado como chamada de cadastro; a lista sem login permanece | 4 |
| [[agendamento]] | Reserva instantânea em chatbot; cadastro antes da retenção de 10 minutos | 20 |
| [[avaliacoes]] | No cliente, opcional, 7 dias, no cartão; "não compareceu" não retém nota | 14 |
| [[cadastro]] | No cliente: chatbot, CPF, quatro botões de sexo, 18 anos, foto, sem SMS | 22 |
| [[seguranca-do-atendimento]] | No cliente, bloqueio sem desbloqueio pelo usuário; sanção do MVP só por suspensão | 27 |
| [[protecao-de-dados]] | LGPD; 2FA é alvo do MVP; o código de senha do serviço de conta não expira de fato; o rastro do núcleo segue só preparado | 20 |
| [[pagamentos]] | Nenhum no MVP; o board pede cobrança e não escolhe gateway; no núcleo a cobrança está sem ação; depois, planos e serviço sem comissão | 12 |
| [[publicidade-e-marcas]] | Receita B2B com marcas; coletar dados antes de vender | 4 |
| [[ia-no-dispositivo]] | Ideias de IA local: desfoque de rosto, antes/depois, ficha, OCR de estoque | 1 |
| [[ecossistema-de-produtos]] | Apps nomeados; retrato 1.0.0 do cliente e do ui_worker; o board pede Expo nos dois apps; Flutter sem pai não entra no MVP | 14 |
| [[lyraui]] | Em discovery; o legado `@wecareu/*` tem retrato de 12 pacotes em 21/10; o board pede biblioteca; pedir tela no Figma não cria a tela no app | 11 |
| [[kit-visual]] | Kit construído; o cliente instala as doze e o artista não; a LyraUI segue o alvo; o board pede biblioteca; pedir tela no Figma não cria a tela no app | 19 |
| [[fluxo-de-entrada]] | `@wecareu/auth-flow` 0.1.0 existe e não está instalado; sessão de 48 h e 7 dias no serviço de conta; o item 24 segue aberto | 18 |
| [[app-do-cliente]] | Retrato de 21/10 do ui_client; o board pede conta, listagem, perfil, favoritos e a estrutura (início, logo, nome, reestruturação); lista, agenda e conversa não leem este backend | 27 |
| [[app-do-artista]] | Retrato de 21/10 do ui_worker; o board pede login, cadastro e a estrutura (início, logo, nome, reestruturação); o app segue em POST User | 22 |
| [[fundamentos-visuais]] | Alvo CLIENT light / WORKER dark; kit de 21/10 com tokens 0.2.8 e Livvic | 5 |
| [[voz-e-escrita]] | No cliente: Artista, categoria no lugar de ofício, sem ponto final na tela | 7 |
| [[figma-lyraui]] | Padrões, file key, variáveis e regras de API/MCP; o board pede telas no Figma e o file key permanece | 4 |
| [[engenharia-de-software]] | BFF confirmado; monorepo em aberto; onze bancos SQL e quatro Mongo em 21/10, sem chave estrangeira | 33 |
| [[beautiful-api]] | BFF `service_api`; 18 microserviços e hosts permanecem; a regra mora em [[bpt-core]]; onda 5 no núcleo; `Br.PaymentPlan.API` segue sem URL; onze bancos SQL e quatro Mongo | 44 |
| [[bpt-core]] | Núcleo dos microserviços por trás do BFF; o app fala com api.wecareu.app; foto de 21/10, ondas 1 a 5; nenhuma nota do núcleo segue sem página | 20 |
| [[lancamento-e-marketing]] | Lançamento público: São Paulo inteira, 01/01/2027; quantidade de artistas e orçamento sem número | 5 |
| [[termos-e-responsabilidades]] | Posição jurídica de intermediária; o texto de dezembro de 2024 no app é texto errado; o texto novo segue diferido | 4 |

## Pendências

Ajuste para o produto do MVP chegar ao alvo. A superfície diz onde o ajuste mora.

| Página | Resumo | Superfície |
|---|---|---|
| [[backend-mvp-listagem]] | Comparativo do que mudar na listagem, no perfil e no endereço | backend |
| [[backend-mvp-agendamento]] | Comparativo do que mudar no pré-agendado, na confirmação e no cancelamento | backend |
| [[backend-mvp-conta]] | Comparativo do que mudar na sessão, no sexo, na exclusão, no bloqueio e na sanção | backend |
| [[backend-mvp-avaliacao-e-avisos]] | Comparativo do que mudar na nota, no não compareceu, nos lembretes e nos pushes | backend |
| [[backend-mvp-fundacoes]] | Comparativo do que mudar na API, nos bairros, na tag Novo, no SMS e no push | backend |
| [[app-cliente-conta]] | Comparativo do que mudar em welcome, cadastro, login, sessão, biometria e exclusão | app-cliente |
| [[app-cliente-descoberta]] | Comparativo do que mudar em home, listagem, card, perfil do artista e endereço | app-cliente |
| [[app-cliente-agendamento]] | Comparativo do que mudar no chat, no cartão, na agenda, no cancelamento, na avaliação e nos pushes | app-cliente |
| [[app-cliente-copys]] | Comparativo da copy que o retrato mostra; termos de dezembro de 2024 saem da tela | app-cliente |

## Fontes

| Página | Resumo |
|---|---|
| [[decisoes-2026-11-05]] | Teste local até 31/12/2026; o pacote 00 a 07 é o alvo; retrato divergente vira pendência |
| [[decisoes-2026-11-03]] | O pacote fecha o conjunto de funções e telas; o detalhe de cada tela vem depois; recomendação não vira decisão |
| [[decisoes-2026-10-21]] | Alvo do MVP manda; lista sem login; avaliação obrigatória; 2FA nos apps; endereço do cliente ainda em aberto |
| [[decisoes-2026-10-20]] | Decisões do usuário (4 rodadas): escopo do MVP, chatbot, app gratuito, cadastro em duas etapas, ranking definido, taxa do cartão paga pelo Artista |
| [[brainstorming-wecareu]] | Requisitos: segurança, pesquisa, cadastro, reviews, gateways |
| [[missao-e-valor]] | Missão, visão, posicionamento, planos como investimento na arte |
| [[pendencias]] | Tarefas e responsáveis: e-mails, criptografia, 7 apps/sites |
| [[plano-de-negocios-interno]] | Plano de negócio para os fundadores; investimento zero |
| [[plano-de-negocios-investidores]] | Plano para captação: R$ 1M, ROI de 12–24 meses, stack |
| [[planos-para-o-futuro]] | Backlog extenso de ideias (B2B, IA, gamificação, UX) |
| [[planos]] | Definição dos planos; atendimento imediato detalhado |
| [[politica-de-privacidade]] | Rascunho de política LGPD |
| [[seguranca-e-protecao-de-dados]] | Recomendações técnicas de segurança |
| [[termos-de-uso-do-app]] | Rascunho dos termos de uso |
| [[lyraui-01-visao-geral]] | LyraUI em discovery; alvo da virada de chave |
| [[lyraui-02-contexto-wecareu]] | Negócio para o time de design; gateway Stripe/MercadoPago a confirmar |
| [[lyraui-03-estado-atual]] | O que estaria em produção em maio de 2026 e o que está na esteira |
| [[lyraui-04-arquitetura]] | Atomic Design alvo, DoD e cadeia de dependência |
| [[lyraui-05-sistema-de-tema]] | CLIENT light, WORKER dark, tema não escolhível |
| [[lyraui-06-catalogo-legado]] | 13 pacotes `@wecareu/*`, auth-flow e telas dos dois apps |
| [[lyraui-07-figma-padroes]] | Nomes, páginas, variáveis e changelog do Figma |
| [[lyraui-08-figma-api]] | File key, bindings e IDs parciais de variáveis |
| [[lyraui-09-fundamentos-visuais]] | Cores, Livvic, Phosphor ainda candidato |
| [[lyraui-10-voz-e-tons]] | Voz, quatro tons, 1ª pessoa do plural |
| [[lyraui-11-escrita]] | Sem ponto final na tela; regras de negrito e itálico |
| [[lyraui-12-principios]] | Aprendizagem, Evolução, Interatividade, Amizade |
| [[lyraui-13-glossario]] | Glossário oficial de design e termos extras não oficiais |
| [[lyraui-14-ferramentas]] | Figma, ZeroHeight, Cursor, Claudinho, Obsidian |
| [[ssot-produto-negocios]] | Ambientes, pontos avulsos, shadow testing |
| [[ssot-ecossistema-engenharia]] | Stack, monorepo Turborepo, regras de código |
| [[ssot-design-system]] | LyraUI sem código; voz em versão curta |
| [[ssot-automacao]] | Kanban, lock por grafo, Yalc, Jest e Maestro |
| [[ssot-sdd]] | Cinco fases do SDD v3 para agentes |
| [[ssot-termos-legais]] | LGPD, 3DS, shadowban, MFA no admin |
| [[ssot-backlog]] | Pós-MVP, gateways, dívida Jest vs Maestro; "sem chat" |
| [[listagem-e-algoritmo-de-busca]] | Filtro, score, fura-fila e desempate |
| [[spec-ranqueamento-listagem]] | Fórmula de 20/10, substituída: +10.000, nota × 1.000, penalidade aos 50 |
| [[spec-busca-e-ranqueamento]] | Spec v0.3.1: faixas, nota bayesiana, grupo por data; fonte vigente do ranking |
| [[mvp-memoria-indice]] | Porta do pacote de 03/11: funções do MVP e spec de busca |
| [[mvp-final]] | Conjunto fechado de funções do Release 1; lançamento em São Paulo em 01/01/2027 |
| [[mvp-e-releases]] | Inventário, hipóteses e releases; onde discorda do fechamento, vale o fechamento |
| [[mvp-mudancas-na-spec]] | O que o MVP muda na spec v0.3.1; recomendações que não viraram decisão |
| [[mvp-revisao-riscos]] | Revisão que produziu o fechamento; equipe de dois e o que ficou como recomendação |
| [[mvp-funcoes-e-telas]] | Detalhe do cliente fechado; artista e painel seguem inventário; pontos para o Bruno |
| [[mvp-alteracoes-pos-congelamento]] | Delta do cliente sobre 00 a 04 e sobre a spec; onde muda, o cliente prevalece |
| [[mvp-copys-cliente]] | 16 fluxos aprovados; só o bloco de textos finais é alvo |
| [[divisao-atomic-design]] | Dois monorepos: library-design-system e library-components |
| [[panorama-do-design-system]] | Porta do kit: WeCareU Design System, 12 pacotes; o README da raiz ficou para trás |
| [[identidade-visual]] | Tokens 0.2.8 e theme 0.3.4; Livvic, roxo, claro e escuro; sem página nem teste |
| [[vocabulario-visual]] | 69 ícones em 1.3.3; bandeira e três animações parciais |
| [[textos-da-interface]] | text-wcu 0.2.4 parcial; quatro papéis; a escala display fica na identidade |
| [[acoes]] | Três botões parciais; a página do degradê ainda fala como o link |
| [[campos-de-formulario]] | Campo livre 0.2.7 e máscaras 0.2.4, prontos; cartão só formata |
| [[escolha-em-lista]] | select 0.2.7; o panorama diz Pronto; os exemplos estão em inglês |
| [[datas]] | date-picker 0.2.6 pronto; calendário em português |
| [[espera-e-carregamento]] | loading 0.4.4 pronto; véu e animação de pontos |
| [[como-o-time-revisa-a-interface]] | storybook-web e playground, sem escopo `@wecareu`; o celular não é vitrine |
| [[library-components-o-que-entrega]] | Porta do fluxo: `library-components` não é o app; `@wecareu/auth-flow` 0.1.0 |
| [[library-components-entrar-na-conta]] | Tela "Entre na sua conta"; cadastro morto; o login ignora o sucesso da senha nova |
| [[library-components-recuperar-senha]] | Três telas; código de 6; reenvio de 2 min; erros que não entram na tela |
| [[library-components-biometria-e-sessao]] | MD5 no lugar da senha; a credencial sobrevive ao sair; renovação não é automática |
| [[library-components-em-que-pe-esta]] | Pronto, parcial e só no papel; este repositório não evidencia instalação |
| [[mapa-do-app-do-cliente]] | Porta do app do cliente: WeCareU 1.0.0; dois jeitos de usar; pé de cada área |
| [[primeira-entrada]] | Abertura, carrossel e visita sem conta; a permissão de localização grava invertida |
| [[criar-conta]] | Três etapas construídas; CEP não encontrado trava; não é chatbot |
| [[entrar-senha-e-biometria]] | Login, código, nova senha e biometria; a extração não cita @wecareu/auth-flow |
| [[encontrar-profissionais]] | Lista parcial de exemplo: foto, nota, distância e faixa de preço |
| [[inicio]] | Parcial: nome e foto da conta; cartão fixo de Karen Watanabe; "Vamos agendar?" não faz nada |
| [[meu-perfil]] | Menu inteiro; editar dados é "em breve"; senha, biometria e sair, com ressalvas |
| [[enderecos]] | CEP e localização no cadastro e na visita; gerenciar no perfil é "em breve" |
| [[avisos-ajuda-e-regras]] | Ajuda abre o site; termos e privacidade estão no app, com data dezembro de 2024 |
| [[agenda]] | Casca: no centro, "Tab Schedules" |
| [[conversa-do-agendamento]] | Casca: no centro, "Tab ChatSchedules"; nenhuma aba abre |
| [[o-que-ainda-nao-esta-no-app]] | Visitante antiga, alterar e-mail, ajuda interna, tipo de serviço, SignUp, cascas |
| [[mapa-do-app-do-artista]] | Porta do app do artista: WeCareU - Artistas 1.0.0; sem uso sem conta; pé de cada área |
| [[abertura-do-artista]] | Seis slides, localização e notificações; a cópia promete o que a tela ainda não tem |
| [[cadastro-do-artista]] | Cinco etapas parciais; a conta nasce e a tela não abre as abas; CEP sem aviso |
| [[entrar-senha-e-biometria-do-artista]] | Login, código, nova senha e biometria; a extração não cita @wecareu/auth-flow |
| [[inicio-do-artista]] | Parcial: olá, nome e foto; cartão fixo de Karen Watanabe; "Vamos agendar?" não faz nada |
| [[pedidos-do-artista]] | Casca: no centro, "Tab Orders" |
| [[agenda-do-artista]] | Casca: no centro, "Tab Schedules"; a conversa existe sem caminho |
| [[planos-do-artista]] | Casca: no centro, "Tab Plans"; não implementa os planos de produto |
| [[perfil-do-artista]] | Menu inteiro; editar perfil é "em breve"; sair pede confirmação |
| [[enderecos-do-artista]] | O endereço do cadastro vai com a conta; gerenciar no perfil é "em breve" |
| [[avisos-ajuda-e-regras-do-artista]] | Ajuda abre o site; notificações no aparelho; termos com data dezembro de 2024 |
| [[o-que-ainda-nao-esta-no-app-do-artista]] | Clientes, conversa, check-in, pagamento e mapa, sem tela em uso |
| [[cruzamento-como-ler]] | Porta dos cruzamentos: quatro peças; o fluxo 0.1.0 existe e não está instalado |
| [[cruzamento-kit-visual]] | O cliente instala as doze; o artista não; o pé da lista e dos ícones fica com a nota da peça |
| [[cruzamento-entrar-senha-e-biometria]] | Três percursos; cliente e artista mais perto entre si do que da peça compartilhada |
| [[cruzamento-criar-conta]] | Três etapas no cliente, cinco no artista; não há peça compartilhada de cadastro em uso |
| [[cruzamento-dentro-da-conta]] | Início e menu no mesmo ponto; editar e endereços "em breve" nos dois |
| [[cruzamento-o-que-so-um-app-tem]] | Visita e lista só no cliente; Pedidos e Planos só no artista; agenda e conversa casca nos dois |
| [[cruzamento-o-que-deveria-ser-uma-peca-so]] | Direção deste retrato, não decisão: cara no kit, percurso numa peça de fluxo |
| [[bff-o-que-e-este-backend]] | Porta do BFF: `service_api`, Beautiful, prefixo `beautiful/api/`; escala de pé |
| [[bff-cliente-e-profissional]] | Dois papéis no cadastro: cliente (User) e profissional (Artist) |
| [[bff-preparado-e-ainda-nao-oferecido]] | Só preparado e fora de uso; canal de e-mail fora da compilação |
| [[bff-entrar-sair-e-senha]] | Caminho `beautiful/api/Login`: entrar, sair, sessão e quatro passos de senha; este backend não envia o e-mail |
| [[bff-cadastro]] | Caminho `beautiful/api/Register`: POST User, POST Artist, e-mail, CPF e CNPJ; campos fora deste repositório |
| [[bff-servicos]] | Porta de serviços no ar, com ressalva: listar e apagar conferem a pessoa; criar e editar, nas duas famílias, não |
| [[bff-planos-e-cupons]] | Porta sem ligação: a ação existe, exige sessão, e o serviço de planos não sobe |
| [[bff-bloqueio]] | Porta de bloqueio no ar; o retrato não diz o efeito na tela |
| [[bff-enderecos]] | Caminho `beautiful/api/Address`, no ar: lista, criar, editar e apagar; a tela do cliente continua em [[enderecos]] |
| [[bff-telefones]] | Caminho `beautiful/api/Phone`, no ar: lista, incluir, editar e apagar; não descreve o telefone |
| [[bff-fotos]] | Caminho `beautiful/api/Photo`, no ar: buscar, guardar e apagar; sem lista e sem edição de foto já guardada |
| [[bff-relatos]] | Caminho `beautiful/api/Report`, no ar: lista, criar, editar, apagar e a foto do relato; não declara o conteúdo |
| [[bff-documentos-para-validacao]] | Caminho `beautiful/api/Validation`, no ar: consultar, enviar, editar e apagar um conjunto; sem aprovar ou recusar |
| [[bff-o-que-a-pessoa-pode-ver]] | Caminho `beautiful/api/System`, no ar: permissões, grupos e a combinação; não nomeia área nem menu |
| [[cruzamento-bff-como-ler]] | Porta dos cruzamentos com o backend: os dois apps falam com o mesmo BFF; quem pede é o próprio app |
| [[cruzamento-bff-conta]] | Conta de ponta a ponta: POST User nos dois; sessão em `login/user/valid`; a porta publicada é GET Valid |
| [[cruzamento-bff-o-que-a-tela-le]] | Início pede `login/user/logged`, caminho não publicado; CEP é mapa da Google; endereço viaja no cadastro |
| [[cruzamento-bff-o-que-ninguem-pede]] | Portas no ar sem pedido dos apps, e três caminhos do app fora das portas deste retrato |
| [[board-indice]] | Porta do board Azure DevOps em 21/10: 15 temas; bugs têm fonte; nenhum tema segue em raw |
| [[board-conta-e-acesso]] | O board pede login e cadastro de cliente e de artista, inclusive telas em chat; retrato de trabalho, não decisão |
| [[board-listagem]] | O board pede listagem: artistas por endereço sem cadastro, card gratuito, tag de propaganda e filtros; retrato de trabalho |
| [[board-inicio-do-cliente]] | O board pede a tela de início do cliente; a integração com o backend está New |
| [[board-perfil]] | O board pede consultar e gerir perfil; a história 254, modal de artista, está sem pai |
| [[board-favoritos]] | O board pede gerir favoritos; a tarefa 385 fala em qualquer item e a 386 limita a usuários e serviços |
| [[board-agendamentos-e-atendimento]] | O board pede telas de agendamento, check-in e importar de outras plataformas; retrato de trabalho, não decisão |
| [[board-review]] | O board pede review de atendimento e médias do artista; não fecha prazo, estrelas internas nem foto |
| [[board-bloqueio]] | O board pede sistema de bloqueio; épico 335 está New; a história 147 não tem descrição |
| [[board-denuncia]] | O board pede denúncia; a tarefa 368 está New; a história 242, Criar Fluxo de Denuncia, está sem pai |
| [[board-servicos]] | O board pede cadastro de serviços; o épico 338, Sistema de cadastro de serviços, está New; a tarefa 356, Endpoint de cadastro de Artista, está New |
| [[board-planos-e-assinaturas]] | O board pede planos e assinaturas; o épico 342 está New; o épico 371 está New; a tarefa 395, Gerar cobrança do cliente, está New; a tarefa 400, Pagamento dinâmico, está New |
| [[board-configuracoes]] | O board pede configurações do app do cliente; o épico 340, Configurações do app, está New; a tarefa 472, tela de politica de privacidade, está Completed; a tarefa 473, tela de termos de uso, está Completed; a tarefa 475, tela de Alteração de Senha, está Completed |
| [[board-estrutura-dos-apps]] | O board pede a estrutura dos dois apps; o épico 417, Estrutura dos Apps, está Active; o épico 441, Create App using Expo, está Completed; a história 214, app cliente em flutter, está sem pai e Completed; a história 456, Criar Wiki interna, está Completed; a história 213, trocar Beautiful por WeCareU, está sem pai e Completed |
| [[board-design-no-figma]] | O board pede telas no Figma; não há épico; a história 175, [DS] Criar telas no figma, está sem pai e Completed; a tarefa 177, [DS] Criar tela Listagem, está Completed; a tarefa 181, [DS] Criar telas Chat agendamento, está Completed; a história 240, Criar divisões no figma de versões, está sem pai e Completed |
| [[board-bugs]] | O board pede 401 quando o login falha; o épico 463, Bugs gerais / Pendências gerais, está New; a tarefa 465, [BE] Código de Resposta HTTP errado ao errar login, está Completed; os épicos 481 a 487 estão sem histórias |
| [[banco-indice]] | Porta da estrutura de 21/10: onze bancos SQL, quatro Mongo, 29 tabelas, sem chave estrangeira |
| [[banco-sql-relacoes]] | Pares SQL inferidos pelo nome da coluna; nenhuma chave estrangeira; colunas sem destino único |
| [[banco-mongo-relacoes]] | Pares entre Mongo e SQL pelo nome do campo; nenhuma constraint; OwnerId sem destino único |
| [[banco-sql-userlogin]] | `UserLogin`: Usuario, Session, forgetpassword, GrupoUsuario, BlockUsers; sem tabela Bilings |
| [[banco-sql-systemservice]] | `SystemService`: Company, CompanyUsers, Schedule, ScheduleServicesProvided, SystemService, UserService |
| [[banco-sql-systemsdata]] | `SystemsData`: EnterpriseSystems, Groups, GroupsPermissions, Permissions, Screens, Systems; sem SystemComplement |
| [[banco-sql-address]] | Banco `address`, tabela `address`, 14 linhas; OwnerId sem destino único |
| [[banco-sql-phone]] | Banco `Phone`, tabela `Telefones`, 1 linha |
| [[banco-sql-email]] | Banco `Email`: EmailOptions (2) e Emails (0); OwnerIndentifier como no servidor |
| [[banco-sql-enterprise]] | Banco `Enterprise`, tabela `Enterprise`, 3 linhas; não é Company |
| [[banco-sql-i18n]] | Banco e tabela `I18N`, 0 linhas |
| [[banco-sql-paymentplans]] | Banco `PaymentPlans`: Cupom, PaymentPlans, PlanDurationValue; 0 linhas |
| [[banco-sql-report]] | Banco `Report`: tabelas `Report` e `ReportFotos`, 0 linhas |
| [[banco-sql-audition]] | Banco `Audition`, tabela `Audit`, 0 linhas |
| [[banco-mongo-photos]] | Mongo `Photos.photos`, 1 documento; não é SQL |
| [[banco-mongo-signature]] | Mongo `Signature.Signature`, vazia; campos não observados |
| [[banco-mongo-template]] | Mongo `Template.Template`, 1 documento; não é SQL |
| [[banco-mongo-validation]] | Mongo `Validation.Documents`, vazia; campos não observados |
| [[core-00-o-que-e-este-nucleo]] | Porta do núcleo BPT-Core: a regra mora nos `Br.*.API`; o app fala com o BFF; pé da porta |
| [[core-01-conta]] | `Br.Login.API`: `Usuario`, sessão de 48 h e 7 dias, código de senha, dois papéis em `Usuario` |
| [[core-02-servicos]] | `Br.User.Service.API`: `SystemService` e `UserService`; checagem invertida nas quatro ações; agenda e empresa no mesmo projeto |
| [[core-03-agenda]] | `Br.User.Service.API`: `Schedule` e `ScheduleServicesProvided`; a tela segue casca; a marcação nova a lista não acha |
| [[core-04-empresa-e-colaboradores]] | `Br.User.Service.API`: `Company` e `CompanyUsers`, empresa do profissional; o cadastro chama outro host |
| [[core-05-a-organizacao]] | `Br.Enterprise.API`: tabela `Enterprise`, dona do aplicativo; checagem invertida; no BFF os dados da empresa seguem só preparados |
| [[core-06-planos-cupons-e-cobranca]] | `Br.PaymentPlan.API` sem host na lista dos 18; cobrança em `Br.Billing.API` sem ação |
| [[core-07-bloqueio]] | `Br.Block.API`: tabela `BlockUsers`; a checagem inverte o login; não esconde perfil, conversa nem agenda |
| [[core-08-enderecos]] | `Br.Address.API`: banco e tabela `address`; criar não confere sessão; o prefixo recolocado recusa ver, alterar e desligar |
| [[core-09-telefones]] | `Br.Phone.API`: banco `Phone`, tabela `Telefones`; o compose aponta `PaymentPlan`; checagem invertida |
| [[core-10-emails]] | `Br.Email.API`: envio e caixa de endereços; três saídas fixas; não fecha o disparador nem o canal fora de uso do BFF |
| [[core-11-fotos]] | `Br.Photos.API`: Mongo `Photos.photos`; a lista devolve toda foto em uso; a checagem não está invertida |
| [[core-12-relatos]] | `Br.Report.API`: `Report` e `ReportFotos`; não é denúncia; o núcleo tem descrição e os dois identificadores |
| [[core-13-documentos-para-validacao]] | `Br.Validation.API`: Mongo `Validation.Documents`, 0 documentos; não aprova nem recusa; a pergunta ao login não recusa |
| [[core-14-assinatura]] | `Br.Signature.API`: coleção `Signature` vazia; o cadastro não chama; no BFF segue só preparada; a pergunta ao login não recusa |
| [[core-15-modelos-de-mensagem]] | `Br.Template.API`: coleção `Template`; listar e desligar recusam quando o login não aceita; no BFF só preparados |
| [[core-16-permissoes-grupos-e-telas]] | `Br.Systems.API`: seis tabelas em `SystemsData`; `Screens` não é tela de aplicativo; a checagem não recusa ninguém |
| [[core-17-idiomas]] | `Br.I18N.API`: banco e tabela `I18N`; no BFF só preparado; checagem invertida; listar e regravar quebram contra o script |
| [[core-18-rastro-e-falhas]] | `Br.Audit.API` e `Br.Error.Loggin.API`; checagem invertida no rastro; falha para Slack ou Discord; grafia `mendagem` |
| [[core-19-o-que-nao-saiu-do-papel]] | `Br.Ticket.Nuget` vazio e consola Vue; não é o app nem microserviço do BFF |
