# Log

Registro cronológico, append-only.

## [2026-10-20] init | Base de conhecimento criada

Criados `CLAUDE.md` (esquema), `ANTIGRAVITY.md` (aponta para o esquema), `index.md`, `log.md`, `raw/`, `raw/assets/`, `wiki/`, `wiki/fontes/`. Domínio ainda não definido. Único tipo: `fonte`.

## [2026-10-20] ingest | Lote inicial de 10 fontes da WeCareU

Fontes: Brainstorming (WeCareU), Missão e Valor, Pendências, Plano de Negócios interno, Plano de Negócios para Investidores, Planos para o futuro, Planos, Política de Privacidade, Segurança e proteção de dados do aplicativo, Termos de Uso do App. Ingest em lote, a pedido do usuário, sem discussão prévia de cada fonte.

Criadas 35 páginas: 10 `fonte`, 3 `entidade`, 20 `conceito`, 2 `sintese`. Registradas 9 contradições em [[contradicoes-e-lacunas]]; as mais graves são a criptografia prometida e ainda pendente, e os dados sensíveis do cadastro que a política de privacidade não cobre.

## [2026-10-20] esquema | Domínio definido e três tipos cunhados

Domínio: WeCareU. Novos tipos: `entidade`, `conceito`, `sintese`. Corrigido o modelo de frontmatter (wikilinks entre aspas). Adicionadas convenções: `origem:` nas fontes, ligação obrigatória a [[contradicoes-e-lacunas]], `desktop.ini` ignorado.

## [2026-10-20] estrutura | Subpastas entidades/ e conceitos/

Regra de crescimento: `entidade` (3 páginas) foi para `wiki/entidades/` e `conceito` (20 páginas) para `wiki/conceitos/`. `sintese` (2) continua na raiz.

## [2026-10-20] ingest | Decisões do usuário sobre as contradições

Nova fonte [[decisoes-2026-10-20]], vinda da conversa. Itens: criptografia e revisão da política antes do MVP; nenhum gateway contratado; chat só via chatbot em 3 fluxos; MVP = app do cliente + app do Artista; marcações do backlog ficam como estão; preços pendentes.

