---
tipo: sintese
criado: 2026-11-07
atualizado: 2026-11-07
fontes: ["[[contradicoes-e-lacunas]]"]
---

# Contradições da conta

Este tema é do MVP. Os outros temas saem de [[contradicoes-e-lacunas]]. Os números são os daquela página.

## Contradições

| # | Tema | Conflito | Status |
| --- | --- | --- | --- |
| 2 | Dados coletados | A política não cobre os campos do [[cadastro]]; orientação sexual é dado sensível | **Encaminhado**: o MVP coleta só sexo (sem gênero nem orientação sexual), e a política será revisada antes do MVP |
| 14 | Dados do cadastro no código | Retrato de 21/10: cliente e artista coletam gênero (cinco opções), sem sexo separado, sem orientação sexual e sem telefone | **Encaminhado no cliente:** sexo em quatro botões, sem gênero nem orientação ([[mvp-alteracoes-pos-congelamento]]). O retrato que coleta gênero é estado atual e vira ajuste em [[app-cliente-conta]]. O artista não herda |
| 15 | 2FA | "Existe para todos" ([[lyraui-03-estado-atual]]) vs. pós-MVP nos apps ([[ssot-backlog]]) vs. só no `web-admin` ([[ssot-termos-legais]]) | **Resolvido no cliente:** as telas do cliente não têm 2FA. A biometria só desbloqueia o app ([[mvp-funcoes-e-telas]]). O artista não herda. O retrato de 21/10 é estado atual. A tarefa 462 de [[board-conta-e-acesso]] pede login usando digital, sem descrição. Isso não é 2FA |
| 25 | Etapas do cadastro | Alvo: duas etapas via chatbot ([[decisoes-2026-10-20]]). | **Resolvido no cliente:** um chatbot, com os campos do alvo, sem SMS ([[mvp-alteracoes-pos-congelamento]]). As duas etapas de outubro não valem mais no cliente. O formulário de 21/10 é estado atual e vira ajuste em [[app-cliente-conta]]. O artista não herda |
| 28 | Porta de abertura de conta | Os dois apps abrem conta pela porta de cliente, POST `User`, em [[bff-cadastro]]. | **Aberto no código.** A decisão de dois papéis, cliente e Artista, permanece ([[decisoes-2026-10-20]]). O retrato não muda o alvo. Login e cadastro de artista em [[board-conta-e-acesso]] não provam que o app usa POST Artist |
| 29 | Momento do cadastro no cliente | Alvo: no app do cliente, a listagem vem antes e a pessoa se cadastra no momento de agendar, não na porta ([[decisoes-2026-10-21]]). | **Resolvido no cliente:** a lista abre sem conta. O cadastro acontece antes do fluxo, nunca com horário retido ([[mvp-alteracoes-pos-congelamento]]). A frase de cadastrar no meio do agendamento não vale mais |
| 34 | SMS do cliente | O conjunto de 03/11 pedia telefone verificado por SMS nos dois apps ([[mvp-final]]). | **Resolvido no cliente.** O SMS do artista não foi revogado e espera o detalhe desse lado |

## Lacunas

- **Campos do cadastro do cliente:** fechados no alvo. CPF, quatro botões de sexo, nascimento com 18 anos, foto, celular sem SMS, e-mail e senha. → [[cadastro]]
- **Código de resposta no login:** o board pede 401; o retrato do login não diz o código. ([[board-bugs]], [[bff-entrar-sair-e-senha]]) → [[backend-mvp-conta]]
