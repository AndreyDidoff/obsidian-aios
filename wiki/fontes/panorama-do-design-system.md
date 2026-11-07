---
tipo: fonte
arquivo: "ingeridos/Panorama do design system.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Panorama do design system"]
---

# Panorama do design system

Porta desta leva. O kit se chama **WeCareU Design System** no repositório `library-design-system`. Não é tela nem app. Cada peça sai no escopo `@wecareu`.

Pé: **Pronto** existe, entra numa tela, tem demonstração e teste. **Parcial** é usável com buraco. **Previsto** foi citado e não está construído aqui.

## Áreas

| Área | Nome npm | Pé |
|---|---|---|
| [[identidade-visual]] | `@wecareu/tokens`, `@wecareu/theme` | Parcial |
| [[vocabulario-visual]] | `@wecareu/icons` | Parcial |
| [[textos-da-interface]] | `@wecareu/text-wcu` | Parcial |
| [[acoes]] | `@wecareu/button-gradient`, `@wecareu/button-link`, `@wecareu/button-close` | Parcial |
| [[campos-de-formulario]] | `@wecareu/input-text`, `@wecareu/input-masked` | Pronto |
| [[escolha-em-lista]] | `@wecareu/select` | Pronto |
| [[datas]] | `@wecareu/date-picker` | Pronto |
| [[espera-e-carregamento]] | `@wecareu/loading` | Pronto |
| [[como-o-time-revisa-a-interface]] | `playground`, `storybook-web` | Parcial |

Identidade não tem página nem teste. A página do degradê ainda fala como se fosse o link. Na de [[escolha-em-lista]], os exemplos estão em inglês; o panorama mesmo assim marca a área como Pronto, e a nota da peça se chama Parcial. `playground` e `storybook-web` não usam `@wecareu`. O app no celular não é vitrine.

Na página dos desenhos, o nome da digital não bate com o desenho: a lista oferece um nome e o desenho responde por outro. Há três animações (pontos, local, aviso). A espera usa só os pontos. No celular a bandeira é emoji; no navegador a imagem vem de fora. A máscara de cartão só formata o número.

## As doze peças

Versão marcada é a escrita em cada peça hoje.

| Peça | Nome npm | Versão | Página | Teste |
|---|---|---|---|---|
| Medidas e cores | `@wecareu/tokens` | 0.2.8 | Não | Não |
| Tema | `@wecareu/theme` | 0.3.4 | Não | Não |
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

A pessoa vê a mesma cara, claro e escuro, com Livvic (regular, semibold, bold) e cor de ação roxo.

## Inconsistência interna

O texto de apresentação da raiz ficou para trás. Lista quatro peças (medidas e cores, tema, ícones e botão de link). O desenho de pastas no mesmo texto é mais curto e nem cita os ícones. O código já tem também texto, degradê, fechar, campo, máscara, lista, data e espera. O mesmo texto fala em mais de 70 ícones. A lista tem 69.

## O que não cobre

Telas de quem procura o serviço, app de quem atende, regras de negócio, preço e pagamento. Ícones de pix, cartão e dinheiro, e a máscara de cartão, não significam que o app cobra. Também não cobre como publicar o kit.

Ver [[kit-visual]].
