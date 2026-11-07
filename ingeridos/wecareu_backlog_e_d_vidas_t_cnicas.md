> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um *snapshot* do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Backlog, Brainstorming e Dívidas Técnicas

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Mapear funcionalidades futuras em fase de *discovery*, soluções de pagamento em análise e registrar os débitos técnicos que precisam de resolução arquitetural.

## 1. Backlog de Produto e Brainstorming (Iterações Futuras)

As funcionalidades abaixo estão mapeadas para o roadmap pós-MVP. Qualquer implementação destas áreas deve passar obrigatoriamente pelo fluxo SDD v3.

* **Segurança e Identidade:**
  * Validação de usuários via upload de documentos de identificação (KYC).
  * Verificação de autenticidade do Artista através de prova de vida (fotos/vídeos com ou sem documentos).
  * Autenticação em Duas Etapas (2FA/MFA) nos aplicativos.

* **Gestão Operacional e Agendamentos:**
  * Parametrização obrigatória do tempo médio de cada serviço pelo Artista, vital para alimentar o algoritmo do "Atendimento Imediato".
  * Trava de segurança: Limite de agendamentos pessoais (externos) consecutivos para impedir que o sistema seja usado como uma mera agenda offline não rentabilizável.
  * Checklist de conformidade obrigatório antes do fechamento de caixa/implantação nas empresas (`ui-business`).

* **Check-in e Geolocalização de Atendimento:**
  * Sistema de Check-in obrigatório pelo Artista no momento em que chega ao cliente.
  * Validação cruzada: Geração de senha aleatória descartável no app do Cliente para o Artista digitar e confirmar o início do serviço.
  * Captura do GPS do Cliente durante a busca, emitindo um *warning* (aviso não-bloqueante) caso o endereço do agendamento divirja da posição atual (permitindo pedidos para terceiros ou locais de trabalho).

* **Avaliações e Integrações (UX):**
  * Não haverá sistema de chat interno (Decisão de Produto).
  * Sincronização automatizada com o Instagram para exibir fotos no portfólio baseadas na hashtag `#wecareu`.
  * Motor de Avaliações: Prioridade de ranqueamento visual para reviews com fotos/vídeos. A interface inicial limitará a exibição às 3 principais avaliações com *expand* ("ver mais").
  * Filtro de busca baseado na nota de estrelas (Planejado para v2).
  * Mapas de calor (Heatmaps) e gravação de sessão para otimização de conversão.
  * Rastreabilidade analítica via Deep Links em Notificações Push para medir retenção.

* **IA On-Device e Expansão B2B:**
  * Privacidade: Filtro e *blur* (desfoque) automático no rosto de clientes em fotos de portfólio rodando nativamente no dispositivo.
  * Produtividade: Uso de *Speech-to-Text* para o Artista ditar o preenchimento de fichas de anamnese.
  * E-commerce P2P: Habilitação para que o Artista realize a venda direta de produtos físicos dentro de seu perfil no app.

## 2. Gateways de Pagamento (Análise de Viabilidade)

A arquitetura transacional exige obrigatoriamente um Gateway com **Checkout Transparente**. A lista de homologação atual inclui:

* BrasPag
* MundiPag
* PagSeguro
* PicPay
* Ebankx
* Paypal
* Pay2me
* AArin
* PayMee
* **Erede:** Atualmente liderando a avaliação técnica devido ao suporte nativo ao protocolo 3DS (Autenticação Forte do Cliente), mitigando riscos de *chargeback*.

## 3. Dívidas Técnicas e Correções de Rota (Technical Debt)

Estes itens representam erros de trajetória ou melhorias de infraestrutura que devem ser resolvidos pelas equipes de engenharia.

* **Correção Crítica: Arquitetura de Qualidade (Jest vs Maestro):**
  * *Histórico do Erro:* Houve uma discussão anterior que sugeria a substituição completa dos testes unitários (Jest) por testes visuais automatizados (Maestro).
  * *Resolução Arquitetural:* Isso é uma falha de engenharia e economicamente inviável (custo excessivo em CI/CD). O **Jest** permanece como ferramenta primária e obrigatória para validação de lógica de negócio, regras de formulários e hooks. O **Maestro** (via MCP) atua *apenas* na ponta da pirâmide (E2E), validando os fluxos críticos de jornada do usuário nos emuladores.

* **Integração Contínua Visual (CI/CD):**
  * Migrar a dependência de validação visual manual através do *Storybook local* para o **Chromatic**.
  * Objetivo: Estabelecer testes de regressão visual autônomos na esteira de *Pull Requests*, validando os componentes da `library-design-system` de forma automatizada antes do merge na `develop`.