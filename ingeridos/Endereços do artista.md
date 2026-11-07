---
tipo: extração
tema: Endereços do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: Parcial. O cadastro grava um endereço; Gerenciar Endereços é casca
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Endereços do artista

Volta para [[Mapa do app do artista]]. O único lugar em que a pessoa preenche um endereço é o [[Cadastro do artista]]. No [[Perfil do artista]], a gestão ainda não existe. O cartão de endereço do [[Início do artista]] é outro assunto.

**Pé:** parcial. O cadastro pede um endereço e pode gravá-lo na conta. A tela Gerenciar Endereços é casca: só anuncia que a função vem depois. Não há lista, não há incluir, editar nem apagar.

## O endereço pedido no cadastro

São duas etapas do [[Cadastro do artista]], a terceira e a quarta. O formulário, as máscaras e o que acontece quando o CEP falha estão lá. Aqui fica a lista do que a pessoa encontra.

Na terceira etapa:

- **País.** Lista de países, Brasil já escolhido.
- **CEP.** Oito dígitos, máscara `00000-000`.
- **Número.** A pessoa digita.
- **Rua e cidade.** Travados. Só aparecem se a busca do CEP devolver alguma coisa. O bairro, quando vem, aparece junto da rua. A pessoa não digita rua, bairro, cidade nem estado.

A busca usa o CEP junto com o número, e só quando o número muda. Não há campo para corrigir à mão. Se o CEP não existe, a tela não diz nada e deixa seguir. A conta pode sair sem rua, sem cidade e até sem número. As frases "Número é obrigatório", "Rua é obrigatória", "Cidade é obrigatória" e "Estado é obrigatório" existem nos textos e não seguram esses campos vazios. CEP fora de oito dígitos mostra "CEP inválido" e aí sim não avança.

Na quarta etapa, um bloco repete o que foi achado e a pessoa completa, tudo opcional:

- **Complemento.** Convite: "Digite o complemento (opcional)".
- **Referência.** Convite: "Digite uma referência. Ex: Casa verde".
- **Tipo de endereço.** Casa ou Trabalho. Casa já vem escolhida.
- **Apelido.** Convite: "Ex: Apartamento, Empresa xxx".

O que a conta guarda, quando a busca funciona: país, CEP, rua, bairro, cidade, estado, número, complemento, referência, apelido, tipo (casa ou trabalho) e a posição do ponto. Sem busca bem-sucedida, rua, bairro, cidade, estado e a posição ficam vazios. Essa posição não aparece para a pessoa. Não há mapa neste fluxo.

Esse rascunho fica no aparelho se a pessoa sair no meio do cadastro. A foto e a senha não ficam; o endereço fica. Ver [[Cadastro do artista]].

## Gerenciar Endereços

No [[Perfil do artista]], a seção **Endereços** tem o item **Gerenciar Endereços**, com o subtítulo "Adicionar, editar ou remover endereços".

A tela que abre não faz isso. Título: **Gerenciar Endereços.** Frase no centro: "Em breve você poderá gerenciar seus endereços aqui." Fechar volta ao perfil.

Não lista o endereço do cadastro. Não deixa acrescentar outro, editar, apagar, escolher casa ou trabalho, nem definir um principal.

## O cartão do início

O [[Início do artista]] mostra um cartão com o rótulo **Endereço:** e o texto fixo "Rua B..., 504" e "Imirim - São Paulo, SP - BR", ao lado de um exemplo de agendamento. Aquele cartão não lê o endereço da conta e não abre esta gestão. O botão de baixo é **Vamos agendar?** e também não leva a lugar nenhum.

## Busca por CEP e por GPS

Busca por CEP existe, e só dentro do [[Cadastro do artista]], do jeito descrito acima.

Não existe busca de endereço por GPS. Nem o cadastro nem Gerenciar Endereços pedem a posição para preencher rua ou CEP. A [[Abertura do artista]] pede permissão de localização para falar de clientes próximos. Isso não escreve endereço nenhum.

## O que ainda não dá para fazer

- Ver, editar ou apagar o endereço depois do cadastro.
- Ter mais de um endereço.
- Completar a rua quando o CEP não é encontrado.
- Achar o endereço pela localização do aparelho.

Dados pessoais seguem o mesmo aviso de "em breve". Ver [[Perfil do artista]] e [[O que ainda não está no app do artista]].
