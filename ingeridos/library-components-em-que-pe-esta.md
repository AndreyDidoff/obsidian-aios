---
titulo: Em que pé está
repositorio: library-components
pacote: "@wecareu/auth-flow"
extraido_em: 2026-10-21
tipo: extracao-produto
tema: maturidade
---

> **Aviso de versionamento (extração via IA — Cursor):** Retrato do repositório `library-components` em 21/10/2026. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Se conflitar com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

Pacote: `@wecareu/auth-flow`

A experiência de entrar na conta e de recuperar a senha está desenhada e versionada como 0.1.0. Ela ainda depende de o aplicativo ligar o serviço de conta: este repositório entrega as telas, os textos e a sessão no aparelho, e quem conversa com o servidor é o app. O aplicativo de teste deste repositório não demonstra o fluxo. Quem usa a tela encontra a jornada principal e buracos visíveis: o cadastro não faz nada, a volta da senha nova chega sem aviso de sucesso, e a biometria entrega ao serviço um resumo da senha, não a senha digitada.

## Pronto

O que está pronto é a experiência desenhada de entrar e de recuperar a senha, ainda dependente do aplicativo conectar o serviço de conta.

Na entrada, a pessoa informa e-mail e senha, pode mostrar ou ocultar a senha e vê uma espera enquanto a tentativa segue. Se a credencial falha, aparece um erro genérico pedindo para conferir e-mail e senha, sem explicar o motivo.

Recuperar a senha ocupa três telas: pedir o e-mail, digitar um código de 6 caracteres e definir a senha nova. O reenvio do código espera 2 minutos. A senha nova pede pelo menos 8 caracteres, uma maiúscula, uma minúscula, um número e um caractere especial, e a confirmação precisa coincidir.

Os textos existem em português e em inglês. A sessão fica guardada no aparelho e é retomada ao abrir de novo. Na tela de login dá para ligar a biometria, entrar com ela e desligá-la. O controle está na tela; as ressalvas vêm a seguir.

## Parcial

O link "Cadastrar" está visível na entrada. O toque não abre cadastro e não avisa nada. A ação por trás do link está vazia.

Quando a senha nova é aceita, a pessoa volta para o login. O fluxo envia junto um sinal de sucesso, chamado showRecoverySuccess. A tela de login ignora esse sinal. Não aparece mensagem de que a senha foi alterada.

O link "Esqueci minha senha" continua na entrada mesmo quando as telas de recuperação são desligadas. O interruptor tira as telas do caminho e deixa o link. Quem toca nele, nesse caso, não tem tela de destino.

As frases de erro da recuperação já estão escritas, em português e em inglês, como falha ao solicitar a recuperação e código inválido ou expirado. Quando o serviço responde que não conseguiu, essas frases não entram na tela. Na primeira tela, se a chamada quebra, o registro pode ir só para o console, e a pessoa permanece no mesmo formulário.

Entrar com biometria pede o rosto ou a digital e manda ao serviço um resumo sem volta da senha (MD5), no lugar da senha digitada. O login comum manda a senha como foi digitada. O código trata o resumo como exigência de um servidor antigo, então os dois caminhos não entregam a mesma coisa. Se o serviço esperar a senha original, a entrada falha mesmo com o reconhecimento certo. Cancelar o pedido do aparelho também cai na frase de falha da biometria. Sair da conta não apaga esse atalho: a credencial e a preferência continuam no aparelho.

O pedido de biometria do sistema fica em inglês, com a frase "Authenticate to continue", quando o aplicativo não passa outra frase. Esse pedido não oferece o PIN do celular.

O parâmetro que preenche o e-mail inicial se chama redirectTo. Pelo nome, parece um destino depois do login. Na prática, só coloca um e-mail no campo.

O texto de apresentação promete renovação automática do acesso. O fluxo guarda o dado para renovar e deixa um método ao aplicativo. Nada aqui dispara essa renovação sozinho.

O mesmo texto aponta uma especificação neste repositório. A pasta de specs não existe aqui.

O inventário automático é de 7 de maio de 2026 e não descreve o disco de 21 de outubro de 2026. Ele dizia que a pasta de build não existia; hoje ela existe. Citava um componente de carregamento entre as peças companheiras. O pacote atual não declara essa peça. As peças declaradas hoje são o botão de fechar, o botão em degradê, o link, os ícones, o campo de texto, o texto e o tema.

## Só no papel

Estes itens existem como contrato, formato ou ação para o aplicativo chamar. A tela não foi feita.

Cadastro de conta nova. Troca de senha de quem já está logado. Invalidar todas as sessões: a ação existe para o aplicativo chamar, sem botão e sem tela. Modo convidado: o aplicativo pode marcar o estado, sem experiência desenhada. Eventos de segurança: o último evento pode ser guardado e lido pelo aplicativo, sem lista e sem aviso. Perfil: o formato da pessoa existe, com nome, e-mail, documento, telefones, endereços e fotos, e a tela não. Atualizar os dados da pessoa e renovar o acesso: métodos para o aplicativo, sem tela.

## Como dá para ver hoje

Os testes automáticos deste repositório cobrem a sessão guardada e a biometria. Não há teste de tela. O aplicativo de demonstração, o playground, não declara este fluxo, então abri-lo não mostra entrar nem recuperar senha. A vitrine web procura histórias dentro da pasta de código de cada pacote; a história deste fluxo está fora dessa pasta, então a vitrine do repositório não mostra este fluxo.

A versão marcada é 0.1.0. Há arquivos de nota de mudança, e o conteúdo está vazio: só o separador, sem uma frase do que mudou. Neste repositório não há evidência de publicação, nem de que os aplicativos de cliente ou de profissional já usem este fluxo em produção.

## Páginas relacionadas

[[library-components-o-que-entrega]]
[[library-components-entrar-na-conta]]
[[library-components-recuperar-senha]]
[[library-components-biometria-e-sessao]]

## Fontes

Conferido em 21/10/2026 no repositório library-components: manifesto do fluxo na versão 0.1.0, pasta de build presente, inventário de 07/05/2026, testes só de sessão e de biometria, manifesto do aplicativo de demonstração, configuração da vitrine, história na raiz do pacote, notas de versão vazias, texto de apresentação e ausência da pasta de especificação.
