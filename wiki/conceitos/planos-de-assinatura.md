---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-22
fontes: ["[[decisoes-2026-10-20]]", "[[planos]]", "[[plano-de-negocios-interno]]", "[[missao-e-valor]]", "[[termos-de-uso-do-app]]", "[[planos-do-artista]]", "[[bff-planos-e-cupons]]", "[[board-planos-e-assinaturas]]", "[[core-06-planos-cupons-e-cobranca]]"]
---

# Planos de assinatura

Ofertas pagas (e programas) para Artistas, estabelecimentos e clientes. Princípio: *os planos têm que garantir que Artista/cliente sempre use o app*. ([[planos]])

| Plano | Status | Resumo |
|---|---|---|
| Fidelidade | a definir | sem descrição |
| [[atendimento-imediato]] | definido | janela de 1–2 h para preencher furo de agenda |
| Atendimento imediato + Promoção | definido | variação para salões, com promoção em destaque |
| [[programa-de-pontos]] | a definir (ideia descrita) | pontos por interação, VIP, validade de 12 meses |
| Agenda pessoal | a definir | mais opções de agendamento pessoal contínuo |

Fonte: [[planos]].

## Como são vendidos

- Para o Artista, como investimento na própria arte, não só como visibilidade. ([[missao-e-valor]])
- Como "pacotes" que dão destaque no [[ranking]] e renovam pontos. ([[plano-de-negocios-interno]])
- Cobrança via parceiros de pagamento; sem reembolso no cancelamento. ([[termos-de-uso-do-app]]) → [[pagamentos]]

**Preços: pendentes.** Nenhum plano tem preço definido. ([[decisoes-2026-10-20]])

**Fora do [[mvp]]:** o lançamento é 100% gratuito, e os planos só serão contratáveis depois que o MVP estiver no ar. ([[decisoes-2026-10-20]]) O benefício principal do plano pago é entrar no bloco de pagantes do [[ranking]], com card destacado.

## O que a aba do artista mostra em 21/10

A aba Planos existe e o centro da tela diz "Tab Plans". Não explica plano nenhum. Não implementa os planos desta página. Os planos de produto continuam definidos aqui e não estão nessa aba. A contratação continua fora do MVP. ([[planos-do-artista]], [[decisoes-2026-10-20]]) Ver [[contradicoes-e-lacunas]].

## O que o backend publica em 21/10

A porta de planos e cupons existe e exige sessão. O serviço de planos não está ligado: não entra na ligação quando o backend sobe, e a configuração não tem endereço de planos. O pacote citado no projeto não conta como capacidade no ar. Os planos desta página continuam definidos e fora do lançamento gratuito. A aba Planos do artista continua casca. A contratação continua fora do MVP. ([[bff-planos-e-cupons]], [[decisoes-2026-10-20]], [[planos-do-artista]]) Ver [[contradicoes-e-lacunas]].

No núcleo, `Br.PaymentPlan.API` não tem host na lista dos 18 nem neste repositório; a aba continua casca, a porta do BFF continua sem ligação, a cobrança segue sem ação, e o lançamento gratuito permanece. ([[core-06-planos-cupons-e-cobranca]])

## O que o board pede em 21/10

O épico 342, Sistema de planos, está New e sem descrição. A história 370, Apresentação dos planos de pagamento, está New, sem descrição e sem tarefas. O épico 371, Sistema de Assinaturas, está New e sem descrição. ([[board-planos-e-assinaturas]]) Os planos desta página continuam definidos e fora do lançamento gratuito. A aba Planos do artista continua casca. O board não preenche essa casca. Nenhum item traz preço. Preços continuam pendentes.
