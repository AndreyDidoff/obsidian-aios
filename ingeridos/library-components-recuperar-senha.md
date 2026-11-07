---
titulo: Recuperar a senha
repositorio: library-components
pacote: "@wecareu/auth-flow"
extraido_em: 2026-10-21
tipo: extracao-produto
tema: recuperar-senha
---

> **Aviso de versionamento (extração via IA — Cursor):** Retrato do repositório `library-components` em 21/10/2026. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Se conflitar com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Pacote: `@wecareu/auth-flow`

# Recuperar a senha

O caminho tem três telas. Cada uma traz um botão de fechar que volta: a primeira para "Entre na sua conta", a segunda para o e-mail, a terceira para o código. Só o sucesso da troca salta direto para a entrada.

## Caminho da pessoa

O atalho é "Esqueci minha senha", na tela de entrar. O resto dessa tela está em [[library-components-entrar-na-conta]].

As três telas entram no fluxo por padrão. Quem monta o app pode deixá-las de fora. A tela de login mostra o atalho sempre: o link é fixo e não consulta essa opção. Com as telas de fora, o toque ainda tenta abrir a primeira, que não está montada.

A tela seguinte só abre se o serviço de conta responder que deu certo.

## Passo a passo com as frases reais

### Pedir o código

"Esqueceu sua senha?"

"Digite seu endereço de email e enviaremos um código para redefinir sua senha."

Um campo de e-mail, exemplo "seu@email.com". Botão "Enviar e-mail de recuperação".

O e-mail é obrigatório e válido. Vazio, a frase é "Email é obrigatório". Fora do formato, "Digite um endereço de email válido". O valor segue em minúsculas, sem espaços nas pontas, e as telas seguintes usam esse mesmo e-mail. Enquanto o pedido corre, o botão desliga. O indicador de espera que existe na tela não chega a aparecer nesse pedido.

### Digitar o código

"Digite o código de verificação"

"Se seu e-mail estiver em nosso sistema, você receberá um código por e-mail. Digite-o abaixo:"

A frase não confirma se a conta existe. O e-mail anterior não aparece.

O código tem exatamente 6 letras ou números. O exemplo é "000000". O que a pessoa digita vira maiúsculas, e caractere fora de letra ou número é ignorado. Não passa de seis. O botão é "Validar código". Com menos de seis, a frase é "O código deve ter exatamente 6 caracteres". "O código deve conter apenas letras e números" está escrito, mas o campo já descarta o resto, então quem digita esbarra na contagem. Seguem o código em maiúsculas e o mesmo e-mail. Só avança se a validação der certo.

"Reenviar código" começa bloqueado por 120 segundos. O texto é "Reenviar código (Xm YYs)": abre em "Reenviar código (2m 00s)" e desce, como "Reenviar código (1m 59s)" e "Reenviar código (0m 09s)", até liberar "Reenviar código". Reenviar pede o código de novo para o mesmo e-mail. Se o pedido volta sem estourar, os 2 minutos recomeçam, mesmo quando o serviço só diz que não deu certo. Não há aviso de reenvio. Se a chamada estoura, a contagem fica como está.

### Escolher a senha nova

"Vamos mudar sua senha:"

"Sua nova senha deve atender a todos os requisitos abaixo."

Dois campos, senha nova e confirmação, com bolinhas de exemplo. "Nova senha" e "Confirmar nova senha" existem nos textos e não aparecem na tela. Mostrar e ocultar nos dois, anunciados como "Mostrar" e "Ocultar".

A lista marca em verde, ao vivo, o que já vale. "Trocar senha" não espera a lista fechar: o toque cedo mostra a cobrança da regra que falta.

Se der certo, volta para "Entre na sua conta" levando um sinal de sucesso. A tela de login não lê esse sinal. Não há mensagem de senha alterada, e os textos não trazem frase pronta para esse sucesso.

## Regras da nova senha

A lista, nesta ordem:

1. "Contém uma letra minúscula"
2. "Contém uma letra maiúscula"
3. "Contém um número"
4. "Contém um caractere especial"
5. "Pelo menos 8 caracteres"
6. "As senhas coincidem"

O item cumprido ganha marcador verde e o texto deixa de ficar apagado. "As senhas coincidem" só marca quando a senha nova já tem algum caractere e os dois campos são iguais. Vazios não coincidem. Espaço conta e precisa ser o mesmo nos dois.

O especial aceito é um destes: ! @ # $ % * ( ) { } + = | / ? . - A lista não enumera esses sinais. Só diz "Contém um caractere especial".

No toque antecipado, as cobranças mudam de frase:

- "A senha deve ter pelo menos 8 caracteres"
- "Inclua pelo menos uma letra minúscula"
- "Inclua pelo menos uma letra maiúscula"
- "Inclua pelo menos um número"
- "Inclua pelo menos um caractere especial (!@#$%*(){}+=|/?.-)"
- "As senhas devem coincidir"

## O que a pessoa não vê quando dá errado

Lacuna do fluxo: "Falha ao solicitar recuperação de senha" e "Código inválido ou expirado" estão escritas, e a recuperação não grava essas frases quando o serviço só devolve falso. Pedir o código, validar e trocar a senha ficam na mesma tela, sem essa explicação.

Se a chamada estoura, a primeira tela só registra no console. A pessoa pode não ver explicação. Validar e reenviar, na segunda tela, também só vão para o console. Na troca, a tela não apanha o estouro nem escreve frase, e "Trocar senha" continua tocável: essa chamada não liga o carregamento que o botão consulta.

## O que fica de fora

Não há tela de trocar senha estando já logado. Isso é capacidade prevista no contrato do app, sem tela. O que existe de sessão está em [[library-components-biometria-e-sessao]].

## Notas relacionadas

- [[library-components-o-que-entrega]]
- [[library-components-entrar-na-conta]]
- [[library-components-biometria-e-sessao]]
- [[library-components-em-que-pe-esta]]

## Fontes

- packages/auth-flow/src/screens/ForgotPassword/index.tsx
- packages/auth-flow/src/screens/SecondStage/index.tsx
- packages/auth-flow/src/screens/ResetPassword/index.tsx
- packages/auth-flow/src/components/forms/ResetPasswordForm/index.tsx
- packages/auth-flow/src/components/forms/shared/PasswordCriteria.tsx
- packages/auth-flow/src/i18n/locales/pt.json
- packages/auth-flow/src/navigation/AuthFlowNavigator.tsx
- packages/auth-flow/src/contexts/AuthContext.tsx (pedido do código, validação do código e aplicação da senha nova)
- packages/auth-flow/src/screens/SignIn/index.tsx (o sinal de sucesso não é lido; "Esqueci minha senha" permanece)
- packages/auth-flow/src/components/forms/LoginForm/index.tsx (atalho fixo na entrada)
- packages/auth-flow/src/services/types.ts (troca de senha já autenticada, só no contrato, sem tela)
