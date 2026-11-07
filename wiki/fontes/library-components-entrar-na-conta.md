---
tipo: fonte
arquivo: ingeridos/library-components-entrar-na-conta.md
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-components, pacote @wecareu/auth-flow; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Entrar na conta"]
---

# Entrar na conta

Volta para [[library-components-o-que-entrega]]. Pacote `@wecareu/auth-flow` 0.1.0.

Título "Entre na sua conta". Subtítulo pede o e-mail e a senha para continuar. Dois campos: e-mail com exemplo e senha com pontinhos. As palavras "Email" e "Senha" existem nas traduções e não vão para os campos. Dá para mostrar e ocultar a senha. O botão diz "Entrar". Na espera, ele desliga e aparece um indicador.

O e-mail é obrigatório e válido. Antes de enviar, as pontas são limpas e o texto vai em minúsculas. A senha é obrigatória, começa vazia e vai como foi digitada. Qualquer senha preenchida passa nesta tela. Mínimo de 8, minúscula, maiúscula, número e caractere especial valem na troca, não aqui.

Se o preenchimento falha ou a entrada não é aceita, as frases surgem numa lista acima dos campos. A falha de login é uma frase só: "Falha no login. Verifique suas credenciais." Não há distinção entre senha errada, conta inexistente ou rede. Se a entrada dá certo, a sessão fica no aparelho. Esta tela não escolhe a próxima. Quem decide é o app.

"Esqueci minha senha" aparece sempre. Continua visível mesmo quando as telas de recuperação são desligadas; nesse caso o toque não tem destino. "Não tem uma conta? Cadastrar" está visível e habilitado, e o toque não abre nada. O comentário na tela diz que o app consumidor cuidaria do cadastro. Cadastro não existe aqui.

Quando a senha nova é aceita, a pessoa volta com o sinal `showRecoverySuccess`. A tela de login ignora esse sinal: não aparece aviso de sucesso.

O parâmetro `redirectTo`, pelo nome, parece destino depois do login. Na prática só preenche o e-mail. A senha não vem preenchida.

Biometria desta tela: [[library-components-biometria-e-sessao]]. Recuperação: [[library-components-recuperar-senha]]. Pé: [[library-components-em-que-pe-esta]].
