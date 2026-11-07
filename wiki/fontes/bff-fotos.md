---
tipo: fonte
arquivo: "ingeridos/10-fotos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Fotos"]
---

# Fotos

O que este backend publica para buscar uma foto pelo identificador, guardar e apagar. Caminho `beautiful/api/Photo`. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Não descreve onde a foto aparece. A foto de um relato é outra porta: [[bff-relatos]].

## O que está publicado

- **Buscar** uma foto, pelo identificador dessa foto.
- **Guardar** uma foto.
- **Apagar** uma foto, pelo identificador dessa foto.

O pedido de busca, de guarda e de exclusão encaminha a foto, ou o identificador dela, junto com o login.

Lista de fotos e edição de uma foto já guardada não fazem parte desta porta.

## Quem pode

A porta está marcada como exigindo pessoa logada. Essa marca pode não valer na entrada: o arranque prepara a sessão e não coloca a leitura dela no caminho do pedido. O detalhe está em [[bff-o-que-e-este-backend]]. Ver [[contradicoes-e-lacunas]].

Buscar, guardar e apagar não releem o identificador da sessão. Encaminham o identificador da foto, ou a foto enviada, junto com o login. Esta nota não separa cliente de profissional.

## Em que pé está

**No ar** para buscar uma foto pelo identificador, guardar e apagar. O serviço de foto está ligado na subida deste backend. Lista de fotos e edição de uma foto já guardada não fazem parte desta porta. A marca de pessoa logada pode não valer na entrada, a mesma lacuna de sessão.

## O que esta nota não cobre

Tela e o lugar em que a foto aparece. A foto de um relato: anexar, editar e tirar essa foto estão em [[bff-relatos]]. O conjunto de documentos de validação: [[bff-documentos-para-validacao]].

## Incertezas

O código não diz se esta foto é de perfil, de portfólio, de documento ou de outro uso. Nenhum desses usos está declarado nesta porta, e esta nota não escolhe um.

Também não está declarado se a foto fica restrita à pessoa logada. Buscar e apagar pedem o identificador da foto. Não dá para afirmar, só com esta leitura, se outra pessoa logada que conheça esse identificador obteria ou apagaria a mesma foto.

Ver [[beautiful-api]].
