---
tipo: extração
tema: Entrar, senha e biometria
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: construído, com falha no aviso de senha errada, na lista da nova senha e na biometria já salva
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Entrar, senha e biometria

Volta para o [[Mapa do app do cliente]].

Esta é a porta de quem já tem conta: entrar com e-mail e senha, recuperar a senha por um código no e-mail, e entrar de novo com digital ou rosto. Quem ainda não tem conta sai daqui para o [[Criar conta]]. A abertura que tenta a biometria sozinha está em [[Primeira entrada]].

**Pé:** construído. Dá para entrar, pedir o código, definir outra senha e usar digital ou rosto quando isso já foi aceito. Três falhas aparecem no caminho. Senha errada não diz que o e-mail ou a senha não servem. A lista da nova senha mostra regras que o botão não cobra, e a linha "as senhas iguais" não marca nunca. Redefinir a senha não atualiza a digital ou o rosto já salvos.

Quem já está dentro troca a senha por outro caminho, em [[Meu perfil]]. Esta nota não descreve essa tela.

## Por onde se chega

- Na abertura, **Já tenho uma conta**.
- No carrossel da [[Primeira entrada]], o mesmo **Já tenho uma conta**, embaixo dos três passos.
- Se a biometria sozinha falha na abertura, o app cai aqui. O carrossel em si está em [[Primeira entrada]].
- Depois de redefinir a senha, esta mesma tela abre de novo, com outra frase no título.

Se a sessão ainda vale ao abrir o app, a pessoa não vê o login: cai no [[Início]]. Se a sessão não vale mais, a biometria salva é desligada junto.

Estas telas abrem por cima da anterior. No canto há um X para fechar e voltar. Não há seta de voltar.

Uma tela antiga de visitante também tem **Já tenho uma conta**, e outra, "Qual é seu endereço?", tem **Entrar ou Cadastrar**. Nenhuma das duas entra neste caminho. Ver [[Primeira entrada]] e [[O que ainda não está no app]].

## Entrar

Logo da WeCareU e o título **Vamos entrar na sua conta:**

- **E-mail.** O exemplo no campo é "Digite seu e-mail". O app não passa para minúsculas: segue como foi digitado.
- **Senha.** O exemplo é "Digite sua senha". Dá para mostrar ou esconder. A única regra nesta tela é ter pelo menos 8 caracteres. Não há lista de maiúscula, número ou símbolo.

**Entrar** começa aceso. Se o toque não passa:

- E-mail vazio: "E-mail é obrigatório".
- E-mail que não parece e-mail: "E-mail inválido".
- Senha com menos de 8 caracteres: "A senha deve ter pelo menos 8 caracteres".

Só uma frase aparece por vez. O e-mail vem na frente da senha. O campo em erro treme ao sair dele. **Entrar** apaga enquanto houver essa reclamação e acende de novo quando a pessoa edita o campo que reclamou. A checagem roda outra vez no próximo toque.

Enquanto a entrada é enviada, a tela fica em carregamento.

Se der certo, a pessoa entra e o app abre o [[Início]]. Em seguida, se o aparelho tem digital ou rosto e isso ainda não está ligado com uma credencial salva, o sistema pede para usar na próxima vez. A entrada já foi aceita: recusar não desfaz. O detalhe está em **Digital ou rosto**, abaixo.

Se a entrada falha, a frase é **Erro ao entrar! Tente novamente.** A frase pronta "E-mail ou senha inválidos" existe nos textos e esta tela não a usa. Senha errada, conta inexistente e falha de rede caem na mesma frase. **Entrar** continua aceso. Editar o e-mail ou a senha apaga a frase.

Abaixo do botão:

- **Esqueci minha senha.** Abre a recuperação.
- **Cadastrar.** Abre o [[Criar conta]].

**Entrar com Biometria** só aparece no meio, entre **Entrar** e **Esqueci minha senha**, quando a biometria já foi aceita e a credencial ainda está no aparelho.

## Esqueci a senha

Título: **Esqueci minha senha.** Um campo, exemplo "Digite seu e-mail", e o botão **Enviar e-mail de recuperação**.

O botão fica apagado até o e-mail parecer um e-mail: algo, arroba, algo, ponto, algo. Não cobra o mínimo de 5 caracteres nem o máximo de 254 que o [[Criar conta]] cobra. As frases "E-mail é obrigatório" e "E-mail inválido" estão preparadas e não aparecem, porque o botão apagado não deixa tocar.

Se o envio dá certo, abre a tela do código. Se falha, fica nesta tela com **Erro ao enviar e-mail! Tente novamente.** O app não diz, aqui, se o e-mail existe ou não.

## O código

Texto: "Se seu e-mail estiver em nosso sistema, você receberá um código por e-mail. Digite-o abaixo:"

O e-mail digitado na tela anterior não é mostrado.

- Campo **Código.** Teclado numérico, no máximo 6 caracteres.
- **Validar código** fica apagado até haver 6 caracteres. Não exige que os seis sejam números: qualquer 6 caracteres acendem o botão.
- **Reenviar código** já entra contando 2 minutos, no formato (2m 0s). Abaixo de 1 minuto fica (59s), (58s) e assim por diante. Enquanto conta, o texto fica mais fraco e tocar não reenvia. No zero, o link volta ao normal e pede o e-mail de novo. Não há uma frase de "código reenviado": a contagem recomeça em 2 minutos. Se o reenvio falha, aparece **Erro ao enviar e-mail! Tente novamente.**

"Código é obrigatório" e "Código deve ter o comprimento correto" estão preparadas e não aparecem, pelo mesmo motivo do botão apagado.

