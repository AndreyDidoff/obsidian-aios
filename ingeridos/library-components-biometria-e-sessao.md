---
titulo: Biometria e sessão
repositorio: library-components
pacote: "@wecareu/auth-flow"
extraido_em: 2026-10-21
tipo: extracao-produto
tema: biometria-e-sessao
---

> **Aviso de versionamento (extração via IA — Cursor):** Retrato do repositório `library-components` em 21/10/2026. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Se conflitar com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Pacote: `@wecareu/auth-flow`

## Entrar com o corpo

O atalho de biometria só aparece na tela de entrada quando o aparelho tem biometria e já existe biometria cadastrada no sistema. Sem as duas condições, o link não entra na tela.

Se a biometria está disponível, ligada neste app e com credencial válida (e-mail e resumo da senha presentes), o link diz "Entrar com biometria". Se está ligada, mas a credencial não está válida, o link diz "Desabilitar login biométrico". Nesse estado o app não oferece habilitar de novo. Se está disponível e ainda não foi ligada, o link diz "Habilitar login biométrico".

Entrar com biometria pede a biometria do aparelho. PIN e senha do celular não servem de alternativa. Se o app não traduzir o pedido, o sistema mostra, em inglês, "Authenticate to continue". Cancelar ou falhar não entra. Nos dois casos a pessoa vê "Falha na autenticação biométrica".

Se a biometria passa, o fluxo chama o login da conta com o e-mail guardado e com o resumo da senha, não com a senha que a pessoa digitou. No login comum, a senha segue como foi digitada. Nos dois caminhos o serviço de conta não recebe a mesma coisa. O código descreve esse resumo como exigência de um servidor antigo. Se o serviço esperar a senha original, entrar com biometria não fecha, e a pessoa vê a mesma mensagem, "Falha na autenticação biométrica".

O app pode desligar a biometria por completo. O padrão é ligada. Desligada, habilitar e entrar pela biometria não seguem.

## Ligar e desligar no aparelho

Habilitar exige e-mail e senha já digitados. Se faltar um dos dois, o app avisa com o título "Complete suas credenciais" e a mensagem "Digite email e senha antes de habilitar o login biométrico." Nesse caso nada é guardado.

Habilitar não entra na conta. Guarda o e-mail e o resumo da senha no aparelho e liga a preferência. Espaços no começo ou no fim da senha são tirados antes desse resumo. A pessoa segue na tela de entrada e pode entrar pela senha ou, na mesma tela, por "Entrar com biometria", assim que a credencial fica válida.

Desligar apaga a credencial e a preferência juntas. Com o aparelho ainda apto, o link volta a "Habilitar login biométrico". Sair da conta não faz esse desligamento.

## O que fica salvo

No aparelho convivem a credencial de biometria e a sessão da conta. Elas não se apagam juntas.

A credencial guarda o e-mail, o resumo da senha e o momento em que foi salva. A preferência, à parte, diz se o login biométrico está ligado neste app. Não é um cofre: o que fica no aparelho é um resumo sem volta (MD5), deixado assim para combinar com um servidor antigo. Quem achar esse registro não lê a senha digitada. Esse mesmo resumo é o que o login biométrico envia no lugar da senha.

A sessão guarda a pessoa e os tokens. Quando o serviço envia, também ficam telefones, endereços e assinatura. A sessão só é retomável se a pessoa e os tokens estiverem os dois salvos. Os sinalizadores de recurso que vêm na resposta do login não são gravados nem aplicados aqui.

Sair limpa a sessão e deixa a biometria. A limpeza apaga a pessoa, os tokens de acesso e de renovação, as validades, telefones, endereços, assinatura e o último evento de segurança. A credencial biométrica e a preferência de biometria ligada continuam no aparelho. Por isso a tela ainda pode mostrar "Entrar com biometria" depois da saída, se o aparelho seguir apto e a credencial seguir válida. Para tirar isso, a pessoa desliga o login biométrico.

## Continuar logado e sair

Ao abrir o app, se havia sessão salva com a pessoa e os tokens juntos, ela é retomada. Não há, neste fluxo, renovação automática do acesso. O token de renovação pode ter sido guardado, e este fluxo não pede um acesso novo com ele. O texto de apresentação do pacote, que promete renovação automática, está à frente do código.

O contrato deixa ao app validar o acesso, renovar o token e buscar de novo a pessoa. Este fluxo só busca a pessoa se alguém pedir para atualizar os dados. Não há tela para isso, e validar ou renovar não são chamados aqui.

Sair pede o encerramento ao serviço. Tenha o serviço respondido ou falhado, a sessão local é limpa e a pessoa fica fora da conta. A credencial de biometria e a preferência sobrevivem a essa limpeza.

Invalidar todas as sessões é uma ação sem tela. O fluxo pede isso ao serviço e, se o pedido segue, repete a mesma limpeza e trata a pessoa como fora da conta. Se o serviço não completa o pedido, a sessão local permanece.

## O que a conta devolve

O login devolve um retrato da conta. Este fluxo não desenha perfil. Guarda o retrato com a sessão e o retoma na abertura, se a sessão ainda estiver salva.

Obrigatórios: identificador, nome e e-mail. Opcionais: nome de exibição, documento, telefones (número, rótulo e se foi verificado), endereços (rua, número, bairro, cidade, estado, CEP e rótulo), fotos, assinatura e metadados. Também podem vir sinalizadores de recurso. Eles chegam na resposta e não são aplicados aqui.

Junto vêm o acesso e, quando o serviço envia, a renovação, cada um com a validade se ela vier. Guardar a renovação não renova o acesso sozinho.

## Previsto sem tela

Trocar a senha de quem já está logado está no contrato que o app deve implementar: senha atual opcional, nova senha e confirmação. Este fluxo nunca chama essa troca e não tem tela para ela.

Modo convidado existe só como um sim ou não que o app pode marcar. Fica na memória enquanto o app está aberto e não é gravado no aparelho. Nenhuma tela deste repositório usa. Sair desmarca.

O fluxo sabe guardar e reler ao abrir, sem mostrar em tela: senha alterada, token invalidado por troca de senha, credenciais de segurança alteradas e todas as sessões invalidadas. Nada neste repositório grava esses eventos sozinho. O app pode registrá-los, e na abertura seguinte o fluxo os relê. Sair apaga o evento guardado junto com a sessão.

## Notas irmãs

- [[library-components-o-que-entrega]]
- [[library-components-entrar-na-conta]]
- [[library-components-recuperar-senha]]
- [[library-components-em-que-pe-esta]]

## Fontes desta extração

- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\components\forms\LoginForm\index.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\contexts\AuthContext.tsx
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\services\BiometricService.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\services\TokenManager.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\services\types.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\types\auth.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\utils\crypto.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\i18n\locales\pt.json
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\src\constants\storage.ts
- c:\Users\Andrey Didoff\Documents\Trabalhos\WeCareU\library-components\packages\auth-flow\README.md
