---
tipo: fonte
arquivo: "ingeridos/09-telefones.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Telefones"]
---

# Telefones

O que este backend publica para o número da pessoa da sessão. Caminho `beautiful/api/Phone`. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Não descreve os dados de um telefone. O telefone do cadastro em duas etapas não é esta porta: o bruto não descreve esse telefone. O alvo permanece em [[cadastro]].

## O que está publicado

- **Ver a lista** dos telefones da pessoa da sessão. O pedido usa o identificador da sessão.
- **Incluir** um telefone. Na nota, a ação é guardar.
- **Editar** um telefone.
- **Apagar** um telefone, pelo identificador desse telefone.

Incluir, editar e apagar encaminham o telefone, ou o identificador do telefone, junto com o login.

No código, várias dessas ações estão nomeadas como se fossem foto. O que esta porta lista, inclui, edita e apaga é telefone.

## Quem pode

A porta está marcada como exigindo pessoa logada. Essa marca pode não valer na entrada: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

A lista usa o identificador da pessoa da sessão. Incluir, editar e apagar encaminham o telefone recebido. Esta nota não separa cliente de profissional.

## Em que pé está

**No ar.** Lista, incluir, editar e apagar estão publicados. O serviço de telefone está ligado na subida deste backend. A marca de pessoa logada pode não valer na entrada, a mesma lacuna de sessão.

## O que esta nota não cobre

Tela e os dados que compõem um telefone. Telefone de outra pessoa. Endereço, foto, relato e documento de validação. O telefone da segunda etapa do [[cadastro]].

## Incertezas

A lista é da pessoa logada. Incluir, editar e apagar, nesta porta, encaminham o que foi enviado. Não dá para afirmar, só com esta leitura, se um telefone de outra pessoa seria recusado mais adiante.

Os dados que formam um telefone não estão declarados nesta porta.

Ver [[beautiful-api]], [[cadastro]].
