---
tipo: extração
tema: Criar conta
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: construído, com falha quando o CEP não é encontrado
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Criar conta

Volta para o [[Mapa do app do cliente]]. A porta de quem ainda não tem conta está em [[Primeira entrada]]. Depois de criada, a pessoa entra direto. O login de quem já tem conta está em [[Entrar, senha e biometria]].

**Pé:** construído. Dá para percorrer as três etapas e criar a conta no serviço da WeCareU. Se o CEP não for encontrado, o fluxo trava: a frase pede para preencher o endereço à mão, mas essa frase não aparece e não há campos para rua, cidade ou estado.

## Por onde se chega

- No login, o link **Cadastrar**.
- Na lista de artistas, o cartaz **Cadastrar** no meio da lista. O texto varia entre três frases: o cadastro é gratuito para ver todos os artistas; a plataforma também é grátis para o artista; a pessoa escolhe quem vai atendê-la.
- Uma tela antiga de visitante também aponta para o cadastro, mas ela não entra em nenhum fluxo. Ver [[O que ainda não está no app]].

O endereço preenchido na [[Primeira entrada]] não vem para cá. Este cadastro guarda o próprio rascunho.

Fechar o cadastro volta para a tela anterior. Se a pessoa estava visitando a lista sem conta, fechar também encerra a visita e volta para a abertura.

## Como a tela se organiza

Uma barra mostra o avanço e o texto **Etapa 1 de 3**, **Etapa 2 de 3** ou **Etapa 3 de 3**.

- **Continuar** só acende quando os campos obrigatórios da etapa atual têm algum valor. Na primeira etapa, a senha também precisa cumprir as regras e coincidir com a confirmação.
- **Voltar** aparece a partir da segunda etapa e não apaga o que já foi digitado.
- Na última etapa o botão vira **Criar conta**. Enquanto o CEP está sendo buscado, ele fica apagado.

Se a pessoa sai no meio, o rascunho fica no aparelho e volta na próxima vez: e-mail, dados pessoais e endereço. Senha, confirmação da senha e foto não ficam salvas. A etapa também não: ela reabre sempre no Acesso, com o resto já preenchido.

Ao criar a conta com sucesso, o rascunho é apagado, a pessoa entra e o app abre o [[Início]]. Se a criação falha, a mensagem fica na tela. O texto genérico é "Ocorreu um erro ao criar sua conta. Tente novamente." Existe também a frase "Você já tem uma conta! Por favor, faça login." nos textos do CPF, mas esta tela não a usa sozinha: ela só aparece se o serviço devolver essa frase.

## Etapa 1 — Acesso

Título: **Acesso.** Subtítulo: "Crie suas credenciais de acesso."

- **País.** Só existe Brasil, e ele já vem escolhido.
- **E-mail.** De 5 a 254 caracteres, no formato de e-mail. O app guarda em letras minúsculas.
- **Senha** e **Confirmar senha.** Uma lista ao lado marca o que já foi cumprido:
  - mínimo de 8 caracteres
  - ao menos 1 letra maiúscula
  - ao menos 1 letra minúscula
  - ao menos 1 número
  - ao menos 1 caractere especial, entre estes: `@ $ ! % * ? &`
  - as duas senhas iguais

Outro símbolo não conta como especial. Se as senhas diferem, a mensagem é "As senhas não conferem".

## Etapa 2 — Dados pessoais

Título: **Dados Pessoais.** Subtítulo: "Conte-nos um pouco sobre você."

- **CPF.** Onze dígitos, com os dígitos verificadores válidos. Sequência com todos os números iguais não passa. Mensagens: "CPF deve ter 11 dígitos" e "CPF inválido".
- **Nome completo.** Pelo menos dois nomes, cada um com 3 letras ou mais. "da", "de", "do", "das", "dos" e "e" não contam como nome. A mensagem é "Digite pelo menos 2 nomes, cada um com 3 ou mais letras".
- **Data de nascimento.** No formato dia/mês/ano. A pessoa precisa ter entre 18 e 120 anos. A frase específica "Você deve ter pelo menos 18 anos" existe nos textos, mas esta tela mostra "Data de nascimento inválida" tanto para data impossível quanto para quem tem menos de 18.
- **Gênero.** Masculino, Feminino, Outro, Não-binário ou Prefiro não dizer.
- **Nome preferido.** Opcional. Se for preenchido, precisa ter pelo menos 2 letras.
- **Foto.** Obrigatória para seguir. Abre a galeria, em recorte quadrado. Se o acesso às fotos for negado, o aviso fala em câmera: "Permissão da câmera é necessária para tirar fotos". Não há opção de tirar a foto na hora.

**Continuar** acende quando CPF, nome, data, gênero e foto têm algum conteúdo. A validade do CPF e da idade só é cobrada ao tocar no botão. Se não passar, a etapa não avança.

## Etapa 3 — Endereço

Título: **Endereço.** Subtítulo: "Onde você mora?"

- **CEP.** Com oito dígitos, o app busca a rua sozinho e mostra um bloco **Endereço encontrado**, com rua, bairro, cidade e estado. O CEP em si precisa ter oito números.
- **Número.** Obrigatório. Ao sair do campo, o app tenta de novo o ponto no mapa já com o número. Se essa segunda busca falhar, mantém o que o CEP tinha achado, sem aviso.
- **Complemento, referência e apelido do endereço.** Opcionais. Os exemplos de texto são "Casa verde" na referência e "Apartamento, Empresa xxx" no apelido.
- **Tipo de endereço.** Casa ou Trabalho. Casa já vem escolhida.

Não há campos para digitar rua, bairro, cidade ou estado. Eles só aparecem no bloco encontrado, e só se a busca do CEP der certo.

Se o CEP não for encontrado, o app prepara a frase "CEP não encontrado. Preencha o endereço manualmente." Essa frase não é mostrada. Como também não há onde digitar a rua, **Criar conta** permanece apagado.

## O que o cadastro ainda não faz

- Não aproveita o endereço da visita sem conta.
- Não deixa concluir o endereço quando o CEP falha.
- Não explica, com a frase certa, que a idade mínima é 18 anos.
- Não oferece tirar a foto com a câmera. O aviso de permissão fala em câmera, mas a ação é a galeria.
- Não guarda em que etapa a pessoa parou.
- Não é o caminho chamado "SignUp" que ainda aparece previsto no app. O cadastro em uso é este.
