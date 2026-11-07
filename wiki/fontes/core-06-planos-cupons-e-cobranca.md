---
tipo: fonte
arquivo: "ingeridos/core-06-planos-cupons-e-cobranca.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Planos, cupons e cobrança"]
---

# Planos, cupons e cobrança

Retrato de 21/10. Planos e cupons: projeto `Br.PaymentPlan.API`. A lista dos 18 em [[beautiful-api]] não tem URL de planos. Este repositório também não publica host `*.bptsoftware.com.br` para esse projeto. Banco [[banco-sql-paymentplans]], SQL `PaymentPlans`, tabelas `Cupom`, `PaymentPlans` e `PlanDurationValue`.

Cobrança: projeto `Br.Billing.API`. Host `https://billingapimicroservice.bptsoftware.com.br/`. A porta não tem ação. O compose cita o Dockerfile como `Br.Biling.API`.

[[bff-planos-e-cupons]] continua porta sem ligação. [[planos-do-artista]] continua casca. Cobrança fica fora do MVP. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

1. No app. [[planos-do-artista]] é casca. Cobrança está fora do MVP.
2. No BFF. O app fala com `api.wecareu.app`. [[bff-planos-e-cupons]] é porta sem ligação. Esta nota não reescreve o miolo dessa porta e não a liga.
3. Planos e cupons, neste projeto: `Br.PaymentPlan.API`, sem host nesta extração.
4. Cobrança, neste projeto: `Br.Billing.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O plano é a oferta de uma empresa num sistema. Guarda nome, descrição, nome curto, ordem, se ainda está em efeito, quando nasceu, quando mudou e quem mudou. Quem mudou vem no pedido. A sessão não preenche isso.

Cada plano leva preços em `PlanDurationValue`. O preço guarda uma data no campo de duração, um valor, desconto em dinheiro, desconto em percentual e a ordem, além do efeito, das datas e de quem mudou. O preço aponta para o plano. O código do plano novo nasce no banco e não é copiado para o preço nesse passo: o vínculo fica como veio no pedido.

O cupom é um desconto nomeado da mesma empresa e do mesmo sistema. Guarda nome, uma data no campo de duração, desconto em dinheiro, desconto em percentual, se ainda está em efeito, as datas e quem mudou. Cupom não aponta para um plano.

A cobrança seria o vínculo de uma pessoa com um plano, na empresa e no sistema, com efeito, datas e quem mudou. A porta não oferece essa ação.

Lista e abertura de plano, e a lista de cupom, devolvem só o que está em efeito, da empresa e do sistema pedidos. A lista de planos sai na ordem. Os preços dessa lista são pedidos sem espera.

## O que já se consegue fazer

Ver a lista de planos em efeito. A lista pode voltar sem os preços. A leitura solta dos preços pode quebrar a chamada.

Abrir um plano em efeito, com os preços em efeito, na ordem. Sem esse plano, a abertura quebra.

Gravar um plano novo, com os preços que vieram sem código. Preço que já tem código é atualizado no mesmo passo. A resposta é que deu certo, e o código do plano não volta. Sem a lista de preços no pedido, a gravação quebra. Plano novo não deixa rastro.

Gravar de novo um plano que já tem código, pela ação de gravar. Não relê. Atualiza o pedido e os preços e responde sucesso, sem o código. O rastro sai como inclusão, antes da gravação.

Alterar um plano. A ação relê o plano em efeito e, na hora de gravar, esbarra na cópia que acabou de ler. A alteração não completa. Sem o plano em efeito, quebra na releitura.

Desfazer um plano. O caminho pede o identificador com o nome de endereço, e a ação espera o código do plano. O código não chega, o plano não é achado e a chamada quebra antes do rastro. A chamada chega como leitura.

Ver a lista de cupons em efeito. O cupom não fica sob `api/Cupom`: as ações respondem na raiz deste serviço.

Abrir um cupom. O caminho nomeia o último trecho como plano, e a ação espera o código do cupom. O trecho não preenche o cupom. A busca não acha e a resposta volta vazia. Ver cupom não recebe o identificador do caminho.

Gravar cupom novo. A ação busca o cupom antes de ele existir e a chamada quebra. Cupom novo quebra antes de gravar. Não deixa rastro.

Gravar de novo um cupom que já existe. A cópia lida é marcada fora de efeito e a gravação do pedido esbarra nessa cópia. Não completa.

Alterar um cupom em efeito. Relê e a gravação esbarra na cópia lida. Alterar plano ou cupom esbarra na cópia relida e não completa.

Desfazer um cupom. O caminho pede o identificador com o nome de endereço. O código do cupom não chega e a chamada quebra. Desfazer plano ou cupom não recebe o identificador do caminho. A chamada chega como leitura.

Conferir um cupom pelo nome existe no miolo e não sobe como ação.

Antes de cada ação de plano e de cupom o serviço pergunta ao login se o acesso vale. Checagem invertida: se o login aceita, a ação é recusada; se o login não aceita, a ação segue.

O rastro do plano nomeia o banco e a tabela como `PaymentPlan`. O dado está em `PaymentPlans`, no banco `PaymentPlans`. O rastro do cupom nomeia o banco como `PaymentPlan` e a tabela como `Cupom`. A tabela do cupom é `Cupom`. Quando o rastro roda, ele exige nos cabeçalhos quem mudou, a empresa e o sistema. Sem isso, a chamada quebra antes de gravar. A falha segue para a operação com texto de endereço, e a chamada estoura.

Cobrança: a porta não tem ação. O miolo interno gravaria uma linha nova e tiraria uma linha de efeito pelo código, e nenhuma ação chama isso.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Pela metade | Listar plano e cupom em efeito e abrir um plano com os preços, sem host público de planos. [[planos-do-artista]] em casca. [[bff-planos-e-cupons]] sem ligação. Gravar plano novo responde sucesso sem o código. A lista pode vir sem preço. Alterar plano ou cupom esbarra na cópia relida e não completa. Ver cupom e desfazer plano ou cupom não recebem o identificador do caminho. Cupom novo quebra antes de gravar. A checagem está invertida |
| Casca | Cobrança. O host `https://billingapimicroservice.bptsoftware.com.br/` não oferece ação |

