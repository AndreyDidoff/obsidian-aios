---
tipo: fonte
arquivo: "ingeridos/05-servicos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Serviços"]
---

# Serviços

O que este backend publica para o serviço da pessoa e para o item do catálogo da plataforma. São duas famílias distintas. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Esta nota não cobre preço, duração, categoria, comissão nem os campos.

## O que está publicado

- **Listar** os serviços da pessoa que está com sessão reconhecida.
- **Criar** um serviço da pessoa.
- **Editar** um serviço da pessoa.
- **Criar** um item do catálogo da plataforma.
- **Editar** um item do catálogo da plataforma.
- **Apagar** um serviço da pessoa.
- **Apagar** um item do catálogo da plataforma.

## Quem pode

A porta não exige sessão em todas as ações.

Listar e apagar olham se há pessoa reconhecida na sessão e, se não houver, recusam dentro da ação. Criar e editar, nas duas famílias, não fazem essa conferência nesta porta. Por isso esta porta não mostra que o catálogo fique restrito à equipe da plataforma.

Essa leitura da pessoa depende da sessão ter sido lida na entrada. Isso está em aberto em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

Estas ações não separam cliente de profissional.

## Em que pé está

**No ar**, com ressalva.

O serviço de serviços está ligado quando este backend sobe, e a configuração tem endereço de serviços.

A ressalva é a trava de sessão, que não está uniforme. Listar e apagar recusam se não houver pessoa reconhecida. Criar e editar o serviço da pessoa, e criar e editar o item do catálogo, não fazem essa conferência nesta porta. A leitura da pessoa continua em aberto na entrada.

## O que esta nota não cobre

Preço, duração, categoria, comissão ou qualquer valor de um serviço. Os campos de criar ou editar. O que o serviço de serviços responde depois do pedido. Fotos, endereços, agenda, busca, relatos e pagamento. Fotos estão em [[bff-fotos]]. Relatos estão em [[bff-relatos]]. Qual papel (cliente, profissional ou equipe) deveria usar cada ação.

## Incertezas

Não dá para afirmar preço, duração, categoria nem comissão. Isso não está neste repositório.

A forma do serviço não está neste repositório. O projeto cita um pacote de serviços da pessoa; esse pacote não vira, nesta nota, uma lista de campos.

Não dá para afirmar se, do outro lado, criar e editar ainda recusam um pedido sem sessão. Esta porta não confere a identidade nessas ações. O que o serviço ligado faz em seguida não está neste repositório.

Não dá para afirmar se o item de catálogo aparece para a pessoa, nem quem da empresa deveria cuidá-lo.

Ver [[beautiful-api]].

O board pede cadastro de serviços ([[board-servicos]]). O épico 338, Sistema de cadastro de serviços, está New e sem descrição. A história 353, Cadastro de serviços do artista, está New e sem descrição. As tarefas 354 e 355 estão New e sem descrição. A tarefa 356, [BE] Endpoint de cadastro de Artista, está New. A descrição pede criação, edição, leitura e deleção dos dados adicionais do artista, como na página de descrição do perfil. New é o estado do work item. Esta porta já está no ar, com ressalva, como retrato de código. Isso não vem do estado do work item. O board não muda esse pé. Cluster e WeCareU.API, nas tarefas 354 e 355, são nomes do pedido. Não confirmam a arquitetura.
