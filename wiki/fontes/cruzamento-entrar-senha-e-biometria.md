---
tipo: fonte
arquivo: "ingeridos/Cruzamento - entrar senha e biometria.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 que cruza ui_client, ui_worker, library-design-system e library-components; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Cruzamento — entrar, senha e biometria"]
---

# Cruzamento — entrar, senha e biometria

A porta é [[cruzamento-como-ler]].

São três percursos. O app do cliente e o app do artista têm cada um o próprio caminho de entrar, recuperar a senha e usar digital ou rosto. Os dois estão mais perto um do outro do que da peça compartilhada: o título da entrada, a regra da senha nessa tela e o aviso depois da senha nova batem entre os apps e mudam na peça. A peça `@wecareu/auth-flow`, versão 0.1.0, existe desenhada e não está ligada a nenhum dos dois apps.

A peça mora à parte. O percurso e os textos ficam nela; botões, campos e cores vêm do kit. A sessão fica no aparelho. Quem fala com o servidor é o app que ligar o serviço de conta. O cadastro dessa peça não faz nada. O sucesso da senha nova não aparece. A biometria manda um resumo da senha. Fonte do pé: [[library-components-em-que-pe-esta]].

No cliente, o login chega por **Já tenho uma conta**, na abertura e no carrossel. Se a biometria sozinha falha ao abrir, também cai aqui. As telas abrem por cima, com um X para fechar. Pé: construído, com falha no aviso de senha errada, na lista da nova senha e na biometria já salva ([[entrar-senha-e-biometria]]).

No artista, o login abre por cima da abertura, com logo e fechar no canto. Fechar volta para a tela de baixo, em geral a abertura. Dá para entrar, recuperar a senha, trocar a senha já logado e ligar digital ou Face ID. A frase de credencial inválida quase não aparece. A senha errada cai na mensagem genérica. A troca logada não pede a senha atual. A biometria não entra sozinha na abertura. O mapa registra o percurso como construído ([[entrar-senha-e-biometria-do-artista]], [[mapa-do-app-do-artista]]).

## O que coincide entre os apps

A peça compartilhada registra outro texto, ou não registra o aviso.

- Os dois títulos de entrada são **Vamos entrar na sua conta:**. A peça usa **Entre na sua conta**, com o apoio "Use seu email e senha para continuar." As notas dos apps não registram esse apoio.
- Na entrada, os dois cobram pelo menos 8 caracteres, com a frase "A senha deve ter pelo menos 8 caracteres". A peça deixa passar qualquer senha preenchida. Vazia, a frase da peça é "Senha é obrigatória". Oito caracteres, maiúscula, minúscula, número e caractere especial valem na troca de senha da peça, não na entrada.
- Os dois devolvem a pessoa ao login com **Senha alterada com sucesso! Faça login com sua nova senha.** Ela não entra sozinha. A peça volta para **Entre na sua conta** com um sinal de sucesso, e a tela de entrada ignora esse sinal. Não há mensagem de senha alterada, e os textos não trazem frase pronta para esse sucesso.
- Os dois chamam a recuperação de **Esqueci minha senha** e a senha nova de **Vamos alterar sua senha:**, com o botão **Redefinir Senha**. A peça usa **Esqueceu sua senha?**, **Vamos mudar sua senha:** e **Trocar senha**.
- Os dois usam "E-mail é obrigatório" e "E-mail inválido" na entrada. A peça usa "Email é obrigatório" e "Digite um endereço de email válido".
- Se a entrada falha, os dois mostram **Erro ao entrar! Tente novamente.** Os dois têm o texto "E-mail ou senha inválidos" e a tela não o usa. No cliente, senha errada, conta inexistente e falha de rede caem na frase genérica. No artista, senha errada e falha de serviço caem nessa frase; a nota não registra conta inexistente nesse aviso. A peça usa "Falha no login. Verifique suas credenciais." e junta senha errada, conta inexistente e falha de rede nessa frase.
- Na entrada, os dois mostram uma frase por vez, o e-mail na frente da senha, e o campo em erro treme ao sair dele. A peça junta as frases numa lista acima dos campos, com o exemplo "seu@email.com" e pontinhos na senha.
- Os dois atalhos de biometria no login se chamam **Entrar com Biometria**. Depois de entrar com a senha, os dois pedem "Use o Face ID para fazer login futuramente", "Use sua impressão digital para fazer login futuramente" ou "Use sua biometria para fazer login futuramente", com **Não permitir** e **Usar senha**. A peça troca o texto do atalho conforme o estado ("Entrar com biometria", "Habilitar login biométrico" ou "Desabilitar login biométrico") e, se o app não traduzir o pedido do sistema, mostra em inglês "Authenticate to continue".
- Nos dois, **Cadastrar** abre o cadastro daquele app ([[criar-conta]], [[cadastro-do-artista]]). Na peça, "Não tem uma conta? Cadastrar" aparece habilitado e o toque não abre cadastro e não avisa nada.
- Na senha nova, os dois mostram uma lista com tamanho, maiúscula, minúscula, número, caractere especial e senhas iguais. Maiúscula, minúscula, número e caractere especial não impedem o botão. O que trava é o mínimo de 8 e a confirmação. A redação e a ordem não são as mesmas: no cliente a lista começa pelo mínimo de 8 caracteres; no artista, sob o título **Sua senha deve conter:**, começa por "Pelo menos um número". A nota do cliente não registra esse título.

Os três percursos registram o botão **Enviar e-mail de recuperação**, a frase "Se seu e-mail estiver em nosso sistema, você receberá um código por e-mail. Digite-o abaixo:", uma espera de reenvio na casa de 2 minutos, e a falha **Falha na autenticação biométrica**.

