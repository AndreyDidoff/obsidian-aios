---
tipo: fonte
arquivo: "ingeridos/02-cliente-e-profissional.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cliente e profissional"]
---

# Cliente e profissional

No cadastro, este backend reconhece dois papéis: cliente (User) e profissional (Artist). Os dois entram pela mesma porta, em caminhos separados. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

O backend está amarrado a uma empresa e a um aplicativo. Esse vínculo participa do cadastro do profissional.

Cadastrar-se como cliente segue com os dados do cadastro. Neste backend, esse pedido não recebe a empresa nem o aplicativo.

Cadastrar-se como profissional recebe a empresa e o aplicativo aos quais este backend está amarrado (CompanyData).

A mesma porta ainda confere e-mail e documentos. Esses dois pedidos não escolhem o papel. O restante do cadastro está em [[bff-cadastro]].

Depois do cadastro, as outras portas tratam a pessoa da sessão. Nenhuma delas abre um caminho próprio de cliente ou de profissional.

## Quem pode

Quem pede o cadastro. A porta de cadastro não declara sessão. Fora desse momento, este backend não mostra quem é cliente e quem é profissional.

## Em que pé está

No ar. A porta de cadastro existe e o serviço de usuário está ligado no arranque, no mesmo serviço usado para entrar.

## O que esta nota não cobre

Telas. Perfil, portfólio e comissão não aparecem neste repositório. Também ficam de fora os campos de cada cadastro e o detalhe das outras capacidades, nomeadas em [[bff-o-que-e-este-backend]].

## Incertezas

Os campos do cadastro de cliente e do cadastro de profissional moram no pacote de usuário, fora deste repositório. Dá para ver que os caminhos são distintos e que o profissional recebe a empresa e o aplicativo. Não dá para listar o que cada cadastro pede.

Nas portas de serviço, bloqueio, endereço, telefone, foto, relato, documento e permissão não há leitura de papel. Se houver diferença entre cliente e profissional depois do cadastro, ela está em outro lugar.

Ver [[beautiful-api]].
