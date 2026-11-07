> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cadastro

## O que isso é para o app

Isto é o que o aplicativo pede ao backend de apoio para abrir conta e para conferir e-mail, CPF e CNPJ. A tela fica no aplicativo. Aqui está o caminho `beautiful/api/Register`.

No código, cliente se chama User e profissional se chama Artist. Nesta nota: cliente e profissional (Artista).

## O que a pessoa já consegue fazer por este backend

Nenhum destes pedidos exige sessão.

- **Abrir conta de cliente.** POST `User`.
- **Abrir conta de profissional (Artista).** POST `Artist`. Este caminho recebe a empresa e o aplicativo configurados neste backend.
- **Ver se o e-mail já existe.** GET `{email}`.
- **Conferir CPF e, se houver, CNPJ.** GET `docs`. O CPF é obrigatório e vai no cabeçalho. O CNPJ é opcional e, quando a pessoa informa, também vai no cabeçalho.

O miúdo do formulário não está neste repositório.

## Quem pode

O aplicativo pede os quatro sem sessão já aberta. Dá para abrir conta de cliente e conta de profissional (Artista).

## Em que pé está

**No ar.** O serviço de usuário está ligado neste backend, e os quatro pedidos acima estão publicados para o aplicativo.

Escala desta base: No ar / Porta sem ligação / Só preparado / Fora de uso.

## O que esta nota não cobre

- Etapas de tela, sexo, chatbot e a lista de campos do formulário.
- Entrar, sair e senha. Ver [[03-entrar-sair-e-senha]].
- Documentos para validação fora desta conferência de CPF e CNPJ. Ver [[12-documentos-para-validacao]].

## Ligações

- [[01-o-que-e-este-backend]]
- [[02-cliente-e-profissional]]
- [[03-entrar-sair-e-senha]]
- [[12-documentos-para-validacao]]

## Incertezas

- A lista de campos do cadastro de cliente e do cadastro de profissional (Artista) não está neste repositório. Os dois pedidos seguem para o serviço de usuário.
- O que a conferência de CPF e de CNPJ decide (formato, duplicidade ou outra regra) não está neste repositório. Dá para afirmar que o CPF é obrigatório, que o CNPJ é opcional e que os dois viajam no cabeçalho.
- O pedido de e-mail devolve um sim ou não. Qual dos dois valores significa “já existe” não está neste repositório: essa leitura mora no serviço de usuário.
