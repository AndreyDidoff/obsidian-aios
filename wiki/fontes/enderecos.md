---
tipo: fonte
arquivo: "ingeridos/Endereços.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_client; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Endereços"]
---

# Endereços

Volta para [[mapa-do-app-do-cliente]].

O endereço de quem visita sem conta está em [[primeira-entrada]]. O endereço que entra com a conta nova está em [[criar-conta]]. Aqui ficam a gestão depois de entrar e uma tela solta que nenhum lugar abre.

**Pé:** parcial. Gerir no perfil é um aviso. A tela solta ninguém abre.

## Gerir depois de entrar

Em [[meu-perfil]], **Gerenciar Endereços**, com o apoio "Adicionar, editar ou remover endereços". É o único lugar que abre esta tela.

Título: **Gerenciar Endereços.** Frase: "Em breve você poderá gerenciar seus endereços aqui." Não há lista. Não há adicionar, editar ou apagar. Não há apelido, Casa ou Trabalho, CEP nem **Usar minha localização**. A tela não lê a conta e não envia nada ao serviço.

O único envio de um endereço completo, neste app, é o da conta nova. Não há ação de trazer esse endereço de volta para uma lista, nem de criar um segundo, editar ou apagar depois de entrar. Depois do login, o app guarda o que o serviço devolveu sobre endereços, e esta tela não mostra essa lista. Nenhuma tela desenha rua, CEP, apelido ou tipo vindos da conta. A extração marca [VERIFICAR] se o que chega no login já é só um código ou se traz o endereço inteiro.

## A tela solta

A pergunta é **Qual é seu endereço?** Em volta, o logo, o mesmo formulário de CEP e de localização da visita, e o botão **Entrar ou Cadastrar**. Esse botão abre o login. ([[entrar-senha-e-biometria]]) Não abre o cadastro direto, não abre a lista e não conclui um endereço.

Não é o terceiro passo do carrossel. Não tem **Finalizar!**. Está registrada para quem ainda não entrou. Nenhum botão, menu ou passo a abre. A abertura estava prevista com uma escolha entre duas opções, e a tela ignora as duas. A extração marca [VERIFICAR] o que cada opção deveria mudar.

Se alguém chegasse nela, os campos seriam os do carrossel. Ela grava no mesmo rascunho local da visita, não no rascunho de [[criar-conta]], e não manda o endereço ao serviço. O aviso "Campos obrigatórios" nesta tela não tem um botão que o dispare.

CEP e localização funcionam no cadastro e na visita. A busca de CEP consulta um mapa de fora. Se as duas tentativas falham, o campo fica em erro, sem uma frase dizendo o motivo. **Usar minha localização** pede o ponto ao aparelho. Existe outra busca, por coordenadas, e nenhuma tela a usa. Há um espaço previsto no aparelho para a lista de endereços da conta. Nada grava nesse espaço.

Quem escolhe Casa ou Trabalho é o [[criar-conta]]. A gestão e a tela solta não perguntam.

## O que o board pede em 21/10

A listagem pede carregamento de artistas por endereço, sem cadastro (história 145), e um campo de troca de endereço no topo da listagem (tarefa 451, sem descrição) ([[board-listagem]]). O retrato acima permanece. Isto não decide quando o endereço aparece para o Artista. O item 16 de [[contradicoes-e-lacunas]] segue aberto.
