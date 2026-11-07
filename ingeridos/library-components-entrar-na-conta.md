---
titulo: Entrar na conta
repositorio: library-components
pacote: "@wecareu/auth-flow"
extraido_em: 2026-10-21
tipo: extracao-produto
tema: entrar-na-conta
---

> **Aviso de versionamento (extração via IA — Cursor):** Retrato do repositório `library-components` em 21/10/2026. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Se conflitar com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Pacote: `@wecareu/auth-flow`

## O que a pessoa vê

No alto está o título "Entre na sua conta" e, logo abaixo, o subtítulo "Use seu email e senha para continuar."

Em seguida há dois campos, um embaixo do outro. O de e-mail mostra o exemplo "seu@email.com". O de senha mostra pontinhos. Esta tela não manda os rótulos "Email" e "Senha" para os campos, embora essas palavras existam nas traduções. O que este fluxo escreve dentro do campo é o exemplo e os pontinhos. Se aparecer um título em cima do campo, ele não vem destes textos: vem da biblioteca visual.

No campo da senha dá para revelar ou esconder o que foi digitado. Enquanto a senha está oculta, o controle se chama "Mostrar". Quando o texto fica visível, o controle passa a se chamar "Ocultar".

O botão principal diz "Entrar". Enquanto a entrada está em espera, esse botão fica desabilitado e, abaixo dele, aparece um indicador de espera.

Dois links ficam centralizados debaixo do botão. "Esqueci minha senha" aparece sempre nesta tela. "Não tem uma conta? Cadastrar" também aparece, e aparece habilitado.

Se o preenchimento falha ou a entrada não é aceita, as frases surgem numa lista acima dos campos, entre o subtítulo e o e-mail, em destaque de erro. A lista junta o que falta no formulário e a falha da tentativa.

Nesta mesma tela pode aparecer a biometria, quando o aparelho oferece esse recurso. O fluxo não entra nesta nota. Está em [[library-components-biometria-e-sessao]].

## O que precisa preencher

O e-mail é obrigatório. Se ficar vazio, a pessoa vê "Email é obrigatório". Se o texto não for um e-mail válido, vê "Digite um endereço de email válido".

A senha também é obrigatória para entrar. Se ficar vazia, a pessoa vê "Senha é obrigatória". Qualquer senha preenchida passa nesta tela. Os critérios fortes — pelo menos oito caracteres, letra maiúscula, letra minúscula, número e caractere especial — valem na troca de senha. Aqui eles não são exigidos.

Antes de enviar, o e-mail é limpo nas pontas e posto em minúsculas. Espaço no começo ou no fim, e letra maiúscula no endereço, não seguem na tentativa. A senha vai como foi digitada. A senha começa sempre vazia.

## O que acontece ao entrar

A pessoa toca em "Entrar". Se o e-mail ou a senha não passam na verificação, nada é enviado. As frases ficam na lista acima dos campos e o botão continua disponível para um novo toque.

Se os dois passam, a espera começa. O botão desabilita e o indicador de espera aparece. Uma falha antiga some no começo dessa nova tentativa.

Se a entrada falha, a espera acaba, o botão volta a aceitar toque e a lista mostra "Falha no login. Verifique suas credenciais." Nesta tela não há distinção entre senha errada, conta inexistente ou falha de rede. Qualquer erro da tentativa cai nessa mesma frase.

Se a entrada dá certo, a sessão fica no aparelho. O aplicativo que usa esta peça é avisado de que a entrada deu certo. A tela de entrar não escolhe a próxima tela. Quem decide o destino é o aplicativo.

## O que ainda não funciona nesta tela

O link "Não tem uma conta? Cadastrar" está habilitado e o toque não leva a lugar nenhum. O vazio é de propósito: o comentário na tela diz que o app consumidor cuidaria do cadastro. Cadastro não existe aqui.

"Esqueci minha senha" tenta abrir a recuperação. O navegador das telas pode desligar esse fluxo e deixar de montar as telas de recuperação. A tela de login não respeita esse interruptor: o link continua. Se as telas de recuperação não estiverem montadas, o link não tem destino útil.

A pessoa pode voltar da troca de senha com um sinal interno de sucesso. A tela de login ignora esse sinal. Não há mensagem de senha alterada.

Dá para abrir a tela já com um e-mail preenchido. O nome interno desse valor sugere um destino depois do login. Na prática, é só o endereço que aparece no campo. A senha não vem preenchida.

## Textos em português

Frases que a pessoa pode ler nesta tela:

- "Entre na sua conta"
- "Use seu email e senha para continuar."
- "seu@email.com"
- "••••••••"
- "Mostrar"
- "Ocultar"
- "Entrar"
- "Esqueci minha senha"
- "Não tem uma conta? Cadastrar"
- "Email é obrigatório"
- "Digite um endereço de email válido"
- "Senha é obrigatória"
- "Falha no login. Verifique suas credenciais."

Existem nas traduções e não aparecem como rótulo nesta tela: "Email" e "Senha".

As frases da biometria desta mesma tela estão em [[library-components-biometria-e-sessao]].

## Notas relacionadas

- [[library-components-o-que-entrega]]
- [[library-components-recuperar-senha]]
- [[library-components-biometria-e-sessao]]
- [[library-components-em-que-pe-esta]]

## Fontes desta extração

- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\screens\SignIn\index.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\components\forms\LoginForm\index.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\i18n\locales\pt.json
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\contexts\AuthContext.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\types\navigation.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\navigation\AuthFlowNavigator.tsx
