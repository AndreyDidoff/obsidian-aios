---
tipo: fonte
arquivo: "ingeridos/06-planos-e-cupons.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Planos e cupons"]
---

# Planos e cupons

O que este backend publica para perguntar quais planos existem e se um cupom informado vale. É uma porta do backend, não a lista comercial da empresa. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Esta porta não apaga a definição dos planos em [[planos-de-assinatura]]. O lançamento segue gratuito, sem planos pagos. A aba Planos do artista continua casca.

## O que está publicado

A porta oferece duas perguntas. Ela está marcada como exigindo pessoa logada:

- **Listar** os planos.
- **Validar** um cupom informado.

A porta não entrega a resposta dessas perguntas. O serviço de planos não está ligado, então lista e validação não se completam por este backend.

## Quem pode

A porta está marcada como exigindo pessoa logada. A ação existe e exige sessão. Se essa marca é aplicada na entrada do pedido fica em aberto, porque o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Ver [[bff-o-que-e-este-backend]] e [[contradicoes-e-lacunas]].

Este repositório não separa cliente de profissional nessas duas perguntas, nem diz quem pode usar um cupom.

## Em que pé está

**Porta sem ligação.**

A ação existe neste backend. O serviço de planos não entra na ligação quando o backend sobe, e a configuração não tem endereço de planos.

O pacote de planos citado no projeto não conta como capacidade no ar.

## O que esta nota não cobre

Nome de plano, preço, benefício, comissão ou prazo. Cobrança, assinatura paga e confirmação de pagamento. A regra de quando um cupom vale, e o que a pessoa recebe se ele valer. Telas de escolha de plano.

## Incertezas

Nenhum nome de plano aparece neste repositório. Esta nota não traz nome vindo de outro documento.

Não dá para afirmar o que a validação de um cupom devolveria, nem a forma do cupom.

Não dá para afirmar se a lista seria a dos planos comerciais da WeCareU.

Não dá para afirmar preço, benefício ou comissão.

Ver [[beautiful-api]], [[planos-de-assinatura]], [[pagamentos]].

O board pede sistema de planos e sistema de assinaturas ([[board-planos-e-assinaturas]]). O épico 342, Sistema de planos, está New e sem descrição. O épico 371, Sistema de Assinaturas, está New e sem descrição. A tarefa 395, [BE] Gerar cobrança do cliente, está New e sem descrição. A tarefa 400, [BE] Criar processo de Pagamento dinâmico utilizando injeção de dependência, está New e sem descrição. New é o estado do work item. Esta porta continua sem ligação, como retrato de código. Isso não vem do estado do work item. O board não liga o serviço de planos. Não escolhe gateway. Não põe cobrança no [[mvp]]. Não preenche a aba Planos.
