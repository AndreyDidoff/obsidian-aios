> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Endereços

## Onde isso mora

1. No app: [[enderecos]] e [[enderecos-do-artista]]. A tela de gerenciar no perfil está em breve; o cadastro grava endereço.
2. No BFF: [[bff-enderecos]]. O app fala com api.wecareu.app.
3. Projeto Br.Address.API. Host https://addressapimicroservice.bptsoftware.com.br/
4. Banco [[banco-sql-address]]. O banco e a tabela se chamam `address`, em minúsculas.

## O que isso é

Este serviço guarda o endereço de um dono. Cada registro leva CEP, cidade, bairro, logradouro, número, complemento, ponto de referência, região, país, latitude e longitude, um nome e um tipo. O tipo aceita casa, trabalho e um terceiro valor gravado como busyness. O registro também marca se está ativo, quando nasceu, quando mudou e quem mudou, e fica ligado a um dono e a um sistema.

## O que já se consegue fazer

- **Listar.** Com sessão, devolve os endereços ativos daquele dono. A lista não separa por sistema. Nesta entrada a conferência da sessão tira o prefixo antes de validar.
- **Ver.** Com sessão, abre um endereço ativo quando dono, sistema e o próprio endereço batem. Aqui a sessão segue inteira para a conferência.
- **Criar.** Grava o endereço e devolve o identificador. Sem identificador na entrada, entra como novo e o identificador nasce na base. Esta entrada não confere sessão e não deixa rastro.
- **Editar.** Confere a sessão, relê o endereço e grava pelo mesmo caminho da criação: identificador vazio inclui, identificador preenchido substitui o que chegou. Se a gravação devolve identificador, tenta deixar rastro. A resposta diz se o rastro foi aceito.
- **Apagar.** Confere a sessão e desliga o endereço ativo daquele dono e daquele sistema. A linha continua em `address` e some da lista e da consulta. A resposta diz se o rastro foi aceito. A entrada pede um usuário que não entra no caminho e não é lido; quem alterou sai da sessão.

## Em que pé está

Dá para listar, abrir, gravar, alterar e desligar. A lista olha só o dono e só o que está ativo. Abrir e desligar exigem dono, sistema e o endereço, e também só enxergam o ativo. Criar não confere quem chama. Alterar e desligar conferem a sessão e gravam o dado antes do rastro: se o rastro quebra, a chamada falha com o endereço já mudado. Os dois rastros nascem rotulados como inclusão. Criar e alterar caem na mesma gravação. O serviço tem um atalho de edição que a entrada de alterar não usa; os dois gravariam igual. Desligar chega como leitura e marca o endereço inativo. A conferência de sessão sempre recoloca o prefixo na frente do que recebeu: por isso a lista, que tira o prefixo, aceita a sessão no formato usual, e ver, alterar e desligar, que mandam o cabeçalho inteiro, recebem essa sessão recusada. OwnerId está sem destino único. SystemId aponta por nome, com força forte, para SystemsData.Systems, em [[banco-sql-relacoes]]; não é constraint.

## O que esta nota não cobre

A tela do app, o cadastro que grava endereço e o que ainda está em breve no perfil. O BFF e o que api.wecareu.app faz na frente. Senha, string de conexão e identificador de empresa ou de aplicativo. O desenho do banco além do necessário para fechar a cadeia: o detalhe fica em [[banco-sql-address]] e [[banco-sql-relacoes]].

## Incertezas

Quem chamar ver, alterar ou desligar com o token cru, sem prefixo, passa na conferência; a lista também passa, porque não acha prefixo para tirar. Não há, neste serviço, um contrato único do formato da sessão.

No alterar, o “antes” do rastro é a resposta da releitura, não uma cópia limpa do endereço. A gravação segue mesmo quando essa releitura não acha nada. No desligar, o antes e o depois são o mesmo objeto, já inativo, então o rastro pode nascer sem diferença. Se não houver endereço ativo com aquele dono, sistema e identificador, desligar quebra em vez de responder que não havia o que desligar.

Se o identificador devolvido na alteração vier vazio, a chamada responde sucesso e não escreve rastro. No desligar, dono vazio também responde sucesso sem rastro. O usuário pedido na entrada de desligar não é o que vai para o rastro.

O terceiro tipo está escrito busyness. Não dá para fechar se isso é o tipo de negócio de propósito.

O mapa no código e o texto do rastro grafam o nome da tabela com inicial maiúscula. Esta nota segue o nome do banco: `address`.
