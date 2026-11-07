---
tipo: conceito
criado: 2026-10-21
atualizado: 2026-10-22
fontes: ["[[library-components-o-que-entrega]]", "[[library-components-entrar-na-conta]]", "[[library-components-recuperar-senha]]", "[[library-components-biometria-e-sessao]]", "[[library-components-em-que-pe-esta]]", "[[entrar-senha-e-biometria]]", "[[primeira-entrada]]", "[[entrar-senha-e-biometria-do-artista]]", "[[abertura-do-artista]]", "[[cruzamento-como-ler]]", "[[cruzamento-entrar-senha-e-biometria]]", "[[bff-entrar-sair-e-senha]]", "[[bff-preparado-e-ainda-nao-oferecido]]", "[[cruzamento-bff-como-ler]]", "[[cruzamento-bff-conta]]", "[[board-conta-e-acesso]]", "[[core-01-conta]]", "[[decisoes-2026-10-21]]"]
---

# Fluxo de entrada

O repositório `library-components` não é o app. A única experiência de produto construída é entrar e recuperar senha, com biometria opcional. Pacote `@wecareu/auth-flow` **0.1.0**. ([[library-components-o-que-entrega]])

O visual não nasce aqui. Vem de [[kit-visual]]. Peças declaradas hoje: botão de fechar, degradê, link, ícones, campo de texto, texto e tema. Não declara data, lista, máscara nem espera. O inventário de 7 de maio de 2026 não descreve o disco de 21/10. ([[library-components-em-que-pe-esta]])

## Pé

**Pronto**, ainda dependente do serviço de conta do app: a tela "Entre na sua conta" (e-mail e senha; a falha de login tem frase na tela) e a recuperação em três telas (pedir o e-mail, código de exatamente 6 caracteres, letras e números, senha nova). Regras da senha nova: mínimo 8, minúscula, maiúscula, número, caractere especial e confirmação igual. O reenvio espera 2 minutos. Os textos estão prontos em português e em inglês. O idioma é o que o app já escolheu. Esta peça não escolhe idioma. A sessão fica no aparelho e é retomada ao abrir. Na entrada dá para ligar a biometria, entrar com ela e desligá-la. Para ligar, e-mail e senha precisam estar preenchidos antes. ([[library-components-entrar-na-conta]], [[library-components-recuperar-senha]], [[library-components-biometria-e-sessao]])

**Parcial:** o link "Não tem uma conta? Cadastrar" está visível e o toque não abre nada. Quando a senha nova é aceita, volta ao login com o sinal `showRecoverySuccess`, e a tela de login ignora esse sinal: não aparece aviso de sucesso. "Esqueci minha senha" continua visível mesmo quando as telas de recuperação são desligadas; nesse caso o toque não tem destino. As frases de erro da recuperação estão escritas em português e em inglês e, em vários casos, não entram na tela. Se a chamada quebra, o registro pode ir só para o console. `redirectTo` só preenche o e-mail. O pedido de biometria fica em inglês ("Authenticate to continue") se o app não passar outra frase. Não oferece o PIN do celular. A pasta de specs citada não existe. ([[library-components-em-que-pe-esta]])

**Só no papel:** cadastro, troca de senha de quem já está logado, invalidar sessões, modo convidado, eventos de segurança, perfil (nome, e-mail, documento, telefones, endereços, fotos), atualizar dados, renovar acesso. Não há home, pedidos nem perfil em tela.

## Sessão, biometria e renovação

Este repositório não chama a API sozinho. Quem fala com o servidor é o serviço de conta do app consumidor. Sem esse serviço, as telas não concluem login nem recuperação. ([[library-components-o-que-entrega]])

Entrar com biometria manda um resumo MD5 da senha, não a senha digitada. O login comum manda a senha como foi digitada. O código trata o resumo como exigência de um servidor antigo. Se o serviço esperar a senha original, a entrada falha mesmo com o reconhecimento certo. Sair da conta não apaga a credencial nem a preferência. ([[library-components-biometria-e-sessao]])

