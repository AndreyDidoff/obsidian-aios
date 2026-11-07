---
tipo: fonte
arquivo: "ingeridos/core-08-enderecos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Endereços"]
---

# Endereços

Retrato de 21/10 do projeto `Br.Address.API`. Host `https://addressapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-address]]. O banco e a tabela se chamam `address`, em minúsculas.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]]. O CEP deste serviço é campo gravado. O CEP do cadastro e da visita no app continua a consulta ao mapa da Google, fora daqui. A tela de gerenciar no perfil segue em breve. O item 16 de [[contradicoes-e-lacunas]], quando o endereço aparece para o Artista, segue aberto.

## Onde isso mora

1. No app: [[enderecos]] e [[enderecos-do-artista]]. A tela de gerenciar no perfil está em breve. O cadastro grava endereço.
2. No BFF: [[bff-enderecos]]. O aplicativo fala com `api.wecareu.app`. Esta nota não reescreve o miolo dessa porta.
3. Neste serviço: `Br.Address.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O endereço de um dono. Cada registro leva CEP, cidade, bairro, logradouro, número, complemento, ponto de referência, região, país, latitude e longitude, um nome e um tipo. O tipo aceita casa, trabalho e um terceiro valor gravado como `busyness`. Não dá para fechar se `busyness` é o tipo de negócio. O registro marca se está ativo, quando nasceu, quando mudou e quem mudou, e fica ligado a um dono e a um sistema.

## O que já se consegue fazer

Listar. Com sessão, devolve os endereços ativos daquele dono. A lista não separa por sistema. Nesta entrada a conferência tira o prefixo antes de validar.

Ver. Com sessão, abre um endereço ativo quando dono, sistema e o próprio endereço batem. Aqui a sessão segue inteira para a conferência.

Criar. Grava o endereço e devolve o identificador. Sem identificador na entrada, entra como novo e o identificador nasce na base. Criar não confere sessão e não deixa rastro.

Editar. Confere a sessão, relê o endereço e grava pelo mesmo caminho da criação: identificador vazio inclui, identificador preenchido substitui o que chegou. Se a gravação devolve identificador, tenta deixar rastro. A resposta diz se o rastro foi aceito.

Desligar. Confere a sessão e desliga o endereço ativo daquele dono e daquele sistema. A linha desligada continua na tabela `address` e some da lista e da consulta. A resposta diz se o rastro foi aceito.

A conferência de sessão sempre recoloca o prefixo na frente do que recebeu. Por isso a lista, que tira o prefixo, aceita a sessão no formato usual, e ver, alterar e desligar, que mandam o cabeçalho inteiro, recebem essa sessão recusada.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito com ressalva | Listar, ver, criar, alterar e desligar. A lista aceita a sessão usual. Ver, alterar e desligar recebem a sessão recusada, porque a conferência recoloca o prefixo. Criar não confere quem chama. A linha desligada continua em `address` |
| Pela metade | Alterar e desligar gravam o dado antes do rastro. Se o rastro quebra, a chamada falha com o endereço já mudado. Os dois rastros nascem rotulados como inclusão |

`OwnerId` está sem destino único. `SystemId` aponta por nome, com força forte, para `SystemsData.Systems`, em [[banco-sql-relacoes]]; não é constraint.

## O que esta nota não cobre

A tela do app, o cadastro que grava endereço e o que ainda está em breve no perfil. Quando o endereço aparece para o Artista: o item 16 segue aberto. O BFF e o que `api.wecareu.app` faz na frente. Senha, string de conexão e identificador de empresa ou de aplicativo. O desenho do banco além do necessário: [[banco-sql-address]] e [[banco-sql-relacoes]].

## Incertezas

Quem chamar ver, alterar ou desligar com o token cru, sem prefixo, passa na conferência. A lista também passa, porque não acha prefixo para tirar. Não há, neste serviço, um contrato único do formato da sessão.

Se não houver endereço ativo com aquele dono, sistema e identificador, desligar quebra em vez de responder que não havia o que desligar.

O terceiro tipo está escrito `busyness`. Não dá para fechar se isso é o tipo de negócio de propósito.

O mapa no código e o texto do rastro grafam o nome da tabela com inicial maiúscula. Esta nota segue o nome do banco: `address`.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
