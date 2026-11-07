> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 12 · Princípios de design

Tags: #lyraui #principios #design-principles #aprendizagem #evolucao #interatividade #amizade

---

## 1. Status

- **LyraUI (alvo, em discovery, não implementada no código):** os princípios guiam as decisões visuais e comportamentais de estilos e componentes que a LyraUI vai construir.
- **WeCareU (produto e empresa):** os princípios refletem o ideal que a WeCareU defende. A LyraUI os traduz em design. Ver [[02-contexto-wecareu]] e [[01-visao-geral-lyraui]].
- Os princípios **também refletem na construção de escrita**. Eles impactam diretamente como a voz se posiciona e como o design se resolve. Ver [[10-voz-e-tons]].

---

## 2. O que são princípios de design

- Diretrizes e considerações que guiam as tomadas de decisão visuais e comportamentais.
- Existem para guiar e **minimizar a subjetividade** da decisão em design. Ver o termo no [[13-glossario]].
- Cada princípio é traduzido por uma palavra, acompanhada de uma explicação clara e tangível.

---

## 3. Os quatro princípios

Cada princípio tem uma descrição e, logo abaixo na fonte, uma linha de **atributos**. A associação entre princípio e atributos vem da posição no documento original.

### 3.1 Aprendizagem

**Atributos:** Objetivo e Eficiente

- Dedicação a criar experiências **fluidas e amigáveis** para as pessoas usuárias.
- É inevitável que novos cenários surjam, trazendo inovação e otimização às interfaces e fluxos.
- Nessas situações, a LyraUI oferece **suporte para tornar toda nova aprendizagem amigável e compreensível**.

Em uma frase: quando algo novo aparece, a pessoa não fica sozinha.

### 3.2 Evolução

**Atributos:** Adaptável, Modular e Universal

- A experiência digital se baseia em **comunicação fluida e sincronizada** com a pessoa usuária.
- **Toda ação gera uma reação**, que entrega à pessoa o que ela busca ou precisa.

Em uma frase: cada ação tem retorno claro e o sistema se adapta.

### 3.3 Interatividade

**Atributos:** Dinâmico

- A WeCareU trabalha para que os melhores recursos estejam disponíveis para a pessoa usuária.
- Por isso a LyraUI visa ser **personalizável**, oferecendo opções de escolha e considerando diferentes possibilidades em seus fluxos.

Em uma frase: a pessoa tem opções, e os fluxos consideram caminhos diferentes.

### 3.4 Amizade

**Atributos:** Simples, Claro e Cuidadoso

- A WeCareU oferece um **espaço livre e seguro** no ambiente digital para acompanhar a navegação da pessoa usuária.
- Está presente em **todas as etapas da jornada**.
- Para gerar confiança, traz **visibilidade nas interações** e confiança ao avançar para as próximas etapas.

Em uma frase: a pessoa sempre sabe onde está e confia no próximo passo.

---

## 4. Resumo

| Princípio | Atributos | Ideia central |
|---|---|---|
| **Aprendizagem** | Objetivo e Eficiente | Apoiar a pessoa diante do que é novo |
| **Evolução** | Adaptável, Modular e Universal | Ação e reação claras, comunicação sincronizada |
| **Interatividade** | Dinâmico | Personalização e opções de escolha |
| **Amizade** | Simples, Claro e Cuidadoso | Espaço seguro, visibilidade e confiança |

---

## 5. Princípios x pilares x voz

Não confundir as listas. O material tem três camadas que se complementam:

| Camada | Itens | Fonte |
|---|---|---|
| **Pilares do ecossistema** | O profissional como artista, estética, cuidado (care), eficiência e simplicidade | Guia de voz |
| **Princípios de design** | Aprendizagem, Evolução, Interatividade, Amizade | Este documento |
| **Características da voz** | Focada em estética, acolhedora, vai direto ao ponto, dignifica o profissional | Guia de voz. Ver [[10-voz-e-tons]] |

---

## 6. Como os princípios aparecem no trabalho

Leitura de apoio, derivada das fontes. Não é uma definição oficial.

| Princípio | Onde tende a aparecer |
|---|---|
| Aprendizagem | Tom **instrutivo** em primeiros acessos, cadastros e portfólios. Ver [[10-voz-e-tons]] |
| Evolução | Estados de componente completos (padrão, disabled, loading, error) e feedback a cada ação. Ver Definition of Done em [[04-arquitetura-e-estrutura-do-ds]] |
| Interatividade | Componentes configuráveis por variantes e tokens, sem valores fixos. Ver [[05-sistema-de-tema]] |
| Amizade | Tom **tranquilizador** em erros, sem culpar a pessoa. Textos curtos e claros. Ver [[11-escrita-e-ortografia]] |

---

## 7. Divergências e pontos em aberto

- **Atributos por princípio:** a associação foi inferida pela posição das linhas no documento original. Confirmar no ZeroHeight.
- **Tensão aparente:** o princípio *Interatividade* fala em personalização, mas o **tema não é exposto à pessoa usuária** e cada app usa um único tema. Ver [[05-sistema-de-tema]]. Vale definir qual personalização o princípio cobre.
- **Documento da persona:** o documento de fundamentos cita um arquivo próprio de persona e princípios (`lyraui-persona-e-principios.md`). Se existir, comparar com este.
- **Critérios práticos:** a fonte não traz exemplos nem forma de medir a aplicação de cada princípio.
- **Nomes das palavras-chave:** o glossário diz que cada princípio é traduzido por uma única palavra ou frase curta. Aqui há quatro nomes e vários atributos. Definir qual é a "palavra" oficial.

---

## Links

Anterior: [[06-catalogo-e-inventario-legado]] · Próximos: [[13-glossario]] · [[14-ferramentas-e-forma-de-trabalho]]
