---
tipo: extração
tema: Meu perfil
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: menu construído; dados pessoais é casca; senha e biometria em uso, com ressalvas
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Meu perfil

Volta para o [[Mapa do app do cliente]]. É a quarta área da barra de baixo, depois de entrar: Início, Artistas, Agenda e Perfil. O ícone é de pessoa. Com a aba selecionada, o nome **Perfil** aparece. O título da tela é **Meu Perfil**.

A própria tela não mostra nome, foto nem e-mail. Nome e foto, quando a conta os tem, aparecem no [[Início]].

**Pé:** o menu está construído e cada entrada leva a algum lugar. **Editar perfil** é casca: não mostra nem salva dado nenhum. **Alterar senha** e a biometria estão em uso, com as ressalvas abaixo. Endereços, notificações, sobre, termos e privacidade têm nota própria.

## O menu

**Dados Pessoais.** **Editar Perfil**, com o texto "Nome, foto, documento e outros dados". Abre uma tela que ainda não edita nada.

**Segurança.** **Alterar Senha**, "Mude sua senha de acesso". Quem já entrou confirma o e-mail, recebe um código e define a senha nova. **Biometria** só aparece se o aparelho tiver digital ou reconhecimento facial já cadastrados. O texto ao lado é **Ativada** ou **Desativada**. Entrar por aí fica em [[Entrar, senha e biometria]].

Há textos prontos para **Alterar Email** e "Mude seu email de acesso". Essa entrada não está no menu e não há tela. Ver [[O que ainda não está no app]].

**Endereços.** **Gerenciar Endereços**, "Adicionar, editar ou remover endereços". O que a tela faz está em [[Endereços]].

**Notificações.** **Configurações de Notificação**, "Gerencie como você recebe notificações". O detalhe está em [[Avisos, ajuda e regras]].

**Suporte.** **Central de Ajuda**, "Encontre respostas para suas dúvidas", abre o site https://wecareu.app/suporte fora do app. Se o link não abrir, o aviso é **Erro** e "Não foi possível abrir o link". O restante da ajuda está em [[Avisos, ajuda e regras]]. **Sobre o App**, "Versão e informações do aplicativo", também fica nessa nota.

**Legal.** **Termos de Uso**, "Leia nossos termos de uso", e **Política de Privacidade**, "Como protegemos seus dados". Os dois estão em [[Avisos, ajuda e regras]].

No fim da lista, fora das seções, o botão **Sair da sua conta**.

## Editar perfil

A tela se chama **Dados Pessoais**. No alto há o logo e um botão de fechar, que volta ao perfil.

O miolo é o título **Dados Pessoais** e a frase "Em breve você poderá editar seus dados pessoais aqui." Não há nome, foto, documento, e-mail nem outro campo. Não há botão de salvar. Nada é lido da conta e nada é gravado.

## Alterar senha

Quem já está na conta não informa a senha atual. São três passos. **Voltar**, no alto, sai do fluxo e volta ao perfil. O que foi digitado não fica guardado.

### Verificar e-mail

Título **Verificar Email**. Texto: "Digite seu email para receber um código de verificação".

A tela mostra **Seu email cadastrado:** e o e-mail da conta mascarado. O domínio aparece inteiro. No trecho antes do @, se houver mais de dois caracteres, ficam a primeira letra, asteriscos e a última. Se houver dois ou menos, esse trecho aparece inteiro.

Abaixo, **Confirme seu email:** e o campo "Digite seu email". **Enviar Código** só acende quando o que foi digitado é igual ao e-mail da conta, letra por letra, inclusive maiúsculas e minúsculas. Se a conferência falhar no envio, a frase é "O email digitado não confere com o email cadastrado."

Se o envio dá certo, o aviso é **Código Enviado** e "Um código de verificação foi enviado para seu email." A tela segue para o código. Se falha, o aviso é **Erro ao Alterar Senha** e "Erro ao enviar o código por email. Tente novamente."

### Código de e-mail

Título **Código de Verificação**. Texto: "Digite o código de 6 dígitos enviado para seu email".

O campo aceita seis números. O exemplo no campo é 000000. **Validar Código** só acende com seis dígitos.

Se o código não serve, a frase é "O código digitado está incorreto ou expirou." Se a validação falha por outro motivo, o aviso é **Erro ao Alterar Senha** e "Erro ao validar o código. Tente novamente."

Se o código serve, o aviso é **Código Válido** e "Código validado com sucesso! Agora defina sua nova senha."

**Reenviar Código** fica escondido por um minuto depois de cada envio bem-sucedido. Nesse intervalo a frase na tela é "Tente novamente em {{seconds}} segundos": o trecho `{{seconds}}` aparece no lugar do número. Passado o minuto, o reenvio volta e manda outro código para o mesmo e-mail.

### Nova senha

Título **Nova Senha**. Texto: "Digite sua nova senha".

Dois campos, cada um com olho para mostrar ou esconder o que foi digitado: "Digite sua nova senha" e "Confirme sua nova senha". Não há campo de senha atual.

**Salvar Nova Senha** só acende quando os dois campos têm algo e são iguais. A lista **Sua senha deve conter:** fica embaixo do botão e muda de cor conforme a pessoa digita. Ela não trava o botão. Dá para salvar uma senha que falhe na lista, desde que as duas coincidam.

