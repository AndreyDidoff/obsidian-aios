---
tipo: extração
tema: Endereços
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: parcial — gerir no perfil é um aviso; a tela solta ninguém abre
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Endereços

Volta para o [[Mapa do app do cliente]].

Esta nota é o que o app faz com endereço **fora** de dois fluxos já escritos. O endereço de quem visita sem conta, no carrossel, está em [[Primeira entrada]]. O endereço que entra junto com a conta nova está em [[Criar conta]]. Aqui ficam duas coisas diferentes: gerir endereços depois de entrar, e uma tela solta que pergunta "Qual é seu endereço?" e que nenhum lugar do app abre.

**Pé:** parcial. No perfil a entrada existe e a tela só avisa que a gestão vem depois. Não há lista, nem adicionar, editar ou apagar. A tela solta tem CEP e localização, e não entra em caminho nenhum.

## Gerir depois de entrar

Em [[Meu perfil]], a seção **Endereços** tem um item: **Gerenciar Endereços**. O texto de apoio promete "Adicionar, editar ou remover endereços". É o único lugar do app que abre esta tela. Ela vem por cima do perfil, com botão de fechar.

O que a pessoa vê:

- Título: **Gerenciar Endereços.**
- Frase: "Em breve você poderá gerenciar seus endereços aqui."

Não há lista de endereços. Não há botão de adicionar, editar ou apagar. Não há apelido, Casa ou Trabalho, CEP nem **Usar minha localização**. A tela não lê a conta e não envia nada ao serviço.

## A tela solta

A pergunta na tela é **Qual é seu endereço?** Em volta: o logo, o mesmo formulário de CEP e de localização da visita sem conta, e o botão **Entrar ou Cadastrar**.

Esse botão abre o login, descrito em [[Entrar, senha e biometria]]. Não abre o cadastro direto, não abre a lista de artistas e não conclui um endereço.

Diferença para a [[Primeira entrada]]: lá o endereço é o terceiro passo do carrossel. O título é "Preencha seu endereço", e **Finalizar!** exige o número antes de entrar como visitante na lista de [[Encontrar profissionais]]. Esta tela não é esse passo. Não tem **Finalizar!**. Não foi feita para ser aberta por aquele carrossel.

Ela está registrada para quem ainda não entrou. Nenhum botão, menu ou passo a abre. A abertura estava prevista com uma escolha entre duas opções, e a tela ignora as duas. [VERIFICAR] o que cada opção deveria mudar na experiência.

Se alguém chegasse nela, os campos seriam os do carrossel: **Usar minha localização**, CEP, rua que não se digita, número e complemento. O comportamento de cada campo está em [[Primeira entrada]]. O destino dos dados é outro ponto: a tela grava no mesmo rascunho local da visita, não no rascunho do [[Criar conta]], e não manda o endereço ao serviço da WeCareU.

O aviso "Campos obrigatórios" nesta tela não tem um botão que o dispare. Ele só aparece se o carrossel já tiver marcado a falta do número. Digitar o número apaga o aviso.

## O que um endereço carrega

Regras previstas para um endereço, no que o app exige:

- Rua, cidade, estado e número são obrigatórios.
- O CEP precisa ter oito dígitos. Fora isso, conta como inválido.
- Complemento, bairro, referência e apelido são opcionais. O exemplo de apelido, no cadastro, é "Apartamento, Empresa xxx". Apelido não aparece na gestão nem na tela solta.
- O tipo só aceita dois valores. Os nomes no app são **Casa** e **Trabalho**. Casa é o padrão quando uma busca preenche o endereço sozinha. Quem escolhe o tipo é o [[Criar conta]]. A gestão e a tela solta não perguntam.
- País. Quando a tela solta grava o rascunho, o país fica Brasil.
- O ponto no mapa pode faltar na regra. A busca por CEP e o GPS preenchem esse ponto quando a busca dá certo.

A tela de gerenciar não aplica nenhuma dessas regras: não há formulário. A tela solta também não passa por essa lista. Ela busca o CEP com oito dígitos e grava o rascunho.

## O que vai para o serviço e o que fica no aparelho

**No serviço da WeCareU.** O único envio de um endereço completo é o da conta nova, em [[Criar conta]]: um endereço, com rua, número, CEP, cidade, estado, bairro, complemento, referência, apelido, tipo, país e o ponto no mapa. Neste app não há ação de trazer esse endereço de volta para uma lista, nem de criar um segundo, editar ou apagar depois de entrar.

Depois do login, o app guarda o que o serviço devolveu sobre endereços, e a tela de gerenciar não mostra essa lista. Nenhuma tela desenha rua, CEP, apelido ou tipo vindos da conta. [VERIFICAR] se o que chega no login já é só um código ou se traz o endereço inteiro.

**Só no aparelho.** CEP, rua, número, complemento e o ponto preenchidos na tela solta ficam no rascunho da visita, o mesmo do carrossel. Apelido, referência e tipo que esse rascunho já tinha são mantidos. Se não houver tipo, fica Casa. Isso não cria nem atualiza a conta.

A busca de CEP consulta um mapa de fora. Devolve rua, bairro, cidade, estado, CEP e o ponto. Se a primeira tentativa falha, tenta de novo com o CEP no formato 00000-000. Se as duas falham, o campo de CEP fica em erro, sem uma frase dizendo o motivo. Isso não grava na WeCareU.

**Usar minha localização** pede o ponto ao aparelho e usa o endereço que o próprio aparelho devolve: rua, cidade, estado e CEP. Número e complemento já digitados são mantidos. Se o aparelho não devolver um endereço, o carregamento some e o formulário fica como estava, sem frase de erro. Existe outra busca, por coordenadas, nesse mapa de fora, e nenhuma tela a usa.

Há um espaço previsto no aparelho para a lista de endereços da conta. Nada grava nesse espaço.

## O que os endereços ainda não fazem

- Não listam os endereços de quem já entrou.
- Não adicionam, editam nem apagam um endereço depois da conta criada. O texto do perfil promete isso, e a tela diz que vem depois.
- Não deixam escolher apelido, Casa ou Trabalho fora do [[Criar conta]].
- Não mostram o endereço que o serviço devolveu no login.
- Não abrem a tela "Qual é seu endereço?".
- Não levam essa tela à lista de artistas nem ao cadastro. O botão vai para o login.
- Não usam a busca por coordenadas que já está pronta.
- Não dizem para que serviam as duas opções previstas na abertura da tela solta. [VERIFICAR]

O que o app cita em outras áreas e não entrega está em [[O que ainda não está no app]].
