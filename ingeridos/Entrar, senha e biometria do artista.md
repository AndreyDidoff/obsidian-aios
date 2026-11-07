---
tipo: extração
tema: Entrar, senha e biometria do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: construído; senha errada cai na mensagem genérica, a troca logada não pede a senha atual, e a biometria não entra sozinha na abertura
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Entrar, senha e biometria do artista

Volta para [[Mapa do app do artista]].

**Pé:** construído. Dá para entrar, recuperar a senha, trocar a senha já logado e ligar digital ou Face ID. A frase de credencial inválida quase não aparece. A troca a partir do [[Perfil do artista]] não pede a senha atual, embora o texto **Senha Atual** exista. A biometria não dispara na [[Abertura do artista]].

## Entrar

O login abre por cima da abertura, com o logo, um fechar no canto e o título **Vamos entrar na sua conta:**.

Campos:

- **Digite seu e-mail**
- **Digite sua senha**, com olho para mostrar ou esconder

**Entrar** começa com cara de botão ativo, mesmo com os campos vazios. O app confere na hora do toque, antes de chamar o serviço:

- E-mail vazio: **E-mail é obrigatório**.
- E-mail em formato estranho: **E-mail inválido**.
- Senha com menos de 8 caracteres, inclusive vazia: **A senha deve ter pelo menos 8 caracteres**.

Só uma mensagem aparece por vez. O e-mail vem na frente da senha. Ao corrigir o campo, o erro daquele campo some. Se a pessoa sai de um campo que está errado, ele treme.

Com e-mail aceito e senha de pelo menos 8 caracteres, o app pede a entrada ao serviço da WeCareU. A senha vai cifrada.

Se o serviço aceita, a pessoa entra nas abas, começando pelo [[Início do artista]]. Em seguida, se o aparelho tem biometria e ela ainda não está ligada com uma credencial válida, o aparelho pede para usar Face ID ou digital para as próximas vezes. Detalhe na seção de biometria. Cancelar esse pedido não desfaz a entrada.

Se o serviço recusa ou a chamada falha, a pessoa vê **Erro ao entrar! Tente novamente**. A tela também tem o texto **E-mail ou senha inválidos**, reservado para uma falha de credencial. O aviso que este pedido devolve não é esse. Senha errada e falha de serviço aparecem com a mesma frase.

Abaixo do botão:

- **Esqueci minha senha** abre a recuperação.
- **Cadastrar** abre o [[Cadastro do artista]].
- **Entrar com Biometria** só aparece se a biometria já foi ligada e a credencial ainda está guardada. Não aparece na abertura.

Fechar volta para a tela de baixo, em geral a [[Abertura do artista]].

Quem já tem sessão aceita não passa por este formulário: a abertura some e as abas abrem. Ver [[Abertura do artista]].

## Esqueci a senha

Três passos, cada um com logo e fechar.

### E-mail

Título: **Esqueci minha senha**. Campo: **Digite seu e-mail**. Botão: **Enviar e-mail de recuperação**.

Vazio: **E-mail é obrigatório**. Sem o formato de e-mail: **E-mail inválido**. O botão fica com cara de desligado até o e-mail parecer válido; o toque ainda mostra o erro.

Se o formato passa, o app pede ao serviço da WeCareU que envie o código. Não confere, na tela, se o e-mail existe. Se a chamada falha: **Erro ao enviar e-mail! Tente novamente**. Se segue, abre o código.

### Código

Texto: "Se seu e-mail estiver em nosso sistema, você receberá um código por e-mail. Digite-o abaixo:"

Campo **Código**, só números, no máximo 6. Botão **Validar código**.

- Vazio: **Código é obrigatório**.
- Tamanho diferente de 6: **Código deve ter o comprimento correto**.
- O serviço diz que o código não vale, ou a chamada falha: **Erro ao validar código**. Não há uma frase separada para código errado e para falha de serviço.

**Reenviar código** já abre contando **(2m 0s)** e vai até os segundos, no formato `(1m 59s)` e, abaixo de um minuto, `(59s)`. Enquanto o tempo corre, o link fica cinza e o toque não pede outro código. No zero, volta à cor e o app pede de novo o envio ao serviço. Falha no reenvio: a mesma **Erro ao enviar e-mail! Tente novamente**.

Código aceito abre a senha nova. O app pede essa validação ao serviço da WeCareU.

### Senha nova

Título: **Vamos alterar sua senha:**. Campos **Senha** e **Confirme sua senha**, os dois com olho. Embaixo, a lista **Sua senha deve conter:**.

O botão **Redefinir Senha** só trava nestes casos:

