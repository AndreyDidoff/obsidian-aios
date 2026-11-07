---
tipo: fonte
arquivo: "ingeridos/Como o time revisa a interface.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Como o time revisa a interface"]
---

# Como o time revisa a interface

Volta para [[panorama-do-design-system]]. Dois lugares para olhar as peças. Nenhum usa o escopo `@wecareu`.

**Pé:** Parcial. O catálogo no navegador mostra as peças que têm página. O app no celular não é vitrine.

## O que a pessoa vê

`storybook-web`, porta 6006, é o lugar que mostra as peças. Cada página abre dentro do tema. Um controle Tema alterna Claro e Escuro. A abertura é o claro. A escolha é gravada no navegador, mas ao abrir o controle volta para o claro e grava o claro de novo. Quem tinha deixado o escuro não reencontra essa escolha. Cada página fica na camada de [[espera-e-carregamento]]. O véu só aparece quando a página pede.

Páginas que existem: [[vocabulario-visual]], [[textos-da-interface]], [[acoes]] (degradê, link e fechar, cada um com a sua), [[campos-de-formulario]] (livre e máscara), [[escolha-em-lista]], [[datas]] e [[espera-e-carregamento]]. A de espera tem um botão "Mostrar Loading".

Sem página própria: [[identidade-visual]]. Claro e escuro aparecem em volta das outras peças, não numa página só deles.

`playground`, chamado Design System Playground, versão marcada **1.0.0**, é o app de demonstração no celular. O título diz "Design System Playground". Embaixo há uma seção só do botão de link, com cinco exemplos. Os três primeiros só mudam o texto: o botão de link não tem tamanho pequeno, médio ou grande. Nenhuma outra peça aparece. O tema dessa tela fica preso no claro.

Há um catálogo preparado dentro do aparelho, na porta 7007. Ele só registraria a página do botão de link, e a tela do app não abre esse catálogo.

## O que não cobre

Como ligar o catálogo ou o app. Telas de quem procura o serviço e o app de quem atende. Se o teste automático passa ou falha agora: a nota só registra que o teste existe, ou não. O mapa está em [[panorama-do-design-system]].

Ver [[kit-visual]], [[engenharia-de-software]].
