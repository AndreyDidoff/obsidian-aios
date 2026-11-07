---
tipo: pendencia
superficie: backend
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[core-08-enderecos]]"]
---

# Ajustes de backend: listagem e endereço

Esta página lista o que o backend precisa mudar na listagem e no endereço para chegar ao alvo do MVP. Não é a especificação do produto.

### Poucas avaliações
- **Alvo:** A API da listagem e do perfil informa que o Artista tem poucas avaliações, com limite de 3 configurável, e nesse caso não envia a nota. A contagem e o limite ficam no backend. ("M05/M02-F05 Perfil do artista visto pelo cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Informar na API da listagem e do perfil quando o Artista tem poucas avaliações, com limite de 3 configurável, e não enviar a nota nesse caso.

### Paginação do perfil
- **Alvo:** O perfil pagina categorias de 5 em 5, serviços de cada categoria de 5 em 5 e regiões de 10 em 10, com "ver mais" por consulta. ("M05/M02-F05 Perfil do artista visto pelo cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Paginar categorias de 5 em 5, serviços de cada categoria de 5 em 5 e regiões atendidas de 10 em 10, cada continuação numa consulta.

### Paginação da listagem
- **Alvo:** A listagem pagina 10 cards, com ordem estável na sessão. ("M05 Scroll infinito", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Entregar 10 cards por página e manter a ordem estável durante a sessão.

### Sorteio de desempate
- **Alvo:** [RECOMENDADO] O sorteio de desempate da sessão se mantém ao atualizar. Renova só em busca nova ou sessão nova. ("M05 Arrastar para atualizar", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Manter o sorteio de desempate da sessão ao atualizar e renová-lo só em busca nova ou sessão nova.

### Lista sem data
- **Alvo:** Sem data escolhida, a lista não tem grupos A e B nem checagem de agenda. Com data, os grupos voltam. ("M05 Filtros e tela Pesquisar", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Sem data, não formar grupos A e B nem checar a agenda. Com data, devolver os grupos A e B.

### Chips com oferta
- **Alvo:** Categorias e serviços só entram quando há pelo menos um Artista aprovado na região. ("M05 Filtros e tela Pesquisar", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Devolver categorias e serviços somente quando houver pelo menos um Artista aprovado na região.

### Limite do calendário
- **Alvo:** O limite futuro do calendário é configurável no backend e acompanha o horizonte da agenda do Artista. ("M05 Filtros e tela Pesquisar", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Expor um limite futuro de calendário configurável no backend, alinhado ao horizonte da agenda do Artista.

### Validação de texto livre
- **Alvo:** A descrição curta e a longa são validadas no backend: bloqueia telefone, e-mail, URL, "@" e script, e sai escapada. O painel remove a foto de divulgação e limpa a descrição. ("M05/M02 Descrição curta do card", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. Validar no backend a descrição curta e a longa, bloqueando telefone, e-mail, URL, "@" e script, com saída escapada, e permitir que o painel remova a foto de divulgação e limpe a descrição.

### Endereço repetido
- **Alvo:** Vários endereços, sem principal. Endereço repetido é recusado pela combinação de CEP, número e complemento. ("Endereço de atendimento e troca pela listagem", [[mvp-funcoes-e-telas]])
- **Hoje:** [[core-08-enderecos]] grava CEP, cidade, bairro, logradouro, número, complemento, nome e um tipo (casa, trabalho ou busyness). Não há a regra de vários endereços sem principal.
- **Ajuste:** Passar a gravar vários endereços do mesmo cliente, sem principal e sem exigir o tipo casa/trabalho. Recusar o repetido por CEP, número e complemento.

### Mínimos de validação
- **Alvo:** [RECOMENDADO] Os mínimos de CEP e de texto não bloqueiam o app. A recomendação é CEP com 8 dígitos e rua, bairro e cidade com pelo menos 2 caracteres; os valores exatos ficam em aberto. ("Welcome: slide 5 (endereço)", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve mínimos de validação.
- **Ajuste:** Tratar como recomendação, sem bloquear o app, CEP com 8 dígitos e rua, bairro e cidade com pelo menos 2 caracteres.

### Campos separados
- **Alvo:** Vários endereços, sem principal, com campos separados: CEP, rua, bairro, número, complemento, nome, cidade e UF. ("Cadastro do cliente: formato e dados", [[mvp-funcoes-e-telas]])
- **Hoje:** [[core-08-enderecos]] grava CEP, cidade, bairro, logradouro, número, complemento, nome e um tipo (casa, trabalho ou busyness). Não há a regra de vários endereços sem principal.
- **Ajuste:** Os campos que o núcleo já grava separados continuam separados. Incluir UF, que o retrato não traz.
