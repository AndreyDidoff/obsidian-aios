---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-final]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[lyraui-03-estado-atual]]", "[[brainstorming-wecareu]]", "[[politica-de-privacidade]]", "[[termos-de-uso-do-app]]", "[[criar-conta]]", "[[cadastro-do-artista]]", "[[bff-cadastro]]", "[[bff-telefones]]", "[[bff-cliente-e-profissional]]", "[[cruzamento-bff-como-ler]]", "[[cruzamento-bff-conta]]", "[[board-conta-e-acesso]]", "[[core-01-conta]]", "[[core-09-telefones]]", "[[core-04-empresa-e-colaboradores]]"]
---

# Cadastro

## Alvo do cliente

O cadastro do cliente é um chatbot. Pede CPF, nome, celular sem SMS, sexo em quatro botões (Masculino, Feminino, Não binário, Prefiro não dizer), nome social opcional, nascimento com mínimo de 18 anos, foto, endereço, e-mail e senha, e o aceite dos termos. A chave de unicidade é CPF e e-mail. O celular pode repetir. Quem tem menos de 18 anos é bloqueado e os dados não são gravados. A foto pode ser adiada no cadastro, mas sem foto não há agendamento. ([[mvp-alteracoes-pos-congelamento]], [[mvp-funcoes-e-telas]])

O cliente logado salva todo endereço novo, com nome. Não existe endereço principal: vale o último escolhido. O deslogado começa com o endereço do welcome. Na listagem, a troca do deslogado não salva. ([[mvp-funcoes-e-telas]])

Gênero e orientação sexual continuam fora. O SMS do artista e o detalhe do cadastro do artista não estão neste alvo. ([[mvp-funcoes-e-telas]])

O retrato de 21/10, abaixo, é estado atual. Não é a regra.

## Campos de usuário

Lista original ([[brainstorming-wecareu]]): nome, apelido, CPF, data de nascimento, sexo, gênero, orientação sexual, e-mail, senha, descrição.

**No [[mvp]], decisão de outubro, substituída no cliente:** o conjunto de 03/11 pedia telefone verificado por SMS. A decisão de outubro pedia apenas sexo, sem as quatro opções. O alvo do cliente, acima, prevalece. ([[mvp-final]], [[decisoes-2026-10-20]], [[mvp-alteracoes-pos-congelamento]])

[[lyraui-03-estado-atual]] afirma que gênero, orientação sexual e nome social **já são coletados em produção**. Se o código estiver assim, a decisão do MVP é uma mudança a fazer antes do lançamento, não uma descrição do que o app faz hoje. Ver [[contradicoes-e-lacunas]].

## Endereços ([[brainstorming-wecareu]])

ID, nome, rua, complemento, ponto de referência, latitude, longitude. Um usuário pode ter vários (ex.: casa e trabalho).

## Como funciona

- **Duas etapas, já no MVP** ([[decisoes-2026-10-20]]):
  1. **Cadastro inicial:** só o mínimo necessário, para não ficar extenso.
  2. **Finalização do cadastro:** dados complementares, entre eles o **telefone**. O app tem chamadas convidando o usuário a completar o cadastro.
- No app do cliente, a listagem vem **antes** do cadastro: a pessoa se cadastra no momento de agendar, não na porta do app. ([[decisoes-2026-10-21]])
- Cada etapa é um fluxo do chatbot. ([[decisoes-2026-10-20]]) O [[brainstorming-wecareu]] tratava o bot de cadastro como "futura versão".
- O bot usa escolhas ou frases simples: texto livre só para dados como o nome completo; campos como sexo são opções. ([[decisoes-2026-10-20]])
- Somente maiores de 18 anos, ou menores com autorização do responsável. ([[termos-de-uso-do-app]])
- Futuro: dicas e barra de progresso para o Artista completar o perfil. ([[brainstorming-wecareu]])

## Revisão da Política de Privacidade

