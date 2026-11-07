> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Serviços

## O que isso é para o app

É a porta de serviços deste backend. Por ela o aplicativo pede o que a pessoa oferece e o que entra no catálogo da plataforma. São duas famílias distintas: o serviço da pessoa e o item do catálogo da plataforma.

## O que a pessoa já consegue fazer por este backend

O aplicativo já pode pedir, nesta porta:

- Listar os serviços da pessoa que está com sessão reconhecida.
- Criar um serviço da pessoa.
- Editar um serviço da pessoa.
- Criar um item do catálogo da plataforma.
- Editar um item do catálogo da plataforma.
- Apagar um serviço da pessoa.
- Apagar um item do catálogo da plataforma.

## Quem pode

A porta não exige sessão em todas as ações.

Listar e apagar olham se há pessoa reconhecida na sessão e, se não houver, recusam dentro da ação. Criar e editar o serviço da pessoa, e criar e editar um item do catálogo da plataforma, não fazem essa conferência. Por isso esta porta não mostra que o catálogo fique restrito à equipe da plataforma.

Essa leitura da pessoa depende da sessão ter sido lida na entrada, e isso está em aberto em [[01-o-que-e-este-backend]].

Estas ações não separam cliente de profissional.

## Em que pé está

**No ar**, com ressalva.

O serviço de serviços está ligado quando este backend sobe, e a configuração tem endereço de serviços. As ações acima já podem ser pedidas.

A ressalva é a trava de sessão, que não está uniforme. Listar e apagar olham se há pessoa reconhecida na sessão e, se não houver, recusam dentro da ação. Criar e editar, nas duas famílias, não fazem essa conferência nesta porta. Essa leitura da pessoa depende da sessão ter sido lida na entrada, e isso está em aberto em [[01-o-que-e-este-backend]].

## O que esta nota não cobre

- Preço, duração, categoria, comissão ou qualquer valor de um serviço.
- Os campos que a pessoa preenche ao criar ou editar um serviço.
- O que o serviço de serviços responde depois de receber o pedido.
- Fotos, endereços, agenda, busca, relatos e pagamento.
- Qual papel (cliente, profissional ou equipe) deveria usar cada ação.

## Ligações

A sessão desta porta conversa com [[03-entrar-sair-e-senha]]. Cliente e profissional estão em [[02-cliente-e-profissional]]. O que a pessoa pode ver está em [[13-o-que-a-pessoa-pode-ver]]. Fotos são outra porta: [[10-fotos]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

- Não dá para afirmar preço, duração ou categoria. Isso não está escrito neste repositório.
- Não dá para afirmar comissão.
- A forma do serviço (quais campos existem) não está neste repositório. O projeto cita um pacote de serviços da pessoa; esse pacote não vira, nesta nota, uma lista de campos.
- Não dá para afirmar se, do outro lado, criar e editar ainda recusam um pedido sem sessão. Esta porta não confere a identidade nessas ações. O que o serviço ligado faz em seguida não está neste repositório.
- Não dá para afirmar se o item de catálogo aparece para a pessoa no aplicativo, nem quem da empresa deveria cuidá-lo.
