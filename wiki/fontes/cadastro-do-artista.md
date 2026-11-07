---
tipo: fonte
arquivo: "ingeridos/Cadastro do artista.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_worker; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cadastro do artista"]
---

# Cadastro do artista

Volta para [[mapa-do-app-do-artista]]. A porta de quem ainda não tem conta está em [[abertura-do-artista]]. Quem já tem conta entra por [[entrar-senha-e-biometria-do-artista]]. O endereço pedido aqui está resumido em [[enderecos-do-artista]].

**Pé:** parcial. Dá para percorrer as cinco etapas e criar a conta no serviço da WeCareU. Ao concluir, a sessão fica no aparelho e a tela não abre as abas nem avisa sucesso. O formulário esvazia e volta à etapa 1. Na próxima abertura, se a sessão for aceita, a pessoa entra. Se a criação falha, o carregamento some e nenhuma frase aparece. Se o CEP não for encontrado, nenhum aviso, a etapa não trava, e a conta pode nascer com rua, cidade e número em branco.

É um formulário em cinco etapas. Não é chatbot. Não pede telefone. Não pede sexo como campo separado de gênero. Não pede orientação sexual. O alvo de duas etapas e de só sexo continua em [[cadastro]] e em [[decisoes-2026-10-20]]. Ver [[contradicoes-e-lacunas]].

## Por onde se chega

Na abertura, **Cadastrar** do último slide. No login, o link **Cadastrar**. Fechar volta para a tela de onde a pessoa veio. O título fica sempre **Cadastro**, com **Etapa 1 de 5** até **Etapa 5 de 5**.

Avançar é uma seta. Na última etapa a seta vira um visto. Não há o texto Continuar nem Criar conta. A seta já nasce acesa. Tocar nela é que cobra os campos. Voltar, a partir da segunda etapa, não apaga o que foi digitado.

Os nomes Informações Pessoais, Endereço, Confirme seu Endereço e Informações da Conta existem nos textos e a tela não os mostra. A etapa da foto não tem nome nos textos.

## Rascunho e o que acontece ao criar

Se a pessoa sai no meio, o rascunho fica no aparelho: dados pessoais e endereço. E-mail, senha, confirmação da senha e foto não ficam. A etapa também não: reabre sempre na primeira, com o resto já preenchido.

Ao criar com sucesso, aparece um carregamento, o rascunho é apagado e o formulário volta vazio para a etapa 1. A sessão fica guardada. Esta tela não marca a pessoa como dentro e ela não cai no [[inicio-do-artista]] nessa hora. Se fechar e abrir de novo, e a sessão for aceita, aí ela entra. Se a criação falha, nenhuma frase. Não há, neste cadastro, um texto genérico do tipo "ocorreu um erro ao criar sua conta".

A frase "Você já tem uma conta! Por favor, faça login." existe nos textos do CPF e esta tela não a usa sozinha.

## Etapa 1 — Dados pessoais

- **CPF.** Onze dígitos, com os dígitos verificadores válidos. Sequência com todos os números iguais não passa.
- **Nome completo.** Pelo menos dois nomes, cada um com 3 letras ou mais. "da", "de", "do", "das", "dos" e "e" não contam como nome.
- **Data de nascimento.** A pessoa precisa ter entre 18 e 120 anos. Data impossível, menor de 18 ou maior de 120 mostram "Data de nascimento inválida". A frase "Você deve ter pelo menos 18 anos" existe nos textos e não aparece aqui.
- **Gênero.** Masculino, Feminino, Outro, Não-binário ou Prefiro não dizer. Sem escolha, a etapa não avança. A frase que aparece não é uma das preparadas em português: é o aviso técnico do validador, em inglês, com os valores internos da lista.
- **Nome preferido.** Opcional. Um nome curto passa. A frase "Nome deve ter pelo menos 2 letras" existe nos textos e esta etapa não a usa.

## Etapa 2 — Foto

Etapa própria. Um círculo com **Selecione uma foto.** Tocar abre a galeria, com recorte quadrado. Não há opção de tirar a foto na hora. Sem foto, a frase é "Foto é obrigatória". Se o acesso às fotos for negado, nada é dito. A frase "Permissão da câmera é necessária para tirar fotos" existe nos textos, esta etapa não a usa, e a ação é a galeria, não a câmera.

## Etapa 3 — Endereço

**País**, com Brasil já escolhido. **CEP** de oito dígitos. **Número**. **Rua** e **cidade** travados: a pessoa não digita. A busca dispara quando o número muda e os dois já têm algum valor. Não dispara ao sair do CEP. Se a pessoa preenche o número antes do CEP, nada é buscado até ela mexer de novo no número.

Se a busca acha, rua, bairro, cidade e estado entram sozinhos, e a conta guarda a posição desse ponto. A pessoa não vê um mapa. Se o CEP não existe, ou a busca falha, nenhum aviso. Rua e cidade ficam como estavam. Esses campos vazios não travam, e um número vazio também não trava esta etapa, embora existam frases dizendo que número, rua, cidade e estado são obrigatórios. A seta segue. Não há campos para digitar rua, bairro, cidade ou estado à mão. Não há busca pelo GPS nesta etapa.

## Etapa 4 — Confirmação do endereço

Um bloco mostra o que já foi achado. Complemento, referência e apelido são opcionais. Tipo: Casa ou Trabalho. Casa já vem escolhida. Nada aqui é obrigatório.

## Etapa 5 — Acesso

**E-mail**, de 5 a 254 caracteres, guardado em minúsculas. **Senha** e **Digite sua senha novamente.** A lista ao lado marca mínimo de 8, maiúscula, minúscula, número, caractere especial e senhas iguais. A lista não diz quais símbolos contam. O que bloqueia é mais estreito: a senha inteira só pode ter letras sem acento, números e `@ $ ! % * ? &`. Outro símbolo pode acender o item "caractere especial" e, ao tocar no visto, cair em "A senha não atende aos requisitos mínimos". O olho da confirmação troca o ícone e o texto continua escondido.

## O que a conta passa a guardar

Nome completo, nome preferido se houver, data de nascimento, CPF, gênero, foto, e-mail e senha. O endereço leva país, CEP, número, complemento, referência, apelido e tipo. Rua, bairro, cidade, estado e a posição só entram se a busca tiver achado. Se a pessoa seguiu com a busca vazia, a conta pode ser criada com rua, cidade e número em branco.

Depois de criada, não dá para revisar isso no perfil. Ver [[perfil-do-artista]] e [[o-que-ainda-nao-esta-no-app-do-artista]].
