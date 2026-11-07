# Esquema da wiki (LLM Wiki — padrão Karpathy)

Este arquivo é lido em toda sessão. É a única memória persistente das regras.
O que não estiver aqui não sobrevive entre sessões.

## Domínio

**WeCareU**: startup brasileira (fase MVP) que constrói um marketplace de beleza e bem-estar, conectando clientes a profissionais ("Artistas") e salões. As fontes são documentos internos de planejamento (produto, negócio, planos, segurança, documentos legais) e snapshots de design system (LyraUI) e de engenharia, exportados do AppFlowy ou extraídos por IA.

Definido em 2026-10-20. Ampliado no mesmo dia com a LyraUI e a engenharia. Snapshots de IA não substituem decisão registrada em `wiki/fontes/decisoes-*.md`.

## Camadas

| Camada | Local | Dono | Regra |
|---|---|---|---|
| Caixa de entrada | `raw/` (imagens em `raw/assets/`) | humano | só fontes **ainda não ingeridas**; deve ficar vazia depois de cada ingest |
| Fontes brutas ingeridas | `ingeridos/` (imagens em `ingeridos/assets/`, quando houver) | humano | conteúdo imutável; é a fonte da verdade citada pelas páginas `fonte` |
| Wiki | `wiki/` | LLM | o LLM escreve e mantém tudo; o humano lê |
| Esquema | `CLAUDE.md` | ambos | co-evoluído; toda mudança é logada |
| Navegação | `index.md`, `log.md` | LLM | atualizados a cada operação |

## Regras invioláveis

1. Nunca edite nem apague o conteúdo de uma fonte bruta, esteja ela em `raw/` ou em `ingeridos/`. A única operação permitida sobre o arquivo é movê-lo de `raw/` para `ingeridos/` ao fim do ingest.
2. Não crie estrutura por antecipação. Nenhuma pasta, tipo, página ou taxonomia sem que as fontes a exijam.
3. Toda afirmação na wiki cita a(s) fonte(s) de onde veio, via wikilink para a página `fonte` correspondente.
4. Contradições entre fontes são registradas explicitamente nas páginas afetadas, nunca resolvidas em silêncio.
5. Toda operação (ingest, query arquivada, lint, mudança de esquema, criação de pasta, novo tipo) gera uma entrada em `log.md`.
6. `index.md` reflete sempre o estado real de `wiki/`.
7. `log.md` é append-only.

## Regra de crescimento

- Toda página nasce solta na raiz de `wiki/`.
- O frontmatter `tipo:` é atribuído sempre, com cuidado. Nenhuma página existe sem ele.
- 3+ páginas do mesmo tipo → cria a subpasta `wiki/<tipo-no-plural>/`, move as páginas, documenta a pasta na tabela abaixo e loga.
- Pasta é cosmética: wikilink resolve por nome, não por caminho. `tipo:` é a arquitetura real.
- Único tipo pré-definido: `fonte`. Os outros são cunhados conforme as fontes revelarem e registrados na tabela abaixo antes do primeiro uso.
- Vocabulário pequeno é melhor que vocabulário preciso. Antes de cunhar um tipo novo, verifique se um existente serve.

### Tipos

| Tipo | Descrição | Pasta | Criado em |
|---|---|---|---|
| `fonte` | Resumo de um documento bruto (ou de decisões dadas no chat), um por fonte | `wiki/fontes/` | pré-definido |
| `entidade` | Ator concreto e nomeado: empresa, pessoa | `wiki/entidades/` | 2026-10-20 |
| `conceito` | Tema, funcionalidade, regra de negócio ou ideia que atravessa fontes | `wiki/conceitos/` | 2026-10-20 |
| `sintese` | Visão transversal da wiki inteira (visão geral, contradições) | raiz de `wiki/` (menos de 3) | 2026-10-20 |
| `pendencia` | Ajuste para o produto do MVP chegar ao alvo. Frontmatter leva `superficie: app-cliente` ou `superficie: backend` | `wiki/pendencias/` | 2026-11-05 |

