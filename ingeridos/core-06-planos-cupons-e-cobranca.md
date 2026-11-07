> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Planos, cupons e cobrança

## Onde isso mora

1. No app. [[planos-do-artista]] é casca. Cobrança está fora do MVP.
2. No BFF. O app fala com api.wecareu.app. [[bff-planos-e-cupons]] é porta sem ligação.
3. Planos e cupons: projeto Br.PaymentPlan.API. A lista dos 18 em beautiful-api não tem URL de planos. Este repositório também não publica host `*.bptsoftware.com.br` para esse projeto.
4. Banco [[banco-sql-paymentplans]], SQL PaymentPlans, tabelas Cupom, PaymentPlans e PlanDurationValue.
5. Cobrança: projeto Br.Billing.API (a pasta). Host https://billingapimicroservice.bptsoftware.com.br/. O compose cita o Dockerfile como Br.Biling.API.

## O que isso é

O plano é a oferta de uma empresa num sistema. Guarda nome, descrição, nome curto, ordem, se ainda está em efeito, quando nasceu, quando mudou e quem mudou. Quem mudou vem no pedido. A sessão não preenche isso.

Cada plano leva preços em PlanDurationValue. O preço guarda uma data no campo de duração, um valor, desconto em dinheiro, desconto em percentual e a ordem, além do efeito, das datas e de quem mudou. O preço aponta para o plano. O código do plano novo nasce no banco e não é copiado para o preço nesse passo: o vínculo fica como veio no pedido.

O cupom é um desconto nomeado da mesma empresa e do mesmo sistema. Guarda nome, uma data no campo de duração, desconto em dinheiro, desconto em percentual, se ainda está em efeito, as datas e quem mudou. Não aponta para um plano.

A cobrança seria o vínculo de uma pessoa com um plano, na empresa e no sistema, com efeito, datas e quem mudou. A porta não oferece essa ação.

Lista e abertura de plano, e a lista de cupom, devolvem só o que está em efeito, da empresa e do sistema pedidos. A lista de planos sai na ordem. Os preços dessa lista são pedidos sem espera.

## O que já se consegue fazer

- Ver a lista de planos em efeito. A lista pode voltar sem os preços. A leitura solta dos preços pode quebrar a chamada.
- Abrir um plano em efeito, com os preços em efeito, na ordem. Sem esse plano, a abertura quebra.
- Gravar um plano novo, com os preços que vieram sem código. Preço que já tem código é atualizado no mesmo passo. A resposta é que deu certo, e o código do plano não volta. Sem a lista de preços no pedido, a gravação quebra. Plano novo não deixa rastro.
- Gravar de novo um plano que já tem código, pela ação de gravar. Não relê. Atualiza o pedido e os preços e responde sucesso, sem o código. O rastro sai como inclusão, antes da gravação.
- Alterar um plano. A ação relê o plano em efeito e, na hora de gravar, esbarra na cópia que acabou de ler. A alteração não completa. Sem o plano em efeito, quebra na releitura.
- Desfazer um plano. O caminho pede o identificador com o nome de endereço, e a ação espera o código do plano. O código não chega, o plano não é achado e a chamada quebra antes do rastro. A chamada chega como leitura.

- Ver a lista de cupons em efeito. O cupom não fica sob api/Cupom: as ações respondem na raiz deste serviço.
- Abrir um cupom. O caminho nomeia o último trecho como plano, e a ação espera o código do cupom. O trecho não preenche o cupom. A busca não acha e a resposta volta vazia.
- Gravar cupom novo. A ação busca o cupom antes de ele existir e a chamada quebra. Não grava e não deixa rastro.
- Gravar de novo um cupom que já existe. A cópia lida é marcada fora de efeito e a gravação do pedido esbarra nessa cópia. Não completa.
- Alterar um cupom em efeito. Relê e a gravação esbarra na cópia lida. Não completa.
- Desfazer um cupom. O caminho pede o identificador com o nome de endereço. O código do cupom não chega e a chamada quebra. A chamada chega como leitura.

Conferir um cupom pelo nome existe no miolo e não sobe como ação.

Antes de cada ação de plano e de cupom o serviço pergunta ao login se o acesso vale. Se o login aceita, a ação é recusada. Se o login não aceita, a ação segue.

O rastro do plano nomeia o banco e a tabela como PaymentPlan. O dado continua em PaymentPlans, no banco PaymentPlans. O rastro do cupom nomeia o banco como PaymentPlan e a tabela como Cupom. A tabela do cupom é Cupom. Quando o rastro roda, ele exige nos cabeçalhos quem mudou, a empresa e o sistema. Sem isso, a chamada quebra antes de gravar. A falha segue para a operação com texto de endereço, e a chamada estoura.

Cobrança: a porta não tem ação. O miolo interno gravaria uma linha nova e tiraria uma linha de efeito pelo código, e nenhuma ação chama isso.

## Em que pé está

Já se lista plano e cupom em efeito e se abre um plano com os preços, sem host público de planos, com [[planos-do-artista]] em casca e [[bff-planos-e-cupons]] sem ligação; gravar plano novo responde sucesso sem o código, a lista pode vir sem preço, alterar plano ou cupom esbarra na cópia relida, ver cupom e desfazer plano ou cupom não recebem o identificador do caminho, cupom novo quebra, a ação é recusada quando o login aceita o acesso, e https://billingapimicroservice.bptsoftware.com.br/ não oferece ação.

## O que esta nota não cobre

A tela além da casca [[planos-do-artista]]. O miolo de [[bff-planos-e-cupons]], além do lugar dessa porta na cadeia. Cobrar de fato: cartão, fatura, recorrência, gateway e o efeito do plano na conta. O conteúdo das linhas já gravadas. A amarração de empresa, sistema e pessoa com os outros bancos.

## Incertezas

A pergunta ao login reenvia o acesso já apresentado como acesso. A consulta pode falhar com uma sessão boa. Quando falha, a ação segue. Não dá para ler a porta como fechada para quem não está logado.

No Windows e no Linux o código abre o catálogo PaymentPlan, no singular. O banco desta extração é PaymentPlans. Fora desses dois sistemas, o contexto procura a entrada Address da configuração, e o arquivo deste projeto declara UserLogin. O conjunto de preços no contexto não usa o nome da tabela. A classe marca PlanDurationValue. Vale a tabela.

A resposta de gravar plano é sempre o sucesso da porta, não o resultado do rastro nem o código gravado. O rastro do cupom, quando a gravação chega nele, escreve o motivo com a grafia Incertion.

Este repositório não declara o host de planos nem o de cobrança. O de cobrança fecha a cadeia pela lista dos 18. O de planos não está nessa lista.

O contexto da cobrança expõe Bilings. A classe marca a tabela Biling. O código abre o catálogo Audition. Bilings não está nos onze bancos de 21/10. O miolo está nomeado como Pagar.me e não chama a gravação nem o desligamento. O compose, além do Dockerfile Br.Biling.API, declara o banco UserLogin para esse serviço e faz o serviço depender dele mesmo.
