---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-22
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[lyraui-03-estado-atual]]", "[[ssot-termos-legais]]", "[[ssot-backlog]]", "[[politica-de-privacidade]]", "[[seguranca-e-protecao-de-dados]]", "[[pendencias]]", "[[planos-para-o-futuro]]", "[[brainstorming-wecareu]]", "[[library-components-o-que-entrega]]", "[[library-components-entrar-na-conta]]", "[[library-components-recuperar-senha]]", "[[library-components-biometria-e-sessao]]", "[[library-components-em-que-pe-esta]]", "[[board-conta-e-acesso]]", "[[board-configuracoes]]", "[[core-01-conta]]", "[[core-10-emails]]", "[[core-18-rastro-e-falhas]]"]
---

# Proteção de dados (LGPD)

## Compromissos públicos ([[politica-de-privacidade]])

- Dados coletados: identificação, agendamentos, geolocalização, dispositivo, pagamento (sem cartão completo).
- Compartilhamento só com fornecedores (pagamento, SMS/WhatsApp, hospedagem), autoridades e, de forma anonimizada, anunciantes.
- Direitos do titular: acesso, correção, exclusão, revogação de consentimento.
- Afirma usar criptografia para dados sensíveis.

## Recomendações técnicas ([[seguranca-e-protecao-de-dados]])

- Coleta mínima, consentimento explícito, anonimização.
- Criptografia em trânsito e em repouso.
- 2FA para Artistas e administradores (também listado em [[planos-para-o-futuro]]); OAuth 2.0 nas APIs.
- Localização transparente, desativável fora do uso.
- Monitoramento de logins, auditorias, plano de resposta a incidentes, backups.

No núcleo, rastro e canal de falha ([[core-18-rastro-e-falhas]]) seguem operação interna: os apps de 21/10 não pedem, no BFF a auditoria continua só preparada, e o destino do canal não está neste repositório, então a lacuna segue aberta ([[contradicoes-e-lacunas]]).

## Estado real

- Criptografia é pendência importante, ainda não feita ([[pendencias]]), e será implementada **antes do lançamento do [[mvp]]** ([[decisoes-2026-10-20]]). Até lá, a política promete algo que ainda não existe.
- Os campos do [[cadastro]] não estão cobertos pela política. A política será **revisada antes do MVP**. ([[decisoes-2026-10-20]]) O MVP coleta só sexo, sem gênero nem orientação sexual, o que elimina o dado sensível mais delicado.
- Sem pagamentos no MVP: a seção de dados de pagamento da política pode sair ou ficar marcada como futura. ([[decisoes-2026-10-20]])
- O Swagger em `https://api.wecareu.app/swagger/index.html` é o da [[beautiful-api]] e usa usuário e senha provisórios. Os dois valores estão no checklist do [[mvp]] e em [[decisoes-2026-10-20]]. Saem antes do lançamento, trocados por um acesso de verdade.
- Rastreamento em tempo real fica para depois do MVP; no lançamento, a geolocalização se limita à busca e ao endereço. ([[decisoes-2026-10-20]]) [[ssot-termos-legais]] descreve o alvo: localização em tempo real só entre as partes e só durante a janela do serviço.
- **2FA faz parte do [[mvp]]** nos apps. ([[decisoes-2026-10-21]]) [[lyraui-03-estado-atual]] afirma que 2FA para todos já existe; [[ssot-backlog]] listava 2FA dos apps como pós-MVP; [[ssot-termos-legais]] exigia MFA só no `web-admin`. Vale a decisão: o MVP precisa ter 2FA. O retrato de 21/10 não confirma implementação. Ver [[contradicoes-e-lacunas]].
- Ambos os documentos legais são modelos e pedem revisão jurídica.

## Senha e sessão no fluxo de entrar

No `@wecareu/auth-flow` 0.1.0, entrar com biometria manda um resumo MD5 da senha. O login comum manda a senha como foi digitada. O código trata o resumo como exigência de um servidor antigo. Se o serviço esperar a senha original, a entrada falha mesmo com o reconhecimento certo. ([[library-components-biometria-e-sessao]], [[library-components-entrar-na-conta]])

Sair limpa a sessão e deixa a credencial biométrica e a preferência no aparelho. ([[library-components-biometria-e-sessao]])

As frases de erro da recuperação estão escritas em português e em inglês e, em vários casos, não entram na tela. Se a chamada quebra, o registro pode ir só para o console. ([[library-components-recuperar-senha]], [[library-components-em-que-pe-esta]])

O texto de apresentação promete renovação automática de acesso. O que está construído: a sessão é guardada e renovar fica com o app. Nada neste repositório dispara a renovação sozinho. ([[library-components-o-que-entrega]], [[library-components-biometria-e-sessao]])

Ver [[fluxo-de-entrada]], [[contradicoes-e-lacunas]].

## Senha no serviço de conta

No `Br.Login.API`, o e-mail de senha nova leva um endereço fixo no código: `https://bptsoftwareloginservice.azurewebsites.net`. Não é o host do microserviço, `https://loginapimicroservice.bptsoftware.com.br`. O código tem prazo de 4 horas no pedido, continua ativo depois do uso, e a conferência não olha o prazo. ([[core-01-conta]]) A lacuna do disparador de e-mails permanece aberta. ([[pendencias]]) O serviço de e-mail do núcleo ([[core-10-emails]]) não é o disparador pendente nem o canal de e-mail fora de uso do BFF. A lacuna continua aberta. Ver [[contradicoes-e-lacunas]].

## O que o board pede em 21/10

A tarefa 462 pede login usando digital e não tem descrição. Isso não é o 2FA do [[mvp]]. O alvo de 2FA nos apps permanece. ([[decisoes-2026-10-21]], [[board-conta-e-acesso]])

A tarefa 475 pede a tela de alteração de senha e não tem descrição. O estado no board é Completed. Alteração de senha não é o 2FA do [[mvp]]. O alvo permanece, resolvido para o alvo. ([[decisoes-2026-10-21]], [[board-configuracoes]])
