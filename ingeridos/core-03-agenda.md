> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Agenda

## Onde isso mora

1. No app. [[agenda]] e [[agenda-do-artista]] são casca em 21/10. O alvo de produto é chatbot; esta nota não vira decisão. O núcleo já tem marcação. A tela não lê isso.
2. No BFF. O retrato do BFF de 21/10 não publica uma porta de agenda.
3. No projeto Br.User.Service.API, no host https://serviceapimicroservice.bptsoftware.com.br/
4. No banco [[banco-sql-systemservice]], SQL SystemService, tabelas Schedule e ScheduleServicesProvided.

## O que isso é

É a marcação de um horário entre quem pediu e quem atende, numa empresa, num endereço de atendimento, com um sinal de se o atendimento é entrega. O horário leva início, fim previsto, duração e um andamento: agendado, em análise, a caminho, em atendimento, concluído ou cancelado. Cada horário carrega as linhas do que vai ser feito: qual serviço, início, fim previsto, uma observação e o mesmo andamento. Horário e linha guardam se ainda estão ativos, quando nasceram, quando mudaram e quem mudou.

Quem pediu e quem atende enxergam a mesma lista, desde que o horário esteja ativo. A lista não separa por empresa, por endereço nem por andamento.

## O que já se consegue fazer

Listar os horários ativos em que a pessoa é quem pediu ou quem atende. Entram junto as linhas cujo vínculo é aquele horário, inclusive linha já cancelada ou inativa. A pessoa vem no pedido. A lista não confere sessão.

Marcar um horário novo, com as linhas que vierem no mesmo pedido. Antes de gravar, a duração do horário é reescrita: em cada linha, soma o fim previsto menos o início em cima da duração que chegou. O horário grava primeiro. Em seguida cada linha recebe, no vínculo com o horário, o próprio identificador da linha, e só então a linha grava. O andamento que fica é o que veio no pedido; se não vier, nasce agendado. Não há ação de alterar o horário, nem de passar a em análise, a caminho, em atendimento ou concluído.

Cancelar o horário. A linha continua na tabela, o andamento passa a cancelado e o horário segue ativo, então continua na lista. Cancelar uma linha de serviço faz o mesmo só nessa linha e não mexe no horário. As duas ações chegam como consulta. Se o horário ou a linha não existem, a chamada quebra em vez de dizer que não havia o que cancelar.

Nenhuma dessas ações confere quem chama, não deixa rastro e não preenche quem alterou. A autenticação preparada na subida do serviço não entra neste caminho.

## Em que pé está

Dá para listar horário ativo, gravar uma marcação nova e cancelar horário ou linha, e a tela de 21/10 não lê isso. O cancelado continua na lista, porque a lista olha quem está ativo e não o andamento. A marcação nova não deixa a linha achável nessa lista, porque o vínculo gravado é o da própria linha, não o do horário. Os outros andamentos existem no registro; a única ação que escolhe um andamento é o cancelamento. ScheduleServicesProvided.ServiceId está sem destino único em [[banco-sql-relacoes]]. ServiceProvideAddressId aponta com força fraca para address.address e não é constraint. CompanyId aponta com força forte para Company, no mesmo banco. RequestedUserId e ProviderUserId são força fraca para Usuario. O código não declara constraint nesses campos e não confere se a pessoa, a empresa, o endereço ou o serviço existem.

## O que esta nota não cobre

O aplicativo, o título das abas e o cartão de próximos agendamentos. A decisão de produto sobre chatbot. O BFF por dentro. A conversa do agendamento. O miolo de serviço, empresa, endereço e conta, além do vínculo. Pagamento. Senha, connection string e identificador de empresa ou aplicativo. O desenho do banco além do necessário para fechar a cadeia: o detalhe fica em [[banco-sql-systemservice]] e [[banco-sql-relacoes]].

## Incertezas

O andamento em análise está grafado OnANalisys no código. É o valor entre agendado e a caminho.

A duração está gravada como data. Somar o intervalo de cada serviço desloca essa data; não vira um tempo de duração solto. Se a marcação chegar sem linhas, a gravação quebra antes de salvar.

Quem alterou sai do pedido. O serviço não copia isso de uma sessão.

[[banco-sql-relacoes]] lê o vínculo da linha como força forte para Schedule, e não é constraint. Na gravação, o código troca esse vínculo pelo identificador da própria linha. Vale o código.

Este repositório não declara o host público de Br.User.Service.API. O endereço https://serviceapimicroservice.bptsoftware.com.br/ fecha a cadeia pedida nesta extração.

O compose do serviço br.user.service.api aponta o banco SystemService, e a configuração deste projeto declara esse catálogo. O código que sobe no Windows e no Linux não lê essa variável: pega a conexão de login e força o catálogo UserLogin. Fora desses dois sistemas, o serviço pede uma conexão chamada Address, e a configuração deste projeto não declara Address. Por este repositório não dá para fechar qual banco o host publicado está usando agora. As tabelas mapeadas continuam Schedule e ScheduleServicesProvided. O contexto nomeia as coleções de outro jeito; vale a tabela. A entrada de agenda está grafada Schedulle.
