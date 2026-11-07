---
tipo: fonte
arquivo: "ingeridos/Campos de formulário.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Campos de formulário"]
---

# Campos de formulário

Volta para [[panorama-do-design-system]]. O que uma tela pede por escrito. Quando a resposta é uma opção, a peça é [[escolha-em-lista]].

**Pé:** Pronto. Campo livre `@wecareu/input-text` **0.2.7**. Máscara `@wecareu/input-masked` **0.2.4**. Os dois têm demonstração e teste. A máscara veste o mesmo campo livre.

## O que a pessoa vê

Borda arredondada na cor da marca, texto no centro. Cores e letra vêm de [[identidade-visual]]. A peça não desenha título acima. A ajuda fica dentro, enquanto está vazio. O erro balança uma vez, a borda vai para a cor de erro e, se houver frase, ela aparece embaixo.

O campo livre troca o teclado: texto, e-mail, senha, número, endereço web e telefone. E-mail, endereço e telefone checam a forma ao sair. Senha nasce escondida; o olho de mostrar e esconder está na demonstração, não nasce sozinho. Desabilitado e somente leitura ficam apagados e não aceitam digitação. Ícone à esquerda e à direita vêm de [[vocabulario-visual]].

O telefone deste campo, em português, guarda o +55. Não é a máscara nacional da outra peça.

## Máscaras

Enquanto a pessoa digita, pontos, traços, barras e espaços entram sozinhos. O que a tela guarda é o miolo, sem esses sinais. Presets: **CPF, CNPJ, CEP, telefone, cartão e data**. Há máscara livre; a demonstração usa uma placa. Se formato livre e preset vierem juntos, vale o formato livre.

A máscara não confere se o CPF é verdadeiro, se o CNPJ existe, se o CEP é de uma rua, se o cartão é de uma bandeira, nem se o dia existe. A de cartão só formata. Data mascarada é digitar o dia. Escolher no calendário é [[datas]].

Ter máscara de CPF não significa que o cadastro pede CPF. Ter cartão não significa que o app cobra.

Ver [[kit-visual]].
