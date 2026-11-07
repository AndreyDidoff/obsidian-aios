> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Idiomas

## Onde isso mora

1. No app. Os textos da tela dos apps não são esta tabela. Esta nota não reescreve essas telas.
2. No BFF. Idiomas ficam só preparados ([[bff-preparado-e-ainda-nao-oferecido]]).
3. No projeto Br.I18N.API, no host https://i18napimicroservice.bptsoftware.com.br/
4. No banco [[banco-sql-i18n]]. O banco e a tabela se chamam I18N. O compose deste repositório (Br.Login.API/docker-compose.yml, serviço br.i18n.api) não declara Database. O wikilink desta nota é o do servidor.

## O que isso é

É o serviço que guarda o texto de uma etiqueta, num idioma, para uma tela, um sistema e uma empresa. Junto vão se a linha ainda está em uso, quando nasceu, quando mudou e quem mudou. O idioma é um código curto. A etiqueta e o texto traduzido viajam na mesma linha.

A lista devolve o que continua em uso para aquela empresa e aquele sistema, em qualquer idioma e qualquer tela. Linha fora de uso não volta.

SystemId é força forte para Systems. Screen é força fraca para Screens. Enterprise é força fraca para Enterprise.Enterprise. As três amarrações estão em [[banco-sql-relacoes]] e não são constraint. Ao gravar, o serviço aceita os três identificadores que vierem e não procura o sistema, a tela nem a empresa.

## O que já se consegue fazer

Listar as traduções em uso de uma empresa e de um sistema. O pedido leva esses dois identificadores. Não há lista por etiqueta, por idioma ou por uma tela só.

Regravar uma tradução. O pedido manda a linha inteira no corpo de uma consulta. Com identificador, essa foto substitui a linha, inclusive datas, quem mudou e se continua em uso. Quem mudou precisa vir na própria linha: o serviço não preenche isso com quem está na sessão. Sem identificador, a mesma ação não abre linha nova. A gravação não acha linha, a chamada responde mesmo assim e o corpo diz que nada foi gravado. Não há conferência de código de idioma, de etiqueta vazia nem de texto vazio além do que a tabela recusar. Não há ação de incluir nem de apagar. A linha só sai da lista se uma regravação a marcar como fora de uso.

Quando o identificador já vem preenchido, antes de gravar o serviço tenta uma trilha. A trilha descreve a mudança como inclusão, nomeia o verbo como envio e grava o banco e a tabela como Email. O dado desta nota continua em I18N. O serviço não olha se a trilha disse que gravou: a regravação segue. Se a trilha estourar, a regravação não acontece. A trilha exige no pedido quem fez, o nome, a empresa e o sistema. Linha sem identificador não passa por essa trilha.

Antes de listar e de regravar, o serviço pergunta ao login se o acesso vale. Se o login aceita, a ação é recusada. Se o login não aceita, a ação segue. A autenticação preparada na subida do serviço não entra no caminho do pedido. A única trava é essa checagem.

O cliente interno que os outros serviços usam lista por consulta, no mesmo caminho da lista. A regravação desse cliente, e a de uma variante mais antiga do mesmo cliente, sai por envio. O serviço só regrava numa consulta. O envio não alcança a ação. A tela de login deste repositório só pede a lista, nesse host.

Lista e regravação, quando falham, saem com o mesmo aviso de carregamento de traduções.

## Em que pé está

Já se pede a lista de traduções em uso de uma empresa e de um sistema, a regravação só substitui linha que já tem identificador e só numa consulta, a ação segue quando o login recusa o acesso, e o modelo pede colunas que o script da tabela não cria.

## O que esta nota não cobre

Os textos desenhados nas telas dos apps. O miolo do que o BFF ainda não oferece; o elo é [[bff-preparado-e-ainda-nao-oferecido]]. Qual idioma aparece para a pessoa, idioma de reserva e arquivo de tradução do aplicativo. Senha e connection string. O conteúdo das linhas já gravadas.

## Incertezas

O modelo que o serviço lê chama a data de criação de DtCreated e quem mudou de DsChangedBy. O script que cria a tabela I18N, e o backup deste repositório, usam Created e ChangedBy. A data de mudança fecha nos dois, como DtChange. Contra esse script, listar e regravar quebram ao ler a linha. Não dá para fechar, por este repositório, se o banco do host publicado já ganhou as colunas que o modelo pede.

No Windows e no Linux o serviço pega a conexão de login e força o catálogo I18N. Fora desses dois sistemas, pede uma conexão chamada Address. A configuração deste projeto declara a conexão I18N e não declara Address. O compose do serviço br.i18n.api não declara Database. O wikilink permanece [[banco-sql-i18n]].

A pergunta ao login reenvia o acesso já apresentado como acesso. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler a porta como fechada para quem não está logado.

A regravação viaja no corpo de uma consulta. Caminho que descarta corpo de consulta chega sem a linha. O cliente interno, se um dia o envio alcançasse a ação, leria o sucesso da chamada e ignoraria um corpo dizendo que nada foi gravado. A conversa com o banco nasce na primeira chamada e as seguintes reaproveitam essa mesma conversa.