Se o código não serve, a frase é **Erro ao validar código.** A mesma frase cobre código errado e falha ao consultar. Se serve, abre a nova senha. O código continua valendo nessa próxima tela.

## Nova senha

Título: **Vamos alterar sua senha:**

- **Senha** e **Confirme sua senha.** Dá para mostrar ou esconder cada uma.
- Uma lista marca o que já foi cumprido:
  - mínimo de 8 caracteres
  - ao menos 1 letra maiúscula
  - ao menos 1 letra minúscula
  - ao menos 1 número
  - ao menos 1 caractere especial
  - as senhas iguais

**Redefinir Senha** não espera a lista inteira. Acende quando as duas têm pelo menos 8 caracteres e são iguais. Maiúscula, minúscula, número e caractere especial podem ficar por cumprir.

A linha "As senhas devem ser iguais" não marca, mesmo quando os dois campos estão iguais.

"Senha é obrigatória", "Senha deve ter pelo menos 8 caracteres", "Confirmação de senha é obrigatória", "Confirmação de senha deve ter pelo menos 8 caracteres" e "As senhas não conferem" estão preparadas e não aparecem: o botão fica apagado até a regra mínima passar.

Se dá certo, volta ao login e o título vira **Senha alterada com sucesso! Faça login com sua nova senha.** E-mail e senha vêm vazios. A pessoa não entra sozinha.

Se falha, fica nesta tela com **Erro ao redefinir a senha!**

Esta troca não atualiza a digital ou o rosto já salvos. A credencial antiga continua até uma tentativa com biometria falhar.

## Digital ou rosto

Há três momentos. O interruptor de quem já entrou é outro: no [[Meu perfil]], a linha **Biometria** mostra **Ativada** ou **Desativada**, só se o aparelho tiver digital ou rosto cadastrados.

### Logo depois de entrar com a senha

O pedido só acontece se o aparelho tem biometria em uso e ainda não há uma credencial salva e ligada.

O texto depende do que o aparelho informa. Se reconhece o rosto, diz **Use o Face ID para fazer login futuramente.** Se reconhece a digital e não o rosto, diz **Use sua impressão digital para fazer login futuramente.** Nos outros casos, **Use sua biometria para fazer login futuramente.**

Recusar está como **Não permitir.** O app também manda o rótulo **Usar senha** e não bloqueia a senha do aparelho. Se esse botão aparece, depende do sistema.

Aceitar liga a biometria para a próxima vez, sem um aviso de sucesso. Recusar deixa a pessoa dentro da conta, com a biometria desligada, e sem frase de erro. As frases prontas "Configure o Face ID", "Configure sua impressão digital" e "Configure sua biometria" existem nos textos e este pedido não as usa. Ele fica em português mesmo quando o restante do app está em inglês.

### O botão Entrar com Biometria

Só na tela de login, e só se já está ligado e a credencial salva ainda existe.

O aviso do sistema, este sim, segue o idioma do app:

- rosto: **Use o Face ID para entrar**
- digital, sem rosto: **Use sua impressão digital para entrar**
- outros casos: **Autentique-se para entrar**

Recusar está como **Cancelar.** De novo o app manda **Usar senha** e não bloqueia a senha do aparelho.

Se a pessoa confirma e a credencial ainda serve, entra no [[Início]].

Se cancela, se a biometria falha ou se a senha salva não serve mais, a tela mostra só **Falha na autenticação biométrica.** Esta frase é fixa em português. Não usa "Tente novamente". Também não usa as frases prontas que existem nos textos e não aparecem aqui:

- "Autenticação biométrica cancelada ou falhou"
- "Credenciais biométricas desatualizadas. Entre novamente."
- "Credenciais não encontradas. Entre novamente para configurar a biometria."
- "Autenticação biométrica não disponível neste dispositivo"
- "Autenticação biométrica não disponível ou não habilitada"

Quando a senha salva não serve mais, a biometria é desligada e o botão some. A frase da tela continua sendo a mesma, genérica.

### Sozinha, ao abrir

Se já está ligada, o aparelho tem o recurso e a credencial ainda existe, a [[Primeira entrada]] tenta entrar sozinha. Se essa tentativa falha, cai no login, sem a frase "Falha na autenticação biométrica". Se a falha foi a senha salva não servir, a biometria é desligada antes de mostrar o login, e o botão não aparece.

Sair da conta, em [[Meu perfil]], também desliga a biometria. A que acabou de ser aceita no login sai junto. A próxima vez pede e-mail e senha, e o pedido do sistema pode voltar.

## O que este fluxo ainda não faz

- Não distingue senha errada de outras falhas. A frase "E-mail ou senha inválidos" não aparece.
- Não mostra, na recuperação, se o e-mail está vazio ou malformado. O botão fica apagado. Também não repete o e-mail na tela do código.
- Não exige que o código tenha só números. Seis caracteres quaisquer acendem **Validar código**.
- Não avisa, com uma frase própria, que o código foi reenviado. A contagem de 2 minutos recomeça.
- Não cobra, na nova senha, as regras que a lista mostra além dos 8 caracteres e da confirmação igual. A linha das senhas iguais não marca nunca.
- Não atualiza a biometria já salva quando a senha é redefinida por aqui. A tentativa seguinte falha, desliga a biometria e, no botão, só diz "Falha na autenticação biométrica".
- Não explica o cancelamento da biometria no botão com a frase pronta. Cancelar e falhar usam o mesmo texto.
- Não oferece biometria em aparelho sem digital ou rosto cadastrados, e não explica isso na tela de login.
- Não é a troca de senha de quem já entrou. Isso fica em [[Meu perfil]].