A [[politica-de-privacidade]] será revisada antes do lançamento do MVP ([[decisoes-2026-10-20]]). Com o cadastro reduzido, a revisão precisa cobrir:

- CPF, data de nascimento e sexo, que hoje não aparecem na política.
- Telefone: no cliente é coletado no chatbot, sem SMS. A política ainda não lista esse campo.
- O cadastro do cliente não é mais em duas etapas. A política antiga descrevia outra coleta.

Os campos do cliente estão fechados na seção "Alvo do cliente". A primeira etapa de outubro não vale mais nesse app. No código de 21/10, a etapa 1 pede país (só Brasil), e-mail e senha. ([[criar-conta]]) No artista, a primeira etapa do retrato é dados pessoais. ([[cadastro-do-artista]]) O detalhe de tela do artista não chegou.

O risco maior (orientação sexual como dado sensível) deixou de existir no MVP. Ver [[protecao-de-dados]].

## O que o app do cliente faz em 21/10

O alvo do cliente está na seção "Alvo do cliente". Não são mais duas etapas, nem telefone verificado, nem sexo sem as quatro opções.

O código do cliente, neste retrato, é outra coisa. São três etapas de formulário: Acesso, Dados pessoais e Endereço. Coleta gênero, em cinco opções (Masculino, Feminino, Outro, Não-binário, Prefiro não dizer). Não mostra sexo separado, nem orientação sexual, nem telefone. Não é chatbot. ([[criar-conta]])

Isso não apaga o alvo. É mudança antes do lançamento, e a decisão de produto permanece. Ver [[contradicoes-e-lacunas]].

## O que o app do artista faz em 21/10

O detalhe de tela do artista não chegou. O retrato abaixo não é o alvo do cliente.

O código do artista, neste retrato, é outra coisa. São cinco etapas de formulário: dados pessoais, foto, endereço, confirmação do endereço e acesso. A primeira é dados pessoais. Coleta gênero, nas cinco opções (Masculino, Feminino, Outro, Não-binário, Prefiro não dizer). Sem escolha, a frase de erro sai em inglês. Não mostra sexo separado, nem orientação sexual, nem telefone. Não é chatbot. ([[cadastro-do-artista]])

O cliente, neste retrato, continua com três etapas de formulário. O alvo do cliente é o chatbot da seção acima. Ver [[contradicoes-e-lacunas]].

## O que o backend publica

O backend publica duas portas, no caminho `beautiful/api/Register`, sem sessão: abrir conta de cliente (POST `User`) e abrir conta de profissional (POST `Artist`). O caminho do profissional recebe a empresa e o aplicativo. Também publica a conferência de e-mail (GET `{email}`) e a de CPF e, se houver, CNPJ (GET `docs`: CPF obrigatório no cabeçalho; CNPJ opcional, no cabeçalho quando informado). Os campos do formulário não estão neste repositório. A tela de 21/10 e o alvo do MVP continuam o que esta página já diz. ([[bff-cadastro]])

O backend publica a gestão de telefone da sessão, no caminho `beautiful/api/Phone`. Isso não é o celular do cadastro do cliente, que é coletado sem SMS. ([[bff-telefones]], [[mvp-alteracoes-pos-congelamento]])

O serviço de telefone do núcleo também não é o celular do cadastro, e os apps de 21/10 seguem sem tela de gerir telefones em uso. ([[core-09-telefones]])

## O que o cruzamento de conta acrescenta

Os dois apps pedem abrir conta de cliente, POST `User`, em [[bff-cadastro]]. O app do artista não pede abrir conta de profissional, POST `Artist`. Em [[bff-cliente-e-profissional]], só o cadastro de profissional recebe a empresa e o aplicativo aos quais este backend está amarrado. Como o app do artista entra pela porta de cliente, esse vínculo não entra no pedido. Isso não muda o alvo de dois papéis. O item 28 de [[contradicoes-e-lacunas]] fica aberto no código. A decisão de produto permanece. ([[cruzamento-bff-como-ler]], [[cruzamento-bff-conta]], [[decisoes-2026-10-20]])