O texto de apresentação promete renovação automática de acesso. O que está construído: a sessão é guardada e renovar fica com o app. Nada aqui dispara a renovação sozinho.

## O que este repositório não vê

Os testes cobrem sessão e biometria, não tela. O playground não declara este fluxo. A história está fora da pasta que a vitrine procura, então a vitrine não mostra o fluxo. Notas de versão vazias. Este repositório não evidencia instalação. ([[library-components-em-que-pe-esta]])

## O que o app do cliente mostra

Percurso próprio deste app, no retrato de 21/10. A extração do cliente não cita `@wecareu/auth-flow`. ([[entrar-senha-e-biometria]])

O login tem o título **Vamos entrar na sua conta:**. Depois de redefinir a senha, a mesma tela abre de novo e o título vira **Senha alterada com sucesso! Faça login com sua nova senha.** E-mail e senha vêm vazios. A pessoa não entra sozinha. Na abertura, se a credencial for válida, o app tenta a biometria sozinho; se falhar, cai no login. A biometria também liga e desliga no perfil. ([[entrar-senha-e-biometria]], [[primeira-entrada]])

## O que o app do artista mostra

Percurso próprio deste app, no retrato de 21/10. A extração do artista não cita `@wecareu/auth-flow`. Os dois apps têm extração própria e nenhuma das duas cita o pacote. ([[entrar-senha-e-biometria-do-artista]])

O login tem o título **Vamos entrar na sua conta:**. Depois de redefinir a senha, a mesma tela abre de novo e o título vira **Senha alterada com sucesso! Faça login com sua nova senha.** A pessoa não entra sozinha. A biometria é pedida no primeiro login com senha e liga e desliga no perfil. A abertura não dispara a biometria sozinha. O atalho **Entrar com Biometria** fica no login, depois que isso já foi ligado. ([[entrar-senha-e-biometria-do-artista]], [[abertura-do-artista]])

## O que o cruzamento dos quatro repositórios vê

Os dois apps têm percurso próprio e a peça compartilhada não está instalada. `@wecareu/auth-flow` 0.1.0 existe e não está ligado a nenhum dos dois. Cliente e artista estão mais perto um do outro do que dessa peça. Isso é retrato. Não é decisão de manter os percursos separados. ([[cruzamento-como-ler]], [[cruzamento-entrar-senha-e-biometria]])

O que coincide entre os apps, e muda na peça: o título **Vamos entrar na sua conta:** (a peça usa **Entre na sua conta**); na entrada, pelo menos 8 caracteres, com a frase "A senha deve ter pelo menos 8 caracteres" (a peça deixa passar qualquer senha preenchida); ao redefinir, os dois devolvem a pessoa ao login com **Senha alterada com sucesso! Faça login com sua nova senha.** e ela não entra sozinha (a peça volta sem essa frase, e a tela de entrada ignora o sinal de sucesso).

Entrar com biometria, na peça, manda um resumo sem volta da senha. A nota do cliente fala em senha salva e não registra um resumo. A do artista não registra um resumo. No login comum da peça, a senha segue como foi digitada. A nota do artista registra que, no login com senha, a senha vai cifrada. A do cliente não registra cifra nem resumo. Sair, nos dois apps, desliga a biometria e apaga a credencial. Na peça, sair limpa a sessão e deixa a credencial e a preferência.

Trocar a senha de quem já entrou está no perfil dos dois apps e não existe como tela na peça.

O item 24 de [[contradicoes-e-lacunas]] segue aberto como retrato, não como escolha da empresa. Quem fala com o backend, hoje, é o próprio app, não a peça compartilhada. ([[cruzamento-bff-como-ler]])

## O que o backend publica

