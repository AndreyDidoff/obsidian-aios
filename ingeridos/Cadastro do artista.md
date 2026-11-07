---
tipo: extração
tema: Cadastro do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: Parcial. As cinco etapas criam a conta; ao concluir a pessoa não entra, e o CEP sem resultado não avisa nem trava
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Cadastro do artista

Volta para [[Mapa do app do artista]]. A porta de quem ainda não tem conta está em [[Abertura do artista]]. Quem já tem conta entra por [[Entrar, senha e biometria do artista]]. O endereço pedido aqui está resumido em [[Endereços do artista]].

**Pé:** parcial. Dá para percorrer as cinco etapas e criar a conta no serviço da WeCareU. Ao concluir, a pessoa não entra no app: o formulário esvazia e ela continua na área de quem não está dentro. Se o CEP não for encontrado, nada é dito e a etapa não trava.

## Por onde se chega

- Na abertura, o botão **Cadastrar** do último cartaz.
- No login, o link **Cadastrar**.

Fechar volta para a tela de onde a pessoa veio, abertura ou login. O que já foi digitado não se perde, com as exceções do rascunho abaixo.

## Como a tela se organiza

São cinco etapas. O título fica sempre **Cadastro**. Embaixo, o texto **Etapa 1 de 5**, **Etapa 2 de 5**, **Etapa 3 de 5**, **Etapa 4 de 5** ou **Etapa 5 de 5**.

Os nomes Informações Pessoais, Endereço, Confirme seu Endereço e Informações da Conta existem nos textos do app, mas a tela não os mostra. A etapa da foto não tem nome nos textos.

- Avançar é uma seta para a direita. Na última etapa a seta vira um visto. Não há o texto Continuar nem Criar conta.
- A seta já nasce acesa em todas as etapas. Tocar nela é que cobra os campos. Se algo falha, o campo treme e a frase aparece embaixo.
- Voltar é uma seta para a esquerda, a partir da segunda etapa. Voltar não apaga o que foi digitado.

Se a pessoa sai no meio, o rascunho fica no aparelho e volta na próxima vez: dados pessoais e endereço. E-mail, senha, confirmação da senha e foto não ficam. A etapa também não: ela reabre sempre na primeira, com o resto já preenchido.

Ao criar a conta com sucesso, aparece um carregamento, o rascunho é apagado e o formulário volta vazio para a etapa 1. A sessão fica guardada no aparelho, mas esta tela não marca a pessoa como dentro. Ela não cai no [[Início do artista]] nessa hora. Se fechar e abrir o app de novo, e a sessão for aceita, aí ela entra. Se a criação falha, o carregamento some e nenhuma frase aparece. Não há, neste cadastro, um texto genérico do tipo "ocorreu um erro ao criar sua conta".

A frase "Você já tem uma conta! Por favor, faça login." existe nos textos do CPF, mas esta tela não a usa sozinha.

## Etapa 1 — Dados pessoais

- **CPF.** Máscara `000.000.000-00`. Onze dígitos, com os dígitos verificadores válidos. Sequência com todos os números iguais não passa. Um CPF curto mostra "CPF deve ter 11 dígitos". Um CPF com tamanho de máscara, mas inválido, mostra "CPF inválido".
- **Nome completo.** Só letras e espaços; número e símbolo saem enquanto a pessoa digita. Pelo menos dois nomes, cada um com 3 letras ou mais. "da", "de", "do", "das", "dos" e "e" não contam como nome. Vazio, a frase é "Cada nome deve ter pelo menos 3 letras". Nome incompleto, a frase é "Digite pelo menos 2 nomes, cada um com 3 ou mais letras".
- **Data de nascimento.** Máscara dia/mês/ano. A pessoa precisa ter entre 18 e 120 anos. Vazio, a frase é "Data de nascimento é obrigatória". Data impossível, menor de 18 ou maior de 120 mostram a mesma frase: "Data de nascimento inválida". A frase "Você deve ter pelo menos 18 anos" existe nos textos e não aparece aqui.
- **Gênero.** Lista: Masculino, Feminino, Outro, Não-binário ou Prefiro não dizer. O convite é "Selecione seu gênero". Sem escolha, a etapa não avança. A frase que aparece não é uma das preparadas em português: é o aviso técnico do validador, em inglês, com os valores internos da lista.
- **Nome preferido.** Opcional. O convite é "Digite seu nome preferido". Números e símbolos saem enquanto digita. A frase "Nome deve ter pelo menos 2 letras" existe nos textos e esta etapa não a usa: um nome curto passa.

## Etapa 2 — Foto

Um círculo com ícone de câmera e o texto **Selecione uma foto.** Tocar abre a galeria, com recorte quadrado. Não há opção de tirar a foto na hora.

A foto é obrigatória para seguir. Sem ela, a frase é "Foto é obrigatória".

Se o acesso às fotos for negado, nada é dito. A frase "Permissão da câmera é necessária para tirar fotos" existe nos textos, mas esta etapa não a usa, e a ação é a galeria, não a câmera.

## Etapa 3 — Endereço