O pedido do app e a porta não têm o mesmo formato na conferência de documento. Ver se o e-mail já existe está publicado, sem sessão, e nenhum dos dois apps pede. Conferir CPF e, se vier, CNPJ está publicado. O CPF vai no cabeçalho. Os dois apps guardam um pedido de conferir CPF e nenhuma tela o dispara. Esse pedido manda o CPF na pergunta, não no cabeçalho. ([[cruzamento-bff-conta]])

A sessão depois de criar a conta também difere. No cliente, a conta nasce, a sessão fica guardada e a pessoa entra no Início. No artista, a conta nasce e a sessão fica guardada, e esta tela não marca a pessoa como dentro. As abas ficam para a próxima abertura, se a sessão for aceita. ([[cruzamento-bff-conta]])

O miúdo que viaja no pedido é o da tela: e-mail, senha, CPF, nome, nascimento, gênero, nome preferido, foto e um endereço. A lista de campos que o backend exige não está no repositório do backend. Gênero nesse pedido, e a contagem de etapas, são o retrato já encaminhado nos itens 14 e 25. O código será alinhado. ([[cruzamento-bff-conta]], [[decisoes-2026-10-21]])

## O que o board pede em 21/10

O board pede cadastro de cliente e de artista. A história 357, Cadastro de Cliente, inclui a tarefa 411, tela de cadastro do cliente em forma de chat. A história 360, Cadastro de Artista, está Blocked no board e inclui a tarefa 416, tela de cadastro do artista em forma de chat, em New. Os títulos 358 e 361 pedem o cadastro no nome WeCareU.API. Há histórias sem pai: 223, tela de cadastro do artista, e 225, modais de cliente e de artista. ([[board-conta-e-acesso]])

A tarefa 411 manda o fim do cadastro para a listagem, para o agendamento ou para o perfil, conforme a origem. A origem inclui a tela inicial do app. A tarefa 450 pede uma chamada de cadastro quando a pessoa deslogada toca home, favoritos, agendamentos ou perfil. No cliente, a lista abre sem conta e o cadastro acontece antes do agendamento, nunca com horário retido. ([[mvp-alteracoes-pos-congelamento]]) A frase de outubro, cadastrar no momento de agendar, não vale mais.

O alvo do cliente é um chatbot, não duas etapas. O retrato de três etapas no cliente e cinco no artista permanece dívida de alinhamento. O chat pedido no board não descreve o código de 21/10. Ver [[contradicoes-e-lacunas]].

## O que o serviço de conta grava

Foto de 21/10 de `Br.Login.API`, host `https://loginapimicroservice.bptsoftware.com.br/`, banco `UserLogin`. O aplicativo não fala com este serviço. Fala com o BFF. Cliente e profissional nascem os dois em `Usuario`. O profissional, além da pessoa, abre uma empresa (razão social, nome fantasia e documento) e fica ligado a ela. O serviço grava gênero. A data de nascimento vem no pedido e não é gravada. E-mail ou documento repetido impede o cadastro. O documento é gravado sem pontuação, e a conferência compara o texto como chegou. O serviço não coloca ninguém em grupo no cadastro. A conta nasce com cinco estrelas e nenhuma avaliação; esse fato está em [[avaliacoes]]. ([[core-01-conta]])

No núcleo, o cadastro do profissional chama outro host, `UrlsSystems` (`https://systemsapimicroservice.bptsoftware.com.br`, sem a barra final), e, ao ligar o colaborador, um caminho sem a barra que a porta espera; o item 28 permanece. ([[core-04-empresa-e-colaboradores]])

O alvo do cliente é sexo em quatro botões, num chatbot, com a data de nascimento gravada. Os itens 14 e 25 de [[contradicoes-e-lacunas]] estão encaminhados a [[app-cliente-conta]].

A data de nascimento chega neste retrato e não é gravada. O alvo do cliente exige a data. Isso está em [[backend-mvp-conta]].