No caminho `beautiful/api/Login`, o serviço de login está ligado. Os pedidos não separam cliente e profissional. Entrar é POST, sem sessão prévia. Sair é GET `logout`, marcado como exigindo pessoa logada. Saber se a sessão ainda vale é GET `Valid`, marcado como exigindo pessoa logada. A senha tem quatro passos, todos sem sessão: pedir a troca a partir do e-mail (GET `Password/Create/{Email}`), recusar a troca (GET `Password/refuse/{Token}`), trocar a senha (POST `Password/Change`) e validar e-mail e token (GET `Password/valid/{Email}/{Token}`). Pedir a troca não faz este backend enviar o e-mail. O formato da senha, a expiração do token e o texto do e-mail não estão neste repositório. ([[bff-entrar-sair-e-senha]], [[bff-preparado-e-ainda-nao-oferecido]])

## O que o cruzamento de conta acrescenta

Os dois apps pedem entrar, sair e as três portas de senha que estão no ar: pedir a troca, validar o código e trocar a senha. O backend não distingue biometria de senha. Ele recebe o pedido de entrar. Quem já entrou não informa a senha atual: informa o e-mail, o código e a senha nova. A porta de recusar a troca existe e nenhum dos dois apps a pede. Há um pedido preparado de trocar a senha informando a senha antiga. Nenhuma tela o dispara. Este bruto não nomeia esse caminho. Se o pedido de sair falha, a tela ainda encerra a sessão neste aparelho. ([[cruzamento-bff-conta]])

Ao reabrir, o app pergunta se a sessão vale em `login/user/valid`. Este retrato do backend não publica esse caminho. A porta publicada é outra: GET `Valid`. Se a resposta traz sessão nova, o app troca a que estava guardada. ([[cruzamento-bff-conta]])

Invalidar todas as sessões está preparado nos dois apps. Nenhuma tela o chama. O caminho `auth/revoke-all-sessions` não aparece nas portas deste retrato.

O item 24 segue aberto.

Ver [[seguranca-do-atendimento]], [[protecao-de-dados]], [[app-do-cliente]], [[app-do-artista]], [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

O board pede telas de login na história 421: esqueci minha senha (422), código (423), nova senha (424), formulário de login (425) e login usando digital (462, sem descrição). Pede logout automático (455) se a pessoa ficar x tempo sem acessar, trocar a senha fora do app ou os tokens expirarem. O texto não diz o valor de x. A história 246, Fluxo de Login, e a tarefa 247, tela de seleção de login ou cadastro, estão sem pai. ([[board-conta-e-acesso]])

Isso não instala `@wecareu/auth-flow`. As telas pedidas não provam que o pacote está em uso. O item 24 permanece retrato. Ver [[contradicoes-e-lacunas]].

## O que o serviço de conta faz

Foto de 21/10 de `Br.Login.API`. O aplicativo não fala com este serviço. Fala com o BFF. A entrada aqui é e-mail e senha. A biometria das notas de app não está neste serviço. O bruto não menciona 2FA. O alvo do [[mvp]] continua precisando de 2FA. ([[core-01-conta]], [[decisoes-2026-10-21]])

Se a sessão ainda vale, a mesma volta. Se não vale, a sessão nova tem 48 horas de acesso e 7 dias para renovar. Sair desta sessão está feito. Sair de todas está feito como ação própria. Na troca de senha, o pedido de sair de todos dispara e a resposta não espera o encerramento. ([[core-01-conta]])

Renovar está pela metade. A sessão nova é gravada e a resposta continua com a antiga. ([[core-01-conta]])

O código de senha nova tem prazo de 4 horas no pedido. Se o e-mail não é de conta ativa, a resposta é a mesma. O código continua ativo depois do uso, e a conferência não olha o prazo. O e-mail de senha nova leva um endereço fixo no código: `https://bptsoftwareloginservice.azurewebsites.net`. Não é o host do microserviço. ([[core-01-conta]])

O grupo é lido no entrar e o retorno está desligado: casca. Ninguém é colocado em grupo no cadastro. ([[core-01-conta]])

O item 24 de [[contradicoes-e-lacunas]] segue aberto.
