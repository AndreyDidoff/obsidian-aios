---
tipo: fonte
arquivo: "ingeridos/Meu perfil.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_client; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Meu perfil"]
---

# Meu perfil

Volta para [[mapa-do-app-do-cliente]]. Quarta área da barra, ícone de pessoa. Com a aba selecionada, o nome **Perfil** aparece. O título da tela é **Meu Perfil**.

A própria tela não mostra nome, foto nem e-mail. Nome e foto, quando a conta os tem, aparecem no [[inicio]].

**Pé:** o menu está construído e cada entrada leva a algum lugar. **Editar perfil** é casca: não mostra nem salva dado nenhum. **Alterar senha** e a biometria estão em uso, com as ressalvas abaixo. O mapa da área classifica o conjunto como parcial.

## O menu

**Dados Pessoais.** **Editar Perfil**, "Nome, foto, documento e outros dados". Abre uma tela que ainda não edita nada.

**Segurança.** **Alterar Senha**, "Mude sua senha de acesso". **Biometria** só aparece se o aparelho tiver digital ou reconhecimento facial já cadastrados. O texto ao lado é **Ativada** ou **Desativada**. Entrar por aí fica em [[entrar-senha-e-biometria]].

Há textos prontos para **Alterar Email** e "Mude seu email de acesso". Essa entrada não está no menu e não há tela. ([[o-que-ainda-nao-esta-no-app]])

**Endereços.** **Gerenciar Endereços**. ([[enderecos]]) **Notificações.** **Configurações de Notificação**. **Suporte.** **Central de Ajuda** abre `https://wecareu.app/suporte` fora do app. Se o link não abrir, o aviso é **Erro** e "Não foi possível abrir o link". **Sobre o App**, **Termos de Uso** e **Política de Privacidade** estão em [[avisos-ajuda-e-regras]].

No fim, fora das seções, **Sair da sua conta**.

## Editar perfil

A tela se chama **Dados Pessoais**. No miolo, o título **Dados Pessoais** e a frase "Em breve você poderá editar seus dados pessoais aqui." Não há campo. Não há botão de salvar. Nada é lido da conta e nada é gravado.

## Alterar senha

Quem já está na conta não informa a senha atual. Três passos. **Voltar** sai do fluxo. O que foi digitado não fica guardado.

**Verificar Email.** Mostra **Seu email cadastrado:** mascarado: o domínio inteiro; antes do @, se houver mais de dois caracteres, a primeira letra, asteriscos e a última. **Enviar Código** só acende quando o digitado é igual ao e-mail da conta, inclusive maiúsculas e minúsculas. Se não confere no envio: "O email digitado não confere com o email cadastrado." Se o envio dá certo: **Código Enviado**.

**Código de Verificação.** Seis números. **Validar Código** só acende com seis dígitos. Se não serve: "O código digitado está incorreto ou expirou." **Reenviar Código** fica escondido por um minuto. Nesse intervalo a frase é "Tente novamente em {{seconds}} segundos": o trecho `{{seconds}}` aparece no lugar do número.

**Nova Senha.** Dois campos, sem senha atual. **Salvar Nova Senha** acende quando os dois têm algo e são iguais. A lista **Sua senha deve conter:** muda de cor e não trava o botão. Dá para salvar uma senha que falhe na lista, desde que as duas coincidam. A lista pede número, minúscula, maiúscula, 8 caracteres, um especial entre `! @ # $ % * ( ) } { + = | / ? . -`, e senhas iguais.

Se dá certo, **Senha Alterada** e "Sua senha foi alterada com sucesso!" O botão para fechar esse aviso não tem "OK" em português. O que a pessoa lê é o texto cru `components.buttons.ok`. Ao tocar, volta ao perfil e continua na conta. A nova senha segue como foi digitada, junto com o e-mail e o código. Em [[entrar-senha-e-biometria]], quem esqueceu a senha também passa por código, e a senha nova não segue do mesmo jeito. A extração marca [VERIFICAR] se o serviço aceita as duas formas. Trocar a senha aqui também não troca a senha guardada para a biometria.

Os textos "Senha Atual" e "Digite sua senha atual" existem e não viram campo.

## Biometria

A linha só existe se o aparelho tiver leitor e uma digital ou um rosto já cadastrados nele. O interruptor e o toque na linha fazem a mesma coisa.

**Ligar.** O aparelho pede confirmação: "Configure o Face ID", "Configure sua impressão digital" ou "Configure sua biometria". O botão para desistir é **Cancelar**. A frase **Usar senha** não entra aqui. Se a pessoa cancela, o aviso é **Cancelar** e "Configuração de biometria cancelada." Se a confirmação do aparelho falha: **Erro** e "Falha na autenticação biométrica. Tente novamente." Se dá certo, o app guarda neste aparelho o e-mail e a senha do último acesso com senha e marca a biometria como ligada. O aviso é **Biometria Ativada!**

Se esse último acesso não estiver guardado, a ativação não conclui. O aviso é **Erro** e a frase em inglês "Error enabling biometric authentication". O texto preparado "Não foi possível ativar a biometria" não é o que aparece. **Sair** apaga esse acesso guardado.

**Desligar.** Pergunta **Desativar Biometria**. **Desativar** apaga o acesso guardado e desliga a opção. O texto "Não foi possível desativar a biometria" existe e esta tela não o mostra.

## Sair

**Sair da sua conta** abre **Sair da WeCareU**: "Tem certeza que deseja sair da sua conta WeCareU?" **Sair** encerra a conta neste aparelho e volta para a abertura. ([[primeira-entrada]]) Também apaga o e-mail e a senha guardados para a biometria e desliga essa opção. Para entrar de novo por digital ou rosto, é preciso entrar com a senha e ligar outra vez no perfil. Se o serviço de saída falhar, a conta ainda é encerrada neste aparelho. Não há aviso de sucesso.

## O que o board pede em 21/10

O board pede consultar e gerir perfil ([[board-perfil]]). Consultar o próprio perfil e o de terceiros convive com o retrato acima: editar dados é em breve.

O board pede a tela de configurações do app do cliente e a tela de alteração de senha ([[board-configuracoes]]). A tarefa 469, de front, está Completed. A tarefa 470, de design, está New. A tarefa 475 está Completed. Nenhuma tem descrição. Completed é o estado do work item. O retrato desta página permanece. Alteração de senha não é 2FA.
