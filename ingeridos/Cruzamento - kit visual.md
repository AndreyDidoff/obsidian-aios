---
tipo: cruzamento
tema: Kit visual nos apps
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza o app do cliente, o app do artista, o kit visual e o fluxo compartilhado de entrar na conta. Descreve o que já está construído, em que pé está e onde a mesma experiência aparece mais de uma vez. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — kit visual

O kit visual é a cara compartilhada das telas: cores, claro e escuro, letra, ícones, botões, campos, escolha, datas e a espera. Não é uma tela. Não é o app de quem procura o serviço, nem o app de quem atende.

O app do cliente instala as doze peças, nas versões da tabela. A identidade é a base das telas que usam o kit. O fluxo compartilhado de entrar na conta, na versão 0.1.0, usa um pedaço: tema, ícones, texto, botão em degradê, botão de link, botão de fechar e campo livre. Não usa data, lista nem máscara. A espera também não entra nesse uso. Medidas e cores não são declaradas por esse fluxo; a cor entra pelo tema. Esse fluxo não está instalado no app do cliente nem no app do artista. O app do artista não instala o kit. Campos, botões e textos dele são desenhados no próprio app.

A coluna do cliente lista usos conferidos nesta extração. Não é o inventário de cada tela.

| Peça | Nome npm | Versão | Pé da peça | No app do cliente | No fluxo compartilhado de entrar | No app do artista |
| --- | --- | --- | --- | --- | --- | --- |
| Medidas e cores | `@wecareu/tokens` | 0.2.8 | Parcial. Tokens 0.2.8 e tema 0.3.4 pintam a tela; não há teste automático nem demonstração da paleta. | Base das telas que usam o kit | Não declara. A cor entra pelo tema | Não instala |
| Tema | `@wecareu/theme` | 0.3.4 | Parcial. Tokens 0.2.8 e tema 0.3.4 pintam a tela; não há teste automático nem demonstração da paleta. | Base das telas que usam o kit | Usa | Não instala |
| Ícones | `@wecareu/icons` | 1.3.3 | Pronto nos desenhos; bandeira e animações parciais | Menu do perfil, etiqueta da pessoa no Início, critérios da senha, termos, privacidade, notificações e sobre o app | Usa | Não instala |
| Texto (TextWcu) | `@wecareu/text-wcu` | 0.2.4 | Parcial. TextWcu 0.2.4 tem demonstração e teste; o teste não confere cor, tamanho nem peso. | Etiqueta da pessoa no Início e troca de senha de quem já entrou | Usa | Não instala |
| Botão em degradê | `@wecareu/button-gradient` | 0.3.3 | Parcial. Os três botões estão usáveis e cada um tem teste. A demonstração do degradê ainda usa o texto e os exemplos do link, inclusive uma história chamada de sublinhado que não sublinha. | Abertura de quem não entrou, Início e troca de senha | Usa | Não instala |
| Botão de link | `@wecareu/button-link` | 0.3.4 | Parcial, junto da área dos três botões. Este botão tem demonstração e teste. O buraco citado na nota de ações está na demonstração do degradê. | Termos, privacidade, notificações, troca de senha, sobre o app e abertura de quem não entrou | Usa | Não instala |
| Botão de fechar | `@wecareu/button-close` | 0.2.4 | Parcial, junto da área dos três botões. Este botão tem demonstração e teste. O buraco citado na nota de ações está na demonstração do degradê. | Cabeçalho e as telas de entrar e de criar conta | Usa | Não instala |
| Campo livre | `@wecareu/input-text` | 0.2.7 | Pronto. Campo livre 0.2.7 e campo com máscara 0.2.4, com demonstração e teste. | Troca de senha de quem já entrou | Usa | Não instala |
| Campo com máscara | `@wecareu/input-masked` | 0.2.4 | Pronto. Campo livre 0.2.7 e campo com máscara 0.2.4, com demonstração e teste. | Documento e CEP no cadastro, e o CEP do endereço | Não usa | Não instala |
| Lista | `@wecareu/select` | 0.2.7 | Parcial. Escolha 0.2.7 usável, com demonstração e teste. Busca vazia sem frase. Textos prontos em inglês. | Sexo, tipo de endereço e país no cadastro | Não usa | Não instala |
| Data | `@wecareu/date-picker` | 0.2.6 | Pronto. Campo e calendário usáveis, com demonstração. O teste automático não abre o calendário. | Data de nascimento no cadastro | Não usa | Não instala |
| Espera | `@wecareu/loading` | 0.4.4 | Pronto | Lista de artistas e troca de senha | Não usa | Não instala |

Na tabela de áreas do [[Panorama do design system]], a [[Escolha em lista]] está como Pronto. A nota da peça diz Parcial. Neste cruzamento vale o pé da peça: Parcial.

O mesmo panorama marca os ícones como Parcial. A nota [[Vocabulário visual]] diz que os desenhos estão prontos, e que a bandeira e as animações ficam parciais. Neste cruzamento vale essa nota.

## Cadastro

Em [[Criar conta]], a data de nascimento usa a data. Sexo, tipo de endereço e país usam a lista. Documento e CEP usam o campo com máscara. O CEP do endereço, em [[Endereços]], também usa o campo com máscara.

## Entrar e fechar

O botão de fechar aparece no cabeçalho e nas telas de entrar e de criar conta, em [[Entrar, senha e biometria]] e [[Criar conta]]. Na abertura de quem não entrou, aparecem o botão em degradê e o botão de link.

## Início

Em [[Início]], a etiqueta da pessoa usa um ícone e o texto TextWcu. O botão em degradê também aparece no Início.

## Perfil e senha

Em [[Meu perfil]], o menu do perfil usa ícones. Termos, privacidade, notificações e sobre o app usam ícones e o botão de link. Os critérios da senha usam ícones. A troca de senha de quem já entrou usa o texto TextWcu, o botão em degradê, o botão de link e o campo livre.

## Lista e espera

A espera aparece na lista de artistas, em [[Encontrar profissionais]], e na troca de senha de quem já entrou, em [[Meu perfil]]. A espera da lista de artistas não é a peça de escolha. A escolha em lista fica no cadastro.

## O que o kit ainda não é

O app do artista desenha a própria cara. O catálogo no navegador e o app de demonstração não são o app da pessoa. O rito de olhar as peças está em [[Como o time revisa a interface]]. O mapa do kit está em [[Panorama do design system]].

## Notas

- [[Panorama do design system]]
- [[Identidade visual]]
- [[Vocabulário visual]]
- [[Textos da interface]]
- [[Ações]]
- [[Campos de formulário]]
- [[Escolha em lista]]
- [[Datas]]
- [[Espera e carregamento]]
- [[Como o time revisa a interface]]
- [[library-components-o-que-entrega]]
