> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 02 · Contexto da empresa WeCareU

Tags: #wecareu #empresa #missao #modelo-de-negocio #lgpd

---

## 1. Status

- **WeCareU:** a empresa e o produto, em operação (MVP). Este documento descreve o negócio e o produto como a empresa os define. Documento de origem válido em **maio de 2026**, com revisão recomendada ao iniciar o desenvolvimento das funcionalidades de salão de beleza.
- **LyraUI:** o design system da WeCareU. Está em **discovery, não implementada no código**, sendo construída em paralelo ao MVP e prevista como versão futura do app. Ela não é a empresa nem o produto. Ver [[01-visao-geral-lyraui]].
- O que existe e o que não existe no produto hoje está em [[03-estado-atual-do-produto]]. Este arquivo mistura o que a empresa **faz** com o que **pretende** fazer. Ao divergir, vale o estado atual.

---

## 2. Missão e visão

| | Texto |
|---|---|
| **Missão** | Proporcionar uma plataforma que conecta clientes a profissionais da beleza, dignificando o trabalho desses Artistas e reconhecendo seu talento como uma forma de arte |
| **Visão** | Ser a plataforma de referência no Brasil que celebra o talento artístico dos profissionais da beleza, destacando sua importância e proporcionando visibilidade e reconhecimento a esses verdadeiros artistas |

Esses valores sustentam os pilares da comunicação da LyraUI: o profissional como artista, estética, cuidado (care), eficiência e simplicidade. Ver [[10-voz-e-tons]].

---

## 3. Proposta de valor

| Para quem | Proposta |
|---|---|
| **Cliente** | Agilidade e comodidade para contratar profissionais de beleza |
| **Artista** | Plataforma que valoriza e dignifica o trabalho, com visibilidade proporcional ao talento e à dedicação |

**Posicionamento:** não é apenas uma plataforma de agendamento. É uma **comunidade que reconhece o trabalho artístico** dos profissionais.

---

## 4. Modelo de negócio

- A plataforma pode ser usada de forma **100% gratuita** por Artistas e clientes.
- Artistas com **plano premium** aparecem no **topo do ranking de busca**.
- Artistas sem premium aparecem **abaixo** na listagem, mas continuam visíveis e contratáveis.
- O premium é posicionado como **investimento em visibilidade e reconhecimento**, não apenas como acesso a funcionalidades.

Implicação para o design e para a escrita: a comunicação do plano premium (tela `Plans` do WORKER) deve seguir esse posicionamento. Ver [[10-voz-e-tons]].

---

## 5. Como o app funciona (fluxo principal)

1. O cliente acessa o app e busca profissionais de beleza.
2. A plataforma funciona como **intermediária**: o cliente **nunca** se comunica diretamente com o Artista.
3. Toda a comunicação acontece pela plataforma (visão-alvo: chat interno com bot e agentes).
4. O Artista **se desloca até o cliente** para realizar o serviço (*home service*).
5. **Futuro:** suporte a salões de beleza, em que o cliente vai até o local.

> **Divergência a validar.** Este documento descreve o chat interno com bot e agentes como parte do fluxo. O documento de estado atual diz que **hoje** o suporte é feito exclusivamente por e-mail e que o bot é objetivo futuro, sem prazo. Tratar o chat como **alvo**. O catálogo, porém, lista a tela `ChatSchedules` nos dois apps. Confirmar o que essa tela faz hoje. Ver [[03-estado-atual-do-produto]] e [[06-catalogo-e-inventario-legado]].

---

## 6. Dados coletados das pessoas usuárias

| Categoria | Itens |
|---|---|
| Identificação | Nome, e-mail, telefone e outros dados pessoais |
| Uso | Histórico de agendamentos e serviços contratados |
| Localização | Geolocalização durante o uso, para viabilizar o deslocamento do Artista |
| Dispositivo | Modelo, sistema operacional e identificadores únicos |
| Pagamento | Dados via gateway externo (cartão **não** armazenado localmente) |

Campos do cadastro em detalhe: ver [[03-estado-atual-do-produto]].

---

## 7. Pagamentos

- Processados por **gateway externo**: Stripe e/ou MercadoPago.
- **Pendente:** confirmar qual gateway está ativo hoje. A informação é responsabilidade do time de back-end e financeiro.

---

## 8. Conformidade

- Operação em conformidade com a **LGPD (Lei nº 13.709/2018)**.
- Textos jurídicos, termos de uso, políticas de privacidade e modais de consentimento seguem pontuação tradicional (com ponto final) por exigência de segurança legal. Ver [[11-escrita-e-ortografia]].

---

## 9. Funcionalidades futuras mapeadas

| Funcionalidade | Observação |
|---|---|
| Suporte a salões de beleza | O cliente se desloca até o local. Terceiro perfil, fora do escopo atual |
| Parcerias com anunciantes de produtos de beleza | **Ainda sem parcerias ativas** |

A lista completa, com status de cada item, está em [[03-estado-atual-do-produto]].

---

## 10. Terminologia interna

| Termo | Significado |
|---|---|
| **Artista** | Profissional de beleza cadastrado na plataforma |
| **CLIENT** | App mobile do cliente final |
| **WORKER** | App mobile do Artista (prestador de serviço) |

Outros termos em [[13-glossario]].

---

## 11. WeCareU x LyraUI: resumo de uso

| Pergunta | Resposta |
|---|---|
| "WeCareU" quer dizer... | A empresa, o produto, os apps CLIENT e WORKER em uso |
| "LyraUI" quer dizer... | O design system futuro, em discovery, que atenderá os apps da WeCareU |
| Quem define o negócio? | WeCareU |
| Quem define a linguagem visual e de escrita? | LyraUI, em nome da WeCareU |

---

## 12. Pontos em aberto

- Gateway de pagamento ativo.
- Papel atual da tela `ChatSchedules` frente à ausência de chat.
- Data de início das funcionalidades de salão, que dispara a revisão deste contexto.
- Perfil Empresas: aparece no guia de voz como plataforma, mas ainda não existe no produto.

---

## Links

Anterior: [[01-visao-geral-lyraui]] · Próximo: [[03-estado-atual-do-produto]]
