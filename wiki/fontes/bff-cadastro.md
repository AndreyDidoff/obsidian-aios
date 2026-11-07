---
tipo: fonte
arquivo: "ingeridos/04-cadastro.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cadastro"]
---

# Cadastro

O que este backend publica para abrir conta e para conferir e-mail, CPF e CNPJ. Caminho `beautiful/api/Register`. No código, cliente se chama User e profissional se chama Artist. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Etapas, sexo, chatbot e a lista de campos ficam em [[cadastro]] e nas decisões. Esta nota não descreve a tela do app.

## O que está publicado

Nenhum destes pedidos exige sessão. O serviço de usuário está ligado.

- **Abrir conta de cliente.** POST `User`.
- **Abrir conta de profissional (Artista).** POST `Artist`. Este caminho recebe a empresa e o aplicativo (CompanyData). Ver [[bff-cliente-e-profissional]].
- **Ver se o e-mail já existe.** GET `{email}`.
- **Conferir CPF e, se houver, CNPJ.** GET `docs`. O CPF é obrigatório e vai no cabeçalho. O CNPJ é opcional e, quando informado, também vai no cabeçalho.

O miúdo do formulário não está neste repositório.

## Quem pode

Os quatro pedidos são publicados sem sessão já aberta. Há abertura de conta de cliente e de profissional (Artista).

## Em que pé está

No ar. O serviço de usuário está ligado, e os quatro pedidos estão publicados.

## O que esta nota não cobre

Etapas de tela, sexo, chatbot e a lista de campos do formulário. O alvo de duas etapas, só sexo e chatbot permanece em [[cadastro]]. Os itens 14 e 25 de [[contradicoes-e-lacunas]] continuam encaminhados: a tela de 21/10 e a decisão seguem o que já está escrito. Esta nota publica o que o backend oferece.

Entrar, sair e senha: [[bff-entrar-sair-e-senha]]. Documentos para validação fora desta conferência de CPF e CNPJ estão em [[bff-documentos-para-validacao]].

## Incertezas

A lista de campos do cadastro de cliente e do cadastro de profissional não está neste repositório. Os dois pedidos seguem para o serviço de usuário.

O que a conferência de CPF e de CNPJ decide (formato, duplicidade ou outra regra) não está neste repositório. Dá para afirmar que o CPF é obrigatório, que o CNPJ é opcional e que os dois viajam no cabeçalho. CNPJ opcional nesta conferência não é decisão de produto.

O pedido de e-mail devolve um sim ou não. Qual dos dois valores significa "já existe" não está neste repositório: essa leitura mora no serviço de usuário.

Ver [[beautiful-api]], [[cadastro]].

O board pede cadastro de cliente e de artista no nome WeCareU.API, tarefas 358 e 361 ([[board-conta-e-acesso]]). A 358, estado Completed no board, pede endpoint com CPF, foto ou foto padrão no AppSetting, sem autenticação padrão, e um hash das chaves de sistema e de empresa. A 361, estado New, pede cadastro de artista, com CNPJ e grupo quando for empresa, vínculo pelo CPF do criador e ao menos um artista. Completed no board não diz que esse pedido está nesta porta. Esta porta já publica POST `User` e POST `Artist`. O pedido não prova que o app do artista usa POST `Artist`. WeCareU.API, no título, é o nome que o board usa, não a arquitetura confirmada deste repositório.
