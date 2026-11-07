> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 10 · Voz e tons

Tags: #lyraui #voz #tom #persona #redacao #ux-writing

---

## 1. Status

- **LyraUI (alvo, em discovery, não implementada no código):** o guia de voz e tons é a referência de comunicação da LyraUI. Ele já orienta quem escreve e projeta, mas os textos dos apps atuais podem não segui-lo por completo.
- **WeCareU (app em produção):** a LyraUI é o design system da WeCareU e fala em nome dela. A voz da LyraUI deve estar alinhada aos valores da empresa. Ver [[02-contexto-wecareu]].
- Contexto em [[01-visao-geral-lyraui]]. Regras de pontuação e formatação em [[11-escrita-e-ortografia]] e princípios em [[12-principios-de-design]].

---

## 2. Para que serve e quem usa

- Estabelece as diretrizes de comunicação da LyraUI: voz e tons.
- Toda comunicação entre as pessoas que constroem a LyraUI e toda comunicação nos aplicativos devem estar alinhadas a ele.
- Serve a todas as pessoas que escrevem e projetam. Todo o time WeCareU tem acesso: tecnologia, produto, marketing e atendimento.
- Objetivo: redação **acessível, significativa, concisa, conversacional e clara**, para qualquer pessoa que use os apps.
- A comunicação deve estar alinhada aos pilares do ecossistema: **o profissional como artista, estética, cuidado (care), eficiência e simplicidade**.

---

## 3. Voz x tom

| | Voz | Tom |
|---|---|---|
| O que é | Escolhas consistentes e reconhecíveis de palavras ao longo de toda a experiência. A personalidade da LyraUI | A variação da voz de ponta a ponta, conforme o contexto e a jornada da pessoa |
| Muda? | **Nunca** | **Sempre se adapta** ao contexto e à tela |
| Analogia do guia | A voz da sua mãe é reconhecível em áudio ou ligação | O tom dela muda se está brava, feliz ou triste |

O tom considera empolgação, pressa no salão, momento de relaxamento ou frustração com um erro.

---

## 4. Quem é a LyraUI (persona)

A LyraUI se apresenta em primeira pessoa:

- É o Design System da WeCareU.
- É inteligente, técnica e muito estética.
- É acolhedora, como o ambiente de "Cuidado" (Care) em que vive.
- É contemporânea: constrói funcionalidades do nosso tempo para diferentes dispositivos.
- É autoral e direta: nasceu para quebrar paradigmas e valorizar o trabalho manual como arte.
- É didática, eficiente e boa ouvinte, para que as pessoas usuárias se sintam confortáveis no ecossistema.

**Propósito:** criar conexões e padronizar, unindo clientes, profissionais, empresas e prestadores de serviço em um ambiente coeso.

---

## 5. As quatro características da voz

| Característica | O que significa |
|---|---|
| **Focada em estética** | Valoriza o polimento visual e o uso dos termos corretos do mercado, respeitando a arte de cada nicho |
| **Acolhedora** | Demonstra "Care" em cada interação, prevendo o erro humano e ajudando a consertá-lo |
| **Vai direto ao ponto** | Comunicação direta e amiga, respeitando o tempo de quem trabalha ou agenda |
| **Dignifica o profissional** | Trata cada prestador de serviço como um talento único, em um ambiente onde ele pode brilhar |

---

## 6. Os quatro tons

| Tom | Quando usar | Exemplos de contexto |
|---|---|---|
| **Celebrativo** | Momentos de sucesso | Novo agendamento, meta alcançada no ranking |
| **Instrutivo** | Auxílio e orientação didática | Primeiros acessos, cadastros, preenchimento de portfólio |
| **Operacional** | Tarefas do dia a dia, de forma simples, direta e puramente funcional | Menus, configurações, ferramentas de gestão |
| **Tranquilizador** | Estados de erro, com empatia e transparência | Assumir a responsabilidade do sistema e oferecer saídas claras, **sem culpar a pessoa usuária** |

---

## 7. Como falamos

### Pessoa gramatical

- Sempre em **1ª pessoa do plural**, porque somos o ambiente acolhedor.
- Nunca se referir à própria marca em 3ª pessoa.

| Falo assim | Não falo assim |
|---|---|
| Preparamos a sua agenda de hoje | A WeCareU preparou a sua agenda |
| Encontramos 5 Artistas perto de você | |

### Linguagem simples

- Falamos com pessoas de diferentes habilidades de leitura e letramento digital.
- Por isso adotamos práticas de **linguagem simples**, para facilitar o entendimento e agilizar o uso.

### Termo "Artista"

- O profissional de beleza cadastrado é chamado de **Artista**, com inicial maiúscula nos exemplos do guia. Ver terminologia em [[02-contexto-wecareu]].

---

## 8. Com quem falamos

Público diverso: clientes, profissionais autônomos, locais de beleza e bem-estar, e a equipe interna.

Comunidades atendidas:
- **Beleza:** cabelos, unhas, pelos, maquiagem, estética.
- **Bem-estar:** massagem, massoterapia, spa.

Cada palavra e texto deve considerar as pluralidades, os ambientes de trabalho e as necessidades dessas pessoas. A linguagem deve informar de modo objetivo e coeso as funções, comandos e particularidades do app.

### Perfis, plataformas e tom provável

| Perfil | Acessa via | Quem é |
|---|---|---|
| Clientes (WeCareU) | `ui-client` (app) e `web-client` (web) | Buscam serviços com confiança, comodidade e estética |
| Artistas (WeCareU - Artistas) | `ui-worker` (app) e `web-worker` (web) | Gerenciam negócios e portfólios, tratados como verdadeiros talentos |
| Empresas (WeCareU - Empresas) | `ui-business` (app) e `web-business` (web) | Administradores e donos de locais de beleza, que precisam de dados analíticos e gestão rápida |
| Equipe interna WeCareU | `web-admin` e `web-wiki` | Controle de acessos, moderações, aprovações, guia de estilo e regras internas |

> **Atenção ao escopo.** Hoje o app em produção cobre CLIENT e WORKER. Os demais nomes são a visão-alvo do guia. Salões e Empresas são funcionalidade futura. Ver [[03-estado-atual-do-produto]].

---

## 9. Aplicação prática por situação

Mapeamento de apoio, derivado das definições acima. Não é uma tabela oficial do guia.

| Situação na jornada | Tom sugerido |
|---|---|
| Agendamento confirmado, meta alcançada | Celebrativo |
| Onboarding, cadastro, portfólio | Instrutivo |
| Menu, configuração, ferramentas de gestão | Operacional |
| Falha, erro de validação, indisponibilidade | Tranquilizador |

---

## 10. Pontos em aberto e divergências

- **Pontuação nos exemplos.** O guia mostra os exemplos de fala com ponto final. Dentro das telas, a regra é **não usar ponto final** em textos curtos. Aplicar a regra de [[11-escrita-e-ortografia]] na interface.
- **Documento da persona.** O documento de fundamentos cita um arquivo próprio da persona e dos princípios (`lyraui-persona-e-principios.md`). O conteúdo deste arquivo vem do guia de voz e tons e do documento de princípios. Se esse arquivo existir, comparar.
- **Escopo dos perfis.** Empresas e salões ainda não existem no produto.
- **Exemplos de microcopy.** O guia traz poucos exemplos. Faltam textos de erro, vazio e confirmação por tom.

---

## Links

Anterior: [[09-fundamentos-visuais]] · Próximos: [[11-escrita-e-ortografia]] · [[12-principios-de-design]]
