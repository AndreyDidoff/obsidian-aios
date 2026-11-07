---
tipo: fonte
arquivo: "ingeridos/board-bugs.md"
origem: "extração via IA (Cursor) do board Azure DevOps da organização piresbno1992, projeto WeCareU, em 2026-10-21; retrato de trabalho, não decisão de produto; em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Bugs"]
---

# Bugs

Porta: [[board-indice]]. Extração em 2026-10-21. Organização `piresbno1992`, projeto WeCareU. Área WeCareU\BUGS em todos os itens deste bruto. Retrato de trabalho, não decisão de produto. Em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Estado no board não é pé do produto. New ou Completed não significa entregue no app nem no [[mvp]].

## O que este tema pede

O board lista bugs. O épico 463 traz uma história de login. Os outros sete épicos estão sem história.

## Épico 463 — Bugs gerais / Pendências gerais

Estado no board: New. Responsável: nenhum. Sem descrição.

### História 464 — Sistema de login

Estado no board: New. Responsável: nenhum. Sem descrição.

#### Tarefa 465 — [BE] Código de Resposta HTTP errado ao errar login

Estado no board: Completed. Responsável: bruno.pires@wecareu.app.

A descrição diz: ao realizar o login no endpoint `https://api.wecareu.app/beautiful/api/Login` e o login falhar, o sistema dá um erro 500. O esperado é o erro 401.

O critério de aceite está ausente. Os comentários estão ausentes.

## Épicos sem história

- Épico 481, Bugs app CLIENT. Estado: New. Sem descrição. Sem histórias.
- Épico 482, Bugs app ARTIST. Estado: New. Sem descrição. Sem histórias.
- Épico 483, Bugs web CLIENT. Estado: New. Sem descrição. Sem histórias.
- Épico 484, Bugs web ARTIST. Estado: New. Sem descrição. Sem histórias.
- Épico 485, Bugs web ADMIN. Estado: New. Sem descrição. Sem histórias.
- Épico 486, Bugs web WIKI. Estado: New. Sem descrição. Sem histórias.
- Épico 487, Bugs Libraries. Estado: New. Sem descrição. Sem histórias.

## O que isto não decide

Completed na tarefa 465 não é o código do retrato de 21/10. O board pede 401 quando o login falha. Isso não declara o conserto em [[bff-entrar-sair-e-senha]]. Esse retrato não diz o código de resposta.

Épico vazio não é escopo de produto. As cascas 481 a 487 não entregam um produto. O épico 486, Bugs web WIKI, não é esta base Obsidian.

Ver [[bff-entrar-sair-e-senha]].