`wiki/fontes/` é a única subpasta que existe desde o início, porque todo ingest produz uma página `fonte`.

## Convenções de página

- Nomes de arquivo: minúsculas, hífens, sem acentos (`nome-da-pagina.md`). Nomes únicos em toda a wiki, já que links resolvem por nome.
- Links internos: wikilinks do Obsidian (`[[nome-da-pagina]]`).
- Frontmatter mínimo:

```yaml
---
tipo: <tipo da tabela acima>
criado: AAAA-MM-DD
atualizado: AAAA-MM-DD
fontes: ["[[fonte-x]]", "[[fonte-y]]"]
---
```

- Wikilinks no frontmatter vão entre aspas; sem aspas o YAML lê `[[...]]` como lista aninhada.
- Páginas `fonte` levam `arquivo: ingeridos/<nome do arquivo>` e `origem:` no lugar de `fontes:`. Se o texto da fonte parece gerado por IA ou é um modelo, registre isso em `origem:`.
- Toda página não-`fonte` aponta para [[contradicoes-e-lacunas]] quando tiver conflito ou decisão em aberto, e essa página é atualizada junto.
- Decisões e correções dadas pelo humano no chat viram uma página `fonte` em `wiki/fontes/decisoes-AAAA-MM-DD.md`, com `arquivo: (conversa no chat, sem arquivo em raw/)`. Nos pontos que tratam, elas têm precedência sobre fontes anteriores; as páginas afetadas são atualizadas e a contradição ganha o status correspondente. O LLM não escreve em `raw/`.
- Arquivos `desktop.ini` (Google Drive) não são fontes; são ignorados e nunca movidos.
- Se um arquivo de `raw/` tiver o mesmo nome de um que já está em `ingeridos/`, não sobrescreva: pergunte ao humano se é uma versão nova da mesma fonte.

## Workflows

### Ingest
1. Ler a fonte em `raw/` (texto primeiro; imagens de `raw/assets/` depois, se relevantes).
2. Discutir com o humano os pontos principais e o que enfatizar.
3. Criar a página `fonte` em `wiki/fontes/`.
4. Atualizar ou criar as páginas afetadas (uma fonte pode tocar 10–15 páginas), na raiz de `wiki/`, com `tipo:` definido.
5. Sinalizar contradições com o conteúdo existente.
6. Aplicar a regra de crescimento (3+ do mesmo tipo → subpasta).
7. Atualizar `index.md`.
8. Mover o arquivo de `raw/` para `ingeridos/` (e as imagens que ele usa de `raw/assets/` para `ingeridos/assets/`), sem renomear, e conferir que o `arquivo:` da página `fonte` aponta para o novo caminho.
9. Logar.

Uma fonte que está em `raw/` ainda não foi ingerida. Para consultar ou reler um original já ingerido, procure em `ingeridos/`.

### Query
1. Ler `index.md` primeiro, depois as páginas relevantes.
2. Responder com citações (wikilinks).
3. Se a resposta tiver valor duradouro (comparação, análise, conexão nova), oferecer arquivá-la como página na wiki, e logar.

### Lint
Procurar: contradições entre páginas, afirmações superadas por fontes mais novas, páginas órfãs, conceitos citados sem página própria, referências cruzadas faltando, lacunas que uma busca resolveria, páginas sem `tipo:` ou com tipo fora da tabela, tipos com 3+ páginas sem subpasta. Reportar, sugerir novas perguntas e fontes, corrigir com aprovação, logar.

## Formato do log

Cada entrada começa com `## [AAAA-MM-DD] <operação> | <título>`, com operação em: `init`, `ingest`, `query`, `lint`, `esquema`, `estrutura`.
Últimas entradas: `grep "^## \[" log.md | tail -5`.
