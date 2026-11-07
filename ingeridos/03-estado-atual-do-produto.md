> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 03 · Estado atual do produto WeCareU

Tags: #wecareu #produto #mvp #funcionalidades #roadmap

---

## 1. Status e como ler

- **WeCareU (produto):** este documento descreve o app **em produção** (MVP) e o que está planejado. Documento de origem gerado em **maio de 2026**, a partir de brainstorming interno e confirmações do Tech Lead.
- **LyraUI (design system):** **não faz parte do que existe hoje.** Está em discovery, não implementada no código, construída em paralelo ao MVP e prevista como versão futura. Ver [[01-visao-geral-lyraui]].
- **Convenção de leitura da fonte:** "existe hoje" significa **implementado e em produção**. Qualquer outra marcação é futuro.

Legenda usada neste arquivo:

| Marca | Significado |
|---|---|
| ✅ Existe hoje | Implementado e em produção |
| 🔜 Na esteira | Priorizado, em fila de desenvolvimento |
| 🕓 Planejado, sem prazo | Há intenção, sem data |
| ❌ Sem previsão | Não existe e não há plano com data |

---

## 2. Autenticação e sessão

| Item | Estado |
|---|---|
| Autenticação via **JWT**, stateless, sem cookies de sessão | ✅ |
| Token via Axios com Bearer token no header `Authorization` | ✅ |
| Headers fixos em todas as requisições | ✅ |
| **2FA** para todos os usuários (clientes e Artistas) | ✅ |
| Controle de sessão por dispositivo (feito no back-end) | ✅ |

Regras do controle de sessão:

| Cenário | Permitido? |
|---|---|
| Mesma conta no app CLIENT e no app WORKER, em dispositivos diferentes | Sim |
| Mesma conta no app CLIENT e no app WORKER, no mesmo dispositivo | Sim |
| Mesma conta em dois dispositivos diferentes **no mesmo app** | **Não** |

### Conta global entre apps

- A conta é **global**: a mesma conta serve ao app CLIENT e ao app WORKER.
- Os apps são distintos, mas compartilham o sistema de autenticação e a base de usuários.

---

## 3. Cadastro de usuário

Campos coletados hoje, válidos para clientes e Artistas:

- Nome, apelido, nome social.
- CPF, data de nascimento, sexo, gênero, orientação sexual.
- E-mail, senha.
- Descrição.
- Endereços (múltiplos): ID, nome, rua, complemento, ponto de referência, latitude e longitude.

> **Atenção para o design e a escrita.** O cadastro coleta dados pessoais sensíveis (como orientação sexual) e localização. Os textos de consentimento seguem a regra jurídica de [[11-escrita-e-ortografia]] e a conformidade LGPD de [[02-contexto-wecareu]].

---

## 4. Pesquisa e listagem de Artistas

| Item | Estado |
|---|---|
| Listagem com lógica de **range geográfico** | ✅ |
| Cidades grandes: range por bairros e adjacências (cerca de 10 km) | ✅ |
| Cidades pequenas: range expandido para cidades próximas | ✅ |
| Pesquisa combinando múltiplos filtros (ex.: unhas + pé traz só Artistas que atendem ambos) | ✅ |
| Filtro por especialidade: soma filtros e traz Artistas que atendem **todos** os selecionados | ✅ |
| Ordenação por regras internas, filtros e planos (**não** por proximidade) | ✅ |
| Artistas que atendem **parcialmente** os filtros | ❌ Não traz |
| Aviso ao cliente quando a lista tem menos de 10 Artistas, sugerindo limitar filtros | ❌ Sem previsão |
| Captura de localização atual com aviso de divergência de endereço | ❌ Sem previsão |

Os detalhes da ordenação estão em um documento próprio de listagem e ranking, que não faz parte desta extração. Relação com o plano premium em [[02-contexto-wecareu]].

---

## 5. Sistema de agendamento

| Item | Estado |
|---|---|
| Agendamento feito **por telas, sem bot** | ✅ |
| **Check-in e Check-out** do Artista | ✅ |
| Endereço do cliente liberado ao Artista **assim que o agendamento é confirmado** | ✅ (hoje) |
| Endereço liberado apenas **24h antes** do horário marcado, por segurança | 🔜 **Crítico** |
| Senha aleatória no Check-in | 🔜 |
| Filtro por dias específicos (ex.: os 3 próximos sábados) | 🔜 |
| Integração com agendas externas (Google Agenda, Apple Calendar) | ❌ Sem previsão |
| Bot de atendimento para agendamento | 🕓 Mudança grande, sem prazo |

