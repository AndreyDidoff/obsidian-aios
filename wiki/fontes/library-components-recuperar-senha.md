---
tipo: fonte
arquivo: ingeridos/library-components-recuperar-senha.md
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-components, pacote @wecareu/auth-flow; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Recuperar a senha"]
---

# Recuperar a senha

Volta para [[library-components-o-que-entrega]]. Pacote `@wecareu/auth-flow` 0.1.0. O atalho é "Esqueci minha senha", na tela de entrar. ([[library-components-entrar-na-conta]])

Três telas, no fluxo por padrão. Quem monta o app pode deixá-las de fora. A entrada não consulta esse interruptor: o link continua. Com as telas de fora, o toque não tem destino. A tela seguinte só abre se o serviço de conta responder que deu certo. Cada tela tem um botão de fechar que volta um passo. Só o sucesso da troca salta direto para a entrada.

1. Pedir o e-mail. Título "Esqueceu sua senha?". O e-mail é obrigatório e válido, segue em minúsculas e sem espaços nas pontas, e as telas seguintes usam esse mesmo endereço. Enquanto o pedido corre, o botão desliga. O indicador de espera que existe na tela não chega a aparecer nesse pedido.
2. Código de exatamente 6 caracteres, letras e números. O que a pessoa digita vira maiúsculas; o resto é descartado. A frase da tela não confirma se a conta existe, e o e-mail anterior não aparece. "Reenviar código" espera 2 minutos: abre em "Reenviar código (2m 00s)" e desce até liberar. Se o pedido volta sem estourar, os 2 minutos recomeçam, mesmo quando o serviço só diz que não deu certo. Não há aviso de reenvio. Se a chamada estoura, a contagem fica como está.
3. Senha nova e confirmação. Regras: mínimo 8, minúscula, maiúscula, número, caractere especial e confirmação igual. A lista marca em verde, ao vivo, o que já vale. "Trocar senha" não espera a lista fechar. O especial aceito é um destes: ! @ # $ % * ( ) { } + = | / ? . - A lista não enumera esses sinais.

Quando a senha nova é aceita, volta ao login com o sinal `showRecoverySuccess`. A tela de login ignora esse sinal: não aparece aviso de sucesso. Os textos não trazem frase pronta para esse sucesso.

As frases de erro estão escritas em português e em inglês e, em vários casos, não entram na tela. "Falha ao solicitar recuperação de senha" e "Código inválido ou expirado" não são gravadas quando o serviço só devolve falso. Pedir, validar e trocar ficam na mesma tela, sem essa explicação. Se a chamada quebra, o registro pode ir só para o console: na primeira tela, e também ao validar e ao reenviar. Na troca, a tela não apanha o estouro nem escreve frase, e "Trocar senha" continua tocável. Essa chamada não liga o carregamento que o botão consulta.

Não há tela de troca de senha para quem já está logado. Isso é capacidade do contrato, sem tela. ([[library-components-biometria-e-sessao]], [[library-components-em-que-pe-esta]])
