---
tipo: fonte
arquivo: "ingeridos/12-documentos-para-validacao.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Documentos para validação"]
---

# Documentos para validação

O que este backend publica para um conjunto de documentos num fluxo de validação. Caminho `beautiful/api/Validation`. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. A consulta é de um conjunto por vez, pelo identificador, limitada à pessoa da sessão. O alvo de validação do Artista, com upload e check-in, permanece em [[seguranca-do-atendimento]]. Esta porta não é esse fluxo. Também não é a conferência de CPF e CNPJ de [[bff-cadastro]].

## O que está publicado

- **Consultar** um conjunto de documentos, pelo identificador desse conjunto.
- **Enviar** um conjunto de documentos.
- **Editar** um conjunto de documentos.
- **Apagar** um conjunto de documentos, pelo identificador desse conjunto.

A consulta pede o identificador do conjunto e o identificador da pessoa na sessão. A exclusão faz o mesmo. Enviar e editar encaminham o conjunto recebido.

Não há lista de todos os conjuntos. Não há, nesta porta, o passo em que alguém aprova ou recusa.

No código, a ação de apagar está nomeada como se apagasse a pessoa. O que ela apaga é o conjunto de documentos.

## Quem pode

A porta está marcada como exigindo pessoa logada. Essa marca pode não valer na entrada: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

Consultar e apagar usam o identificador do conjunto e o identificador da pessoa na sessão. Enviar e editar encaminham o conjunto recebido. Esta nota não separa cliente de profissional.

## Em que pé está

**No ar.** Consultar um conjunto pelo identificador, enviar, editar e apagar estão publicados. O serviço de validação está ligado na subida deste backend. Uma lista de todos os conjuntos não faz parte desta porta. O passo de aprovar ou recusar não faz parte desta porta. A marca de pessoa logada pode não valer na entrada, a mesma lacuna de sessão.

## O que esta nota não cobre

Tela. O passo em que alguém aprova ou recusa o conjunto. A foto pedida fora deste conjunto: [[bff-fotos]]. Endereço, telefone e relato. A conferência de CPF e CNPJ de [[bff-cadastro]]. O upload e o check-in da validação do Artista.

## Incertezas

Existe um fluxo de validação. Não dá para afirmar quais documentos entram no conjunto. O código não declara RG, CPF, certificado nem outro tipo, e esta nota não escolhe um.

Enviar e editar encaminham o conjunto recebido. Não dá para afirmar, só com esta leitura, se um conjunto enviado em nome de outra pessoa seria recusado mais adiante. Os passos posteriores da validação, além de consultar, enviar, editar e apagar o conjunto, não aparecem nesta porta.

Ver [[beautiful-api]], [[seguranca-do-atendimento]].
