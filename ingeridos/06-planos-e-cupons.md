> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Planos e cupons

## O que isso é para o app

É a porta de planos e cupons deste backend. Por ela o aplicativo pergunta quais planos existem e se um cupom informado vale. É uma porta do backend, não a lista comercial da empresa.

## O que a pessoa já consegue fazer por este backend

A porta já oferece duas perguntas. Ela está marcada como exigindo pessoa logada:

- Listar os planos.
- Validar um cupom informado.

A porta não entrega a resposta dessas perguntas. O serviço de planos não está ligado, então lista e validação não se completam por este backend.

## Quem pode

A porta está marcada como exigindo pessoa logada. Se essa marca é aplicada na entrada do pedido fica em aberto, porque o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. Veja [[01-o-que-e-este-backend]].

Este repositório não separa cliente de profissional nessas duas perguntas, nem diz quem pode usar um cupom.

## Em que pé está

**Porta sem ligação.**

A ação existe neste backend. O serviço de planos não está conectado: ele não entra na ligação quando o backend sobe, e a configuração de endereços não tem endereço de planos.

O pacote de planos citado no projeto não conta como capacidade no ar.

## O que esta nota não cobre

- Nome de plano, preço, benefício, comissão ou prazo.
- Cobrança, assinatura paga e confirmação de pagamento.
- A regra de quando um cupom vale, e o que a pessoa recebe se ele valer.
- Telas de escolha de plano.

## Ligações

A sessão desta porta conversa com [[03-entrar-sair-e-senha]]. Cliente e profissional estão em [[02-cliente-e-profissional]]. O que está preparado e ainda não é oferecido está em [[14-preparado-e-ainda-nao-oferecido]]. Serviços são outra porta: [[05-servicos]].

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[04-cadastro]] [[05-servicos]] [[06-planos-e-cupons]] [[07-bloqueio]] [[08-enderecos]] [[09-telefones]] [[10-fotos]] [[11-relatos]] [[12-documentos-para-validacao]] [[13-o-que-a-pessoa-pode-ver]] [[14-preparado-e-ainda-nao-oferecido]]

## Incertezas

- Nenhum nome de plano aparece neste repositório. Esta nota não traz nome vindo de outro documento.
- Não dá para afirmar o que a validação de um cupom devolveria, nem a forma do cupom.
- Não dá para afirmar se a lista seria a dos planos comerciais da WeCareU.
- Não dá para afirmar preço, benefício ou comissão.
