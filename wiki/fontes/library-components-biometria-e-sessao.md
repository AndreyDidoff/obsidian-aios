---
tipo: fonte
arquivo: ingeridos/library-components-biometria-e-sessao.md
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-components, pacote @wecareu/auth-flow; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Biometria e sessão"]
---

# Biometria e sessão

Volta para [[library-components-o-que-entrega]]. Pacote `@wecareu/auth-flow` 0.1.0.

O atalho só entra na tela de entrada se o aparelho tem biometria e já existe biometria cadastrada no sistema. Com credencial válida (e-mail e resumo da senha), o link diz "Entrar com biometria". Ligada e sem credencial válida, diz "Desabilitar login biométrico" e não oferece habilitar de novo. Disponível e ainda desligada, diz "Habilitar login biométrico". O app pode desligar a biometria por completo. O padrão é ligada.

Entrar pede a biometria do aparelho. Não oferece o PIN do celular. O pedido do sistema fica em inglês ("Authenticate to continue") se o app não passar outra frase. Cancelar ou falhar cai na frase "Falha na autenticação biométrica".

Entrar com biometria manda ao serviço um resumo MD5 da senha, não a senha digitada. O login comum manda a senha como foi digitada. O código trata o resumo como exigência de um servidor antigo. Se o serviço esperar a senha original, a entrada falha mesmo com o reconhecimento certo, e a pessoa vê a mesma frase. Para ligar, precisa ter preenchido e-mail e senha antes. Se faltar um dos dois, nada é guardado. Habilitar não entra na conta: guarda o e-mail e o resumo e liga a preferência. Espaços nas pontas da senha saem antes do resumo. Desligar apaga a credencial e a preferência juntas.

A credencial guarda o e-mail, o resumo MD5 e o momento em que foi salva. A preferência, à parte, diz se o login biométrico está ligado neste app. Não é um cofre: quem achar o registro não lê a senha digitada. Esse mesmo resumo é o que o login biométrico envia.

A sessão guarda a pessoa e os tokens. Quando o serviço envia, também ficam telefones, endereços e assinatura. Só é retomável se a pessoa e os tokens estiverem os dois salvos. Os sinalizadores de recurso que vêm na resposta não são gravados nem aplicados aqui. Ao abrir, se havia essa sessão, ela é retomada.

Sair pede o encerramento ao serviço. Tenha o serviço respondido ou falhado, a sessão local é limpa: pessoa, tokens de acesso e de renovação, validades, telefones, endereços, assinatura e o último evento de segurança. A credencial biométrica e a preferência continuam. A tela ainda pode mostrar "Entrar com biometria" depois da saída. Sair da conta não apaga a credencial nem a preferência.

Não há, neste fluxo, renovação automática. O token de renovação pode ter sido guardado, e este fluxo não pede um acesso novo com ele. O texto de apresentação, que promete renovação automática, está à frente do código. O contrato deixa ao app validar o acesso, renovar o token e buscar de novo a pessoa. Este fluxo só busca a pessoa se alguém pedir para atualizar os dados. Não há tela para isso, e validar ou renovar não são chamados aqui. Guardar a renovação não renova o acesso sozinho.

O login devolve um retrato da conta. Este fluxo não desenha perfil. Obrigatórios: identificador, nome e e-mail. Opcionais: nome de exibição, documento, telefones, endereços, fotos, assinatura e metadados.

## Só no contrato, sem tela

Troca de senha de quem já está logado: senha atual opcional, nova senha e confirmação. Este fluxo nunca chama essa troca.

Invalidar todas as sessões: se o pedido segue, repete a limpeza local. Se o serviço não completa, a sessão local permanece.

Modo convidado: um sim ou não na memória enquanto o app está aberto. Não é gravado. Nenhuma tela deste repositório usa. Sair desmarca.

Eventos de segurança (senha alterada, token invalidado por troca de senha, credenciais de segurança alteradas, todas as sessões invalidadas): o fluxo sabe guardar e reler ao abrir, sem mostrar. Nada neste repositório grava esses eventos sozinho. Sair apaga o evento junto com a sessão.

Ver [[library-components-entrar-na-conta]], [[library-components-recuperar-senha]], [[library-components-em-que-pe-esta]].
