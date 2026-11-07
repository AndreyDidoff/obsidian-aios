---
tipo: extração
tema: Panorama do design system
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/tokens", "@wecareu/theme", "@wecareu/icons", "@wecareu/text-wcu", "@wecareu/button-gradient", "@wecareu/button-link", "@wecareu/button-close", "@wecareu/input-text", "@wecareu/input-masked", "@wecareu/select", "@wecareu/date-picker", "@wecareu/loading"]
pé: Parcial — várias peças prontas para a tela; a identidade não tem página nem teste, e o celular não é vitrine
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Panorama do design system

Isto é o kit visual compartilhado das telas do app. O nome no repositório é **WeCareU Design System**. Não é uma tela. Não é o app de quem procura o serviço, nem o app de quem atende.

Cada peça sai publicada com um nome npm, no escopo `@wecareu`. Esse nome é o cruzamento com as outras notas. A tabela de áreas e a de peças trazem o nome inteiro.

O que a pessoa do produto ganha: a mesma cara nas telas, claro e escuro, textos, ícones, botões, campos, escolha em lista, datas e a espera. A fonte prevista é a Livvic, em três pesos (regular, semibold e bold). A cor de ação é o roxo. Há degradê para o botão de destaque, medida de respiro e arredondamento.

## Como ler o pé de cada área

| Pé | Significado |
|----|-------------|
| Pronto | A peça existe, dá para colocar numa tela, tem demonstração e teste automático. |
| Parcial | Existe e dá para usar, mas demonstração, teste ou texto interno está incompleto, ou o comportamento cobre só parte do que o nome promete. |
| Previsto | Citado e não construído neste repositório. |

## As áreas

| Área | Nome npm | O que cobre | Pé | Nota |
|------|----------|-------------|----|------|
| [[Identidade visual]] | `@wecareu/tokens`, `@wecareu/theme` | Cores, claro e escuro, fonte, respiro, cantos e degradê | Parcial | A base existe e as outras peças usam. Não há página só dela, nem teste automático |
| [[Vocabulário visual]] | `@wecareu/icons` | 69 desenhos (seta, pessoa, casa, pix, cartão, dinheiro, calendário e outros) e três animações curtas | Parcial | Dá para colocar o desenho. A página mostra um por vez, e o teste não percorre a lista |
| [[Textos da interface]] | `@wecareu/text-wcu` | Título, corpo, rótulo e legenda, com cor, tamanho e peso | Parcial | Há página e teste. A escala maior (display e vários tamanhos de título) fica só na identidade |
| [[Ações]] | `@wecareu/button-gradient`, `@wecareu/button-link`, `@wecareu/button-close` | Botão em degradê, botão de link e botão de fechar | Parcial | Os três existem, com página e teste. A página do degradê ainda fala como se fosse o link |
| [[Campos de formulário]] | `@wecareu/input-text`, `@wecareu/input-masked` | Campo livre e campo com máscara | Pronto | E-mail, senha, número, telefone, endereço web, ícone e erro. Máscaras de CPF, CNPJ, CEP, telefone, cartão e data |
| [[Escolha em lista]] | `@wecareu/select` | Uma ou várias opções, com busca | Pronto | Também bandeira, ícone, limpar, erro, desligado e somente leitura. Os exemplos da página estão em inglês |
| [[Datas]] | `@wecareu/date-picker` | Um dia, um intervalo ou vários dias | Pronto | Pode incluir a hora, um limite, dias bloqueados e o campo desligado. O calendário está em português |
| [[Espera e carregamento]] | `@wecareu/loading` | Um véu por cima da tela com a animação de pontos | Pronto | A página tem um botão que mostra o véu por alguns segundos. Há teste |
| [[Como o time revisa a interface]] | `playground`, `storybook-web` | Catálogo no navegador e app de demonstração no celular | Parcial | O catálogo mostra as peças que têm página. O app no celular não é uma vitrine. Esses dois nomes não usam o escopo `@wecareu` |

Na página dos desenhos, o nome da digital não bate com o desenho: a lista oferece um nome e o desenho responde por outro. As três animações curtas são pontos, local e aviso. A espera usa só os pontos. Elas não têm página própria.

No celular, a bandeira de um país é o emoji. No navegador, a imagem da bandeira vem de fora.

O botão de fechar é redondo e tem três tamanhos. O botão de link pode levar ícone, sublinhado e ficar desligado. O botão em degradê é o de destaque. Na página dele, um exemplo se chama sublinhado, e o botão não muda.

A máscara de cartão só formata o número digitado.

## As peças

Versão marcada é a que está escrita em cada peça hoje.

| Peça | Nome npm | Versão marcada | Página de demonstração | Teste automático |
|------|----------|----------------|------------------------|------------------|
| Medidas e cores | `@wecareu/tokens` | 0.2.8 | Não | Não |
| Tema (claro e escuro) | `@wecareu/theme` | 0.3.4 | Não | Não |
| Ícones | `@wecareu/icons` | 1.3.3 | Sim | Sim |
| Texto | `@wecareu/text-wcu` | 0.2.4 | Sim | Sim |
| Botão em degradê | `@wecareu/button-gradient` | 0.3.3 | Sim | Sim |
| Botão de link | `@wecareu/button-link` | 0.3.4 | Sim | Sim |
| Botão de fechar | `@wecareu/button-close` | 0.2.4 | Sim | Sim |
| Campo de texto | `@wecareu/input-text` | 0.2.7 | Sim | Sim |
| Campo com máscara | `@wecareu/input-masked` | 0.2.4 | Sim | Sim |
| Lista | `@wecareu/select` | 0.2.7 | Sim | Sim |
| Data | `@wecareu/date-picker` | 0.2.6 | Sim | Sim |
| Espera | `@wecareu/loading` | 0.4.4 | Sim | Sim |

## O texto de apresentação da raiz ficou para trás

O texto de apresentação da raiz ainda lista quatro peças: medidas e cores, tema, ícones e botão de link. O desenho de pastas no mesmo texto é ainda mais curto: medidas e cores, tema e botão de link. Não cita os ícones.

O código já tem, além desses, o texto, o botão em degradê, o botão de fechar, o campo de texto, o campo com máscara, a lista, a data e a espera.

O mesmo texto fala em mais de 70 ícones. A lista de desenhos tem 69.

## O que esta extração não cobre

- Telas do app de quem procura o serviço
- App de quem atende
- Regras de negócio, preços e pagamento de verdade
- Ícones de pix, cartão e dinheiro existem como desenho. Isso não significa que o app cobra
- A máscara de cartão não cobra
- Como publicar o kit, nem o passo a passo de quem desenvolve

## Ordem sugerida para as próximas notas

1. [[Identidade visual]]
2. [[Vocabulário visual]]
3. [[Textos da interface]]
4. [[Ações]]
5. [[Campos de formulário]]
6. [[Escolha em lista]]
7. [[Datas]]
8. [[Espera e carregamento]]
9. [[Como o time revisa a interface]]
