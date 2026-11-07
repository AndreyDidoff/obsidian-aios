---
titulo: O que o library-components entrega
repositorio: library-components
pacote: "@wecareu/auth-flow"
extraido_em: 2026-10-21
tipo: extracao-produto
tema: panorama
---

> **Aviso de versionamento (extração via IA — Cursor):** Retrato do repositório `library-components` em 21/10/2026. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Se conflitar com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Pacote: `@wecareu/auth-flow`

## O que é esta peça para a empresa

O repositório library-components não é o aplicativo WeCareU inteiro. É a peça compartilhada que os aplicativos da empresa reutilizam quando a mesma experiência precisa existir em mais de um aplicativo.

Hoje a única experiência de produto construída aqui é entrar na conta e recuperar a senha, com biometria opcional. O nome interno dessa peça é @wecareu/auth-flow, na versão 0.1.0. A descrição oficial é: fluxo de autenticação centralizado para os aplicativos da WeCareU.

O visual não nasce neste repositório. Botões, campos e cores vêm da biblioteca visual da WeCareU, que mora em outro repositório, o library-design-system. Aqui ficam o percurso da pessoa e os textos das telas. A aparência segue o que aquela biblioteca já entrega.

## O que a pessoa já consegue fazer aqui

Na entrada, a tela se chama Entre na sua conta. A pessoa informa email e senha e segue. O texto de apoio pede para usar o email e a senha para continuar. Se o aparelho oferecer biometria e essa opção estiver disponível no fluxo, ela também pode entrar com biometria, habilitar o login biométrico ou desabilitá-lo. Para habilitar, precisa ter preenchido email e senha antes.

Quem esqueceu a senha percorre mais três telas. Em Esqueceu sua senha?, informa o email e pede o envio do e-mail de recuperação. A tela avisa que um código será enviado para redefinir a senha. Em Digite o código de verificação, a pessoa digita o código recebido por e-mail. O código tem exatamente seis caracteres, só letras e números. Dá para validar o código e, se precisar, pedir o reenvio. Em Vamos mudar sua senha, ela cria a nova senha e confirma. A nova senha precisa ter pelo menos oito caracteres, uma letra minúscula, uma letra maiúscula, um número e um caractere especial. As duas senhas precisam coincidir. Quando a troca dá certo, a pessoa volta para Entre na sua conta.

Os textos desse percurso já estão prontos em português e em inglês. O idioma que aparece é o que o app já escolheu. Esta peça não escolhe o idioma por conta própria.

Depois que a entrada dá certo, a sessão fica guardada no aparelho e é retomada quando o aplicativo abre de novo. A falha de login e a falha de biometria têm frase pronta e aparecem na tela. As frases de falha da recuperação de senha estão escritas e, em vários casos, não aparecem. O detalhe está em [[library-components-recuperar-senha]] e em [[library-components-em-que-pe-esta]].

## O que ainda não está neste repositório

Não há home, não há pedidos e não há perfil em tela. O cadastro aparece como link, com o texto "Não tem uma conta? Cadastrar", e não faz nada. Não há tela de troca de senha para quem já está logado.

A renovação do acesso também não acontece sozinha. O texto de apresentação do pacote promete renovação automática de acesso. O que está construído é outro comportamento: a sessão é guardada no aparelho, e renovar o acesso fica com o app que consome esta peça. Este repositório não chama a API sozinho.

Trocar a senha de quem já está logado, invalidar sessões e buscar a pessoa entram no serviço que o app precisa ligar. Não há tela correspondente aqui para essas três ações.

## Como isso se encaixa nos apps

Quem consome este fluxo precisa ligar o próprio serviço de conta. Esse serviço é quem fala com o servidor. Ele precisa saber entrar, sair, pedir o código, validar o código, definir a nova senha, buscar a pessoa, renovar o acesso, invalidar sessões e trocar a senha de quem já está logado.

Esta peça desenha a experiência e guarda a sessão no aparelho. Sem o serviço de conta do app, as telas não concluem o login nem a recuperação de senha.

Depois que a pessoa entra, o app consumidor decide para qual tela ir. Ao sair, o app consumidor decide para onde voltar. Esses destinos não estão definidos neste repositório. O retorno depois de definir a nova senha, ainda dentro da recuperação, é a própria tela de entrada.

## Notas irmãs

- [[library-components-entrar-na-conta]]
- [[library-components-recuperar-senha]]
- [[library-components-biometria-e-sessao]]
- [[library-components-em-que-pe-esta]]

## Fontes desta extração

- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\README.md
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\INVENTORY.md
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\README.md
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\package.json
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\index.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\navigation\AuthFlowNavigator.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\i18n\locales\pt.json
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\services\types.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\screens\SignIn\index.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\screens\ResetPassword\index.tsx
