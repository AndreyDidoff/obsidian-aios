---
tipo: fonte
arquivo: "ingeridos/Cruzamento - kit visual.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 que cruza ui_client, ui_worker, library-design-system e library-components; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cruzamento — kit visual"]
---

# Cruzamento — kit visual

A porta é [[cruzamento-como-ler]].

O kit visual é a cara compartilhada das telas: cores, claro e escuro, letra, ícones, botões, campos, escolha, datas e a espera. Não é uma tela. Não é o app de quem procura o serviço, nem o app de quem atende.

O app do cliente instala as doze peças, nas versões desta nota. A identidade é a base das telas que usam o kit. O fluxo compartilhado de entrar na conta, na versão 0.1.0, usa um pedaço: tema, ícones, texto, botão em degradê, botão de link, botão de fechar e campo livre. Não usa data, lista nem máscara. A espera também não entra nesse uso. Medidas e cores não são declaradas por esse fluxo; a cor entra pelo tema. Esse fluxo não está instalado no app do cliente nem no app do artista. O app do artista não instala o kit. Campos, botões e textos dele são desenhados no próprio app.

A coluna do cliente, na nota bruta, lista usos conferidos nesta extração. Não é o inventário de cada tela.

## Quem usa cada peça

| Peça | Versão | Pé neste cruzamento | Cliente | Fluxo 0.1.0 | Artista |
|---|---|---|---|---|---|
| `@wecareu/tokens` | 0.2.8 | Parcial. Tokens e tema pintam a tela; não há teste nem demonstração da paleta | Base das telas que usam o kit | Não declara. A cor entra pelo tema | Não instala |
| `@wecareu/theme` | 0.3.4 | Parcial, o mesmo buraco da paleta | Base das telas que usam o kit | Usa | Não instala |
| `@wecareu/icons` | 1.3.3 | Pronto nos desenhos; bandeira e animações parciais | Menu do perfil, etiqueta da pessoa no Início, critérios da senha, termos, privacidade, notificações e sobre o app | Usa | Não instala |
| `@wecareu/text-wcu` | 0.2.4 | Parcial. Há demonstração e teste; o teste não confere cor, tamanho nem peso | Etiqueta da pessoa no Início e troca de senha de quem já entrou | Usa | Não instala |
| `@wecareu/button-gradient` | 0.3.3 | Parcial. Usável, com teste. A demonstração ainda usa o texto e os exemplos do link, inclusive uma história chamada de sublinhado que não sublinha | Abertura de quem não entrou, Início e troca de senha | Usa | Não instala |
| `@wecareu/button-link` | 0.3.4 | Parcial, junto da área dos três botões. O buraco citado na nota de ações está na demonstração do degradê | Termos, privacidade, notificações, troca de senha, sobre o app e abertura de quem não entrou | Usa | Não instala |
| `@wecareu/button-close` | 0.2.4 | Parcial, junto da área dos três botões. O buraco citado está na demonstração do degradê | Cabeçalho e as telas de entrar e de criar conta | Usa | Não instala |
| `@wecareu/input-text` | 0.2.7 | Pronto, com demonstração e teste | Troca de senha de quem já entrou | Usa | Não instala |
| `@wecareu/input-masked` | 0.2.4 | Pronto, com demonstração e teste | Documento e CEP no cadastro, e o CEP do endereço | Não usa | Não instala |
| `@wecareu/select` | 0.2.7 | Parcial. Usável, com demonstração e teste. Busca vazia sem frase. Textos prontos em inglês | Sexo, tipo de endereço e país no cadastro | Não usa | Não instala |
| `@wecareu/date-picker` | 0.2.6 | Pronto. Campo e calendário usáveis, com demonstração. O teste automático não abre o calendário | Data de nascimento no cadastro | Não usa | Não instala |
| `@wecareu/loading` | 0.4.4 | Pronto | Lista de artistas e troca de senha | Não usa | Não instala |

## Onde o panorama e a nota da peça divergem

Na tabela de áreas do [[panorama-do-design-system]], a [[escolha-em-lista]] está como Pronto. A nota da peça diz Parcial. Neste cruzamento vale o pé da peça: Parcial.

O mesmo panorama marca os ícones como Parcial. A nota [[vocabulario-visual]] diz que os desenhos estão prontos, e que a bandeira e as animações ficam parciais. Neste cruzamento vale essa nota.

## Onde o cliente usa

Em [[criar-conta]], a data de nascimento usa a data. Sexo, tipo de endereço e país usam a lista. Documento e CEP usam o campo com máscara. O CEP do endereço, em [[enderecos]], também usa o campo com máscara. A nota [[criar-conta]] chama o campo de gênero e diz que não há sexo separado. Este cruzamento diz sexo, e não lista as opções. Ver o item 14 de [[contradicoes-e-lacunas]].

O botão de fechar aparece no cabeçalho e nas telas de entrar e de criar conta ([[entrar-senha-e-biometria]], [[criar-conta]]). Na abertura de quem não entrou, aparecem o botão em degradê e o botão de link.

Em [[inicio]], a etiqueta da pessoa usa um ícone e o texto TextWcu. O botão em degradê também aparece no Início.

Em [[meu-perfil]], o menu usa ícones. Termos, privacidade, notificações e sobre o app usam ícones e o botão de link. Os critérios da senha usam ícones. A troca de senha de quem já entrou usa o texto, o botão em degradê, o botão de link e o campo livre.

A espera aparece na lista de artistas ([[encontrar-profissionais]]) e na troca de senha de quem já entrou. A espera da lista de artistas não é a peça de escolha. A escolha em lista fica no cadastro.

## O que o kit ainda não é

O app do artista desenha a própria cara. O catálogo no navegador e o app de demonstração não são o app da pessoa. O rito de olhar as peças está em [[como-o-time-revisa-a-interface]]. O mapa do kit está em [[panorama-do-design-system]].

Ver [[kit-visual]], [[identidade-visual]], [[textos-da-interface]], [[acoes]], [[campos-de-formulario]], [[datas]], [[espera-e-carregamento]], [[library-components-o-que-entrega]].
