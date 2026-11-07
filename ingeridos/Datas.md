---
tipo: extração
tema: Datas
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/date-picker"]
pé: Pronto. Campo e calendário usáveis, com demonstração. O teste automático não abre o calendário.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Datas

Volta para o [[Panorama do design system]].

**Pé:** Pronto. Escolher data está usável e tem demonstração. Há teste do campo fechado e teste da escrita. O calendário aberto fica na demonstração: o teste automático troca a folha do mês por um espaço vazio. O rito de olhar a interface está em [[Como o time revisa a interface]].

A pessoa escolhe uma data. O que volta para a tela é um texto de data, com hora se a tela pediu hora. Esta peça não marca horário com um profissional.

Os dias ficam na grade do mês. Uma lista de opções é [[Escolha em lista]].

## Três modos

Os três existem.

- Um dia. É o padrão. O nome no tipo é single.
- Um intervalo, com início e fim. O nome no tipo é range. Na tela aparece início, uma seta e fim. Exemplo: 01/12/2025 → 31/12/2025.
- Vários dias. O nome no tipo é multiple. Um dia só mostra a data. Dois ou mais mostram a contagem, por exemplo **3 datas selecionadas**. A lista dos dias não aparece no campo.

Limpar um dia ou um intervalo esvazia a escolha. Limpar vários dias deixa a lista vazia.

## Duas caras

Os dois nomes existem: field e bare. Os dois são um controle fechado. O calendário abre no toque, numa folha que sobe de baixo. Não há uma cara com o mês já aberto na tela.

**field** é o padrão. Parece um campo dos [[Campos de formulário]]: borda na cor da marca, cantos bem arredondados, texto no centro, ícone à direita. O rótulo, se a tela mandar um, fica acima da borda.

**bare** é o texto e o ícone, lado a lado, sem borda e sem caixa. O rótulo não aparece nesta cara, mesmo que a tela mande um.

Vazio, o texto padrão é **Selecionar data**. A tela pode trocar essa frase. O ícone é um calendário. Com valor, o ícone vira um X e o toque nele limpa a data. O nome que o leitor de tela ouve nesse ícone é **Limpar data** ou **Selecionar data**.

## Como a data aparece

Dia, mês e ano, no jeito do Brasil: 31/12/2025.

Com horário, a mesma data e a hora com minutos: 31/12/2025 14:30. Os segundos não aparecem.

O horário começa desligado. Ligado, a pessoa marca o dia (ou os dois dias do intervalo) e depois vê hora e minuto, com setas para subir e descer. A hora vai de 00 a 23. O minuto vai de 00 a 59. **‹ Voltar** retorna ao mês. **Confirmar** grava e fecha.

No intervalo, o relógio é um só: a mesma hora vale para o início e para o fim.

Em vários dias o relógio não abre. A pessoa marca e desmarca dias e confirma a lista.

## Limites

Dá para impedir o que vem antes de uma data mínima, o que vem depois de uma data máxima, e dias avulsos numa lista proibida. Esses dias aparecem apagados e não respondem ao toque. Dá para passar o mês mesmo assim.

Desabilitado, o campo fica com fundo apagado, o texto esmaece e nem o calendário nem o limpar abrem.

Somente leitura parece um campo normal e também não abre.

Esta peça não mostra mensagem de erro.

## O calendário

A folha traz o mês por extenso e o ano, em português: Janeiro, Fevereiro, e os outros. À esquerda, o mês anterior. À direita, o próximo. A semana começa no domingo. As letras são D, S, T, Q, Q, S, S.

Um toque num dia, sem horário, grava e fecha. No intervalo, o primeiro toque é o início e o segundo é o fim. Se o segundo dia vier antes do primeiro, a peça inverte. Os dias do meio ficam numa faixa clara da cor da marca. O dia marcado fica preenchido com a cor da marca, a da [[Identidade visual]].

Em vários dias, cada toque já entra ou sai da lista. **Confirmar** fecha. Se houver dias marcados, o botão escreve a contagem, por exemplo **Confirmar (3)**. Tocar na área escura em volta também fecha, e o que já foi tocado permanece. Confirmar e Voltar nascem nesta folha. Os três botões da biblioteca estão em [[Ações]].

Há um traço no topo da folha. Ele não arrasta a folha.

As palavras fixas (meses, **Confirmar**, **‹ Voltar**, **N datas selecionadas**, **Selecionar data**) estão em [[Textos da interface]].

O leitor de tela trata o campo como botão, com o nome da data visível ou do texto vazio. No mês, ouve **Mês anterior** e **Próximo mês**. Cada dia é um botão, com o número do dia. A área escura se chama **Fechar calendário**. No relógio, ouve aumentar e diminuir a hora e o minuto.

## Versão, demonstração e teste

`@wecareu/date-picker`, versão **0.2.6**.

Demonstração: sim. No disco há um dia na cara field, um dia na cara bare, um dia com rótulo, um intervalo, vários dias, um dia com horário, limite de ano, dias proibidos e o campo desabilitado.

Teste: sim, em dois arquivos.

- O teste da peça olha o campo fechado: texto vazio, data 31/12/2025, intervalo com a seta, a frase de três datas e o limpar. O calendário, nesse teste, é um espaço vazio.
- O teste da escrita confere 31/12/2025, 31/12/2025 14:30, o intervalo, a contagem de vários dias, e a regra do dia proibido: antes do mínimo, depois do máximo, ou na lista.

## O que o texto de instalação troca

Ele chama o rótulo de flutuante e diz que o campo é igual ao campo de texto. Nesta peça o rótulo fica parado, acima da borda.

Ele diz que o horário aparece depois de escolher a data ou as datas. O relógio abre num dia e num intervalo. Em vários dias, não abre.

Um exemplo desse texto usa o rótulo de uma consulta. A peça devolve o texto da data. Quem marca com um profissional é a tela que usar a peça.