A lista pede:

- Pelo menos um número
- Pelo menos uma letra minúscula
- Pelo menos uma letra maiúscula
- Pelo menos 8 caracteres
- Pelo menos um caractere especial, entre estes: ! @ # $ % * ( ) } { + = | / ? . -
- As senhas devem ser iguais

Sair do campo não faz outra conferência.

Se o salvamento dá certo, o aviso é **Senha Alterada** e "Sua senha foi alterada com sucesso!" O botão para fechar esse aviso não tem a palavra "OK" em português. O que a pessoa lê no botão é o texto cru `components.buttons.ok`. Ao tocar, volta ao perfil e continua na conta.

Se falha, o aviso é **Erro ao Alterar Senha** e "Erro ao alterar a senha. Tente novamente." Se os campos não estiverem válidos no momento de salvar, o aviso é **Formulário Inválido** e "Por favor, preencha todos os campos corretamente."

A nova senha segue como foi digitada, junto com o e-mail e o código. Em [[Entrar, senha e biometria]], quem esqueceu a senha também passa por código, mas a senha nova não segue do mesmo jeito. [VERIFICAR] se o serviço aceita as duas formas. Trocar a senha aqui também não troca a senha guardada para a biometria.

## Biometria

A linha só existe se o aparelho tiver leitor e uma digital ou um rosto já cadastrados nele. Sem isso, **Segurança** fica só com **Alterar Senha**.

O interruptor e o toque na linha fazem a mesma coisa.

**Ligar.** O interruptor vai para ligado e o aparelho pede confirmação. Se o aparelho informar reconhecimento facial, o pedido é "Configure o Face ID", mesmo que também tenha digital. Se houver só digital, "Configure sua impressão digital". Nos outros casos, "Configure sua biometria". O botão para desistir nesse pedido é **Cancelar**. A frase **Usar senha** não entra aqui. Ela é do login, em [[Entrar, senha e biometria]].

Se a pessoa cancela, o interruptor volta para desligado. O aviso tem o título **Cancelar** e o texto "Configuração de biometria cancelada."

Se a confirmação do aparelho falha, o aviso é **Erro** e "Falha na autenticação biométrica. Tente novamente." O interruptor volta para desligado.

Se a confirmação dá certo, o app guarda neste aparelho o e-mail e a senha do último acesso com senha e marca a biometria como ligada. O aviso é **Biometria Ativada!** e "A autenticação biométrica foi configurada com sucesso." Usar isso para entrar está em [[Entrar, senha e biometria]].

Se esse último acesso não estiver guardado, a ativação não conclui, mesmo depois da confirmação do aparelho. O aviso é **Erro** e a frase em inglês "Error enabling biometric authentication". O texto preparado "Não foi possível ativar a biometria" não é o que aparece nesse caso. **Sair** apaga esse acesso guardado.

**Desligar.** O app pergunta **Desativar Biometria** e "Tem certeza que deseja desativar a autenticação biométrica?" **Cancelar** deixa como está. **Desativar** apaga o acesso guardado para a biometria e desliga a opção. O aviso é **Biometria Desativada** e "A autenticação biométrica foi desativada com sucesso." O texto "Não foi possível desativar a biometria" existe e esta tela não o mostra.

## Sair

**Sair da sua conta** abre **Sair da WeCareU**: "Tem certeza que deseja sair da sua conta WeCareU?" **Cancelar** fica. **Sair** encerra a conta neste aparelho e volta para a abertura, em [[Primeira entrada]].

Sair também apaga o e-mail e a senha guardados para a biometria e desliga essa opção. Para entrar de novo por digital ou rosto, é preciso entrar com a senha e ligar outra vez no perfil. O que a abertura faz com a biometria está em [[Entrar, senha e biometria]].

Se o serviço de saída falhar, a conta ainda é encerrada neste aparelho. Não há aviso de sucesso.

## O que o perfil ainda não faz

- Mostrar, nesta tela, nome, foto ou e-mail da conta.
- Editar nome, foto, documento ou qualquer outro dado pessoal. A entrada existe. A tela só avisa que isso vem depois.
- Alterar o e-mail. Os textos **Alterar Email** e "Mude seu email de acesso" existem, sem entrada no menu. Ver [[O que ainda não está no app]].
- Pedir a senha atual. Os textos "Senha Atual" e "Digite sua senha atual" existem e não viram campo.
- Impedir uma senha que falhe na lista. O botão de salvar olha se os dois campos estão preenchidos e iguais.
- Colocar o número de segundos na espera do reenvio. A frase fica com `{{seconds}}`.
- Dar um rótulo em português ao botão do aviso "Senha Alterada".
- Enviar a senha nova do mesmo jeito que o fluxo de quem esqueceu a senha, em [[Entrar, senha e biometria]]. [VERIFICAR] se as duas formas são aceitas.
- Atualizar a senha guardada para a biometria quando a senha da conta muda por aqui.
- Mostrar "Não foi possível ativar a biometria" e "Não foi possível desativar a biometria" nos fracassos descritos acima.