- **País.** Lista de países em português, em ordem alfabética. Brasil já vem escolhido. O convite é "Selecione seu país".
- **CEP.** Máscara `00000-000`. Precisa ter oito números. Outro tamanho mostra "CEP inválido". A frase "CEP deve ter 8 dígitos" existe nos textos e não é a que aparece. O campo continua sendo CEP mesmo se o país não for o Brasil: um código postal de outro tamanho não passa.
- **Número.** Teclado numérico. O convite é "Digite o número". A frase "Número é obrigatório" existe nos textos, mas um número vazio não trava esta etapa.
- **Rua e cidade.** A pessoa não digita. São dois campos travados. Quando a busca acha, o primeiro mostra rua e bairro, e o segundo mostra cidade e estado. Vazios, os convites são "Rua" e "Cidade". As frases "Rua é obrigatória", "Cidade é obrigatória" e "Estado é obrigatório" existem nos textos e não travam o campo vazio.

A busca do CEP não acontece ao sair do CEP. Ela só dispara quando o número muda e os dois já têm algum valor. Se a pessoa preenche o número antes do CEP, nada é buscado até ela mexer de novo no número. Cada dígito do número busca de novo.

Se a busca acha, rua, bairro, cidade e estado entram sozinhos, e a conta guarda também a posição desse ponto. A pessoa não vê um mapa. O país pode ser trocado pelo que a busca devolver. Complemento, referência, tipo e apelido, da etapa seguinte, são mantidos.

Se o CEP não existe, ou a busca falha, nenhum aviso aparece. Rua e cidade ficam como estavam. Como esses campos vazios não travam, a seta segue para a etapa seguinte.

Não há campos para digitar rua, bairro, cidade ou estado à mão. Não há busca pelo GPS nesta etapa. O detalhe do que fica guardado está em [[Endereços do artista]].

## Etapa 4 — Confirmação do endereço

Um bloco mostra o que já foi achado: rua, número, complemento, referência entre parênteses, bairro, cidade, estado e CEP. O país não entra nesse bloco.

- **Complemento.** Opcional. O convite é "Digite o complemento (opcional)".
- **Referência.** Opcional. O convite é "Digite uma referência. Ex: Casa verde".
- **Tipo de endereço.** Casa ou Trabalho. Casa já vem escolhida. Trocar guarda a escolha. O destaque do botão pode sumir depois do toque, porque a marcação visual não acompanha o valor guardado.
- **Apelido.** Opcional. O convite é "Ex: Apartamento, Empresa xxx".

Nada aqui é obrigatório. A seta avança mesmo com tudo vazio, desde que a etapa anterior tenha passado.

## Etapa 5 — Acesso

- **E-mail.** De 5 a 254 caracteres, no formato de e-mail. A conta guarda em letras minúsculas. Frases: "E-mail deve ter pelo menos 5 caracteres", "E-mail não pode ter mais de 254 caracteres" e "E-mail inválido".
- **Senha** e **Digite sua senha novamente.** Um olho na senha mostra ou esconde o texto. O olho da confirmação troca o ícone e o texto continua escondido.

Uma lista ao lado marca o que já foi cumprido, sob o título "Sua senha deve conter:":

- Pelo menos um número
- Pelo menos uma letra minúscula
- Pelo menos uma letra maiúscula
- Pelo menos 8 caracteres
- Pelo menos um caractere especial
- As senhas devem ser iguais

A lista não diz quais símbolos contam. O que de fato bloqueia é mais estreito: a senha inteira só pode ter letras sem acento, números e estes símbolos: `@ $ ! % * ? &`. Outro símbolo pode acender o item "caractere especial" na lista e, ao tocar no visto, a senha cair em "A senha não atende aos requisitos mínimos". Se as duas senhas diferem, a frase é "As senhas não conferem".

## O que a conta passa a guardar

Nome completo, nome preferido se houver, data de nascimento, CPF, gênero, foto, e-mail e senha. O endereço leva país, CEP, número, complemento, referência, apelido e tipo (casa ou trabalho). Rua, bairro, cidade, estado e a posição do ponto só entram se a busca tiver achado. A pessoa não vê essa posição na tela. Se a pessoa seguiu com a busca vazia, a conta pode ser criada com rua, cidade e número em branco.

Depois de criada, não dá para revisar isso no perfil. Dados pessoais abrem a frase "Em breve você poderá editar seus dados pessoais aqui." Endereços abrem a frase de [[Endereços do artista]]. Ver [[Perfil do artista]] e [[O que ainda não está no app do artista]].

## O que o cadastro ainda não faz

- Não entra no [[Início do artista]] quando a conta é criada. A sessão fica no aparelho e só vale numa próxima abertura, se for aceita.
- Não mostra frase quando a criação falha.
- Não avisa quando o CEP não existe e não oferece preencher a rua à mão. Também não impede seguir com rua, cidade e número vazios, embora existam frases dizendo que são obrigatórios.
- Não busca o endereço ao terminar o CEP, só quando o número muda.
- Não explica, com a frase certa, que a idade mínima é 18 anos.
- Não tem frase em português para gênero vazio. Mostra o aviso técnico em inglês.
- Não oferece tirar a foto com a câmera. Se a galeria for negada, não avisa. A frase pronta fala em câmera.
- Não guarda e-mail, senha, foto nem a etapa em que a pessoa parou.
- A lista da senha aceita símbolos que a regra final recusa.
- O olho da confirmação da senha não revela o texto.
