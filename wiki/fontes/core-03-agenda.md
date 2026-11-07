---
tipo: fonte
arquivo: "ingeridos/core-03-agenda.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Agenda"]
---

# Agenda

Retrato de 21/10 do projeto `Br.User.Service.API`. Host `https://serviceapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-systemservice]], SQL `SystemService`, tabelas `Schedule` e `ScheduleServicesProvided`. É o mesmo projeto, o mesmo host e o mesmo banco de [[core-02-servicos]].

Foto desse serviço. O alvo continua chatbot, em [[agendamento]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. Isto não implementa o agendamento do produto.

## Onde isso mora

1. No app. [[agenda]] e [[agenda-do-artista]] seguem casca em 21/10. O alvo de produto é chatbot. Esta nota não vira decisão. O núcleo já tem marcação. A tela não lê isso.
2. No BFF. O retrato do BFF de 21/10 não publica porta de agenda.
3. Neste serviço: `Br.User.Service.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

A marcação de um horário entre quem pediu e quem atende, numa empresa, num endereço de atendimento, com um sinal de se o atendimento é entrega. O horário leva início, fim previsto, duração e um andamento: agendado, em análise, a caminho, em atendimento, concluído ou cancelado. Cada horário carrega as linhas do que vai ser feito: qual serviço, início, fim previsto, uma observação e o mesmo andamento. Horário e linha guardam se ainda estão ativos, quando nasceram, quando mudaram e quem mudou.

Quem pediu e quem atende enxergam a mesma lista, desde que o horário esteja ativo. A lista não separa por empresa, por endereço nem por andamento.

## O que já se consegue fazer

Dá para listar horário ativo, gravar marcação e cancelar.

Listar os horários ativos em que a pessoa é quem pediu ou quem atende. Entram junto as linhas cujo vínculo é aquele horário, inclusive linha já cancelada ou inativa. A pessoa vem no pedido. A lista não confere sessão.

Marcar um horário novo, com as linhas que vierem no mesmo pedido. Antes de gravar, a duração do horário é reescrita: em cada linha, soma o fim previsto menos o início em cima da duração que chegou. O horário grava primeiro. Em seguida cada linha recebe, no vínculo com o horário, o próprio identificador da linha, e só então a linha grava. A marcação nova não fica achável na lista: o vínculo gravado é o da própria linha, não o do horário. O andamento que fica é o que veio no pedido; se não vier, nasce agendado. Não há ação de alterar o horário, nem de passar a em análise, a caminho, em atendimento ou concluído.

Cancelar o horário. A linha continua na tabela, o andamento passa a cancelado e o horário segue ativo. O cancelado continua na lista, porque a lista olha quem está ativo e não o andamento. Cancelar uma linha de serviço faz o mesmo só nessa linha e não mexe no horário. As duas ações chegam como consulta. Se o horário ou a linha não existem, a chamada quebra em vez de dizer que não havia o que cancelar.

Nenhuma ação confere quem chama. Nenhuma deixa rastro nem preenche quem alterou. A autenticação preparada na subida do serviço não entra neste caminho.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito com ressalva | Listar horário ativo, gravar uma marcação nova e cancelar horário ou linha. A tela de 21/10 não lê isso |
| Pela metade | A marcação nova não deixa a linha achável na lista. O cancelado continua na lista. Os outros andamentos existem no registro; a única ação que escolhe um andamento é o cancelamento |
| Casca | A autenticação preparada na subida. Ela não entra neste caminho. Isto não implementa o agendamento do produto |

`OnANalisys` é a grafia do andamento em análise. É o valor entre agendado e a caminho.

`ScheduleServicesProvided.ServiceId` está sem destino único em [[banco-sql-relacoes]]. `ServiceProvideAddressId` aponta com força fraca para `address.address` e não é constraint. `CompanyId` aponta com força forte para `Company`, no mesmo banco. `RequestedUserId` e `ProviderUserId` são força fraca para `Usuario`. O código não declara constraint nesses campos e não confere se a pessoa, a empresa, o endereço ou o serviço existem.

## O que esta nota não cobre

O aplicativo, o título das abas e o cartão de próximos agendamentos. A decisão de produto sobre chatbot. O BFF por dentro. A conversa do agendamento. O miolo de serviço, empresa, endereço e conta, além do vínculo. Pagamento. Senha, string de conexão e identificador. O desenho do banco além do necessário: [[banco-sql-systemservice]] e [[banco-sql-relacoes]].

## Incertezas

A duração está gravada como data. Somar o intervalo de cada serviço desloca essa data; não vira um tempo de duração solto. Se a marcação chegar sem linhas, a gravação quebra antes de salvar.

Quem alterou sai do pedido. O serviço não copia isso de uma sessão.

[[banco-sql-relacoes]] lê o vínculo da linha como força forte para `Schedule`, e não é constraint. Na gravação, o código troca esse vínculo pelo identificador da própria linha. Vale o código.

Este repositório não declara o host público de `Br.User.Service.API`. O endereço `https://serviceapimicroservice.bptsoftware.com.br/` fecha a cadeia pedida nesta extração.

O compose do serviço `br.user.service.api` aponta o banco `SystemService`, e a configuração deste projeto declara esse catálogo. O código que sobe no Windows e no Linux não lê essa variável: pega a conexão de login e força o catálogo `UserLogin`. Fora desses dois sistemas, o serviço pede uma conexão chamada `Address`, e a configuração deste projeto não declara `Address`. Por este repositório não dá para fechar qual banco o host publicado está usando agora. As tabelas mapeadas continuam `Schedule` e `ScheduleServicesProvided`. O contexto nomeia as coleções de outro jeito; vale a tabela. A entrada de agenda está grafada `Schedulle`.

Ver [[bpt-core]] e [[core-02-servicos]].
