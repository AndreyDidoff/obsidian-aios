---
tipo: pendencia
superficie: backend
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[core-01-conta]]", "[[bff-entrar-sair-e-senha]]", "[[core-07-bloqueio]]", "[[core-12-relatos]]"]
---

# Ajustes de backend: conta

Esta página lista o que o backend precisa mudar na conta para chegar ao alvo do MVP. Não é a especificação do produto.

### Código de senha
- **Alvo:** O código de recuperação tem 5 dígitos e vale 5 minutos, valor configurável no backend, inclusive na troca de senha de quem já está logado. ("Login e recuperação de senha do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** O serviço de conta pede senha nova por e-mail, com 4 horas de prazo no pedido. Se o e-mail não for de uma conta ativa, a resposta é a mesma. Confere se o código combina com o e-mail e grava a senha nova. Quem já está dentro também troca a própria senha. No fechamento, o código continua ativo e a conferência não olha o prazo. ([[core-01-conta]]) O BFF publica o pedido de troca. O envio do e-mail não é ação desse backend, e a expiração desse token não está nesse repositório. ([[bff-entrar-sair-e-senha]])
- **Ajuste:** O serviço passa a emitir um código de 5 dígitos, válido por 5 minutos e configurável, também na troca de senha de quem já está logado, e a recusar código expirado ou já usado. A resposta segue a mesma quando o e-mail não é de uma conta ativa.

### Limites de tentativa
- **Alvo:** Cinco códigos errados e cinco senhas erradas no login bloqueiam por um tempo. O reenvio do código espera 60 segundos. Números e tempos são configuráveis. ("Login e recuperação de senha do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. O serviço passa a recusar por um tempo o login após 5 senhas erradas e o código após 5 erros, a segurar o reenvio por 60 segundos, e a ler esses números e tempos da configuração.

### Confirmação de e-mail
- **Alvo:** O reenvio do link de confirmação espera 60 segundos. O link novo invalida o anterior e o link expira. Na troca de e-mail, a confirmação ocorre primeiro no e-mail antigo e depois no novo. ("Confirmação de e-mail do cliente"; "Editar Perfil do cliente e troca de e-mail", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. O serviço passa a reenviar o link com intervalo de 60 segundos, a invalidar o anterior, a recusar link expirado e a gravar o e-mail novo só depois da confirmação no antigo, pedindo em seguida a confirmação do novo.

### Sessão e 401
- **Alvo:** Qualquer perda de autorização devolve 401 genérico, sem motivo. A troca de senha, o bloqueio e 2 meses sem acesso encerram o token. Depois de 7 dias sem acesso, e antes de 2 meses, o refresh é renovado e a pessoa segue logada. ("Sessão do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** O serviço de conta reaproveita a sessão ainda no prazo e, sem ela, abre outra com 48 horas de acesso e 7 dias para renovar. Se o acesso venceu e a renovação ainda vale, grava outra sessão, e a resposta da renovação continua com a sessão antiga. ([[core-01-conta]]) O BFF prepara a sessão e a leitura não entra no caminho do pedido. O retrato não declara o código 401. ([[bff-entrar-sair-e-senha]])
- **Ajuste:** O serviço passa a devolver 401 genérico, sem motivo, em qualquer perda de autorização, a encerrar o token na troca de senha, no bloqueio e após 2 meses sem acesso, e a renovar o refresh depois de 7 dias devolvendo a sessão nova. A leitura da sessão entra no caminho do pedido.

### Biometria
- **Alvo:** [a validar] token do aparelho emitido pelo backend, revogável, nunca a senha, para a biometria reentrar após inatividade. A biometria não substitui o login e não vale quando o token morre por troca de senha, bloqueio ou conta suspensa. ("Login e recuperação de senha do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. [a validar] a tarefa é decidir se o serviço emite um token de aparelho revogável para a biometria e recusa usar a senha nesse papel, sem manter a biometria quando a sessão morre por troca de senha, bloqueio ou suspensão.

### Aceite dos termos
- **Alvo:** O aceite dos termos grava versão, data e hora. O cadastro não conclui sem o aceite. ("Cadastro do cliente: formato e dados", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. O serviço passa a gravar versão, data e hora do aceite e a recusar concluir o cadastro sem esse registro.

### Unicidade
- **Alvo:** Só CPF e e-mail são únicos. O celular pode repetir. Não há código SMS no cliente. ("Cadastro do cliente: formato e dados", [[mvp-funcoes-e-telas]])
- **Hoje:** Se o e-mail ou o documento já existem, o cadastro para. O documento é gravado sem pontuação e a conferência compara o texto como chegou. ([[core-01-conta]])
- **Ajuste:** O serviço passa a recusar o cadastro quando o CPF ou o e-mail já existem, comparando o documento sem máscara, a aceitar o mesmo celular em mais de uma conta e a não exigir código SMS.

### Sexo no lugar de gênero
- **Alvo:** O cadastro do cliente grava sexo em quatro valores (Masculino, Feminino, Não binário, Prefiro não dizer). Não grava gênero. ("Cadastro do cliente: formato e dados", [[mvp-funcoes-e-telas]])
- **Hoje:** O serviço de conta grava gênero. ([[core-01-conta]])
- **Ajuste:** O serviço passa a gravar sexo nesses quatro valores e deixa de gravar gênero.

### Data de nascimento
- **Alvo:** A data de nascimento é gravada e o cadastro de quem tem menos de 18 anos não é concluído. ("Cadastro do cliente: formato e dados", [[mvp-funcoes-e-telas]])
- **Hoje:** A data chega no pedido e não é gravada. ([[core-01-conta]])
- **Ajuste:** O serviço passa a gravar a data de nascimento e a recusar concluir o cadastro de quem tem menos de 18 anos.

### Nota ao nascer a conta
- **Alvo:** A conta não nasce com nota. A média é bayesiana (prior 4,7, peso 10) e o cliente só vê número com 3 ou mais avaliações. ("Fluxo de avaliação do cliente (M10)", [[mvp-funcoes-e-telas]])
- **Hoje:** A conta nasce com cinco estrelas e nenhuma avaliação. ([[core-01-conta]])
- **Ajuste:** O serviço deixa de criar a conta com cinco estrelas. Sem avaliação, não há nota para exibir.

### Exclusão do cliente
- **Alvo:** A exclusão é recusada enquanto houver agendamento ativo. A conta fica "em processo de exclusão" por 30 dias e o login nesse prazo reativa. Depois, o soft delete vale só para o usuário do app do cliente; os dados do artista permanecem. ("Excluir conta do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. O serviço passa a recusar a exclusão com agendamento ativo, a gravar "em processo de exclusão" por 30 dias e reativar no login nesse prazo, e a aplicar soft delete só ao usuário do app do cliente, com os dados do artista como estão.

### Motivo da exclusão
- **Alvo:** [A CRIAR] gravar motivo, texto livre e desfecho (excluiu, ficou ou foi denunciar), inclusive quando a pessoa desiste, sem ação automática. ("Excluir conta do cliente", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. [A CRIAR] o serviço passaria a gravar motivo, texto livre e desfecho da exclusão, inclusive na desistência, sem disparar sanção nem outra ação a partir desse registro.

### Bloqueio
- **Alvo:** Ao bloquear, os agendamentos futuros entre as duas pessoas são cancelados, o Artista sai da listagem e da busca desse cliente e o perfil deixa de abrir. Se o Artista bloqueia o cliente, o cliente deixa de agendar com ele. Não há desbloqueio pelo usuário. ("Bloqueio (M12-F02)", [[mvp-funcoes-e-telas]])
- **Hoje:** O bloqueio grava quem bloqueia e quem é bloqueado, permite desfazer, não guarda prazo, e nenhum outro serviço lê esse registro para esconder perfil ou agenda. ([[core-07-bloqueio]])
- **Ajuste:** O serviço continua gravando quem bloqueia e quem é bloqueado, sem prazo, e passa a recusar o desfazer pedido pelo usuário, deixando o desfazer com a equipe. A listagem, a busca, o perfil e os agendamentos passam a ler esse registro para esconder o Artista daquele cliente, impedir o agendamento no sentido inverso e cancelar os agendamentos futuros entre os dois.

### Sanção
- **Alvo:** A sanção do MVP é suspensão por tempo indeterminado, registrada por conta e por app. Cancela os agendamentos futuros e avisa o outro lado do cancelamento. A mensagem de sanção sai só na tentativa de login. ("5. Conta suspensa ou banida pelo backoffice", [[mvp-funcoes-e-telas]])
- **Hoje:** o retrato lido não descreve este comportamento.
- **Ajuste:** O retrato não mostra esta regra. O serviço passa a gravar a suspensão por tempo indeterminado por conta e por app, a devolver a resposta de conta suspensa só na tentativa de login desse app e a encerrar a sessão já aberta em 401 genérico. Também cancela os agendamentos futuros e avisa o outro lado do cancelamento.

### Denúncia
- **Alvo:** A denúncia chega ao backoffice com motivo, número do agendamento quando houver, denunciante e denunciado. O alvo pode ser a foto de divulgação. A descrição tem limite de 500 caracteres e é obrigatória só no motivo "Outros". Não há trava de repetição nem ação automática. ("Denúncia do cliente (M12-F01)", [[mvp-funcoes-e-telas]])
- **Hoje:** O relato guarda descrição e os dois identificadores. A foto é um identificador. Não há ação automática de sanção. ([[core-12-relatos]])
- **Ajuste:** O serviço passa a gravar também o motivo e o número do agendamento, quando houver, junto da descrição e dos dois identificadores, e a guardar a foto como identificador, sem abrir o arquivo. O relato segue sem ação automática de sanção e fica disponível ao backoffice, inclusive quando se repete.