## O que esta nota não cobre

A tela além da casca [[planos-do-artista]]. O miolo de [[bff-planos-e-cupons]], além do lugar dessa porta na cadeia. Cartão, fatura, recorrência, gateway e o efeito do plano na conta. O conteúdo das linhas já gravadas. A amarração de empresa, sistema e pessoa com os outros bancos. Senha, string de conexão e identificador.

## Incertezas

A pergunta ao login reenvia o acesso já apresentado como acesso. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler a porta como fechada para quem não está logado.

No Windows e no Linux o código abre o catálogo `PaymentPlan`, no singular. O banco desta extração é `PaymentPlans`. Fora desses dois sistemas, o contexto procura a entrada `Address` da configuração, e o arquivo deste projeto declara `UserLogin`. O conjunto de preços no contexto não usa o nome da tabela. A classe marca `PlanDurationValue`. Vale a tabela. Por este repositório não dá para fechar qual banco o host publicado estaria usando. O wikilink permanece [[banco-sql-paymentplans]].

A resposta de gravar plano é sempre o sucesso da porta, não o resultado do rastro nem o código gravado. O rastro do cupom, quando a gravação chega nele, escreve o motivo com a grafia `Incertion`.

Este repositório não declara o host de planos nem o de cobrança. O de cobrança fecha a cadeia pela lista dos 18, a linha `UrlsBilling` de [[beautiful-api]]. O de planos não está nessa lista. Esta nota não inventa URL de planos.

O contexto da cobrança expõe `Bilings`. A classe marca a tabela `Biling`. O código abre o catálogo `Audition`. `Bilings` não está nos onze bancos de 21/10. O miolo está nomeado como Pagar.me e não chama a gravação nem o desligamento. O compose, além do Dockerfile `Br.Biling.API`, declara o banco `UserLogin` para esse serviço e faz o serviço depender dele mesmo. A porta segue sem ação.

Ver [[bpt-core]], [[planos-de-assinatura]] e [[pagamentos]].
