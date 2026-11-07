---
tipo: cruzamento
tema: Criar conta
extraido_em: 2026-10-21
idioma: pt-BR
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app como um todo em 21/10/2026, feito para a ingestão. Cruza o app do cliente, o app do artista, o kit visual e o fluxo compartilhado de entrar na conta. Descreve o que já está construído, em que pé está e onde a mesma experiência aparece mais de uma vez. Linguagem de produto. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Cruzamento — criar conta

O cliente e o artista criam conta no serviço da WeCareU por desenhos próprios. No cliente são três etapas. No artista são cinco, em outra ordem, com uma etapa só de foto. Não existe peça compartilhada de cadastro em uso. O fluxo compartilhado de entrar na conta mostra o link Cadastrar, o toque não abre nada, e esse fluxo não está instalado em nenhum app.

## Lado a lado

| Assunto | Cliente | Artista | Peça compartilhada |
| --- | --- | --- | --- |
| Pé | Construído, com falha quando o CEP não é encontrado. Dá para percorrer as três etapas e criar a conta. | Parcial. As cinco etapas criam a conta. Ao concluir, a pessoa não entra. O CEP sem resultado não avisa nem trava. | Não há cadastro. O link Cadastrar aparece na entrada e o toque não abre nada. Cadastro de conta nova está só no papel. O fluxo não está instalado em nenhum app. |
| Quantas etapas | 3 | 5 | Nenhuma |
| Nomes das etapas | Acesso, Dados Pessoais e Endereço. A barra mostra Etapa 1 de 3, Etapa 2 de 3 e Etapa 3 de 3. | A tela mostra o título Cadastro e o contador de Etapa 1 de 5 a Etapa 5 de 5. O percurso é dados pessoais, foto, endereço, confirmação do endereço e acesso. Os textos Informações Pessoais, Endereço, Confirme seu Endereço e Informações da Conta existem e a tela não os mostra. A etapa da foto não tem nome nos textos. | Nenhuma |
| O que acontece ao concluir | A conta é criada, o rascunho é apagado, a pessoa entra e o app abre o Início. Se a criação falha, a mensagem fica na tela. O texto genérico é "Ocorreu um erro ao criar sua conta. Tente novamente." | A conta é criada no serviço. Aparece um carregamento, o rascunho é apagado e o formulário volta vazio para a etapa 1. A sessão fica no aparelho, e a tela não abre as abas. Na próxima abertura, se a sessão for aceita, a pessoa entra. Se a criação falha, o carregamento some e nenhuma frase aparece. | O toque no link não abre cadastro e não avisa nada. |
| Rascunho | E-mail, dados pessoais e endereço. A tela reabre sempre no Acesso, com o resto já preenchido. | Dados pessoais e endereço. A tela reabre sempre na primeira etapa, com o resto já preenchido. | Nenhum |
| O que não entra no rascunho | Senha, confirmação da senha, foto e a etapa em que a pessoa parou. | E-mail, senha, confirmação da senha, foto e a etapa em que a pessoa parou. | Nenhum |
| CEP quando não acha | A frase "CEP não encontrado. Preencha o endereço manualmente." fica preparada e não aparece. Não há campos de rua, cidade ou estado. Criar conta permanece apagado. | Nenhum aviso. Rua e cidade ficam como estavam. A etapa não trava e a seta segue. A conta pode ser criada com rua, cidade e número em branco. | Não se aplica |
| Por onde se chega | Link Cadastrar no login. Cartaz Cadastrar no meio da lista de artistas. Uma tela antiga de visitante também aponta para o cadastro, e não entra em nenhum fluxo. | Botão Cadastrar do último cartaz na abertura. Link Cadastrar no login. | Na entrada, o texto "Não tem uma conta? Cadastrar". O toque não faz nada. |

## O que é o mesmo

A pessoa cria uma conta no serviço da WeCareU. Se sai no meio, o aparelho guarda um rascunho e, na próxima vez, reabre na primeira etapa com o que esse rascunho tiver. A senha e a confirmação da senha ficam de fora do rascunho nos dois apps. A foto também fica de fora.

A frase "Você já tem uma conta! Por favor, faça login." existe nos textos do CPF dos dois cadastros, e a tela não a usa sozinha. No cliente, ela só aparece se o serviço devolver essa frase.

## O que não é o mesmo

São desenhos diferentes, com outra ordem e outra contagem.

No cliente o caminho é Acesso, Dados Pessoais e Endereço. Acesso pede país (só Brasil, já escolhido), e-mail e senha com confirmação. Dados Pessoais pede CPF, nome completo, data de nascimento, gênero, nome preferido (opcional) e foto. Endereço pede CEP e número, mais complemento, referência, apelido e tipo Casa ou Trabalho. Rua, bairro, cidade e estado só aparecem no bloco Endereço encontrado, quando a busca acha.

No artista o caminho é dados pessoais, foto, endereço, confirmação do endereço e acesso. Dados pessoais pede CPF, nome completo, data de nascimento, gênero e nome preferido (opcional). A etapa seguinte é só a foto, com o texto Selecione uma foto. Endereço pede país (lista, Brasil já escolhido), CEP e número, e mostra rua e cidade travados quando a busca acha. A confirmação repete o que foi achado e pede complemento, referência, tipo Casa ou Trabalho e apelido, tudo opcional. Acesso, por último, pede e-mail e senha com confirmação.

O artista tem uma etapa só de foto. O cliente pede a foto dentro de Dados Pessoais. Nos dois a foto abre a galeria, em recorte quadrado, e não há opção de tirar na hora.

Ao concluir, o cliente entra e abre o Início. O artista cria a conta, guarda a sessão e permanece na área de quem não está dentro: o formulário esvazia e as abas não abrem. A entrada do artista fica para a próxima abertura, se a sessão for aceita.

Quando o CEP não é encontrado, o cliente trava o fim do cadastro: a frase de preenchimento à mão não aparece, não há onde digitar rua, cidade ou estado, e Criar conta fica apagado. O artista segue em silêncio. A busca dele dispara quando o número muda, não ao sair do CEP. Sem resultado, nada é dito, a etapa não trava, e a conta pode sair sem rua, sem cidade e sem número.

Os rótulos do avanço também divergem. No cliente, o botão se chama Continuar e, na última etapa, Criar conta. Continuar só acende quando o que a etapa exige tem algum valor; na primeira etapa a senha ainda precisa cumprir as regras e coincidir com a confirmação. No artista, avançar é uma seta para a direita, que na última etapa vira um visto. Não há o texto Continuar nem Criar conta. A seta já nasce acesa, e o toque é que cobra os campos.

O rascunho guarda coisas diferentes. No cliente ficam e-mail, dados pessoais e endereço. No artista ficam dados pessoais e endereço; o e-mail não fica.

A porta de entrada muda conforme o app. No cliente, o link Cadastrar do login e o cartaz Cadastrar no meio da lista de artistas. No artista, o botão Cadastrar do último cartaz da abertura e o link Cadastrar do login. No fluxo compartilhado de entrar na conta, o mesmo rótulo Cadastrar está na entrada e não leva a lugar nenhum.

## Páginas

- [[Criar conta]]
- [[Cadastro do artista]]
- [[Endereços]]
- [[Endereços do artista]]
- [[library-components-o-que-entrega]]
