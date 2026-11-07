---
tipo: fonte
arquivo: "ingeridos/Cruzamento - BFF o que ninguém pede.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 que cruza ui_client, ui_worker e service_api; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cruzamento — o que ninguém pede"]
---

# Cruzamento — o que ninguém pede

A porta é [[cruzamento-bff-como-ler]].

O backend de apoio publica mais do que os apps usam. Os apps também pedem dois caminhos que este retrato do backend não publica, e um terceiro que nenhuma tela chama. Porta no ar não é tela pronta.

Nenhuma destas portas separa cliente de profissional, salvo o cadastro de profissional, que o app do artista não usa. Ver [[bff-cliente-e-profissional]].

A ressalva de sessão vale para as portas marcadas como pessoa logada. O arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Ver [[bff-o-que-e-este-backend]] e [[contradicoes-e-lacunas]].

## Porta no ar, sem pedido dos apps

Os dois apps foram conferidos. Não há pedido a estas portas. O pé é o da nota do backend.

- **Abrir conta de profissional**, em [[bff-cadastro]]. No ar. Serviria para criar a conta de quem atende, já amarrada à empresa e ao aplicativo deste backend. O app do artista abre conta de cliente. O vínculo de empresa e aplicativo não entra.
- **Ver se o e-mail já existe**, em [[bff-cadastro]]. No ar. A tela não pergunta. A frase de CPF já cadastrado existe nos textos e a tela não a usa sozinha.
- **Conferir CPF e CNPJ**, em [[bff-cadastro]]. No ar. Os apps guardam o pedido e nenhuma tela o dispara. O formato também diverge: o app mandaria o CPF na pergunta, o backend espera no cabeçalho.
- **Recusar a troca de senha**, em [[bff-entrar-sair-e-senha]]. No ar. Nenhuma tela oferece recusar.
- **Serviços da pessoa e catálogo da plataforma**, em [[bff-servicos]]. No ar, com ressalva na sessão. Não há tela de serviço. Os nomes de unha e botox do Início são exemplo.
- **Bloqueio**, em [[bff-bloqueio]]. No ar. Não há tela de bloquear. O efeito no restante do app também não está na porta.
- **Endereços**, em [[bff-enderecos]]. No ar. Gerenciar no perfil é "em breve". O endereço real viaja só dentro do cadastro.
- **Telefones**, em [[bff-telefones]]. No ar. O cadastro dos dois apps não pede telefone. Não há tela de telefone.
- **Fotos**, em [[bff-fotos]]. No ar para buscar uma, guardar e apagar. Sem lista e sem edição. A foto do cadastro vai dentro do pedido de abrir conta. Não há galeria pedida a esta porta. O código desta porta não diz se a foto é de perfil, de portfólio ou de documento.
- **Relatos**, em [[bff-relatos]]. No ar. Não há tela. A porta não diz se o relato é denúncia, avaliação ou atendimento.
- **Documentos para validação**, em [[bff-documentos-para-validacao]]. No ar. Não há tela. A porta não lista RG, CPF nem certificado. A conferência de CPF do cadastro é outra porta.
- **O que a pessoa pode ver**, em [[bff-o-que-a-pessoa-pode-ver]]. No ar. As abas são fixas em cada app. Nenhum dos dois consulta esta porta para montar o menu.

## Porta sem ligação, e tela que também não pede

[[bff-planos-e-cupons]] oferece listar planos e validar um cupom, e o serviço de planos não está ligado. A aba [[planos-do-artista]] só mostra "Tab Plans". Ela não pergunta a porta. O app do cliente não tem essa área.

## Preparado, sem ação para o app

Em [[bff-preparado-e-ainda-nao-oferecido]]: auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem e o cliente de e-mail. Não há porta. O canal de e-mail está fora de uso. Por isso pedir a troca de senha não envia o e-mail por este backend.

O banco local sobe com o backend e não guarda o negócio. Bloqueio e senha que o app já pede seguem para os serviços ligados, não para esse banco.

## Pedido do app sem porta neste retrato

- **Ler a pessoa logada**, `login/user/logged`. Preencheria nome, foto e nota no Início, em [[inicio]] e [[inicio-do-artista]], ao abrir. Este retrato não publica. Entrar devolve a sessão. A leitura da pessoa é outro caminho.
- **Saber se a sessão vale**, `login/user/valid`. Reabriria sem senha, na abertura dos dois apps. O backend publica outra forma: GET `Valid`, em [[bff-entrar-sair-e-senha]]. O detalhe do app está em [[cruzamento-bff-conta]].
- **Invalidar todas as sessões**, `auth/revoke-all-sessions`. Encerraria a conta em outros aparelhos. Nenhuma tela chama. Este retrato não publica.

Ver [[beautiful-api]], [[cruzamento-bff-o-que-a-tela-le]].
