---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-22
fontes: ["[[decisoes-2026-10-20]]", "[[ssot-backlog]]", "[[lyraui-02-contexto-wecareu]]", "[[brainstorming-wecareu]]", "[[politica-de-privacidade]]", "[[termos-de-uso-do-app]]", "[[seguranca-e-protecao-de-dados]]", "[[abertura-do-artista]]", "[[o-que-ainda-nao-esta-no-app-do-artista]]", "[[bff-planos-e-cupons]]", "[[board-planos-e-assinaturas]]", "[[core-06-planos-cupons-e-cobranca]]"]
---

# Pagamentos

## No MVP: nenhum

O [[mvp]] é **100% gratuito**, sem nenhum pagamento pelo app. Os planos só passam a ser contratáveis depois que o MVP estiver no ar. ([[decisoes-2026-10-20]])

Com isso, escolher o gateway deixa de ser requisito do MVP (antes era, pela primeira rodada de [[decisoes-2026-10-20]]).

## Depois do MVP

- **[[planos-de-assinatura]]** pagos pelos Artistas.
- **Serviço do cliente ao Artista:** a WeCareU não cobrará nada sobre o serviço realizado; apenas a taxa do meio de pagamento será repassada, e quem a paga é o **Artista**. ([[decisoes-2026-10-20]]) Fica implícito que o pagamento do serviço poderá passar pelo app no futuro.
- **Comunicação da taxa:** deve ficar explícito, para o Artista, que o valor não é uma taxa do app, e sim da empresa de cartão de crédito, pelo serviço de pagamento ou parcelamento. ([[decisoes-2026-10-20]]) Isso protege o argumento central de "zero comissão" do [[modelo-de-receita]].

## Gateway: não escolhido

Nenhum gateway foi contratado; a fase de aquisição de meios de pagamento não começou. As menções nos documentos legais são provisórias. ([[decisoes-2026-10-20]])

Candidatos citados até agora:

| Fonte | Gateways citados |
|---|---|
| [[brainstorming-wecareu]] e [[ssot-backlog]] ("ainda em análise"; e-Rede na frente pelo 3DS) | BrasPag, MundiPag, PagSeguro, PicPay, Ebanx, PayPal, Pay2me, e-Rede, Aarin, PayMee |
| [[lyraui-02-contexto-wecareu]] | Stripe e/ou MercadoPago, "a confirmar com back-end e financeiro" |
| [[politica-de-privacidade]] | Stripe ou MercadoPago |
| [[termos-de-uso-do-app]] | Stripe, PayPal etc. |
| [[seguranca-e-protecao-de-dados]] | Stripe, PayPal, MercadoPago |

## Requisitos (para quando houver pagamento)

- Checkout transparente. ([[brainstorming-wecareu]])
- Não armazenar dados completos de cartão. ([[politica-de-privacidade]], [[termos-de-uso-do-app]])
- Criptografia em trânsito e em repouso. ([[seguranca-e-protecao-de-dados]])

## O que o app do artista mostra em 21/10

Nenhum pagamento está construído neste retrato. A aba Planos é casca. Ícone ou slide não é cobrança. ([[o-que-ainda-nao-esta-no-app-do-artista]])

A abertura promete "pagamentos direto no app". Isso é cópia da tela, não alvo novo. A decisão permanece: o MVP é 100% gratuito, sem pagamento no lançamento. ([[abertura-do-artista]], [[decisoes-2026-10-20]]) Ver [[contradicoes-e-lacunas]].

## O que o backend publica em 21/10

Esta leva não publica cobrança. A nota de planos e cupons não cobre cobrança, assinatura paga nem confirmação de pagamento. ([[bff-planos-e-cupons]])

No núcleo, `Br.Billing.API` tem o host `https://billingapimicroservice.bptsoftware.com.br/` e a porta está sem ação; o MVP segue gratuito. ([[core-06-planos-cupons-e-cobranca]], [[decisoes-2026-10-20]])

## Em aberto

- Os documentos legais ainda descrevem pagamentos e planos pagos; para o MVP gratuito, isso fica desalinhado. Ver [[termos-e-responsabilidades]].

## O que o board pede em 21/10

O épico 371 pede assinatura. A tarefa 395, [BE] Gerar cobrança do cliente, está New e sem descrição. A tarefa 398, [BE] Gerar Cobrança do artista, está New e sem descrição. A tarefa 400, [BE] Criar processo de Pagamento dinâmico utilizando injeção de dependência, está New e sem descrição. As tarefas 396 e 397 pedem validade do pacote. Estão New e sem descrição. ([[board-planos-e-assinaturas]]) Isso não escolhe gateway. Não põe cobrança no [[mvp]]. O lançamento continua 100% gratuito. O item 3 de [[contradicoes-e-lacunas]] permanece resolvido para o MVP.
