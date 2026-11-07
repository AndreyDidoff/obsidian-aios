---
tipo: cruzamento
tema: Portas sem tela e pedidos sem porta
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza os dois apps com o backend de apoio. Descreve onde a tela lê ou grava um dado, por que a pessoa precisa dele, e se essa porta existe no backend. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — o que ninguém pede

O backend de apoio publica mais do que os apps usam. Os apps também pedem dois caminhos que este retrato do backend não publica. Esta nota lista os dois lados, para a ingestão não tratar porta no ar como tela pronta.

Nenhuma destas portas separa cliente de profissional, salvo o cadastro de profissional, que o app do artista não usa. Ver [[02-cliente-e-profissional]].

## Porta no ar, sem pedido dos apps

Os dois apps foram conferidos. Não há pedido a estas portas. O pé é o da nota do backend.

| Porta | Pé no backend | Por que existiria para a pessoa | O que a tela faz no lugar |
|-------|---------------|----------------------------------|---------------------------|
| Abrir conta de profissional, em [[04-cadastro]] | No ar | Criar a conta de quem atende, já amarrada à empresa e ao aplicativo deste backend | O app do artista abre conta de cliente. O vínculo de empresa e aplicativo não entra. |
| Ver se o e-mail já existe, em [[04-cadastro]] | No ar | Avisar, antes de concluir, que o e-mail já tem conta | A tela não pergunta. A frase de CPF já cadastrado existe nos textos e a tela não a usa sozinha. |
| Conferir CPF e CNPJ, em [[04-cadastro]] | No ar | Saber se o documento já está na base | Os apps guardam o pedido e nenhuma tela o dispara. O formato também diverge: o app mandaria o CPF na pergunta, o backend espera no cabeçalho. |
| Recusar a troca de senha, em [[03-entrar-sair-e-senha]] | No ar | A pessoa recebeu o pedido de troca e não foi ela | Nenhuma tela oferece recusar. |
| Serviços da pessoa e catálogo da plataforma, em [[05-servicos]] | No ar, com ressalva na sessão | O que a pessoa oferece, e o catálogo da plataforma | Não há tela de serviço. Os nomes de unha e botox do Início são exemplo. |
| Bloqueio, em [[07-bloqueio]] | No ar | Ver, registrar e desfazer um bloqueio da pessoa logada | Não há tela de bloquear. O efeito no restante do app também não está na porta. |
| Endereços, em [[08-enderecos]] | No ar | Listar, criar, editar e apagar os locais da pessoa logada | Gerenciar no perfil é "em breve". O endereço real viaja só dentro do cadastro. |
| Telefones, em [[09-telefones]] | No ar | Listar, guardar, editar e apagar telefones da pessoa logada | O cadastro dos dois apps não pede telefone. Não há tela de telefone. |
| Fotos, em [[10-fotos]] | No ar para buscar uma, guardar e apagar. Sem lista e sem edição | Uma imagem pelo identificador | A foto do cadastro vai dentro do pedido de abrir conta. Não há galeria pedida a esta porta. O código desta porta não diz se a foto é de perfil, de portfólio ou de documento. |
| Relatos, em [[11-relatos]] | No ar | Lista, gravação e fotos de um relato da pessoa logada | Não há tela. A porta não diz se o relato é denúncia, avaliação ou atendimento. |
| Documentos para validação, em [[12-documentos-para-validacao]] | No ar | Enviar e consultar um conjunto, limitado à pessoa logada | Não há tela. A porta não lista RG, CPF nem certificado. A conferência de CPF do cadastro é outra porta. |
| O que a pessoa pode ver, em [[13-o-que-a-pessoa-pode-ver]] | No ar | Permissões, grupos e, a partir dos grupos, quais áreas mostrar | As abas são fixas em cada app. Nenhum dos dois consulta esta porta para montar o menu. |

A ressalva de sessão vale para as portas marcadas como pessoa logada. O arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Ver [[01-o-que-e-este-backend]].

## Porta sem ligação, e tela que também não pede

[[06-planos-e-cupons]] oferece listar planos e validar um cupom, e o serviço de planos não está ligado. A aba [[Planos do artista]] só mostra "Tab Plans". Ela não pergunta a porta. O app do cliente não tem essa área.

## Preparado, sem ação para o app

Em [[14-preparado-e-ainda-nao-oferecido]]: auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem e o cliente de e-mail. Não há porta. O canal de e-mail está fora de uso. Por isso pedir a troca de senha não envia o e-mail por este backend.

O banco local sobe com o backend e não guarda o negócio. Bloqueio e senha que o app já pede seguem para os serviços ligados, não para esse banco.

## Pedido do app sem porta neste retrato

| Pedido | Por que o app faria | Onde dispararia | O que este retrato do backend publica |
|--------|---------------------|-----------------|----------------------------------------|
| Ler a pessoa logada, `login/user/logged` | Preencher nome, foto e nota no Início | [[Início]] e [[Início do artista]], ao abrir | Não publica. Entrar devolve a sessão. A leitura da pessoa é outro caminho. |
| Saber se a sessão vale, `login/user/valid` | Reabrir sem senha | Abertura dos dois apps | Publica outra forma: GET `Valid`, em [[03-entrar-sair-e-senha]]. |
| Invalidar todas as sessões, `auth/revoke-all-sessions` | Encerrar a conta em outros aparelhos | Nenhuma tela chama | Não publica. |

## Notas

- [[01-o-que-e-este-backend]]
- [[02-cliente-e-profissional]]
- [[03-entrar-sair-e-senha]]
- [[04-cadastro]]
- [[05-servicos]]
- [[06-planos-e-cupons]]
- [[07-bloqueio]]
- [[08-enderecos]]
- [[09-telefones]]
- [[10-fotos]]
- [[11-relatos]]
- [[12-documentos-para-validacao]]
- [[13-o-que-a-pessoa-pode-ver]]
- [[14-preparado-e-ainda-nao-oferecido]]
- [[Planos do artista]]
- [[Início]]
- [[Início do artista]]
- [[Cruzamento - BFF conta]]
- [[Cruzamento - BFF o que a tela lê]]
