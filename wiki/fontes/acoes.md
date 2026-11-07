---
tipo: fonte
arquivo: "ingeridos/Ações.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Ações"]
---

# Ações

Volta para [[panorama-do-design-system]]. Três papéis. O degradê é a ação principal. O link é a secundária, com cara de link. O fechar só dispensa. Ícones vêm de [[vocabulario-visual]]. Cores vêm de [[identidade-visual]].

**Pé:** Parcial. Os três estão usáveis e cada um tem teste. O cabeçalho do bruto diz Pronto; o corpo e o panorama dizem Parcial, porque a demonstração do degradê ainda usa o texto e os exemplos do link.

Nenhum mostra espera. Quem usa a peça diz o que acontece no toque. As frases do degradê e do link são as que a tela escrever. O fechar não mostra palavra.

## O que a pessoa vê

`@wecareu/button-gradient` **0.3.3**. Fundo de `#BC4CF7` a `#7873EE`, o mesmo no claro e no escuro. Texto branco. Não sublinha. No toque, encolhe e fica mais transparente. Desabilitado, o degradê fica lavado e o toque não responde. O teste confere o texto, o toque e o toque morto.

`@wecareu/button-link` **0.3.4**. Sem fundo e sem borda. Texto na cor secundária (lilás no claro). O sublinhado começa desligado. Ícone, sublinhado e desligado existem. O teste também confere que o sublinhado começa desligado.

`@wecareu/button-close` **0.2.4**. Círculo com um X. Pequeno 32/16, médio 40/20 (padrão), grande 48/24. No claro o círculo é claro e o X é escuro; no escuro, o inverso. O leitor de tela ouve **Fechar**. A peça aceita outro ícone; nenhuma demonstração mostra outro.

## O que a página do degradê troca

Um exemplo chamado sublinhado não muda o botão. Sublinhado é do link. Uma faixa junta quatro degradês iguais. O texto de instalação descreve tamanhos pequeno, médio e grande, um degradê cinza no desabilitado e um toque que só baixa a opacidade. A peça não tem esses tamanhos. Desabilitada, continua roxa e azul, mais transparente. No toque ela encolhe e fica mais transparente.

Ver [[como-o-time-revisa-a-interface]], [[kit-visual]].
