---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-21
fontes: ["[[lyraui-07-figma-padroes]]", "[[lyraui-08-figma-api]]", "[[lyraui-14-ferramentas]]", "[[board-design-no-figma]]"]
---

# Figma da LyraUI

Ambiente de criação do design system. O arquivo está sendo refeito; os IDs abaixo são do arquivo atual e podem morrer na refação. ([[lyraui-07-figma-padroes]], [[lyraui-08-figma-api]])

## Arquivo

File key `cgiDSTP8mJptixfc06ErRt`. Mais de 30 páginas. O padrão-alvo é Design System (Components, Tokens) e, por app, Screens, Flows e Archive. Archive não é fonte da verdade. A organização atual (fundamentos, moléculas, utilitários) ainda não é essa. ([[lyraui-08-figma-api]])

## Regras

- Nome `Categoria/NomeDoComponente`, mapeado para o pacote `@lyra-ui/*`.
- Variável em tudo. Sem token correspondente, parar e falar com o Tech Lead.
- Tela nova: prefixo `[NEW]` e pasta Screens do app.
- Mudança em componente existente entra no Changelog: `data | componente | tipo | descrição`.
- Identificar pelo `node-id`, que sobrevive ao rename.
- No código via MCP, nomes com barra (`headings/desktop/font-heading-sm`) só viram objeto aninhado se houver uma regra escrita. Essa regra não existe. ([[lyraui-08-figma-api]])

## Divergência de nome

Os exemplos falam `spacing/md`. As coleções do arquivo chamam-se spacings, paddings e borders. Opacity é citada e não tem ID registrado. ([[lyraui-07-figma-padroes]])

Ver [[fundamentos-visuais]], [[lyraui]].

## O que o board pede em 21/10

O board pede telas no Figma ([[board-design-no-figma]]). Não há épico. A história 175, [DS] Criar telas no figma, está sem pai e Completed. A história 240, Criar divisões no figma de versões, está sem pai e Completed. A tarefa 219, [DS] Criar Splash Screen no Figma, está sem pai e Completed. Sem descrição. As tarefas 177 a 187 e a 241 estão Completed e sem descrição. A história 175 está sem descrição. O critério de aceite dela está ausente. A história 240 está sem descrição. Este bruto não traz file key. O file key já escrito nesta página permanece. Completed não prova a tela no app nem no Figma de produção.
