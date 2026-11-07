---
tipo: conceito
criado: 2026-10-21
atualizado: 2026-10-21
fontes: ["[[panorama-do-design-system]]", "[[identidade-visual]]", "[[vocabulario-visual]]", "[[textos-da-interface]]", "[[acoes]]", "[[campos-de-formulario]]", "[[escolha-em-lista]]", "[[datas]]", "[[espera-e-carregamento]]", "[[como-o-time-revisa-a-interface]]", "[[library-components-o-que-entrega]]", "[[library-components-entrar-na-conta]]", "[[library-components-recuperar-senha]]", "[[library-components-biometria-e-sessao]]", "[[library-components-em-que-pe-esta]]", "[[cruzamento-kit-visual]]", "[[criar-conta]]", "[[board-estrutura-dos-apps]]", "[[board-design-no-figma]]"]
---

# Kit visual

O que o código entrega hoje no repositório `library-design-system`. O nome lá é **WeCareU Design System**. Não é tela nem app. Os pacotes saem no escopo `@wecareu`. ([[panorama-do-design-system]])

A [[lyraui]] continua o alvo, em discovery, na virada para `@lyra-ui/*`. Este retrato não usa esse nome. Se bater com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial. ([[panorama-do-design-system]])

A porta é [[panorama-do-design-system]].

## Pé e versões

Retrato de 21/10. Doze pacotes versionados, mais a revisão.

| Área | Pacotes | Versão | Pé |
|---|---|---|---|
| Identidade | `@wecareu/tokens`, `@wecareu/theme` | 0.2.8, 0.3.4 | Parcial |
| Vocabulário | `@wecareu/icons` | 1.3.3 | Parcial |
| Textos | `@wecareu/text-wcu` | 0.2.4 | Parcial |
| Ações | `@wecareu/button-gradient`, `@wecareu/button-link`, `@wecareu/button-close` | 0.3.3, 0.3.4, 0.2.4 | Parcial |
| Campos | `@wecareu/input-text`, `@wecareu/input-masked` | 0.2.7, 0.2.4 | Pronto |
| Escolha em lista | `@wecareu/select` | 0.2.7 | Pronto |
| Datas | `@wecareu/date-picker` | 0.2.6 | Pronto |
| Espera | `@wecareu/loading` | 0.4.4 | Pronto |
| Revisão | `playground`, `storybook-web` | playground 1.0.0 | Parcial |

Identidade não tem página nem teste. `playground` e `storybook-web` não usam `@wecareu`. O app no celular não é vitrine. ([[identidade-visual]], [[como-o-time-revisa-a-interface]])

A nota de [[escolha-em-lista]] chama a peça de Parcial. O panorama marca a área como Pronto. O [[cruzamento-kit-visual]] fica com a nota da peça: Parcial. O mesmo panorama marca os ícones como Parcial. A nota [[vocabulario-visual]] diz que os desenhos estão prontos, e que a bandeira e as animações ficam parciais. Neste cruzamento vale essa nota.

## O que a pessoa vê

- Claro e escuro. Livvic em regular, semibold e bold. Cor de ação roxo. ([[identidade-visual]])
- 69 desenhos e três animações: pontos, local e aviso. A espera usa só os pontos. O nome da digital não bate com o desenho. Bandeira: emoji no celular, imagem externa no navegador. ([[vocabulario-visual]], [[panorama-do-design-system]], [[espera-e-carregamento]])
- Quatro papéis de texto. A escala display fica na identidade. ([[textos-da-interface]])
- Três botões. A página do degradê ainda fala como se fosse o link. Um exemplo chamado sublinhado não muda o botão. ([[acoes]])
- Máscaras de CPF, CNPJ, CEP, telefone, cartão e data. A de cartão só formata. Ícones de pix, cartão e dinheiro não significam que o app cobra. ([[campos-de-formulario]], [[vocabulario-visual]])
- Exemplos da lista em inglês. Calendário em português. Véu com pontos, sem frase. ([[escolha-em-lista]], [[datas]], [[espera-e-carregamento]])

O texto da raiz ficou para trás: lista quatro peças e fala em mais de 70 ícones; a lista tem 69. ([[panorama-do-design-system]])

`@wecareu/auth-flow` consome um pedaço deste kit: tema, ícones, texto, botões, campo livre e fechar. Não usa data, lista nem máscara. Também não declara a espera. ([[library-components-o-que-entrega]], [[library-components-entrar-na-conta]], [[library-components-recuperar-senha]], [[library-components-biometria-e-sessao]], [[library-components-em-que-pe-esta]])

O [[cruzamento-kit-visual]] diz quem instala. O app do cliente instala as doze. O fluxo compartilhado, na versão 0.1.0, usa tema, ícones, texto, botão em degradê, botão de link, botão de fechar e campo livre. Não usa data, lista nem máscara. A espera também não entra nesse uso. Medidas e cores não são declaradas por esse fluxo; a cor entra pelo tema. Esse fluxo não está instalado no cliente nem no artista. O app do artista não instala o kit. Campos, botões e textos dele nascem no próprio app. Os usos no cliente, nesse cruzamento, são os que a extração conferiu, não o inventário de cada tela. No cadastro do cliente, o cruzamento diz que sexo, tipo de endereço e país usam a lista. [[criar-conta]] chama o campo de gênero e diz que não há sexo separado. Ver o item 14 de [[contradicoes-e-lacunas]].

## Fora deste retrato

Telas dos apps e pagamento. ([[panorama-do-design-system]])

Ver [[fundamentos-visuais]], [[voz-e-escrita]], [[engenharia-de-software]], [[fluxo-de-entrada]], [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

O board pede biblioteca de componentes e biblioteca de design system ([[board-estrutura-dos-apps]]). A história 460 está New. A história 488 está New. Há tarefas Completed de biblioteca inicial e de pipeline para um feed privado, no escopo `@wecareu/*`. A tarefa 490, integrar bibliotecas no app client, está Removed. Este retrato de 21/10 permanece. O cliente instala as doze. O artista não instala o kit. `@wecareu/auth-flow` continua não instalado.

O board pede telas no Figma ([[board-design-no-figma]]). Não há épico. A história 175 e a história 240 estão sem pai e Completed. A tarefa 219 está sem pai e Completed. Pedir a tela no Figma não cria a tela no app. Este retrato de 21/10 permanece.