## Onde divergem

- E-mail na entrada. No cliente, segue como foi digitado e a nota não registra limpeza de espaços nas pontas. No artista, não vira minúsculo na tela, não cobra o tamanho de 5 a 254 que o cadastro do artista cobra, e a nota não registra o valor enviado nem se os espaços das pontas saem. Na peça, sai limpo nas pontas e em minúsculas, e o e-mail da recuperação segue em minúsculas para as telas seguintes.
- Esqueci a senha. No cliente, o botão fica apagado até o e-mail parecer um e-mail, e as frases de e-mail vazio ou inválido estão preparadas e não aparecem. No artista, o botão tem cara de desligado e o toque ainda mostra essas frases. Na peça, as frases aparecem, com outro texto para o e-mail fora do formato.
- Código. No cliente, o teclado é numérico, no máximo 6, e 6 caracteres quaisquer acendem **Validar código**. "Código é obrigatório" e "Código deve ter o comprimento correto" estão preparadas e não aparecem. No artista, o campo é só números, no máximo 6, e essas duas frases aparecem. Na peça, são 6 letras ou números, o exemplo é "000000", o digitado vira maiúsculas, e menos de seis diz "O código deve ter exatamente 6 caracteres". Nenhuma das notas de app registra essa conversão para maiúsculas. A do cliente não registra letras no código. A do artista não registra caractere que não seja número.
- Contagem do reenvio. No cliente, abre em (2m 0s) e, abaixo de 1 minuto, fica (59s). A nota não registra o formato (1m 59s). No artista, passa por (2m 0s), (1m 59s) e (59s). Na peça, o texto é "Reenviar código (2m 00s)", desce como "Reenviar código (1m 59s)" e "Reenviar código (0m 09s)", e a nota não registra a forma (59s) sem os minutos.
- Lista da senha nova. No cliente, a linha "As senhas devem ser iguais" não marca nunca, mesmo com os dois campos iguais, e as frases de senha obrigatória, tamanho e "As senhas não conferem" estão preparadas e não aparecem. A nota do artista não registra essa linha apagada: número, minúscula, maiúscula e símbolo ficam vermelhos ou verdes e não impedem o botão, e o toque mostra "As senhas não conferem" quando as duas diferem. Na peça, "As senhas coincidem" marca quando a senha nova já tem algum caractere e os dois campos são iguais. **Trocar senha** não espera a lista fechar: o toque cedo mostra a cobrança da regra que falta. As notas da peça dizem que a senha nova pede 8 caracteres, maiúscula, minúscula, número, especial e confirmação igual.
- Sinais do caractere especial. A nota do cliente não lista quais sinais contam. A do artista registra um conjunto da lista, entre eles ! @ # $ % * ( ) e alguns a mais, e diz que esse conjunto não é o do cadastro do artista. A da peça registra outro conjunto escrito: ! @ # $ % * ( ) { } + = | / ? . - Esta nota não trata os conjuntos como o mesmo.
- Aviso de sucesso. No cliente, e-mail e senha voltam vazios. A nota do artista não registra se os campos voltam vazios. Na peça, o sinal de sucesso chega e a tela de entrada não o lê.
- Biometria na abertura. No cliente, a primeira entrada tenta sozinha quando já está ligada. **Entrar com Biometria** só aparece no login, entre **Entrar** e **Esqueci minha senha**, quando já foi aceita e a credencial ainda está no aparelho. Redefinir a senha por aqui não atualiza a digital ou o rosto já salvos. A nota fala em senha salva e não registra um resumo da senha. No artista, o mesmo atalho só no login, se já foi ligada e a credencial ainda está guardada. Não aparece na abertura e não dispara sozinha: a pessoa vê os slides, toca **Já tenho uma conta** e só então o botão. Ao aceitar depois da senha, guarda o e-mail e a senha daquela entrada. A nota não registra se redefinir a senha atualiza essa credencial, nem um resumo da senha, nem a posição do botão entre os outros. A peça não registra tentativa sozinha na abertura. O que a abertura retoma, se pessoa e tokens estiverem salvos juntos, é a sessão. Entrar na peça manda ao serviço um resumo sem volta da senha, não a senha digitada. No login comum da peça, a senha segue como foi digitada. A nota do artista ainda registra que, no login com senha, a senha vai cifrada. A do cliente não registra cifra nem resumo.
- Sair da conta. Nos dois apps, sair desliga a biometria e apaga a credencial. Na peça, sair limpa a sessão e deixa a credencial e a preferência; o atalho pode continuar.
- **Usar senha** no pedido do aparelho. Os dois apps registram esse rótulo no login. A nota do cliente diz que o app não bloqueia a senha do aparelho. A do artista não registra esse bloqueio. A peça diz que PIN e senha do celular não servem de alternativa.
- Idioma do pedido logo depois de entrar. A nota do cliente diz que esse pedido fica em português mesmo com o restante do app em inglês. A do artista não registra o idioma desse pedido. Na peça, sem frase vinda do app, o sistema mostra "Authenticate to continue".
- **Entrar** enquanto o campo reclama. No cliente, o botão apaga durante a reclamação e acende de novo quando a pessoa edita o campo. A nota do artista não registra esse apagar: o botão começa com cara de ativo, o erro daquele campo some ao corrigir, e a conferência é no toque.

Trocar a senha de quem já entrou está no perfil ([[meu-perfil]], [[perfil-do-artista]]) e não existe como tela na peça compartilhada.

Ver [[fluxo-de-entrada]], [[library-components-o-que-entrega]], [[library-components-entrar-na-conta]], [[library-components-recuperar-senha]], [[library-components-biometria-e-sessao]], [[contradicoes-e-lacunas]].
