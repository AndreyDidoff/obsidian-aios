---
tipo: fonte
arquivo: "ingeridos/11-relatos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Relatos"]
---

# Relatos

O que este backend publica para o relato da pessoa da sessão e para a foto desse relato. Caminho `beautiful/api/Report`. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Não declara texto, motivo nem sobre quem é o relato. A foto pedida sozinha, fora de um relato, está em [[bff-fotos]].

## O que está publicado

- **Ver a lista** dos relatos da pessoa da sessão.
- **Criar** um relato.
- **Editar** um relato.
- **Apagar** um relato, pelo identificador desse relato.
- **Anexar** uma foto a um relato.
- **Editar** a foto de um relato.
- **Tirar** uma foto de um relato, pelo identificador do relato e pelo identificador da foto.

A lista sai da pessoa que está na sessão. A exclusão do relato também usa o identificador dessa pessoa. Criar e editar encaminham o relato recebido. Anexar e editar a foto encaminham a foto do relato. Tirar uma foto aponta o relato e a foto.

## Quem pode

A porta está marcada como exigindo pessoa logada. Essa marca pode não valer na entrada: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

A lista e a exclusão do relato usam o identificador da sessão. Criar, editar, anexar foto e editar a foto do relato encaminham o que foi enviado. Tirar uma foto aponta o relato e a foto. Esta nota não separa cliente de profissional.

## Em que pé está

**No ar.** Lista, criar, editar e apagar o relato, e anexar, editar e tirar uma foto desse relato, estão publicados. O serviço de relato está ligado na subida deste backend. A marca de pessoa logada pode não valer na entrada, a mesma lacuna de sessão.

## O que esta nota não cobre

Tela. Texto, motivo e sobre quem é o relato: esta porta não declara esses dados. A foto geral, fora do relato, está em [[bff-fotos]]. Endereço, telefone e documento de validação.

## Incertezas

O código não diz se o relato é denúncia, avaliação ou registro de atendimento. Nenhum desses sentidos está declarado nesta porta, e esta nota não escolhe um.

Criar e editar encaminham o relato recebido. Não dá para afirmar, só com esta leitura, se um relato enviado em nome de outra pessoa seria recusado mais adiante. Também não está declarado o que a foto do relato mostra.

Ver [[beautiful-api]], [[seguranca-do-atendimento]].

O board pede um sistema de denúncia ([[board-denuncia]]). É outro retrato. Esta porta não é esse sistema. O código não diz se o relato é denúncia, avaliação ou atendimento. O pedido de denúncia fica ao lado. Esta porta não declara o sentido. A história 242 está Completed no board. Completed é o estado do work item. Esta porta já está no ar como retrato de código. Isso não vem do estado do work item.
