---
tipo: cruzamento
tema: Conta no backend
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza os dois apps com o backend de apoio. Descreve onde a tela lê ou grava um dado, por que a pessoa precisa dele, e se essa porta existe no backend. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — conta no backend

A conta é o único bloco em que os dois apps já pedem o backend de apoio de ponta a ponta. O caminho publicado está em [[03-entrar-sair-e-senha]] e em [[04-cadastro]]. A tela está em [[Entrar, senha e biometria]], [[Entrar, senha e biometria do artista]], [[Criar conta]] e [[Cadastro do artista]].

Os dois apps pedem as mesmas ações de conta. O que muda é o que a tela faz com a resposta.

## Entrar

**Por que.** A pessoa já tem conta e quer as abas.

**Onde.** **Já tenho uma conta**, nos dois apps. Se a biometria já foi aceita, o aparelho confirma a digital ou o rosto e o app segue para a mesma entrada. O backend não distingue biometria de senha. Ele recebe o pedido de entrar.

**Como.** Os dois pedem a porta de entrar de [[03-entrar-sair-e-senha]]. Essa porta está no ar e não exige sessão prévia. Não separa cliente de profissional.

**O que volta, e o que a tela faz.** O app guarda a sessão no aparelho e marca a pessoa como dentro. No ato de entrar, o nome, a foto e a nota ainda não preenchem o Início. Isso é uma segunda leitura, em [[Cruzamento - BFF o que a tela lê]].

## Sair

**Por que.** Encerrar a conta neste aparelho.

**Onde.** **Sair da sua conta**, no perfil dos dois. A confirmação é **Sair da WeCareU**.

**Como.** Os dois pedem sair, a porta marcada como pessoa logada em [[03-entrar-sair-e-senha]]. Se esse pedido falha, a tela ainda encerra a sessão neste aparelho. As notas de perfil já dizem isso. A biometria ligada neste aparelho deixa de valer.

Se a marca de pessoa logada vale na entrada do backend fica em aberto, em [[01-o-que-e-este-backend]].

## A sessão ao reabrir

**Por que.** Não pedir e-mail e senha de novo se a sessão ainda vale.

**Onde.** A abertura dos dois apps, antes das abas.

**Como.** O app pergunta se a sessão ainda vale. O caminho que ele usa não é o que este retrato publica. A porta publicada é saber se a sessão ainda vale, GET `Valid`, em [[03-entrar-sair-e-senha]]. O app pede outro caminho, `login/user/valid`.

Se a resposta traz sessão nova, o app troca a que estava guardada. Se não vale, a pessoa cai na abertura e a biometria salva é desligada, como nas notas de entrar.

## Senha

**Por que.** A pessoa esqueceu a senha, ou já está dentro e quer outra.

**Onde.** **Esqueci minha senha** na entrada dos dois. E **Alterar Senha** no perfil dos dois. As duas telas fazem o mesmo percurso no backend: pedir o código, validar o código, gravar a senha nova. Quem já entrou não informa a senha atual. Informa o e-mail, o código e a senha nova. Ver [[Meu perfil]] e [[Perfil do artista]].

**Como.** Três portas no ar, sem sessão prévia, em [[03-entrar-sair-e-senha]]:

- Pedir a troca a partir do e-mail. O backend não envia o e-mail. O envio não é ação daqui. Ver [[14-preparado-e-ainda-nao-oferecido]].
- Validar e-mail e código.
- Trocar a senha.

O app do cliente e o do artista pedem as três. A porta de recusar a troca existe no backend e nenhum dos dois apps a pede.

Há, nos dois apps, um pedido preparado de trocar a senha informando a senha antiga. Nenhuma tela deste retrato o dispara. A tela que existe usa o código.

## Abrir conta

**Por que.** A pessoa ainda não tem conta.

**Onde.** [[Criar conta]], três etapas, e [[Cadastro do artista]], cinco etapas. Não são a mesma tela. Ver [[Cruzamento - criar conta]].

**Como.** Os dois pedem abrir conta de cliente, POST `User`, em [[04-cadastro]]. O app do artista não pede abrir conta de profissional, POST `Artist`.

Isso muda o que o backend faz com o papel. Em [[02-cliente-e-profissional]], só o cadastro de profissional recebe a empresa e o aplicativo aos quais este backend está amarrado. O cadastro de cliente não recebe esse vínculo. Como o app do artista entra pela porta de cliente, esse vínculo não entra no pedido.

O miúdo do formulário viaja junto: e-mail, senha, CPF, nome, nascimento, gênero, nome preferido, foto e um endereço. A lista de campos que o backend exige não está no repositório do backend. O que a tela pede está nas notas de cadastro.

**O que a tela faz com a resposta.**

- No cliente, a conta é criada, a sessão fica guardada e a pessoa entra no [[Início]] na hora.
- No artista, a conta é criada e a sessão fica guardada, mas esta tela não marca a pessoa como dentro. As abas ficam para a próxima abertura, se a sessão for aceita. Ver [[Cadastro do artista]].

## Conferências que a tela não dispara

O backend publica, sem sessão, ver se o e-mail já existe. Nenhum dos dois apps pede isso neste retrato.

O backend publica conferir CPF e, se vier, CNPJ. O CPF vai no cabeçalho. Os dois apps guardam um pedido de conferir CPF, e nenhuma tela o dispara. Esse pedido ainda manda o CPF na pergunta, não no cabeçalho. A frase "Você já tem uma conta! Por favor, faça login." existe nos textos dos dois cadastros e a tela não a usa sozinha.

## Pedido do app sem porta neste retrato

Invalidar todas as sessões está preparado nos dois apps. Nenhuma tela o chama. O caminho que ele usaria, `auth/revoke-all-sessions`, não aparece nas portas de [[03-entrar-sair-e-senha]] nem no restante deste retrato do backend.

## Notas

- [[01-o-que-e-este-backend]]
- [[02-cliente-e-profissional]]
- [[03-entrar-sair-e-senha]]
- [[04-cadastro]]
- [[14-preparado-e-ainda-nao-oferecido]]
- [[Criar conta]]
- [[Cadastro do artista]]
- [[Entrar, senha e biometria]]
- [[Entrar, senha e biometria do artista]]
- [[Meu perfil]]
- [[Perfil do artista]]
- [[Cruzamento - criar conta]]
- [[Cruzamento - entrar senha e biometria]]
