---
tipo: sintese
criado: 2026-11-07
atualizado: 2026-11-07
fontes: ["[[contradicoes-e-lacunas]]"]
---

# Escopo e lançamento

Este tema é do MVP. Os outros temas saem de [[contradicoes-e-lacunas]]. Os números são os daquela página.

Cabe o que entra no MVP, o que fica fora e o que precisa estar pronto antes.

## Contradições

| # | Tema | Conflito | Status |
| --- | --- | --- | --- |
| 1 | Criptografia | A [[politica-de-privacidade]] diz que já usa; nas [[pendencias]] ela não está feita | **Encaminhado**: será implementada antes do [[mvp]] |
| 3 | Gateway | Lista "em análise" ([[brainstorming-wecareu]]) vs. Stripe/MercadoPago/PayPal nos documentos legais | **Resolvido para o MVP**: sem pagamentos no lançamento; o gateway será escolhido depois. Cobrança, validade de pacote e pagamento dinâmico pedidos em [[board-planos-e-assinaturas]] não escolhem gateway e não entram no lançamento |
| 5 | Estágio do MVP | "Fase avançada" ([[plano-de-negocios-investidores]]) vs. 7 superfícies pendentes | **Resolvido**: o MVP é app do cliente + app do Artista, em desenvolvimento. O texto para investidores precisa ser calibrado |
| 10 | Escopo do MVP | O [[plano-de-negocios-interno]] incluía web para locais | **Resolvido**: fora do MVP |
| 11 | Documentos legais vs. MVP gratuito | Os [[termos-de-uso-do-app]] e a política descrevem planos pagos e gateway; o MVP não tem nenhum dos dois. No app do cliente, o texto fixo de dezembro de 2024 repete planos pagos e gateways: Stripe e PayPal na tela de termos; Stripe ou MercadoPago na de privacidade ([[avisos-ajuda-e-regras]]). No app do artista, o mesmo texto fixo de dezembro de 2024: Stripe e PayPal nos termos; Stripe ou MercadoPago na privacidade ([[avisos-ajuda-e-regras-do-artista]]). O board pede as telas de termos e de privacidade ([[board-configuracoes]]). Isso não atualiza o texto fixo de dezembro de 2024. | Aberto: alinhar os termos é sugestão da wiki, não decisão |
| 12 | MVP já lançado? | [[lyraui-03-estado-atual]] diz "em produção" (maio de 2026). Os MDs do Cursor dos dois apps chegaram em 21/10. O cliente está em 1.0.0, com cascas e exemplo fixo ([[mapa-do-app-do-cliente]]). O artista também está em 1.0.0, com cascas e exemplo ([[mapa-do-app-do-artista]]) | **Aberto, com prevalência:** isso não confirma lançamento. [[decisoes-2026-10-20]] mantém o MVP em desenvolvimento. A tarefa 458 de [[board-estrutura-dos-apps]], definir wiki como produção, está Completed. Isso não confirma lançamento |
| 26 | Promessa da abertura do artista | A [[abertura-do-artista]] promete pagamento no app, escolha de horários e preços, check-in e check-out. Essas telas não existiam no retrato. O [[mvp]] é gratuito | **Encaminhado:** a cópia e as telas serão alinhadas ao MVP ([[decisoes-2026-10-21]]). A promessa na tela não vira alvo |
| 30 | Detalhe das telas do MVP | O conjunto de funções de 03/11 está fechado ([[mvp-final]]). Decisões de outubro ainda descrevem 2FA, chatbot, lista sem login, avaliação obrigatória e cadastro só com sexo. O inventário não redescreve esses pontos. Chat livre está fora do conjunto | **Fechado no cliente.** O detalhe do cliente está em [[mvp-funcoes-e-telas]] e [[mvp-alteracoes-pos-congelamento]]. O detalhe de tela do artista continua aberto. Termos, política e e-mails transacionais seguem diferidos ([[decisoes-2026-11-05]]) |

## Pendências antes do MVP

Consolidadas em [[mvp]]: criptografia, revisão da política, disparador de e-mails e troca do acesso provisório do Swagger. Gateway e preços saíram da lista porque o MVP é gratuito.

## Lacunas

- **Detalhe de cada tela do cliente:** fechado em 05/11. 2FA saiu das telas do cliente. Cadastro e agendamento são chatbot. A lista abre sem conta. A avaliação não é obrigatória. O sexo tem quatro botões. O detalhe do artista continua aberto. → [[mvp]], [[decisoes-2026-11-05]]
- **Região de lançamento:** São Paulo inteira, 01/01/2027. → [[lancamento-e-marketing]], [[mvp-final]]
- **Quantidade de artistas e orçamento de marketing:** sem número, de propósito. A quantidade seria chute: o formato do lançamento ainda não está definido. O orçamento só no fim de dezembro de 2026. → [[lancamento-e-marketing]], [[decisoes-2026-11-05]]
