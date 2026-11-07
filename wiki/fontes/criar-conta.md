---
tipo: fonte
arquivo: "ingeridos/Criar conta.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_client; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Criar conta"]
---

# Criar conta

Volta para [[mapa-do-app-do-cliente]]. A porta de quem ainda não tem conta está em [[primeira-entrada]]. Depois de criada, a pessoa entra e o app abre o [[inicio]]. O login de quem já tem conta está em [[entrar-senha-e-biometria]].

**Pé:** construído, com falha quando o CEP não é encontrado. Dá para percorrer as três etapas e criar a conta no serviço da WeCareU. Se o CEP não for encontrado, o fluxo trava.

É um formulário em três etapas. Não é chatbot. Não pede telefone. Não pede sexo como campo separado de gênero. Não pede orientação sexual.

## Por onde se chega

No login, o link **Cadastrar**. Na lista de artistas, o cartaz **Cadastrar**. Uma tela antiga de visitante também aponta para o cadastro e não entra em nenhum fluxo. ([[o-que-ainda-nao-esta-no-app]])

O endereço da visita não vem para cá. Este cadastro guarda o próprio rascunho. Fechar volta para a tela anterior. Se a pessoa estava visitando a lista sem conta, fechar também encerra a visita e volta para a abertura.

A barra mostra **Etapa 1 de 3**, **Etapa 2 de 3** ou **Etapa 3 de 3**. **Continuar** só acende quando os obrigatórios da etapa têm algum valor. Na primeira, a senha também precisa cumprir as regras e coincidir com a confirmação. **Voltar** aparece a partir da segunda e não apaga o que já foi digitado. Na última, o botão vira **Criar conta**. Enquanto o CEP está sendo buscado, ele fica apagado.

Se a pessoa sai no meio, o rascunho fica no aparelho: e-mail, dados pessoais e endereço. Senha, confirmação e foto não ficam. A etapa também não: reabre sempre no Acesso, com o resto já preenchido. Ao criar com sucesso, o rascunho é apagado, a pessoa entra e o app abre o Início. Se falha, a mensagem fica na tela. O texto genérico é "Ocorreu um erro ao criar sua conta. Tente novamente." A frase "Você já tem uma conta! Por favor, faça login." existe nos textos do CPF e só aparece se o serviço a devolver.

## Etapa 1 — Acesso

Título: **Acesso.** Subtítulo: "Crie suas credenciais de acesso."

- **País.** Só existe Brasil, e ele já vem escolhido.
- **E-mail.** De 5 a 254 caracteres, no formato de e-mail. O app guarda em letras minúsculas.
- **Senha** e **Confirmar senha.** A lista ao lado marca: mínimo de 8 caracteres; ao menos 1 maiúscula; ao menos 1 minúscula; ao menos 1 número; ao menos 1 especial, entre `@ $ ! % * ? &`; as duas senhas iguais. Outro símbolo não conta como especial. Se diferem, a mensagem é "As senhas não conferem".

## Etapa 2 — Dados pessoais

Título: **Dados Pessoais.** Subtítulo: "Conte-nos um pouco sobre você."

- **CPF.** Onze dígitos, com os dígitos verificadores válidos. Sequência com todos os números iguais não passa. Mensagens: "CPF deve ter 11 dígitos" e "CPF inválido".
- **Nome completo.** Pelo menos dois nomes, cada um com 3 letras ou mais. "da", "de", "do", "das", "dos" e "e" não contam como nome. A mensagem é "Digite pelo menos 2 nomes, cada um com 3 ou mais letras".
- **Data de nascimento.** Dia/mês/ano. A pessoa precisa ter entre 18 e 120 anos. A frase "Você deve ter pelo menos 18 anos" existe nos textos, e a tela mostra "Data de nascimento inválida" tanto para data impossível quanto para quem tem menos de 18.
- **Gênero.** Masculino, Feminino, Outro, Não-binário ou Prefiro não dizer.
- **Nome preferido.** Opcional. Se for preenchido, precisa ter pelo menos 2 letras.
- **Foto.** Obrigatória. Abre a galeria, em recorte quadrado. Se o acesso às fotos for negado, o aviso fala em câmera: "Permissão da câmera é necessária para tirar fotos". Não há opção de tirar a foto na hora.

**Continuar** acende quando CPF, nome, data, gênero e foto têm algum conteúdo. A validade do CPF e da idade só é cobrada ao tocar no botão.

## Etapa 3 — Endereço

Título: **Endereço.** Subtítulo: "Onde você mora?"

- **CEP.** Com oito dígitos, o app busca a rua e mostra o bloco **Endereço encontrado**, com rua, bairro, cidade e estado. Rua, bairro, cidade e estado só aparecem se a busca achar. Não há campos para digitá-los.
- **Número.** Obrigatório. Ao sair do campo, o app tenta de novo o ponto no mapa já com o número. Se essa segunda busca falhar, mantém o que o CEP tinha achado, sem aviso.
- **Complemento, referência e apelido.** Opcionais. Os exemplos são "Casa verde" na referência e "Apartamento, Empresa xxx" no apelido.
- **Tipo.** Casa ou Trabalho. Casa já vem escolhida.

Se o CEP não é encontrado, a frase "CEP não encontrado. Preencha o endereço manualmente." está preparada e não aparece. Não há campos manuais. **Criar conta** permanece apagado.

Não é o caminho chamado "SignUp", que ainda aparece previsto. O cadastro em uso é este.
