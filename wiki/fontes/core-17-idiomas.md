---
tipo: fonte
arquivo: "ingeridos/core-17-idiomas.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Idiomas"]
---

# Idiomas

Retrato de 21/10 do projeto `Br.I18N.API`. Host `https://i18napimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-i18n]]. O banco e a tabela se chamam `I18N`. O compose deste repositório (`Br.Login.API/docker-compose.yml`, serviço `br.i18n.api`) não declara `Database`. O wikilink permanece o do servidor, [[banco-sql-i18n]]. No Windows e no Linux o código força o catálogo `I18N`.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. Isto não é o texto desenhado nas telas dos apps. No BFF, idiomas seguem só preparados ([[bff-preparado-e-ainda-nao-oferecido]]).

## Onde isso mora

1. No app. Os textos da tela dos apps não são esta tabela. Esta nota não reescreve essas telas.
2. No BFF. Idiomas ficam só preparados. O elo é [[bff-preparado-e-ainda-nao-oferecido]]. O aplicativo fala com `api.wecareu.app`.
3. Neste serviço: `Br.I18N.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O serviço que guarda o texto de uma etiqueta, num idioma, para uma tela, um sistema e uma empresa. Junto vão se a linha ainda está em uso, quando nasceu, quando mudou e quem mudou. O idioma é um código curto. A etiqueta e o texto traduzido viajam na mesma linha.

`Screen` aqui não é tela de aplicativo. É o identificador da linha, com força fraca para `Screens`. `SystemId` é força forte para `Systems`. `Enterprise` é força fraca para `Enterprise.Enterprise`. As três amarrações estão em [[banco-sql-relacoes]] e não são constraint. Ao gravar, o serviço aceita os três identificadores que vierem e não procura o sistema, a tela nem a empresa.

A lista devolve o que continua em uso para aquela empresa e aquele sistema, em qualquer idioma e qualquer `Screen`. Linha fora de uso não volta.

## O que já se consegue fazer

Listar as traduções em uso de uma empresa e de um sistema. O pedido leva esses dois identificadores. Não há lista por etiqueta, por idioma ou por uma tela só.

Regravar uma tradução. O pedido manda a linha inteira no corpo de uma consulta. Com identificador, essa foto substitui a linha, inclusive datas, quem mudou e se continua em uso. Quem mudou precisa vir na própria linha: o serviço não preenche isso com quem está na sessão. Sem identificador, a mesma ação não abre linha nova. A gravação não acha linha, a chamada responde mesmo assim e o corpo diz que nada foi gravado. Não há conferência de código de idioma, de etiqueta vazia nem de texto vazio além do que a tabela recusar.

Não há ação de incluir nem de apagar. A regravação só substitui linha que já tem identificador, e só numa consulta. A linha só sai da lista se uma regravação a marcar como fora de uso.

Quando o identificador já vem preenchido, antes de gravar o serviço tenta uma trilha. A trilha descreve a mudança como inclusão, nomeia o verbo como envio e grava o banco e a tabela como `Email`. O dado desta nota continua em `I18N`. O serviço não olha se a trilha disse que gravou: a regravação segue. Se a trilha estourar, a regravação não acontece. A trilha exige no pedido quem fez, o nome, a empresa e o sistema. Linha sem identificador não passa por essa trilha.

A checagem de acesso está invertida. Antes de listar e de regravar, o serviço pergunta ao login se o acesso vale. Se o login aceita, a ação é recusada. Se o login não aceita, a ação segue. A autenticação preparada na subida do serviço não entra no caminho do pedido. A única trava é essa checagem.

O cliente interno que os outros serviços usam lista por consulta, no mesmo caminho da lista. A regravação desse cliente, e a de uma variante mais antiga do mesmo cliente, sai por envio. O serviço só regrava numa consulta. O envio não alcança a ação. A tela de login deste repositório só pede a lista, nesse host.

Lista e regravação, quando falham, saem com o mesmo aviso de carregamento de traduções.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Pela metade | Já se pede a lista de traduções em uso de uma empresa e de um sistema. A regravação só substitui linha que já tem identificador e só numa consulta. Não há incluir nem apagar. A checagem está invertida. No BFF, idiomas seguem só preparados. Isto não é o texto desenhado nas telas dos apps |
| Casca | O modelo pede `DtCreated` e `DsChangedBy`; o script da tabela usa `Created` e `ChangedBy`. Contra esse script, listar e regravar quebram ao ler a linha |

## O que esta nota não cobre

Os textos desenhados nas telas dos apps. O miolo do que o BFF ainda não oferece; o elo é [[bff-preparado-e-ainda-nao-oferecido]]. Qual idioma aparece para a pessoa, idioma de reserva e arquivo de tradução do aplicativo. Senha e connection string. O conteúdo das linhas já gravadas.

## Incertezas

O modelo que o serviço lê chama a data de criação de `DtCreated` e quem mudou de `DsChangedBy`. O script que cria a tabela `I18N`, e o backup deste repositório, usam `Created` e `ChangedBy`. A data de mudança fecha nos dois, como `DtChange`. Contra esse script, listar e regravar quebram ao ler a linha. Não dá para fechar, por este repositório, se o banco do host publicado já ganhou as colunas que o modelo pede. Esta nota não fecha isso.

No Windows e no Linux o serviço pega a conexão de login e força o catálogo `I18N`. Fora desses dois sistemas, pede uma conexão chamada `Address`. A configuração deste projeto declara a conexão `I18N` e não declara `Address`. O compose do serviço `br.i18n.api` não declara `Database`. O wikilink permanece [[banco-sql-i18n]].

A pergunta ao login reenvia o acesso já apresentado como acesso. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler a porta como fechada para quem não está logado.

A regravação viaja no corpo de uma consulta. Caminho que descarta corpo de consulta chega sem a linha. O cliente interno, se um dia o envio alcançasse a ação, leria o sucesso da chamada e ignoraria um corpo dizendo que nada foi gravado. A conversa com o banco nasce na primeira chamada e as seguintes reaproveitam essa mesma conversa.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
