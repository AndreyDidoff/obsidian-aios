---
tipo: fonte
arquivo: "ingeridos/Identidade visual.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Identidade visual"]
---

# Identidade visual

Volta para [[panorama-do-design-system]]. Prateleira de cara do kit: modo, cor, folga, canto e letra. Os tokens guardam os valores. O tema entrega esses valores já separados por modo.

**Pé:** Parcial. `@wecareu/tokens` **0.2.8**. `@wecareu/theme` **0.3.4**, apontando para esses tokens. Dá para usar numa tela. Não há página da paleta nem teste automático. O código existir não basta para o pé Pronto. Uma mudança de hex não quebra teste destes pacotes, porque o teste não existe.

## O que a pessoa vê

Dois modos, claro e escuro. Quem monta a tela escolhe. Se ninguém escolhe, abre no claro. A pessoa que usa o app não escolhe neste repositório. O interruptor do app do cliente não está aqui. O kit permite alternar com a tela aberta; quem consome é que liga esse gesto a um controle.

A cor de ação é o roxo `#712fc1` no claro e `#803ed0` no escuro. A ação secundária no claro é o lilás `#817eb9`. O degradê do botão, igual nos dois modos, vai de `#BC4CF7` a `#7873EE`. O fundo da página é `#ecedf4` no claro e `#0b0c13` no escuro. Há nove famílias (tela, neutras, erro, sucesso, aviso, informação, degradê, transparência e sombra). Vários papéis dividem o mesmo hex. O comentário no arquivo diz que as cores de tela seguem o app principal. Isso não é guia de marca.

A letra é Livvic. O pacote traz três arquivos: regular (400), seminegrito (600) e negrito (700). Os nomes na tela são Livvic, LivvicSemiBold e LivvicBold. O peso médio (500) é só número: não há arquivo de fonte. O tema monta catorze receitas. [[textos-da-interface]] usa quatro. Folga de 4 a 48. Canto de 4 até a pílula (9999).

## O que falta e o que o arquivo não decide

Não há regra de gesto para hover, pressionado e desabilitado, nem de quando valem disponível, ocupado, online, offline e estrela. A borda leve só existe no claro.

O texto de instalação ainda cita `#2E6BE6` para a marca clara. O código usa os hex da tabela. O mesmo texto lista a folga só até 32 e omite o canto 4. Um resumo curto de cores, feito para compatibilidade, diverge do tema que a tela lê: no escuro, a superfície desse resumo é `#1e1d34`; a que o tema entrega é a do cartão, `#231639`.

Um hex guardado não é regra do que a marca permite. O alvo de 20/10 está em [[fundamentos-visuais]]. O conflito fica em [[contradicoes-e-lacunas]].

Ver [[acoes]], [[kit-visual]].