> **Ponto de atenção.** Hoje o endereço do cliente fica disponível ao Artista assim que o agendamento é confirmado. A regra de liberar só 24h antes está marcada como **crítica**, por segurança. Qualquer tela ou texto que mostre endereço deve prever essa mudança.

---

## 6. Tempo de atendimento

- ✅ Exibição do tempo médio de atendimento **por serviço**.
- O tempo se baseia no **valor configurado pelo próprio Artista** nas configurações da conta.
- ❌ Não existe análise em tempo real do tempo médio a partir de histórico.

---

## 7. Sistema de avaliações (reviews)

| Item | Estado |
|---|---|
| Avaliação por **estrelas** | ✅ |
| Review por escrito | 🕓 Planejado, sem prazo |
| Fotos no review | 🕓 Planejado, sem prazo |
| Filtro de reviews por estrelas | ❌ Sem previsão |

Regras atuais:

- A avaliação **não é obrigatória**. O app solicita ao cliente **até 3 vezes** após o atendimento.
- Prazo para avaliar: **até 15 dias** após o atendimento, pela aba de atendimentos.
- Se o atendimento **não for avaliado em 1 semana**, o sistema registra internamente **5 estrelas**. Esse valor **não é exibido ao cliente**.

---

## 8. Segurança e validação de Artistas

| Item | Estado |
|---|---|
| Controle de sessão por dispositivo | ✅ |
| Upload de documentos para validação do Artista | 🔜 |
| Validação por foto ou vídeo | 🔜 |
| Captura de localização do cliente com aviso de divergência de endereço | ❌ Sem previsão |

---

## 9. Suporte e comunicação

- ✅ Suporte ao cliente **exclusivamente por e-mail** hoje.
- ❌ Não existe comunicação direta entre cliente e Artista. Toda interação passa pela plataforma.
- 🕓 Futuro: chat interno via bot e agentes humanos. Bot de atendimento é objetivo futuro, sem prazo.

> **Divergência a validar.** O catálogo de telas lista `ChatSchedules` nos apps CLIENT e WORKER. Confirmar o que essa tela entrega hoje, já que não há chat. Ver [[06-catalogo-e-inventario-legado]].

---

## 10. Funcionalidades futuras (fora do escopo atual)

| Funcionalidade | Status |
|---|---|
| Upload de documentos para validação do Artista | 🔜 Na esteira |
| Validação por foto ou vídeo | 🔜 Na esteira |
| Senha aleatória no Check-in | 🔜 Na esteira |
| Endereço liberado 24h antes do atendimento | 🔜 Na esteira, **crítico** |
| Filtro por dias específicos | 🔜 Na esteira |
| Bot de atendimento para agendamento | 🕓 Planejado, sem prazo |
| Review por escrito e com fotos | 🕓 Planejado, sem prazo |
| Aviso de lista reduzida na pesquisa | ❌ Sem previsão |
| Captura de localização com aviso de divergência | ❌ Sem previsão |
| Integração com agendas externas | ❌ Sem previsão |
| Filtro de reviews por estrelas | ❌ Sem previsão |
| Salões de beleza (terceiro perfil) | Futuro, fora do escopo atual |

---

## 11. Conexões com a LyraUI

Leitura de apoio, derivada das fontes. Não é uma definição oficial.

- Telas novas previstas no padrão do Figma (`[NEW] SecurityCenter`, `[NEW] ReviewScreen`) se conectam a itens desta lista: validação de Artistas e reviews. Ver [[07-figma-padroes-e-tokens]].
- Funcionalidades marcadas como futuras **não devem** aparecer em componentes, textos ou telas como se existissem. Isso vale para exemplos na documentação.
- Tom dos textos de erro e de espera deve considerar que o suporte é só por e-mail. Ver [[10-voz-e-tons]].

---

## 12. Pontos em aberto

- Papel atual da tela `ChatSchedules`.
- Prazo do endereço liberado 24h antes (item crítico).
- Detalhes de ordenação e ranking (documento fora desta extração).
- Gateway de pagamento ativo: ver [[02-contexto-wecareu]].

---

## Links

Anterior: [[02-contexto-wecareu]] · Próximo: [[06-catalogo-e-inventario-legado]]
