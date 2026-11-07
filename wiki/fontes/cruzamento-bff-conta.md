---
tipo: fonte
arquivo: "ingeridos/Cruzamento - BFF conta.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 que cruza ui_client, ui_worker e service_api; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cruzamento — conta no backend"]
---

# Cruzamento — conta no backend

A porta é [[cruzamento-bff-como-ler]].

A conta é o único bloco em que os dois apps já pedem o backend de apoio de ponta a ponta. O caminho publicado está em [[bff-entrar-sair-e-senha]] e em [[bff-cadastro]]. A tela está em [[entrar-senha-e-biometria]], [[entrar-senha-e-biometria-do-artista]], [[criar-conta]] e [[cadastro-do-artista]].

Os dois apps pedem as mesmas ações de conta. O que muda é o que a tela faz com a resposta.

## Entrar

A pessoa já tem conta e quer as abas. O lugar é **Já tenho uma conta**, nos dois apps. Se a biometria já foi aceita, o aparelho confirma a digital ou o rosto e o app segue para a mesma entrada. O backend não distingue biometria de senha. Ele recebe o pedido de entrar.

Os dois pedem a porta de entrar de [[bff-entrar-sair-e-senha]]. Essa porta está no ar e não exige sessão prévia. Não separa cliente de profissional.

O app guarda a sessão no aparelho e marca a pessoa como dentro. No ato de entrar, o nome, a foto e a nota ainda não preenchem o Início. Isso é uma segunda leitura, em [[cruzamento-bff-o-que-a-tela-le]].

## Sair

O lugar é **Sair da sua conta**, no perfil dos dois. A confirmação é **Sair da WeCareU**.

Os dois pedem sair, a porta marcada como pessoa logada em [[bff-entrar-sair-e-senha]]. Se esse pedido falha, a tela ainda encerra a sessão neste aparelho. As notas de perfil já dizem isso. A biometria ligada neste aparelho deixa de valer.

Se a marca de pessoa logada vale na entrada do backend fica em aberto, em [[bff-o-que-e-este-backend]] e na lacuna de sessão de [[contradicoes-e-lacunas]].

## A sessão ao reabrir

A abertura dos dois apps, antes das abas, pergunta se a sessão ainda vale para não pedir e-mail e senha de novo.

O caminho que o app usa não é o que este retrato publica. A porta publicada é saber se a sessão ainda vale, GET `Valid`, em [[bff-entrar-sair-e-senha]]. O app pede outro caminho, `login/user/valid`. Este retrato não publica esse caminho.

Se a resposta traz sessão nova, o app troca a que estava guardada. Se não vale, a pessoa cai na abertura e a biometria salva é desligada, como nas notas de entrar.

## Senha

**Esqueci minha senha** na entrada dos dois, e **Alterar Senha** no perfil dos dois. As duas telas fazem o mesmo percurso no backend: pedir o código, validar o código, gravar a senha nova. Quem já entrou não informa a senha atual. Informa o e-mail, o código e a senha nova. Ver [[meu-perfil]] e [[perfil-do-artista]].

Três portas no ar, sem sessão prévia, em [[bff-entrar-sair-e-senha]]: pedir a troca a partir do e-mail (o backend não envia o e-mail; o envio não é ação daqui; ver [[bff-preparado-e-ainda-nao-oferecido]]), validar e-mail e código, e trocar a senha. O app do cliente e o do artista pedem as três. A porta de recusar a troca existe no backend e nenhum dos dois apps a pede.

Há, nos dois apps, um pedido preparado de trocar a senha informando a senha antiga. Nenhuma tela deste retrato o dispara. A tela que existe usa o código. Este bruto não nomeia o caminho desse pedido preparado.

## Abrir conta

[[criar-conta]] tem três etapas. [[cadastro-do-artista]] tem cinco. Não são a mesma tela. Ver [[cruzamento-criar-conta]].

Os dois pedem abrir conta de cliente, POST `User`, em [[bff-cadastro]]. O app do artista não pede abrir conta de profissional, POST `Artist`.

Em [[bff-cliente-e-profissional]], só o cadastro de profissional recebe a empresa e o aplicativo aos quais este backend está amarrado. O cadastro de cliente não recebe esse vínculo. Como o app do artista entra pela porta de cliente, esse vínculo não entra no pedido.

O miúdo do formulário viaja junto: e-mail, senha, CPF, nome, nascimento, gênero, nome preferido, foto e um endereço. A lista de campos que o backend exige não está no repositório do backend. O que a tela pede está nas notas de cadastro.

No cliente, a conta é criada, a sessão fica guardada e a pessoa entra no [[inicio]] na hora. No artista, a conta é criada e a sessão fica guardada, mas esta tela não marca a pessoa como dentro. As abas ficam para a próxima abertura, se a sessão for aceita. Ver [[cadastro-do-artista]].

## Conferências que a tela não dispara

O backend publica, sem sessão, ver se o e-mail já existe. Nenhum dos dois apps pede isso neste retrato.

O backend publica conferir CPF e, se vier, CNPJ. O CPF vai no cabeçalho. Os dois apps guardam um pedido de conferir CPF, e nenhuma tela o dispara. Esse pedido ainda manda o CPF na pergunta, não no cabeçalho. A frase "Você já tem uma conta! Por favor, faça login." existe nos textos dos dois cadastros e a tela não a usa sozinha.

## Pedido do app sem porta neste retrato

Invalidar todas as sessões está preparado nos dois apps. Nenhuma tela o chama. O caminho que ele usaria, `auth/revoke-all-sessions`, não aparece nas portas de [[bff-entrar-sair-e-senha]] nem no restante deste retrato do backend.

Ver [[fluxo-de-entrada]], [[cadastro]], [[contradicoes-e-lacunas]].