- senha vazia: **Senha é obrigatória**
- senha com menos de 8: **Senha deve ter pelo menos 8 caracteres**
- confirmação vazia: **Confirmação de senha é obrigatória**
- confirmação com menos de 8: **Confirmação de senha deve ter pelo menos 8 caracteres**
- as duas diferentes: **As senhas não conferem**

A lista também fala em número, minúscula, maiúscula e símbolo. Esses itens ficam vermelhos ou verdes, e não impedem o botão. Uma senha de 8 caracteres sem letra e sem símbolo segue adiante.

No sucesso, o app pede a troca ao serviço da WeCareU, com a senha cifrada. A pessoa volta ao login e o título vira, em destaque: **Senha alterada com sucesso! Faça login com sua nova senha.** Ela não entra sozinha. Se o serviço recusa: **Erro ao redefinir a senha!**

## Troca já logado, a partir do perfil

No [[Perfil do artista]], em Segurança, **Alterar Senha** tem o apoio "Mude sua senha de acesso". São três passos na mesma tela, com **Voltar**.

### 1. Verificar Email

"Digite seu email para receber um código de verificação."

Mostra **Seu email cadastrado:** com o e-mail da conta mascarado: a primeira e a última letra da parte de antes do @, o meio em asteriscos, e o domínio inteiro. Se essa parte tem duas letras ou menos, ela aparece inteira.

**Confirme seu email:** campo **Digite seu email**. **Enviar Código** só fica com cara de ativo quando o que foi digitado é idêntico, letra por letra, ao e-mail que o app guarda da conta. Se não confere, a pessoa vê embaixo do campo: "O email digitado não confere com o email cadastrado." Isso é aviso local. O serviço não é chamado. O título **Email Inválido** existe no app e esta tela não o mostra.

Se confere, o app pede o código ao serviço da WeCareU. Sucesso: alerta **Código Enviado**, "Um código de verificação foi enviado para seu email.", e segue para o código. Falha: alerta **Erro ao Alterar Senha**, "Erro ao enviar o código por email. Tente novamente."

### 2. Código de Verificação

"Digite o código de 6 dígitos enviado para seu email." Campo com a dica **000000**, no máximo 6 números. **Validar Código** só parece ativo com 6 dígitos.

Menos de 6, ou o serviço diz que o código não vale: "O código digitado está incorreto ou expirou." Aviso no campo. O título **Código Inválido** não aparece como alerta. Se a chamada falha: alerta **Erro ao Alterar Senha**, "Erro ao validar o código. Tente novamente."

Código aceito: alerta **Código Válido**, "Código validado com sucesso! Agora defina sua nova senha."

O reenvio espera **60 segundos**, não os 2 minutos da recuperação. Enquanto corre, a tela diz "Tente novamente em X segundos" e o botão **Reenviar Código** fica escondido. No zero, o botão volta e pede outro código ao serviço, com o mesmo alerta de envio.

### 3. Nova Senha

"Digite sua nova senha." Campos **Digite sua nova senha** e **Confirme sua nova senha**, com olho. A mesma lista **Sua senha deve conter:**.

**Salvar Nova Senha** só exige os dois campos preenchidos e iguais. Não exige 8 caracteres, número, maiúscula, minúscula nem símbolo. A lista pode estar toda vermelha e o toque segue. Se falta um campo ou as duas senhas diferem, o alerta é **Formulário Inválido**, "Por favor, preencha todos os campos corretamente." Não usa **As senhas não conferem**.

Não há campo de senha atual. O texto **Senha Atual** e o placeholder "Digite sua senha atual" existem no app e não entram neste fluxo. O serviço da WeCareU tem um pedido de troca que usa a senha antiga; esta tela não o usa. Ela pede a troca com e-mail, código e senha nova. Diferente da recuperação, a senha nova vai como foi digitada, sem a cifra daquele outro caminho.

Se o serviço confirma: alerta **Senha Alterada**, "Sua senha foi alterada com sucesso!" **OK** volta ao perfil. A pessoa continua logada. Não é mandada ao login. Se o serviço recusa: alerta **Erro ao Alterar Senha**, "Erro ao alterar a senha. Tente novamente." Se a resposta não confirma e também não falha, a tela não avisa e não sai do passo.

## O que a senha pede, comparado ao cadastro

No [[Cadastro do artista]], a senha que o app aceita precisa, ao mesmo tempo, de:

- 8 caracteres ou mais
- uma letra minúscula
- uma letra maiúscula
- um número
- um destes símbolos: @ $ ! % * ? &

Fora letras, números e esses símbolos, o cadastro recusa. Espaço, acento e outros sinais não passam. A confirmação tem de ser igual. O e-mail do cadastro precisa ter de 5 a 254 caracteres, formato de e-mail, e o app o guarda em minúsculas.

A lista das telas de senha nova (recuperação e troca logada) mostra:

- Pelo menos um número
- Pelo menos uma letra minúscula
- Pelo menos uma letra maiúscula
- Pelo menos 8 caracteres
- Pelo menos um caractere especial
- As senhas devem ser iguais

O "caractere especial" dessa lista acende com outro conjunto, entre eles ! @ # $ % * ( ) e alguns sinais a mais. O & do cadastro não acende a lista. O # acende a lista e o cadastro não aceita. E, nestas duas telas, a lista não trava o botão. No login, a senha só precisa ter 8 caracteres. O e-mail do login não cobra o tamanho de 5 a 254 nem vira minúsculo na tela.

## Biometria

O aparelho oferece biometria quando tem o recurso e a pessoa já cadastrou digital ou rosto nele. Se o aparelho não tem isso, o perfil não mostra o interruptor e o login não mostra o atalho.

Há três pedidos diferentes, com textos diferentes.

**Depois de entrar com e-mail e senha**, se ainda não está ligado com credencial válida, o aparelho pergunta na hora. A pessoa já pode estar no [[Início do artista]] quando o aviso aparece.

- Rosto: "Use o Face ID para fazer login futuramente"
- Digital: "Use sua impressão digital para fazer login futuramente"
- Sem um dos dois: "Use sua biometria para fazer login futuramente"
- Recusar: **Não permitir**
- Outro caminho do sistema: **Usar senha**

Se o rosto e a digital existem no mesmo aparelho, o texto usado é o do Face ID. Aceitar guarda o e-mail e a senha daquela entrada e liga a biometria. **Não permitir**, ou cancelar, não mostra alerta. A entrada com senha permanece. Na próxima vez o atalho não aparece, até ela aceitar de novo ou ligar no perfil.

**No perfil**, em Segurança, a linha **Biometria** diz **Ativada** ou **Desativada**. O interruptor e o toque na linha fazem a mesma coisa.

Ao ligar, o aparelho pede:

- Rosto: "Configure o Face ID"
- Digital: "Configure sua impressão digital"
- Sem um dos dois: "Configure sua biometria"
- **Cancelar** nas duas ações do aviso

Cancelar: o interruptor volta para desligado e o alerta traz o título **Cancelar** e o texto "Configuração de biometria cancelada." Outra falha nesse pedido: título **Erro**, "Falha na autenticação biométrica. Tente novamente."

Se o aparelho aceita, o app liga usando o e-mail e a senha da última entrada que ainda guarda. Isso sobrevive a fechar e abrir o app, e some ao sair da conta. Sucesso: **Biometria Ativada!**, "A autenticação biométrica foi configurada com sucesso." Se não há essa cópia, ou a gravação falha, o interruptor volta e o alerta de erro pode mostrar uma frase em inglês ("Error enabling biometric authentication"). O texto em português "Não foi possível ativar a biometria" fica de reserva e não é o que aparece quando essa frase em inglês vem junto.

**Na próxima abertura**, a biometria não entra sozinha. A pessoa vê os slides, toca **Já tenho uma conta** e, no login, **Entrar com Biometria**. Aí o aparelho pede:

- Rosto: "Use o Face ID para entrar"
- Digital: "Use sua impressão digital para entrar"
- Sem um dos dois: "Autentique-se para entrar"
- **Cancelar**
- **Usar senha**

Aceitar: o app entra com a credencial guardada, pelo mesmo pedido de entrada do serviço, e abre o [[Início do artista]].

Cancelar, ou o aparelho recusar: a pessoa continua no login e vê **Falha na autenticação biométrica**. O app tem as frases "Autenticação biométrica cancelada ou falhou" e "Credenciais biométricas desatualizadas. Entre novamente." Esta tela não as mostra.

Se a credencial guardada não entra mais (o serviço recusa), o app apaga a biometria e a credencial. O atalho some. A frase na tela é a mesma **Falha na autenticação biométrica**. Para ligar de novo, é preciso entrar com e-mail e senha e aceitar o pedido, ou usar o interruptor do perfil depois disso.

**Desligar** no perfil pede confirmação: **Desativar Biometria**, "Tem certeza que deseja desativar a autenticação biométrica?" **Cancelar** mantém ligado. **Desativar** apaga a credencial e o liga/desliga. Sucesso: **Biometria Desativada**, "A autenticação biométrica foi desativada com sucesso." Sair da conta faz o mesmo apagamento, sem esse alerta. Se desligar falha, o texto "Não foi possível desativar a biometria" não é mostrado e o interruptor segue ligado.

Sair da conta, e uma sessão que a abertura não confirma, apagam biometria e credencial. A abertura seguinte não oferece o atalho. Se o serviço derruba a sessão porque a senha mudou ou as sessões foram invalidadas, a credencial também some; a marca de "ligada" pode ficar no aparelho, mas sem credencial o atalho não aparece.
