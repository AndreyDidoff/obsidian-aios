---
tipo: fonte
arquivo: "ingeridos/08-enderecos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Endereços"]
---

# Endereços

O que este backend publica para o local da pessoa da sessão. Caminho `beautiful/api/Address`. Esta fonte é [[bff-enderecos]]. A fonte do app do cliente continua [[enderecos]]. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Não descreve mapa nem o formato do endereço. Não é o CEP da Google.

## O que está publicado

- **Ver a lista** dos endereços da pessoa que está na sessão.
- **Criar** um endereço.
- **Editar** um endereço.
- **Apagar** um endereço, pelo identificador desse endereço.

A lista sai da pessoa que está na sessão. A exclusão também usa o identificador dessa pessoa. Criar e editar encaminham o endereço recebido.

No código, a ação de apagar está nomeada como se fosse foto. O que ela apaga é o endereço.

## Quem pode

A porta está marcada como exigindo pessoa logada. Essa marca pode não valer na entrada: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

A lista e a exclusão usam o identificador da sessão. Criar e editar encaminham o endereço recebido. Esta nota não separa cliente de profissional: o código desta porta fala em pessoa logada.

## Em que pé está

**No ar.** Lista, criar, editar e apagar estão publicados. O serviço de endereço está ligado na subida deste backend. A marca de pessoa logada pode não valer na entrada, a mesma lacuna de sessão.

## O que esta nota não cobre

Tela, mapa e o formato dos dados que compõem um endereço. Não é o CEP da Google. Endereço de outra pessoa. Telefone, foto, relato e documento de validação. A tela do app do cliente continua em [[enderecos]].

## Incertezas

Criar e editar encaminham o endereço recebido. Nesta porta não aparece uma segunda conferência que troque esse endereço pelo identificador da sessão. Não dá para afirmar, só com esta leitura, se um endereço enviado em nome de outra pessoa seria recusado mais adiante.

Os campos de um endereço não estão declarados nesta porta.

Ver [[beautiful-api]].
