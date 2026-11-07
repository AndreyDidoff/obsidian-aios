> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# O que é este backend

## O que isso é para o app

Este repositório é o backend de apoio ao aplicativo da WeCareU. O nome interno do projeto é Beautiful. No catálogo de rotas, o título exposto é "We Care U Service". Os pedidos do aplicativo entram pelo prefixo `beautiful/api/`.

Ele não desenha tela. Encaminha o pedido aos serviços da empresa. A regra de negócio mora nesses serviços.

Está amarrado a uma empresa e a um aplicativo. Esse vínculo sobe com o backend, no dado interno CompanyData (empresa e aplicativo). Os identificadores ficam na configuração e não entram nesta nota.

Há um banco local declarado no arranque. Ele não mapeia informação de negócio. Comentários antigos de atualização para idiomas, bloqueio, auditoria, usuário de sistema e redefinição de senha estão desligados. Este backend não é o lugar onde esses dados moram.

## O que a pessoa já consegue fazer por este backend

Cada linha é uma nota. O detalhe mora nela.

- [[02-cliente-e-profissional]] — dois papéis no cadastro: cliente e profissional. O profissional recebe, neste backend, a empresa e o aplicativo.
- [[03-entrar-sair-e-senha]] — entrar, sair, conferir a sessão e o fluxo de senha: pedir a troca, recusar, validar o pedido e trocar.
- [[04-cadastro]] — cadastrar cliente ou profissional, conferir o e-mail e conferir documentos (CPF e, se vier, CNPJ).
- [[05-servicos]] — ver, gravar, editar e apagar serviços da pessoa e serviços do sistema.
- [[06-planos-e-cupons]] — a porta lista planos e valida cupom, e exige sessão. O serviço por trás não está conectado.
- [[07-bloqueio]] — ver os bloqueios da pessoa da sessão, registrar um bloqueio e desfazer, com sessão.
- [[08-enderecos]] — ver, criar, editar e apagar endereços, com sessão.
- [[09-telefones]] — ver, incluir, editar e apagar telefones, com sessão.
- [[10-fotos]] — obter uma foto, incluir e apagar, com sessão.
- [[11-relatos]] — ver, gravar, editar e apagar relatos e as fotos do relato, com sessão.
- [[12-documentos-para-validacao]] — obter, enviar, editar e apagar documentos de validação, com sessão.
- [[13-o-que-a-pessoa-pode-ver]] — permissões e grupos do aplicativo, e o que um conjunto de grupos libera, com sessão.
- [[14-preparado-e-ainda-nao-oferecido]] — serviços que o backend já conhece e ainda não oferece ao aplicativo, o canal de e-mail fora de uso e o banco local vazio de negócio.

## Quem pode

Quem usa o aplicativo. O cadastro separa cliente (User) e profissional (Artist). Entrar, o fluxo de senha e o cadastro não declaram sessão. Sair, conferir a sessão, bloqueio, endereços, telefones, fotos, relatos, documentos de validação, permissões, grupos e planos declaram sessão. Fora do cadastro, as portas tratam a pessoa da sessão e não escolhem o caminho pelo papel.

## Em que pé está

No ar — entrar e sair, senha, cadastro, serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação, permissões e grupos. A porta existe e o serviço por trás está ligado no arranque.

Porta sem ligação — planos e cupons. A porta existe e exige sessão. O serviço de planos não está registrado no arranque, e a lista de endereços dos serviços não nomeia planos.

Só preparado — auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem e o cliente de e-mail. O backend conhece o serviço e não oferece a ação ao aplicativo.

Fora de uso — o canal de e-mail. Há código da porta, vazio, e ele está desligado da compilação.

O banco local sobe com o backend e não guarda o negócio. O detalhe está em [[14-preparado-e-ainda-nao-oferecido]].

## O que esta nota não cobre

Telas, campos dos pacotes de fora deste repositório, senha, chave de sessão, identificadores da empresa e do aplicativo, e endereço dos serviços. O passo a passo de cada capacidade está nas notas ligadas.

## Ligações

[[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

O arranque prepara a sessão. A leitura da sessão não entra no caminho do pedido. As portas que declaram sessão podem receber o pedido sem a pessoa preenchida. Isso fica em aberto até o comportamento em execução ou uma decisão da empresa.

Várias portas recebem um cliente de auditoria e um cliente de autenticação e não os chamam. A ação oferecida de sessão é entrar, sair e conferir a sessão, pelo serviço de login.

A configuração nomeia um serviço de registro de falhas. O arranque não liga esse cliente. O canal de e-mail fora de uso ainda o pede.

Os campos de cadastro, plano, endereço, telefone, foto, relato e documento moram em pacotes fora deste repositório. Esta nota não completa esses campos.
