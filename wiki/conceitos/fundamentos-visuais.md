---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-10-21
fontes: ["[[lyraui-05-sistema-de-tema]]", "[[lyraui-09-fundamentos-visuais]]", "[[identidade-visual]]", "[[panorama-do-design-system]]", "[[vocabulario-visual]]"]
---

# Fundamentos visuais

Alvo da [[lyraui]]. O app em uso ainda consome `@wecareu/tokens` e `@wecareu/theme`. ([[lyraui-05-sistema-de-tema]])

## Tema

Light e dark existem, e a pessoa **não escolhe**. CLIENT é só light; WORKER é só dark. A diferença é intencional, para separar os dois apps. Não há tela de alternar tema. ([[lyraui-05-sistema-de-tema]])

Regra: nenhuma cor, espaçamento ou tipografia hardcoded. O que não existe como token é decidido com o Tech Lead antes de entrar. ([[lyraui-05-sistema-de-tema]])

## Cores

| Paleta | Base |
|---|---|
| Primary | `#712FC1` |
| Secondary | `#D85A30` (era violeta; virou coral para não brigar com a Primary) |
| Tertiary | `#FF0098` |
| Neutral | 12 passos, ancorada em quatro cores já usadas no app |

Escalas coloridas de 8 passos (100 a 800), ancoradas no 500, com matiz e saturação HSL constantes. Light e dark se espelham (100↔800). O fundo do dark, `#0B0C13`, fica fora da escala. Grades WCAG existem, mas os hex dos passos não estão nas fontes. ([[lyraui-09-fundamentos-visuais]])

## Tipografia e ícones

- Títulos: **Livvic**, só em tamanho grande (x-height baixa).
- Corpo e labels: Plus Jakarta Sans ou DM Sans, sem escolha.
- Ícones: outline. Phosphor é a candidata; Tabler e Lucide ficam de reserva. O ícone do Pix é um SVG avulso, qualquer que seja a biblioteca. ([[lyraui-09-fundamentos-visuais]])

## O kit em 21/10

Isto não substitui o alvo acima. `@wecareu/tokens` 0.2.8 e `@wecareu/theme` 0.3.4 pintam a tela. Não há página nem teste dos dois. ([[identidade-visual]], [[panorama-do-design-system]])

- Claro e escuro. Se ninguém escolhe, abre no claro. A pessoa não escolhe neste repositório, e o kit permite alternar com a tela aberta. O interruptor do app do cliente não está no repositório do kit. ([[identidade-visual]])
- Ação no claro: roxo `#712fc1`, o mesmo Primary do alvo. Ação secundária no claro: lilás `#817eb9`. O texto de instalação dos tokens ainda cita `#2E6BE6`. ([[identidade-visual]])
- A letra do kit é Livvic no corpo, no rótulo e no botão, em regular, semibold e bold. ([[identidade-visual]])
- Fundo da página no escuro: `#0b0c13`, o mesmo `#0B0C13` do alvo. ([[identidade-visual]])
- Ícones do kit: `@wecareu/icons` 1.3.3, 69 desenhos. ([[vocabulario-visual]])

O alvo de 20/10 continua com Livvic só no título grande, corpo em aberto, Secondary coral e CLIENT light / WORKER dark. O kit não confirma esses três. Ver [[contradicoes-e-lacunas]], [[kit-visual]].

## Em aberto

Fonte de corpo, biblioteca de ícones, espelho da Neutral de 12 passos, e qual tema um futuro app de Empresas usaria. O kit de 21/10 já pinta o corpo em Livvic; a escolha de corpo do alvo continua em aberto. Phosphor segue candidato no alvo. ([[lyraui-09-fundamentos-visuais]], [[identidade-visual]])
