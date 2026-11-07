---
tipo: fonte
arquivo: "ingeridos/Datas.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Datas"]
---

# Datas

Volta para [[panorama-do-design-system]]. A pessoa escolhe uma data. O que volta para a tela é um texto, com hora se a tela pediu hora. Esta peça não marca horário com um profissional. Uma lista de opções é [[escolha-em-lista]].

**Pé:** Pronto. `@wecareu/date-picker` **0.2.6**. Usável, com demonstração. Há teste do campo fechado e da escrita. O teste automático não abre o calendário: troca a folha do mês por um espaço vazio.

## O que a pessoa vê

Três modos: um dia (padrão), um intervalo, ou vários dias. No intervalo a tela mostra início, uma seta e fim. Em vários dias, dois ou mais mostram a contagem, por exemplo **3 datas selecionadas**. A lista dos dias não aparece no campo.

Duas caras, as duas fechadas. O calendário abre no toque, numa folha que sobe. Não há mês já aberto na tela. **field** (padrão) parece um campo de [[campos-de-formulario]], com rótulo parado acima da borda, se a tela mandar um. **bare** é texto e ícone, sem borda; o rótulo não aparece. Vazio, o texto padrão é **Selecionar data**. O ícone é um calendário; com valor, vira um X (**Limpar data**).

A data aparece no jeito do Brasil: 31/12/2025. Com horário: 31/12/2025 14:30, sem segundos. O relógio começa desligado. No intervalo, a mesma hora vale para o início e para o fim. Em vários dias o relógio não abre.

O mês sai por extenso, em português. A semana começa no domingo. Dá para limitar mínimo, máximo e dias proibidos. Desabilitado e somente leitura não abrem. Esta peça não mostra mensagem de erro. Digitar a data com máscara é [[campos-de-formulario]].

O texto de instalação chama o rótulo de flutuante e diz que o horário abre também em vários dias. Nesta peça o rótulo fica parado, e em vários dias o relógio não abre.

Ver [[kit-visual]].
