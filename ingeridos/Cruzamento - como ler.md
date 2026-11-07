---
tipo: cruzamento
tema: Como ler os cruzamentos
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza o app do cliente, o app do artista, o kit visual e o fluxo compartilhado de entrar na conta. Descreve o que já está construído, em que pé está e onde a mesma experiência aparece mais de uma vez. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — como ler

Esta nota é a porta das outras seis. Cada extrato sozinho descreve um repositório. Aqui está o que acontece quando os quatro são lidos juntos.

Há quatro peças. Duas são o app que a pessoa abre. Duas são casas compartilhadas, para a mesma cara ou o mesmo percurso não nascer duas vezes.

| Peça | O que é | Quem usa hoje |
|------|---------|---------------|
| App do cliente | WeCareU. Quem procura o serviço. Mapa em [[Mapa do app do cliente]]. | Instala as doze peças do kit visual. Não instala o fluxo compartilhado de entrar. |
| App do artista | WeCareU - Artistas. Quem atende. Mapa em [[Mapa do app do artista]]. | Não instala o kit visual. Não instala o fluxo compartilhado de entrar. Campos, botões e textos nascem no próprio app. |
| Kit visual | Cara das telas: cor, texto, ícone, botão, campo, lista, data e espera. Não é uma tela. Mapa em [[Panorama do design system]]. | O cliente instala as doze. O fluxo compartilhado de entrar usa um pedaço (tema, ícones, texto, botões, campo livre e fechar). O artista não instala. |
| Fluxo compartilhado de entrar | Entrar na conta, recuperar a senha e biometria, versão 0.1.0, nome `@wecareu/auth-flow`. O que entrega está em [[library-components-o-que-entrega]]. | Existe e não está instalado em nenhum dos dois apps. Cada app tem o próprio percurso. |

O fluxo compartilhado não está no app. O kit visual está no cliente e, em parte, nesse fluxo. O artista ainda não usa o kit.

## Onde o artista está atrás, e onde não está

Atrás, no mesmo percurso em que o cliente já andou:

- A cara das telas. O cliente veste o kit. O artista desenha a própria.
- O fim do cadastro. O cliente entra no Início. O artista cria a conta e não abre as abas nessa hora.

No mesmo ponto, não é atraso:

- Editar dados e gerenciar endereços. Os dois abrem "em breve".
- O cartão do início. Os dois mostram o mesmo exemplo, Karen Watanabe, e **Vamos agendar?** não faz nada.
- Agenda e a conversa do agendamento. Casca nos dois.

Não é atraso, porque o cliente nem tem a área:

- Pedidos e Planos. Só existem no artista, e ainda são casca.

Criar conta não é a mesma tela. O cliente tem três etapas. O artista tem cinco, com uma etapa só de foto. O detalhe está em [[Cruzamento - criar conta]].

## As notas

| Nota | O que cruza |
|------|-------------|
| [[Cruzamento - kit visual]] | Peça a peça: versão, pé, se o cliente usa, se o fluxo de entrar usa, se o artista instala. |
| [[Cruzamento - entrar senha e biometria]] | Três percursos lado a lado. Cliente e artista estão mais perto um do outro do que da peça compartilhada, e essa peça não está ligada a nenhum dos dois. |
| [[Cruzamento - criar conta]] | Três etapas contra cinco. Nenhuma peça compartilhada de cadastro em uso. |
| [[Cruzamento - dentro da conta]] | Início, menu do perfil, senha de quem já entrou, endereços, ajuda, termos. Onde os dois estão no mesmo "em breve". |
| [[Cruzamento - o que só um app tem]] | Visita sem conta e lista de artistas. Abertura em slides, Pedidos e Planos. Agenda e conversa, casca nos dois. |
| [[Cruzamento - o que deveria ser uma peça só]] | Direção de manutenção deste retrato, não decisão da empresa. Cara da tela no kit visual. Percurso igual numa peça de fluxo. Cadastro só depois de alinhar as jornadas. |

## Como ler o pé

O pé de cada linha vem da nota de origem. Quando o panorama e a nota da peça divergem, o cruzamento fica com a nota da peça e registra a divergência. Isso acontece na escolha em lista e nos ícones. Ver [[Cruzamento - kit visual]].
