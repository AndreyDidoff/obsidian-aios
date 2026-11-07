---
tipo: fonte
arquivo: ingeridos/library-components-em-que-pe-esta.md
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-components, pacote @wecareu/auth-flow; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Em que pé está"]
---

# Em que pé está

Volta para [[library-components-o-que-entrega]]. Pacote `@wecareu/auth-flow` **0.1.0**. As telas, os textos e a sessão no aparelho estão aqui. Quem conversa com o servidor é o app. Sem o serviço de conta, login e recuperação não concluem.

**Pronto**, ainda dependente desse serviço: entrar com e-mail e senha, mostrar ou ocultar a senha, espera na tentativa e uma frase genérica se a credencial falha. Recuperar a senha em três telas: pedir o e-mail, código de exatamente 6 caracteres (letras e números), senha nova. Reenvio espera 2 minutos. Regras da senha nova: mínimo 8, minúscula, maiúscula, número, caractere especial e confirmação igual. Textos em português e em inglês. Sessão guardada no aparelho e retomada ao abrir. Na entrada dá para ligar a biometria, entrar com ela e desligá-la.

**Parcial:**

- "Não tem uma conta? Cadastrar" está visível e o toque não abre nada.
- Quando a senha nova é aceita, volta ao login com o sinal `showRecoverySuccess`. A tela de login ignora esse sinal: não aparece aviso de sucesso.
- "Esqueci minha senha" continua visível mesmo quando as telas de recuperação são desligadas; nesse caso o toque não tem destino.
- As frases de erro da recuperação estão escritas em português e em inglês e, em vários casos, não entram na tela. Se a chamada quebra, o registro pode ir só para o console.
- Entrar com biometria manda um resumo MD5 da senha, não a senha digitada. O login comum manda a senha como foi digitada. O código trata o resumo como exigência de um servidor antigo. Se o serviço esperar a senha original, a entrada falha mesmo com o reconhecimento certo. Cancelar o pedido do aparelho cai na frase de falha. Sair da conta não apaga a credencial nem a preferência. O pedido do sistema fica em inglês ("Authenticate to continue") se o app não passar outra frase. Não oferece o PIN do celular.
- `redirectTo`, pelo nome, parece destino depois do login. Na prática só preenche o e-mail.
- O texto de apresentação promete renovação automática de acesso. O que está construído: a sessão é guardada e renovar fica com o app. Nada aqui dispara a renovação sozinho.
- O mesmo texto aponta uma pasta de specs. A pasta citada não existe aqui.
- O inventário de 7 de maio de 2026 não descreve o disco de 21/10. Dizia que a pasta de build não existia; hoje existe. Citava um componente de carregamento que o pacote atual não declara. Peças declaradas hoje: botão de fechar, degradê, link, ícones, campo de texto, texto e tema. Não declara data, lista, máscara nem espera.

**Só no papel** (contrato, sem tela): cadastro, troca de senha de quem já está logado, invalidar sessões, modo convidado, eventos de segurança, perfil (nome, e-mail, documento, telefones, endereços, fotos), atualizar dados, renovar acesso. Não há home, pedidos nem perfil em tela.

Os testes cobrem sessão e biometria, não tela. O playground não declara este fluxo. A história está fora da pasta que a vitrine procura, então a vitrine não mostra o fluxo. Notas de versão vazias: só o separador, sem uma frase do que mudou. Este repositório não evidencia publicação nem instalação nos apps de cliente ou de profissional. A confirmação por app não está neste retrato.

Ver [[fluxo-de-entrada]], [[library-components-entrar-na-conta]], [[library-components-recuperar-senha]], [[library-components-biometria-e-sessao]].
