---
tipo: fonte
arquivo: "ingeridos/Entrar, senha e biometria.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_client; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Entrar, senha e biometria"]
---

# Entrar, senha e biometria

Volta para [[mapa-do-app-do-cliente]].

Fluxo próprio deste app: login, esqueci a senha, código, nova senha, digital ou rosto. A biometria também liga e desliga no perfil. ([[meu-perfil]]) A abertura que tenta a biometria sozinha está em [[primeira-entrada]]. Quem ainda não tem conta sai daqui para [[criar-conta]].

A extração do cliente não cita `@wecareu/auth-flow`.

**Pé:** construído, com falha no aviso de senha errada, na lista da nova senha e na biometria já salva. Dá para entrar, pedir o código, definir outra senha e usar digital ou rosto quando isso já foi aceito. Senha errada não diz que o e-mail ou a senha não servem. A lista da nova senha mostra regras que o botão não cobra, e a linha "as senhas iguais" não marca nunca. Redefinir a senha não atualiza a digital ou o rosto já salvos.

Quem já está dentro troca a senha por outro caminho, em [[meu-perfil]]. Esta nota não descreve essa tela.

## Por onde se chega

Na abertura, **Já tenho uma conta**. No carrossel, o mesmo link embaixo dos três passos. Se a biometria sozinha falha na abertura, o app cai aqui. Depois de redefinir a senha, esta mesma tela abre de novo, com outra frase no título.

Se a sessão ainda vale ao abrir o app, a pessoa não vê o login: cai no [[inicio]]. Se a sessão não vale mais, a biometria salva é desligada junto.

As telas abrem por cima da anterior, com um X para fechar. Não há seta de voltar. A tela antiga de visitante e a tela "Qual é seu endereço?" não entram neste caminho.

## Entrar

Título: **Vamos entrar na sua conta:**

O e-mail segue como foi digitado: o app não passa para minúsculas. A senha dá para mostrar ou esconder. A única regra nesta tela é ter pelo menos 8 caracteres. **Entrar** começa aceso. As frases de campo, uma por vez, são "E-mail é obrigatório", "E-mail inválido" e "A senha deve ter pelo menos 8 caracteres".

Se der certo, a pessoa entra e o app abre o Início. Em seguida, se o aparelho tem digital ou rosto e isso ainda não está ligado com uma credencial salva, o sistema pede para usar na próxima vez. Recusar não desfaz a entrada.

Se a entrada falha, a frase é **Erro ao entrar! Tente novamente.** A frase pronta "E-mail ou senha inválidos" existe nos textos e esta tela não a usa. Senha errada, conta inexistente e falha de rede caem na mesma frase.

**Esqueci minha senha** abre a recuperação. **Cadastrar** abre o cadastro. **Entrar com Biometria** só aparece quando a biometria já foi aceita e a credencial ainda está no aparelho.

## Esqueci a senha, o código e a nova senha

**Esqueci minha senha.** O botão **Enviar e-mail de recuperação** fica apagado até o e-mail parecer um e-mail. Não cobra o mínimo de 5 nem o máximo de 254 do cadastro. As frases "E-mail é obrigatório" e "E-mail inválido" estão preparadas e não aparecem. Se falha, **Erro ao enviar e-mail! Tente novamente.** O app não diz se o e-mail existe.

O código. Texto: "Se seu e-mail estiver em nosso sistema, você receberá um código por e-mail. Digite-o abaixo:" O e-mail da tela anterior não é mostrado. **Validar código** acende com 6 caracteres, não exige que os seis sejam números. **Reenviar código** entra contando 2 minutos, no formato (2m 0s). Não há frase de "código reenviado": a contagem recomeça. Se o código não serve, **Erro ao validar código.** A mesma frase cobre código errado e falha ao consultar.

**Vamos alterar sua senha:** A lista marca mínimo de 8, maiúscula, minúscula, número, especial e senhas iguais. **Redefinir Senha** acende quando as duas têm pelo menos 8 caracteres e são iguais. Maiúscula, minúscula, número e especial podem ficar por cumprir. A linha "As senhas devem ser iguais" não marca, mesmo quando os dois campos estão iguais.

Se dá certo, volta ao login e o título vira **Senha alterada com sucesso! Faça login com sua nova senha.** E-mail e senha vêm vazios. A pessoa não entra sozinha. Se falha, **Erro ao redefinir a senha!** Esta troca não atualiza a digital ou o rosto já salvos. A credencial antiga continua até uma tentativa com biometria falhar.

## Digital ou rosto

Há três momentos. O interruptor de quem já entrou fica em [[meu-perfil]]: a linha **Biometria** mostra **Ativada** ou **Desativada**, só se o aparelho tiver digital ou rosto cadastrados.

Logo depois de entrar com a senha, o pedido só acontece se o aparelho tem biometria em uso e ainda não há credencial salva e ligada. O texto depende do aparelho: **Use o Face ID para fazer login futuramente.**, **Use sua impressão digital para fazer login futuramente.** ou **Use sua biometria para fazer login futuramente.** Recusar está como **Não permitir.** Aceitar liga para a próxima vez, sem aviso de sucesso. Recusar deixa a pessoa dentro da conta, com a biometria desligada. Este pedido fica em português mesmo quando o restante do app está em inglês.

O botão **Entrar com Biometria**, na tela de login, usa o idioma do app: **Use o Face ID para entrar**, **Use sua impressão digital para entrar** ou **Autentique-se para entrar**. Se cancela, se a biometria falha ou se a senha salva não serve mais, a tela mostra só **Falha na autenticação biométrica.** Quando a senha salva não serve mais, a biometria é desligada e o botão some. A frase continua a mesma.

Sozinha, ao abrir: se já está ligada, o aparelho tem o recurso e a credencial ainda existe, a [[primeira-entrada]] tenta entrar sozinha. Se essa tentativa falha, cai no login, sem a frase "Falha na autenticação biométrica". Se a falha foi a senha salva não servir, a biometria é desligada antes de mostrar o login.

Sair da conta também desliga a biometria. A próxima vez pede e-mail e senha.
