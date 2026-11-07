---
tipo: fonte
arquivo: "ingeridos/core-09-telefones.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Telefones"]
---

# Telefones

Retrato de 21/10 do projeto `Br.Phone.API`. Host `https://phoneapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-phone]]. O servidor nomeia o banco `Phone` e a tabela `Telefones`. O compose aponta `Database` para `PaymentPlan`. O wikilink permanece o do servidor. No Windows e no Linux o código força o catálogo `Phone`. Não dá para fechar qual banco o host publicado usa agora.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. Isto não é o telefone da segunda etapa do [[cadastro]].

## Onde isso mora

1. No app. Os apps de 21/10 não têm tela de gerir telefones em uso. O telefone entra no cadastro como dado. Esta nota não reescreve essa tela.
2. No BFF. [[bff-telefones]]. O aplicativo fala com `api.wecareu.app`. Esta nota não reescreve o miolo dessa porta.
3. Neste serviço: `Br.Phone.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O telefone de um dono: o número, um nome para esse telefone, se é celular, se ainda está em uso, quando nasceu, quando mudou e quem mudou. O dono vai no `OwnerId`. A lista do dia a dia só devolve telefone que continua ativo. `OwnerId` está sem destino único em [[banco-sql-relacoes]]; não é constraint. O serviço aceita o dono que vier sem conferir se esse cadastro existe.

## O que já se consegue fazer

Listar os telefones ativos de um dono. O identificador desse pedido é o dono, não o código de um telefone. Número desligado não volta.

Incluir um telefone. Se o pedido chega sem identificador, o serviço cria um e grava a linha. Se o identificador já vem preenchido, esse mesmo pedido regrava a linha existente. O telefone entra ativo quando o pedido não diz o contrário. Viajam juntos o número, o nome, se é celular, quem alterou e as datas. Não há conferência de formato do número, nem regra de um telefone só por dono.

Editar um telefone. O pedido manda o telefone inteiro, e essa foto substitui a linha. Identificador vazio nesse pedido vira inclusão, não alteração. A edição não deixa trilha.

Apagar um telefone. A linha não sai da tabela: fica fora de uso e deixa de aparecer na lista. A trilha que roda antes trata o identificador como dono e fica com o primeiro telefone ativo desse dono. O desligamento procura um telefone cujo código seja esse mesmo identificador. As duas leituras não apontam para a mesma coisa. Se não houver telefone ativo para aquele dono, a trilha quebra e o número permanece como estava. Quando a trilha chega a ser escrita, ela nomeia a tabela como `Phone`. O modelo da linha aponta para `Telefones`.

A checagem de acesso está invertida, igual à de [[core-07-bloqueio]]: token aceito pelo login vira recusa, e token recusado deixa listar, incluir, editar e apagar seguirem. A autenticação preparada na subida não entra no caminho do pedido. A única trava é essa checagem.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito com ressalva | Listar, incluir, editar e apagar estão escritos e respondem. A checagem está invertida. Não há conferência de formato nem regra de um telefone só. Os apps de 21/10 seguem sem tela para gerir telefones em uso |
| Pela metade | O apagar pode quebrar na trilha antes de desligar o número. A trilha grava a tabela como `Phone`; o modelo aponta para `Telefones` |
| Casca | A autenticação preparada na subida. Ela não entra no caminho do pedido |

## O que esta nota não cobre

O aplicativo e a tela de cadastro em que o número é digitado. O telefone da segunda etapa do [[cadastro]]. O BFF por dentro; o elo é [[bff-telefones]]. Operadora, DDD, máscara, WhatsApp e qual tipo de cadastro pode ser dono do número. Senha, connection string e identificador de empresa ou de aplicativo.

## Incertezas

O wikilink do banco permanece [[banco-sql-phone]]: o servidor nomeia o banco `Phone` e a tabela `Telefones`. O compose deste repositório aponta `Database` para `PaymentPlan`. No Windows e no Linux o código força o catálogo `Phone`. Por este repositório não dá para fechar qual banco o host publicado está usando agora.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
