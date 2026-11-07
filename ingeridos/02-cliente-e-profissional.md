> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cliente e profissional

## O que isso é para o app

No cadastro, este backend reconhece dois papéis: cliente (User) e profissional (Artist). Os dois entram pela mesma porta de cadastro, em caminhos separados.

O backend está amarrado a uma empresa e a um aplicativo. Esse vínculo participa do cadastro do profissional.

## O que a pessoa já consegue fazer por este backend

Cadastrar-se como cliente. Esse pedido segue com os dados do cadastro. Neste backend, ele não recebe a empresa nem o aplicativo.

Cadastrar-se como profissional. Esse pedido recebe a empresa e o aplicativo aos quais este backend está amarrado.

A mesma porta ainda confere e-mail e documentos. Esses dois pedidos não escolhem o papel. O restante do cadastro está em [[04-cadastro]].

Depois do cadastro, as outras portas tratam a pessoa da sessão. Nenhuma delas abre um caminho próprio de cliente ou de profissional.

## Quem pode

Quem pede o cadastro. A porta de cadastro não declara sessão. Fora desse momento, este backend não mostra quem é cliente e quem é profissional.

## Em que pé está

No ar. A porta de cadastro existe e o serviço de usuário está ligado no arranque, no mesmo serviço usado para entrar.

## O que esta nota não cobre

Telas. Perfil, portfólio e comissão não aparecem neste repositório. Também ficam de fora os campos de cada cadastro e o detalhe de entrar, senha, serviços, bloqueio, endereço, telefone, foto, relato, documento, permissão e plano.

## Ligações

[[01-o-que-e-este-backend]] [[03-entrar-sair-e-senha]] [[04-cadastro]]

## Incertezas

Os campos do cadastro de cliente e do cadastro de profissional moram no pacote de usuário, fora deste repositório. Dá para ver que os caminhos são distintos e que o profissional recebe a empresa e o aplicativo. Não dá para listar o que cada cadastro pede.

Nas portas de serviço, bloqueio, endereço, telefone, foto, relato, documento e permissão não há leitura de papel. Se o aplicativo trata cliente e profissional de forma diferente depois do cadastro, essa diferença está em outro lugar.
