---
tipo: fonte
arquivo: "ingeridos/banco-mongo-relacoes.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 da estrutura MongoDB da WeCareU; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Relações do MongoDB"]
---

# Relações do MongoDB

Pares inferidos pelo nome do campo em 21/10. Nada nesta lista é constraint. O Mongo não declara chave estrangeira para o SQL. Porta: [[banco-indice]]. O lado SQL está em [[banco-sql-relacoes]].

## Do Mongo para o SQL

- `Template.Template.IdEnterprise` para `Enterprise.Enterprise.Id`. Força fraca.
- `Template.Template.IdSystem` para `SystemsData.Systems.Id`. Força fraca.

## Do SQL para o Mongo

- `Report.ReportFotos.PhotoId` para `Photos.photos._id`. Força fraca.
- `SystemsData.Systems.PhotoId` para `Photos.photos._id`. Força fraca.

## Sem destino único

`Photos.photos.OwnerId`. O nome se repete em `address.address` e `Phone.Telefones`, e não há tabela `Owner`.