Criada [[mvp]] (`conceito`, direto em `wiki/conceitos/`). Atualizadas: seguranca-do-atendimento, agendamento, cadastro, protecao-de-dados, pagamentos, planos-de-assinatura, ecossistema-de-produtos, estabelecimento, visao-geral, contradicoes-e-lacunas (status por item; nova contradição #10 sobre o escopo do MVP, já resolvida).

## [2026-10-20] esquema | Decisões em conversa viram fonte

Adicionada a convenção para registrar decisões do chat como página `fonte` `decisoes-AAAA-MM-DD`, sem escrever em `raw/`.

## [2026-10-20] ingest | Decisões do usuário, segunda rodada

Itens 6 a 10 acrescentados a [[decisoes-2026-10-20]]: chatbot sem texto livre; rastreamento em tempo real fora do MVP; MVP 100% gratuito, com só a taxa do meio de pagamento repassada no futuro; só sexo no cadastro; ranking com regra única e dois blocos. O item 8 substitui o 3: gateway deixa de ser requisito do MVP.

Atualizadas: mvp (checklist sem gateway e preços; nova seção "Depois do MVP"), cadastro, ranking, pagamentos, seguranca-do-atendimento, agendamento, modelo-de-receita, planos-de-assinatura, atendimento-imediato, protecao-de-dados, busca-e-filtros, termos-e-responsabilidades, visao-geral, contradicoes-e-lacunas (#3, #4 e #9 resolvidas; nova #11 sobre documentos legais vs. MVP gratuito).

## [2026-10-20] ingest | Decisões do usuário, terceira rodada

Itens 11 a 14 acrescentados a [[decisoes-2026-10-20]]: a taxa do cartão é paga pelo Artista e comunicada como taxa da operadora, não do app; programa de pontos fora do MVP; cadastro em duas etapas no MVP, com telefone na segunda e chamadas para completar; fórmula do ranking virá depois.

Atualizadas: pagamentos, modelo-de-receita, termos-e-responsabilidades, programa-de-pontos, cadastro, ranking, mvp, visao-geral, contradicoes-e-lacunas (saem as lacunas da taxa e do telefone; entra a lacuna dos campos da primeira etapa).

## [2026-10-20] estrutura | raw/ vira caixa de entrada; originais vão para ingeridos/

A pedido do usuário. Os 10 arquivos já ingeridos foram movidos de `raw/` para a nova pasta `ingeridos/`, sem alteração de conteúdo nem de nome. O `arquivo:` das 10 páginas `fonte` foi atualizado e conferido. `raw/` ficou só com `assets/` e os `desktop.ini` do Google Drive.

## [2026-10-20] esquema | Regra de imutabilidade ajustada

A regra 1 passa a proibir só editar ou apagar o conteúdo das fontes; mover de `raw/` para `ingeridos/` vira o passo 8 do ingest. Tabela de camadas atualizada. Adicionada a regra de não sobrescrever quando houver nome repetido em `ingeridos/`.

## [2026-10-20] ingest | 24 snapshots de LyraUI, engenharia e ranking

Série 01–14 (extração Claude), sete SSoT Gemini (`wecareu_*`) e três specs Gemini (`gemini-code-*`). Todos avisam que podem divergir do repositório. Onde conflitam com [[decisoes-2026-10-20]], a decisão prevalece e o conflito fica em [[contradicoes-e-lacunas]] (itens 12 a 19).

Páginas novas: [[lyraui]], [[fundamentos-visuais]], [[voz-e-escrita]], [[figma-lyraui]], [[engenharia-de-software]], e 24 páginas `fonte`. A fórmula candidata de ranking (+10.000 do plano de listagem, nota × 1.000, Acampamento, 3 dias de plano imediato) entrou em [[ranking]] como não confirmada.

## [2026-10-20] esquema | Domínio ampliado

O domínio no `CLAUDE.md` passa a incluir design system (LyraUI) e engenharia, e registra que snapshot de IA não substitui decisão.

## [2026-10-20] ingest | Fórmula de ranking confirmada

Quarta rodada de [[decisoes-2026-10-20]]. O usuário confirmou como definida a fórmula de [[spec-ranqueamento-listagem]] e [[listagem-e-algoritmo-de-busca]]. O limiar da penalidade fica em 50 avaliações. O que está no código continua em aberto: virá em MDs do Cursor; os snapshots desta leva não são inventário do repositório.

Atualizadas: ranking, modelo-de-receita, visao-geral, contradicoes-e-lacunas (#19 resolvida; #12 anotada), as duas páginas `fonte` da listagem.

## [2026-10-20] ingest | Acesso provisório do Swagger

Item 17 em [[decisoes-2026-10-20]]: `https://api.wecareu.app/swagger/index.html` tem usuário e senha temporários, que saem antes do [[mvp]] e dão lugar a um acesso de verdade. Anotado também no checklist do MVP e em [[protecao-de-dados]]. O usuário pediu para manter a senha nos arquivos até a remoção.

## [2026-10-20] ingest | BFF Beautiful.API e microserviços BPT

Quinta rodada de [[decisoes-2026-10-20]]. O app consome o BFF Beautiful.API, repositório Azure `service_api`, CNAME `api.wecareu.app`. Criada [[beautiful-api]] com as 17 URLs `*.bptsoftware.com.br`. `UrlsAuth` e `UrlsLogin` compartilham o host de login. O host de logging foi copiado com a grafia `slackloggin`.

Atualizadas: engenharia-de-software, ecossistema-de-produtos, protecao-de-dados, wecareu, contradicoes-e-lacunas (lacuna: e-mail do BFF versus disparador pendente).

## [2026-10-20] ingest | UrlsBilling no BFF

Correção do usuário: `UrlsBilling` = `https://billingapimicroservice.bptsoftware.com.br/` tinha ficado de fora. Incluída em [[beautiful-api]] e no item 18 de [[decisoes-2026-10-20]]. A lista passa a ter 18 microserviços.

## [2026-10-20] lint | Ordem cronológica do log restaurada

Conferência pós-ingest: `raw/` vazio, 34 originais em `ingeridos/`, todo `arquivo:` aponta para um arquivo existente, todas as páginas têm `tipo:` e estão no `index.md`. Problema achado: as cinco entradas do ingest dos 24 snapshots em diante tinham sido inseridas antes de "raw/ vira caixa de entrada" e "Regra de imutabilidade ajustada". Com aprovação do usuário, essas duas entradas voltaram para antes das novas. Nenhum texto foi alterado.

## [2026-10-21] ingest | Kit visual do design system

Onda 1: dez extrações Cursor de 21/10 do repositório `library-design-system`. Fontes: [[panorama-do-design-system]], [[identidade-visual]], [[vocabulario-visual]], [[textos-da-interface]], [[acoes]], [[campos-de-formulario]], [[escolha-em-lista]], [[datas]], [[espera-e-carregamento]], [[como-o-time-revisa-a-interface]]. Conceito novo: [[kit-visual]], o que o código entrega hoje (`@wecareu/*`, WeCareU Design System, 12 pacotes versionados). A [[lyraui]] segue em discovery.

Atualizadas: lyraui, fundamentos-visuais, voz-e-escrita, engenharia-de-software, contradicoes-e-lacunas. Itens 20 a 23 abertos: catálogo de 13 pacotes com `image-upload` contra 12 sem ele; Livvic só no título grande contra Livvic no corpo; Secondary coral contra ação secundária lilás; CLIENT light / WORKER dark contra o kit que abre no claro e permite alternar. O item 18 continua aberto: o retrato só nomeia `library-design-system`, e registra `playground` e `storybook-web`. [[decisoes-2026-10-20]] não foi reescrita. Os dez brutos foram de `raw/` para `ingeridos/`, sem renomear.

## [2026-10-21] ingest | Fluxo compartilhado de entrar

Onda 2: cinco extrações Cursor de 21/10 do repositório `library-components`, pacote `@wecareu/auth-flow` 0.1.0. Fontes: [[library-components-o-que-entrega]], [[library-components-entrar-na-conta]], [[library-components-recuperar-senha]], [[library-components-biometria-e-sessao]], [[library-components-em-que-pe-esta]]. Conceito novo: [[fluxo-de-entrada]].

Atualizadas: [[kit-visual]], [[seguranca-do-atendimento]], [[protecao-de-dados]], [[contradicoes-e-lacunas]]. Item 24 aberto: o catálogo legado trata o pacote como peça da biblioteca ao lado das telas dos apps; este repositório não evidencia instalação, e o inventário de maio não descreve o disco de 21/10. A instalação em cada app fica para as próximas ondas. O item 18 continua aberto. [[decisoes-2026-10-20]] não foi reescrita. Os cinco brutos foram de `raw/` para `ingeridos/`, sem renomear.

## [2026-10-21] ingest | Ponteiro do auth-flow na LyraUI

No gate da onda 2, [[lyraui]] ainda afirmava que `@wecareu/auth-flow` roda nos apps, citando o catálogo de 20/10. A frase do catálogo permanece. Foi acrescentado o ponteiro ao item 24: o retrato de 21/10 não evidencia instalação. Ver [[fluxo-de-entrada]]. [[decisoes-2026-10-20]] não foi reescrita.

## [2026-10-21] ingest | App do cliente

Onda 3: doze extrações Cursor de 21/10 do repositório `ui_client`. Fontes: [[mapa-do-app-do-cliente]], [[primeira-entrada]], [[criar-conta]], [[entrar-senha-e-biometria]], [[encontrar-profissionais]], [[inicio]], [[meu-perfil]], [[enderecos]], [[avisos-ajuda-e-regras]], [[agenda]], [[conversa-do-agendamento]], [[o-que-ainda-nao-esta-no-app]]. Conceito novo: [[app-do-cliente]].

Atualizadas: [[ecossistema-de-produtos]], [[cadastro]], [[agendamento]], [[busca-e-filtros]], [[ranking]], [[mvp]], [[fluxo-de-entrada]], [[seguranca-do-atendimento]], [[contradicoes-e-lacunas]], [[index]]. Itens 12 (MDs do cliente em 1.0.0, com casca e exemplo, sem confirmar lançamento), 13 (ChatSchedules é casca no cliente; o alvo continua chatbot sem texto livre), 14 (o cliente coleta gênero, sem sexo separado, sem orientação sexual e sem telefone; a decisão segue só sexo), 17 (a nota 5,0 do Início é fallback de tela) e 25 (duas etapas no alvo, três no formulário do cliente). O item 11 ganha o texto fixo de dezembro de 2024 no app. O item 24 ganha a frase de que a extração do cliente não cita `@wecareu/auth-flow` e continua aberto: falta o artista. Os itens 4 e 19 não foram reabertos. [[decisoes-2026-10-20]] não foi reescrita. [[kit-visual]] não foi editado: nenhum bruto desta onda cita instalação dos pacotes. Os doze brutos foram de `raw/` para `ingeridos/`, sem renomear. App do artista e cruzamentos continuam em `raw/`.

## [2026-10-21] ingest | App do artista

Onda 4: doze extrações Cursor de 21/10 do repositório `ui_worker`. Fontes: [[mapa-do-app-do-artista]], [[abertura-do-artista]], [[cadastro-do-artista]], [[entrar-senha-e-biometria-do-artista]], [[inicio-do-artista]], [[pedidos-do-artista]], [[agenda-do-artista]], [[planos-do-artista]], [[perfil-do-artista]], [[enderecos-do-artista]], [[avisos-ajuda-e-regras-do-artista]], [[o-que-ainda-nao-esta-no-app-do-artista]]. Conceito novo: [[app-do-artista]].

Atualizadas: [[artista]], [[ecossistema-de-produtos]], [[cadastro]], [[planos-de-assinatura]], [[pagamentos]], [[agendamento]], [[mvp]], [[fluxo-de-entrada]], [[seguranca-do-atendimento]], [[contradicoes-e-lacunas]], [[index]]. Itens 11 (o artista repete o texto de dezembro de 2024), 12 (os dois apps em 1.0.0, com casca e exemplo, sem confirmar lançamento), 13 (no artista a tela diz "Tab ChatSchedules" e não tem caminho), 14 (o artista também coleta gênero, sem sexo, orientação sexual nem telefone), 24 (a extração do artista não cita `@wecareu/auth-flow`; segue aberto), 25 (cinco etapas no artista, três no cliente, alvo de duas) e 26 (a abertura promete pagamento, check-in e check-out; as telas não existem; o MVP gratuito permanece). [[decisoes-2026-10-20]] não foi reescrita. [[kit-visual]] não foi editado: nenhum bruto desta onda cita os pacotes. [[app-do-cliente]] não foi reescrito. Os doze brutos foram de `raw/` para `ingeridos/`, sem renomear. Cruzamentos continuam em `raw/`.

## [2026-10-21] lint | Contagem de fontes da página de contradições

No gate da onda 4, o [[index]] dizia 35 fontes em [[contradicoes-e-lacunas]]. O array tem 36. A coluna foi corrigida. Nenhum outro texto foi alterado.

## [2026-10-21] ingest | Cruzamentos dos quatro repositórios

Onda 5, a última: sete cruzamentos de 21/10 entre `ui_client`, `ui_worker`, `library-design-system` e `library-components`. Fontes: [[cruzamento-como-ler]], [[cruzamento-kit-visual]], [[cruzamento-entrar-senha-e-biometria]], [[cruzamento-criar-conta]], [[cruzamento-dentro-da-conta]], [[cruzamento-o-que-so-um-app-tem]], [[cruzamento-o-que-deveria-ser-uma-peca-so]]. O tipo `cruzamento` dos brutos não virou tipo da wiki. Nenhuma síntese nova. Nenhum conceito novo.

Atualizadas: [[visao-geral]], [[kit-visual]], [[fluxo-de-entrada]], [[app-do-cliente]], [[app-do-artista]], [[contradicoes-e-lacunas]], [[index]]. O item 24 segue aberto como retrato: os dois apps têm percurso próprio e a peça compartilhada não está instalada; não é decisão de manter separado. Item 27: divergência de pé entre o panorama e a nota da peça, na escolha em lista e nos ícones; o cruzamento fica com a nota da peça. Lacuna nova: cara da tela no kit e percurso igual numa peça de fluxo, com cadastro só depois de alinhar as jornadas; direção deste retrato, não decisão da empresa e não alvo do MVP. O item 14 registra que o cruzamento do kit chama a lista do cadastro de sexo, e [[criar-conta]] chama o campo de gênero; a decisão de só sexo permanece. O item 25 registra que não há peça compartilhada de cadastro em uso; segue aberto no código. A coluna de fontes de [[contradicoes-e-lacunas]] acompanha o array: antes desta entrada ele tinha 35 wikilinks e o index dizia 36; com as seis fontes novas, array e coluna ficam em 41. [[decisoes-2026-10-20]] não foi reescrita. Os sete brutos foram de `raw/` para `ingeridos/`, sem renomear. `raw/` ficou sem markdown de fonte. `desktop.ini` permanece.

## [2026-10-21] ingest | Decisões depois do retrato de front

Nova fonte [[decisoes-2026-10-21]], vinda da conversa. Itens: o alvo do MVP manda e o código de 21/10 será alinhado depois (não reabre produto); endereço do cliente para o Artista continua em aberto (24h, checkout do anterior, ou só bairro/região); avaliação obrigatória, detalhes depois; listagem sem login no MVP, cadastro na hora de agendar; 2FA nos apps.

Atualizadas: mvp, avaliacoes, busca-e-filtros, cadastro, agendamento, seguranca-do-atendimento, protecao-de-dados, app-do-cliente, visao-geral, contradicoes-e-lacunas (itens 13, 14, 25 e 26 encaminhados; 15 e 17 resolvidos no alvo; 16 permanece aberto), index.

## [2026-10-21] ingest | Mapa do BFF

Onda 1 do backend de apoio: três extrações Cursor de 21/10 do repositório `service_api`. Fontes: [[bff-o-que-e-este-backend]], [[bff-cliente-e-profissional]], [[bff-preparado-e-ainda-nao-oferecido]]. Não houve conceito novo. [[beautiful-api]] ganhou o retrato de 21/10 (Beautiful, prefixo `beautiful/api/`, escala de pé, CompanyData, banco local sem negócio) sem apagar a tabela dos 18 microserviços.

Lacunas atualizadas, sem fechar: o canal de e-mail do BFF está fora da compilação e o cliente de e-mail está ligado sem ação exposta, e isso não decide se é o disparador de [[pendencias]]; a leitura da sessão não entra no caminho do pedido. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. A escrita das páginas foi interrompida antes do movimento; o gate moveu os três brutos de `raw/` para `ingeridos/`, sem renomear. As notas 03 a 13 e os cruzamentos do BFF continuam em `raw/`.

## [2026-10-21] ingest | Conta no BFF

Onda 2 do retrato de `service_api`: entrar, sair, senha e cadastro. Fontes: [[bff-entrar-sair-e-senha]] (caminho `beautiful/api/Login`, sete pedidos; este backend não envia o e-mail; não menciona 2FA e não publica porta de 2FA) e [[bff-cadastro]] (caminho `beautiful/api/Register`: POST `User`, POST `Artist`, GET `{email}`, GET `docs`). Não houve conceito novo. Não houve item 28.

Atualizadas: [[beautiful-api]] (a linha No ar aponta as duas notas; os 18 microserviços permanecem), [[fluxo-de-entrada]] (o que o backend publica; o item 24 segue aberto), [[cadastro]] (duas portas e a conferência de e-mail, CPF e CNPJ; a tela de 21/10 e o alvo do MVP permanecem), [[contradicoes-e-lacunas]] (a lacuna de sessão ganha GET `logout` e GET `Valid`). Ponteiros nas três fontes da onda 1, onde o texto ainda dizia que o passo não era página. Itens 14, 15, 24 e 25 não foram reabertos. CNPJ opcional na conferência de documentos ficou na fonte e no parágrafo de [[cadastro]], sem contradição numerada. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os dois brutos foram de `raw/` para `ingeridos/`, sem renomear. As notas 05 a 13 e os cruzamentos do BFF continuam em `raw/`.

## [2026-10-21] ingest | Portas do BFF

Onda 3 do retrato de `service_api`: serviços, planos e cupons, bloqueio, endereços e telefones. Fontes: [[bff-servicos]] (no ar, com ressalva), [[bff-planos-e-cupons]] (porta sem ligação; caminho de planos ausente na configuração), [[bff-bloqueio]] (no ar), [[bff-enderecos]] (caminho `beautiful/api/Address`) e [[bff-telefones]] (caminho `beautiful/api/Phone`). Não houve conceito novo. Não houve item 28.

Atualizadas: [[beautiful-api]] (a tabela de pé aponta as cinco; os 18 microserviços permanecem), [[planos-de-assinatura]] (a porta existe e o serviço não está ligado; os planos continuam definidos e fora do lançamento gratuito; a aba continua casca), [[pagamentos]] (esta leva não publica cobrança), [[seguranca-do-atendimento]] (a porta de bloqueio está no ar e o retrato não diz o efeito na tela), [[cadastro]] (gestão de telefone da sessão; o bruto não descreve o telefone das duas etapas; o alvo permanece), [[contradicoes-e-lacunas]] (a lacuna de sessão cita estas portas). Ponteiros em [[bff-o-que-e-este-backend]] e [[bff-preparado-e-ainda-nao-oferecido]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os cinco brutos foram de `raw/` para `ingeridos/`, sem renomear. As notas 10 a 13 e os cruzamentos do BFF continuam em `raw/`.

## [2026-10-21] ingest | Mídia e permissão no BFF

Onda 4 do retrato de `service_api`: fotos, relatos, documentos para validação e o que a pessoa pode ver. Fontes: [[bff-fotos]] (caminho `beautiful/api/Photo`, no ar para buscar, guardar e apagar; sem lista e sem edição de foto já guardada), [[bff-relatos]] (caminho `beautiful/api/Report`, no ar; não declara texto, motivo nem sobre quem é), [[bff-documentos-para-validacao]] (caminho `beautiful/api/Validation`, no ar; sem aprovar ou recusar; não é a conferência de CPF e CNPJ nem o alvo de validação do Artista) e [[bff-o-que-a-pessoa-pode-ver]] (caminho `beautiful/api/System`, no ar; permissões, grupos e a combinação; não nomeia área nem menu). Não houve conceito novo. Não houve item 28.

Atualizadas: [[beautiful-api]] (a tabela de pé aponta as quatro; os 18 microserviços permanecem), [[seguranca-do-atendimento]] (documentos e relatos no ar, sem virar check-in, shadowban nem chatbot; o alvo de validação do Artista permanece), [[contradicoes-e-lacunas]] (a lacuna de sessão cita estas quatro portas). Ponteiros em [[bff-o-que-e-este-backend]], [[bff-bloqueio]], [[bff-servicos]], [[bff-cadastro]] e [[bff-entrar-sair-e-senha]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os quatro brutos foram de `raw/` para `ingeridos/`, sem renomear. Os cruzamentos do BFF continuam em `raw/`.

## [2026-10-21] ingest | Cruzamento do BFF com os apps

Onda 5, a última, do retrato de `service_api` cruzado com `ui_client` e `ui_worker`. Fontes: [[cruzamento-bff-como-ler]], [[cruzamento-bff-conta]], [[cruzamento-bff-o-que-a-tela-le]], [[cruzamento-bff-o-que-ninguem-pede]]. O tipo `cruzamento` dos brutos não virou tipo da wiki. Nenhuma síntese nova. Nenhum conceito novo.

Atualizadas: [[visao-geral]], [[beautiful-api]] (o que os apps pedem contra o que está publicado; os 18 microserviços e a tabela de pé permanecem), [[fluxo-de-entrada]], [[cadastro]], [[app-do-cliente]], [[app-do-artista]], [[contradicoes-e-lacunas]], [[index]]. Os dois apps falam com o mesmo backend. Quem fala com ele, hoje, é o próprio app. O item 24 segue aberto, com essa frase. Item 28 aberto no código: os dois apps usam POST `User`; a porta POST `Artist` existe e o app do artista não a usa; a decisão de dois papéis permanece. A lacuna de sessão ganha o caminho `login/user/valid`, que este retrato não publica; a porta publicada é GET `Valid`. Itens 13, 14, 25 e 26 não foram reabertos. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os quatro brutos foram de `raw/` para `ingeridos/`, sem renomear. `raw/` ficou sem markdown de fonte. `desktop.ini` permanece.

## [2026-10-21] ingest | Mapa do board Azure DevOps

Onda 1 do board WeCareU (Azure DevOps, extração de 21/10). Fonte: [[board-indice]]. Só o mapa: 15 temas, 25 épicos, 50 histórias, 125 tarefas. Nenhuma ficha de épico. Não houve conceito novo. Não houve item novo na tabela de contradições. Lacuna: os 15 temas seguem em raw/. Ponteiros em [[visao-geral]] e [[engenharia-de-software]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-21] ingest | Conta e acesso no board

Onda 2 do board WeCareU. Fonte: [[board-conta-e-acesso]]. Épicos 329 (login) e 337 (cadastro), mais histórias sem pai 223, 225 e 246. Retrato de trabalho. Não houve conceito novo. Itens 14, 15, 24, 25 e 28 não foram reabertos. Login com digital não é 2FA. Cadastro em chat no board não substitui as duas etapas do alvo. Pedido de login e cadastro de artista não apaga o uso de POST User nos dois apps. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear. Catorze temas do board seguem em raw/.

Item 29 foi criado. Nenhuma linha cobria o momento do cadastro no cliente. A tarefa 411 prevê fim de cadastro vindo da listagem, do agendamento ou da tela inicial do app. A tarefa 450 pede chamada de cadastro em home, favoritos, agendamentos e perfil. A decisão permanece: no cliente, cadastro na hora de agendar, não na porta. O item 25 segue só sobre a quantidade de etapas.

[[Andrey Didoff]] fica responsável pelo épico 329. [[bruno]], Bruno Pires de Almeida, fica responsável pela história 343. Sem lista de tarefas. [[engenharia-de-software]] deixou de dizer que os 15 temas ainda não entraram: conta e acesso entrou; 14 seguem em raw/.

## [2026-10-21] ingest | Descoberta do cliente no board

Onda 3 do board WeCareU. Fontes: [[board-listagem]], [[board-inicio-do-cliente]], [[board-perfil]], [[board-favoritos]]. Conceito novo: [[favoritos]]. A história 145 encontra a lista sem login; o alvo não foi reaberto. Itens 14, 15, 16, 19, 24, 25, 28 e 29 não foram reabertos. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os quatro brutos foram de raw/ para ingeridos/, sem renomear. Dez temas do board seguem em raw/.

## [2026-10-21] lint | Campo fontes fora das páginas fonte

Nas fontes [[inicio]], [[meu-perfil]] e [[enderecos]], o campo `fontes:` foi retirado. Página fonte leva `arquivo:` e `origem:`. O cruzamento com o board permanece no corpo.

## [2026-10-21] ingest | Atendimento e review no board

Onda 4 do board WeCareU. Fontes: [[board-agendamentos-e-atendimento]], [[board-review]]. Não houve conceito novo. O alvo continua chatbot, sem texto livre. O item 16 segue aberto: check-in no board não decide quando o endereço aparece. Review no board não fecha prazo, estrelas internas nem foto. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os dois brutos foram de raw/ para ingeridos/, sem renomear. Oito temas do board seguem em raw/.

## [2026-10-21] ingest | Bloqueio e denúncia no board

Onda 5 do board WeCareU. Fontes: [[board-bloqueio]], [[board-denuncia]]. Não houve conceito novo. A porta [[bff-relatos]] continua sem sentido declarado. O board de denúncia não é essa porta. [[bff-bloqueio]] continua sem dizer se o bloqueio esconde perfil, chat ou agenda. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os dois brutos foram de raw/ para ingeridos/, sem renomear. Seis temas do board seguem em raw/.

## [2026-10-21] ingest | Serviços e planos no board

Onda 6 do board WeCareU. Fontes: [[board-servicos]], [[board-planos-e-assinaturas]]. Não houve conceito novo. Cobrança pedida no board permanece fora do lançamento. O item 3 não foi reaberto. As portas [[bff-servicos]] e [[bff-planos-e-cupons]] mantêm o pé do retrato de código. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os dois brutos foram de raw/ para ingeridos/, sem renomear. Quatro temas do board seguem em raw/.

## [2026-10-21] ingest | Configurações no board

Onda 7 do board WeCareU. Fonte: [[board-configuracoes]]. Não houve conceito novo. Telas de termos e privacidade pedidas no board não atualizam o texto de dezembro de 2024. O item 11 segue aberto. Alteração de senha não é 2FA. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear. Três temas do board seguem em raw/.

## [2026-10-21] ingest | Estrutura dos apps no board

Onda 8 do board WeCareU. Fonte: [[board-estrutura-dos-apps]]. Épicos 417 e 441, mais itens sem pai, inclusive Flutter. Não houve conceito novo. Wiki interna do board não é esta base. Flutter não é stack do MVP. Biblioteca pedida no board não reescreve o retrato do kit nem da LyraUI. Itens 12, 18 e 24 não foram reabertos. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear. Design no Figma e bugs seguem em raw/.

## [2026-10-21] ingest | Design no Figma no board

Onda 9 do board WeCareU. Fonte: [[board-design-no-figma]]. Sem épico. Histórias 175 e 240 sem pai. Não houve conceito novo. Tarefa de tela no Figma não prova tela no app. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear. Bugs segue em raw/.

## [2026-10-21] ingest | Bugs no board

Onda 10, a última de tema, do board WeCareU. Fonte: [[board-bugs]]. Épicos-casca sem história, salvo o 463. A tarefa 465 pede 401 no lugar de 500 quando o login falha. Estado Completed no board. O retrato de [[bff-entrar-sair-e-senha]] não diz o código de resposta e não foi reescrito para declarar o conserto. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear. Os 15 temas do board têm fonte. `desktop.ini` permanece em raw/.

## [2026-10-21] lint | Fechamento do board Azure DevOps

Os 16 brutos do board estão em `ingeridos/`. `raw/` ficou sem markdown de fonte. `desktop.ini` permanece. 200 ids de épico, história e tarefa, sem repetição. As 16 páginas `fonte` têm `tipo:` e `arquivo:` em `ingeridos/`, sem campo `fontes:`. Wikilinks do board resolvem. O índice cobre as páginas. A lacuna do mapa fechou: os 15 temas têm fonte. [[engenharia-de-software]] passou a citar [[board-design-no-figma]], que a frase dos 15 temas tinha pulado; a contagem foi para 15. Três contagens do índice que já divergiam do frontmatter foram alinhadas: [[wecareu]] 7, [[estabelecimento]] 5, [[programa-de-pontos]] 4. Não houve conceito novo neste lint. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas.

## [2026-10-22] ingest | Índice dos bancos

Fonte: [[banco-indice]]. Onze bancos SQL e quatro Mongo, 29 tabelas, sem chave estrangeira declarada. `Signature` e `Validation.Documents` vazias. Não houve conceito novo. Ponteiros em [[engenharia-de-software]] e [[beautiful-api]]. Lacuna nova em [[contradicoes-e-lacunas]]: a estrutura é leitura, não decisão; os outros brutos dessa leva seguem em raw/. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Relações entre os bancos SQL

Fonte: [[banco-sql-relacoes]]. Nenhuma chave estrangeira. Pares pelo nome da coluna, força forte ou fraca. Colunas sem destino único, entre elas `FkFoto`, `FkSignature`, `Logo` e `ServiceId`. Não houve conceito novo. Ponteiros em [[engenharia-de-software]], [[beautiful-api]] e [[contradicoes-e-lacunas]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Relações do MongoDB

Fonte: [[banco-mongo-relacoes]]. `Template` aponta empresa e sistema. `ReportFotos.PhotoId` e `Systems.PhotoId` apontam `Photos.photos`. `OwnerId` da foto não tem destino único. Nenhuma constraint. Não houve conceito novo. Ponteiros em [[engenharia-de-software]], [[beautiful-api]] e [[contradicoes-e-lacunas]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Banco UserLogin

Fonte: [[banco-sql-userlogin]]. Tabelas `Usuario`, `Session`, `forgetpassword`, `GrupoUsuario` e `BlockUsers`. Não há `Bilings`. Não houve conceito novo. Ponteiro em [[engenharia-de-software]]. Lacuna em [[contradicoes-e-lacunas]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Banco SystemService

Fonte: [[banco-sql-systemservice]]. Tabelas `Company`, `CompanyUsers`, `Schedule`, `ScheduleServicesProvided`, `SystemService` e `UserService`. Só `SystemService` tem linhas (28). Não houve conceito novo. Ponteiro em [[engenharia-de-software]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Banco SystemsData

Fonte: [[banco-sql-systemsdata]]. Seis tabelas: `EnterpriseSystems`, `Groups`, `GroupsPermissions`, `Permissions`, `Screens`, `Systems`. Não há `SystemComplement`. `Screens` não é tela de aplicativo. Não houve conceito novo. Ponteiro em [[engenharia-de-software]]. Lacuna em [[contradicoes-e-lacunas]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. O bruto foi de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Endereço, telefone, e-mail, empresa, idiomas e planos

Fontes: [[banco-sql-address]] (tabela `address`, 14 linhas), [[banco-sql-phone]] (banco `Phone`, tabela `Telefones`), [[banco-sql-email]] (`EmailOptions` e `Emails`), [[banco-sql-enterprise]] (distinta de `Company`), [[banco-sql-i18n]] (banco e tabela `I18N`, vazia) e [[banco-sql-paymentplans]] (banco `PaymentPlans`, três tabelas vazias). Não houve conceito novo. Ponteiros em [[engenharia-de-software]]. A lacuna do telefone registra que o servidor diz `Phone` e o compose do BPT-Core, ainda sem fonte, diz `PaymentPlan`. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os seis brutos foram de raw/ para ingeridos/, sem renomear.

## [2026-10-22] ingest | Relatos, auditoria e Mongo

Fontes: [[banco-sql-report]] (`Report` e `ReportFotos`), [[banco-sql-audition]] (`Audit`), [[banco-mongo-photos]] (coleção `photos`, 1 documento), [[banco-mongo-template]] (coleção `Template`, 1 documento), [[banco-mongo-signature]] e [[banco-mongo-validation]] (vazias; campos não inventados). Não houve conceito novo. Ponteiros em [[engenharia-de-software]]. A lacuna de estrutura passa a dizer que os 18 brutos estão ingeridos. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os seis brutos foram de raw/ para ingeridos/, sem renomear. `desktop.ini` permanece em raw/.

## [2026-10-22] ingest | Mapa do núcleo BPT-Core

Fontes: [[core-00-o-que-e-este-nucleo]], [[core-01-conta]] e [[core-19-o-que-nao-saiu-do-papel]]. Conceito novo: [[bpt-core]]. O aplicativo fala com o BFF; a regra mora nos projetos `Br.*.API`. Pé da porta: feito com ressalva, pela metade, casca e operação interna. Conta em `Br.Login.API`. Ticket e a consola Vue não saíram do papel e não viram página de app. Não houve item 30. A data de nascimento que chega e não é gravada ficou em [[cadastro]]. O código de senha que continua ativo ficou em [[fluxo-de-entrada]] e [[protecao-de-dados]]. O item 17 ganhou a frase das cinco estrelas ao nascer a conta e segue resolvido no alvo. Os itens 14 e 25 seguem encaminhados. O item 24 segue aberto. A lacuna do disparador de e-mail não fechou. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. As outras notas `core-*` seguem em `raw/`. Os três brutos foram de `raw/` para `ingeridos/`, sem renomear. `desktop.ini` permanece.

## [2026-10-22] ingest | Bloqueio, endereço, telefone e serviços do núcleo

Fontes: [[core-07-bloqueio]] (`Br.Block.API`, tabela `BlockUsers`), [[core-08-enderecos]] (`Br.Address.API`, banco e tabela `address`), [[core-09-telefones]] (`Br.Phone.API`; o servidor nomeia `Phone` e `Telefones`) e [[core-02-servicos]] (`Br.User.Service.API`, `SystemService` e `UserService`). As quatro passam a ser página em [[bpt-core]]. Agenda e empresa seguem em texto, `core-03-agenda` e `core-04-empresa-e-colaboradores`, no mesmo projeto, host e banco. A checagem de bloqueio, telefone e serviços pergunta ao login e inverte a resposta. No endereço, a conferência recoloca o prefixo. A lacuna de sessão do BFF segue aberta: o arranque prepara a sessão e não a lê no caminho do pedido. São camadas diferentes. O retrato de [[bff-servicos]] permanece. O item 16 segue aberto. Não houve item 30. A divergência do catálogo de telefone segue aberta. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. As outras notas `core-*` seguem em `raw/`. Os quatro brutos foram de `raw/` para `ingeridos/`, sem renomear. `desktop.ini` permanece.

## [2026-10-22] ingest | Agenda, empresa, organização e planos do núcleo

Onda 3 do núcleo BPT-Core. Fontes: [[core-03-agenda]] (`Br.User.Service.API`, tabelas `Schedule` e `ScheduleServicesProvided`; a tela segue casca; a marcação nova a lista não acha), [[core-04-empresa-e-colaboradores]] (`Company` e `CompanyUsers`, empresa do profissional; o cadastro chama outro host), [[core-05-a-organizacao]] (`Br.Enterprise.API`, tabela `Enterprise`; checagem invertida; no BFF os dados da empresa seguem só preparados) e [[core-06-planos-cupons-e-cobranca]] (`Br.PaymentPlan.API` sem host na lista dos 18; `Br.Billing.API` sem ação). Não houve conceito novo. Não houve item 30. O alvo de agendamento continua chatbot. O MVP gratuito e a cobrança fora do MVP permanecem. O item 28 permanece.

Atualizadas: [[bpt-core]], [[agendamento]], [[planos-de-assinatura]], [[pagamentos]], [[beautiful-api]] (a tabela dos 18 permanece, com `UrlsBilling`; sem URL de planos), [[cadastro]], [[contradicoes-e-lacunas]] (a lacuna de sessão do BFF segue aberta; a checagem invertida da organização e dos planos entra como outra camada), [[core-02-servicos]], [[core-00-o-que-e-este-nucleo]], [[core-01-conta]], [[index]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os quatro brutos foram de `raw/` para `ingeridos/`, sem renomear. E-mail, fotos, relatos, documentos para validação, assinatura, modelos, permissões, idiomas e rastro seguem em `raw/`. `desktop.ini` permanece.

## [2026-10-22] ingest | E-mail, idiomas, fotos e relatos do núcleo

Onda 4 do núcleo BPT-Core. Fontes: [[core-10-emails]] (`Br.Email.API`, https://emailapimicroservice.bptsoftware.com.br/, banco `Email`, tabelas `Emails` e `EmailOptions`; envio e caixa de endereços; não é o disparador pendente nem o canal fora de uso do BFF), [[core-17-idiomas]] (`Br.I18N.API`, https://i18napimicroservice.bptsoftware.com.br/, banco e tabela `I18N`; no BFF só preparado; checagem invertida), [[core-11-fotos]] (`Br.Photos.API`, https://photosapimicroservice.bptsoftware.com.br/, Mongo `Photos.photos`; listar, abrir, editar e desligar recusam quando o login não aceita; esta checagem não está invertida) e [[core-12-relatos]] (`Br.Report.API`, https://reportapimicroservice.bptsoftware.com.br/, `Report` e `ReportFotos`; o núcleo tem a descrição e os dois identificadores; o retrato [[bff-relatos]] não declara esses campos). Não houve conceito novo. Não houve item 30. A lacuna do disparador de e-mail segue aberta. A lacuna de sessão do BFF segue aberta.

Atualizadas: [[bpt-core]], [[beautiful-api]] (a tabela dos 18 permanece), [[protecao-de-dados]], [[contradicoes-e-lacunas]], [[core-00-o-que-e-este-nucleo]], [[core-01-conta]], [[index]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. [[bff-relatos]] não foi reescrita. Os quatro brutos foram de `raw/` para `ingeridos/`, sem renomear. Documentos para validação, assinatura, modelos de mensagem, permissões e rastro seguem em `raw/`. `desktop.ini` permanece.

## [2026-10-22] ingest | Validação, assinatura, modelos, permissões e rastro do núcleo

Onda 5 do núcleo BPT-Core. Fontes: [[core-13-documentos-para-validacao]] (`Br.Validation.API`, Mongo `Validation.Documents`, 0 documentos; não aprova nem recusa; a pergunta ao login acontece e não recusa), [[core-14-assinatura]] (`Br.Signature.API`, coleção `Signature` vazia; o cadastro não chama; no BFF segue só preparada; a mesma porta de acesso que não recusa), [[core-15-modelos-de-mensagem]] (`Br.Template.API`; listar e desligar recusam quando o login não aceita; esta checagem não está invertida; no BFF só preparados), [[core-16-permissoes-grupos-e-telas]] (`Br.Systems.API`, seis tabelas; `Screens` não é tela de aplicativo; a checagem não recusa ninguém) e [[core-18-rastro-e-falhas]] (`Br.Audit.API` e `Br.Error.Loggin.API`; checagem invertida no rastro; o miolo não sobe; falha para Slack ou Discord, destino fora deste repositório). Não houve conceito novo. Não houve item 30. A lacuna de sessão do BFF segue aberta: o arranque prepara a sessão e não a lê no caminho do pedido.

Atualizadas: [[bpt-core]], [[beautiful-api]] (a tabela dos 18 permanece; a linha `slacklogginapimicroservice` segue como está), [[protecao-de-dados]], [[contradicoes-e-lacunas]], [[core-00-o-que-e-este-nucleo]], [[core-01-conta]], [[index]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Nenhuma nota do núcleo segue sem página. Os cinco brutos foram de `raw/` para `ingeridos/`, sem renomear. `desktop.ini` permanece.

## [2026-11-03] ingest | Conjunto de funções do MVP e spec de ranqueamento v0.3.1

O pacote fecha quais funções e telas entram no [[mvp]]. O dono vai trazer outro arquivo com o detalhe de cada tela. Esse detalhe não muda o conjunto. O que está [RECOMENDADO] no pacote não virou decisão. ([[decisoes-2026-11-03]])

Fontes: [[mvp-memoria-indice]], [[mvp-e-releases]], [[mvp-mudancas-na-spec]], [[mvp-revisao-riscos]], [[mvp-final]] e [[spec-busca-e-ranqueamento]] (v0.3.1). A fórmula de 20/10 (+10.000, Acampamento, plano imediato) cede a esta spec. Itens 9 e 19 de [[contradicoes-e-lacunas]] atualizados. Item 16 resolvido: endereço do cliente às 00:00:01 do dia anterior. Item 30 aberto: 2FA, forma da tela, lista sem login, obrigatoriedade da avaliação e campos do cadastro além de endereço, bairro e SMS esperam o arquivo de telas. Lançamento público: São Paulo inteira, 01/01/2027.

Atualizadas: [[mvp]], [[ranking]], [[busca-e-filtros]], [[agendamento]], [[avaliacoes]], [[cadastro]], [[lancamento-e-marketing]], [[seguranca-do-atendimento]], [[visao-geral]], [[contradicoes-e-lacunas]], [[index]]. [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]] não foram reescritas. Os seis brutos foram de `raw/` para `ingeridos/`, sem renomear. `desktop.ini` permanece.

## [2026-11-05] ingest | Critério de pronto do MVP e metas sem número

Decisão do dono no chat, sem arquivo em `raw/`. Fonte: [[decisoes-2026-11-05]].

O critério de pronto do [[mvp]] neste trimestre é os dois apps passarem no teste ponta a ponta em ambiente local até 31/12/2026. Publicação nas lojas fica fora. O lançamento público permanece São Paulo inteira, em 01/01/2027. Quantidade de artistas não foi fixada: o formato do lançamento ainda não está definido e um número seria chute. O orçamento de marketing só no fim de dezembro de 2026.

Atualizadas: [[mvp]], [[lancamento-e-marketing]], [[visao-geral]], [[contradicoes-e-lacunas]], [[index]]. Nenhuma contradição mudou de status. A lacuna de quantidade e orçamento foi aberta de propósito.

## [2026-11-05] ingest | Alvo do cliente e pendências de ajuste

Os arquivos 05, 06 e 07 fecham como o app do cliente precisa ser. Onde o cliente muda 00 a 04, prevalece o delta. Onde não muda, o alvo de 03/11 continua. O retrato de 21/10 é estado atual. Tela, copy ou backend fora do alvo viram pendência de ajuste. O detalhe de tela do artista fica de fora. Termos, política e e-mails transacionais seguem diferidos. ([[decisoes-2026-11-05]])

Fontes: [[mvp-funcoes-e-telas]], [[mvp-alteracoes-pos-congelamento]], [[mvp-copys-cliente]]. A página [[decisoes-2026-11-05]] ganhou a seção do alvo e manteve o critério de pronto de 31/12/2026.

Atualizadas: [[mvp]], [[cadastro]], [[agendamento]], [[avaliacoes]], [[busca-e-filtros]], [[ranking]], [[seguranca-do-atendimento]], [[voz-e-escrita]], [[visao-geral]], [[contradicoes-e-lacunas]]. Itens 4, 13, 14, 15, 17, 25, 29 e 30 tratados só no cliente. Itens 31 a 35 são linhas novas de produto. Itens 12, 18, 20 a 24, 27 e 28 continuam retrato.

Tipo novo: `pendencia`, pasta `wiki/pendencias/`. Páginas: [[backend-mvp-listagem]], [[backend-mvp-agendamento]], [[backend-mvp-conta]], [[backend-mvp-avaliacao-e-avisos]], [[backend-mvp-fundacoes]], [[app-cliente-conta]], [[app-cliente-descoberta]], [[app-cliente-agendamento]], [[app-cliente-copys]]. [[pendencias]] não foi reescrita. Criptografia, Swagger e o disparador antigo continuam em [[mvp]].

Os três brutos foram de `raw/` para `ingeridos/`, sem renomear. `desktop.ini` permanece.

## [2026-11-05] lint | Welcome do cliente não é chatbot

Correção em [[app-cliente-conta]]. O welcome é um carrossel de 5 slides. O chatbot é só o cadastro. A frase que juntava os dois estava errada. A fonte já dizia isso em "Welcome do cliente: estrutura" ([[mvp-funcoes-e-telas]]). Nenhuma outra página tratava o welcome como chatbot.

## [2026-11-05] lint | Pendências do backend viram comparativo

[[backend-mvp-conta]], [[backend-mvp-agendamento]], [[backend-mvp-listagem]], [[backend-mvp-avaliacao-e-avisos]] e [[backend-mvp-fundacoes]] passam a ter Alvo, Hoje e Ajuste. O Ajuste é a tarefa. Onde o retrato do núcleo ou do BFF não descreve o comportamento, o Ajuste diz isso. Em [[backend-mvp-conta]], sexo no lugar de gênero, data de nascimento e nota ao nascer a conta são itens próprios. O endereço em [[backend-mvp-listagem]] parte do que [[core-08-enderecos]] já grava. Criptografia, Swagger e o disparador antigo continuam em [[mvp]].

## [2026-11-05] lint | Pendências do app viram comparativo

[[app-cliente-conta]], [[app-cliente-descoberta]], [[app-cliente-agendamento]] e [[app-cliente-copys]] deixam de ser lista do produto esperado. Cada item traz Alvo, Hoje e Ajuste. O Ajuste é o que uma tarefa do app precisa fazer. Onde o retrato de 21/10 não descreve a tela, o Ajuste começa dizendo que o retrato não tem a tela. Em [[app-cliente-copys]], os fluxos sem texto no retrato ficam só com o nome. O texto de dezembro de 2024 que fala em Stripe, PayPal e MercadoPago sai da tela; a redação nova dos termos continua diferida.

## [2026-11-05] lint | Conferência do alvo do cliente

A releitura do `05` e do `06` achou frases que o alvo não diz, ou que o alvo de outubro ainda repetia como se valesse.

- [[app-cliente-copys]]: a lista dos 16 fluxos tinha nomes inventados. Vale a lista de [[mvp-copys-cliente]]. Confirmação e Endereços não são fluxos. Faltavam Sessão e SMS de convite.
- [[app-cliente-descoberta]]: a home não abre sem conta. Sem conta, Início, Agenda e Perfil abrem a tela de bloqueio. A aba Artistas fica livre. O deslogado não "usa endereço sem salvar" em todo caso: começa com o do welcome; na troca pela listagem, o botão é "Usar este endereço". O logado salva todo endereço novo. A foto de divulgação não aparece no perfil no MVP.
- [[app-cliente-agendamento]]: o cartão tem menu. O toque não abre detalhe. Sem check-out, o cartão fica em Próximos até a meia-noite.
- [[cadastro]], [[busca-e-filtros]], [[agendamento]], [[mvp]], [[app-do-cliente]] e [[app-do-artista]]: saíram as frases que ainda tratavam duas etapas, telefone na segunda, "espera o arquivo de telas" e "endereço sem salvar" como alvo do cliente. O detalhe de tela do artista continua sem chegar.

## [2026-11-07] estrutura | Contradições divididas por tema

[[contradicoes-e-lacunas]] virou índice. Do MVP: [[contradicoes-conta]], [[contradicoes-agendamento]], [[contradicoes-busca]], [[contradicoes-avaliacao]], [[contradicoes-escopo]]. Fora do produto do MVP: [[contradicoes-negocio]], [[contradicoes-kit]], [[contradicoes-engenharia]]. Os números 1 a 35 permanecem. Nenhum status mudou.

## [2026-11-07] esquema | Síntese passa a ter pasta

Dez páginas `sintese` passaram para `wiki/sinteses/`. A tabela de tipos em CLAUDE.md aponta essa pasta. O wikilink continua por nome.
