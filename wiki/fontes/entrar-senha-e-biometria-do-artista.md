---
tipo: fonte
arquivo: "ingeridos/Entrar, senha e biometria do artista.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_worker; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Entrar, senha e biometria do artista"]
---

# Entrar, senha e biometria do artista

Volta para [[mapa-do-app-do-artista]].

Fluxo próprio deste app: login, esqueci a senha, código, nova senha, digital ou rosto. A biometria também liga e desliga no [[perfil-do-artista]]. A [[abertura-do-artista]] não dispara a biometria sozinha. Quem ainda não tem conta sai daqui para o [[cadastro-do-artista]].

A extração do artista não cita `@wecareu/auth-flow`.

**Pé:** construído. Dá para entrar, recuperar a senha, trocar a senha já logado e ligar digital ou Face ID. A frase de credencial inválida quase não aparece: senha errada e falha de serviço caem em **Erro ao entrar! Tente novamente**. O texto **E-mail ou senha inválidos** existe e não é o aviso que este pedido devolve. A troca a partir do perfil não pede a senha atual, embora o texto **Senha Atual** exista. A biometria não entra sozinha na abertura.

## Entrar

O login abre por cima da abertura, com logo, fechar e o título **Vamos entrar na sua conta:**.

Campos: **Digite seu e-mail** e **Digite sua senha**. **Entrar** confere na hora do toque. E-mail vazio, e-mail em formato estranho, ou senha com menos de 8 caracteres, inclusive vazia, mostram uma frase. Com e-mail aceito e senha de pelo menos 8 caracteres, o app pede a entrada ao serviço. A senha vai cifrada.

Se o serviço aceita, a pessoa entra nas abas, começando pelo [[inicio-do-artista]]. Em seguida, se o aparelho tem biometria e ela ainda não está ligada com uma credencial válida, o aparelho pede para usar Face ID ou digital nas próximas vezes. Cancelar esse pedido não desfaz a entrada.

Abaixo: **Esqueci minha senha**, **Cadastrar** e **Entrar com Biometria**. O atalho de biometria só aparece se ela já foi ligada e a credencial ainda está guardada. Não aparece na abertura. Fechar volta para a tela de baixo, em geral a abertura. Quem já tem sessão aceita não passa por este formulário.

## Esqueci a senha

Três passos.

1. **Esqueci minha senha.** E-mail e **Enviar e-mail de recuperação**. A tela não confere se o e-mail existe. Se segue, abre o código.
2. **Código.** No máximo 6 números. **Validar código**. **Reenviar código** já abre contando 2 minutos.
3. **Vamos alterar sua senha:**. A lista **Sua senha deve conter:** fala em número, minúscula, maiúscula, 8 caracteres, símbolo e senhas iguais. Esses itens mudam de cor e não impedem o botão. O botão trava em vazio, menos de 8 e senhas diferentes.

No sucesso, a pessoa volta ao login e o título vira **Senha alterada com sucesso! Faça login com sua nova senha.** Ela não entra sozinha. A senha nova vai cifrada. Se o serviço recusa: **Erro ao redefinir a senha!**

No [[cadastro-do-artista]], o que bloqueia a senha é mais estreito (letras sem acento, números e `@ $ ! % * ? &`). Nestas telas de senha nova, a lista não trava o botão. No login, a senha só precisa ter 8 caracteres.

## Troca já logado

No perfil, **Alterar Senha**. Três passos: confirmar o e-mail da conta, código de 6 dígitos (o reenvio espera 60 segundos, não os 2 minutos da recuperação) e senha nova. **Salvar Nova Senha** só exige os dois campos preenchidos e iguais. Não há campo de senha atual. A senha nova vai como foi digitada, sem a cifra do outro caminho. Se o serviço confirma, o alerta **Senha Alterada** volta ao perfil. A pessoa continua logada.

## Biometria

O aparelho oferece biometria quando tem o recurso e a pessoa já cadastrou digital ou rosto nele. Sem isso, o perfil não mostra o interruptor e o login não mostra o atalho.

No primeiro login com senha, o pedido aparece na hora. Aceitar guarda o e-mail e a senha daquela entrada. **Não permitir** não desfaz a entrada. No perfil, a linha **Biometria** diz **Ativada** ou **Desativada**. Ao ligar, o app usa o e-mail e a senha da última entrada que ainda guarda. Isso some ao sair da conta.

Na próxima abertura, a biometria não entra sozinha. A pessoa vê os slides, toca **Já tenho uma conta** e, no login, **Entrar com Biometria**. Aceitar abre o [[inicio-do-artista]]. Se a credencial guardada não entra mais, o app apaga a biometria e a credencial. O atalho some. A frase na tela é **Falha na autenticação biométrica**.

**Desligar** no perfil pede confirmação. Sair da conta apaga biometria e credencial, sem esse alerta. Se desligar falha, o texto "Não foi possível desativar a biometria" não é mostrado e o interruptor segue ligado. Se não há cópia da senha ao ligar, o alerta de erro pode mostrar uma frase em inglês ("Error enabling biometric authentication").
