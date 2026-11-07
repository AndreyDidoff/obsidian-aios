> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um _snapshot_ do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Produto, Negócios e Estratégia

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Atuar como Single Source of Truth (SSoT) para regras de negócio, modelo de monetização e estratégia de Go-To-Market do ecossistema WeCareU.

## 1. Visão Executiva e Proposta de Valor

A WeCareU é uma plataforma bilateral digital focada nos nichos de beleza (cabelos, unhas, pelos, maquiagem, estética) e bem-estar (massagem, massoterapia, spa).

* **Diferencial de Posicionamento:** O eixo central de marketing é a elevação do prestador de serviço ao status de **"Artista"**. O produto visa dignificar o trabalho manual, tratando-o como uma forma de arte e proporcionando visibilidade baseada em mérito e avaliações reais.

* **Proposta para o Cliente (B2C):** Confiança, comodidade, estética e segurança no agendamento, com foco na descoberta ágil de profissionais bem ranqueados.

* **Proposta para o Artista (B2B/Autônomo):** Uma ferramenta completa de produtividade diária (agenda, portfólio, métricas) aliada a uma vitrine de atração, sem a cobrança de taxas sobre o suor do seu trabalho.

## 2. O Ecossistema de Produto (Mapeamento de Ambientes)

O modelo de negócios é sustentado por uma arquitetura multiplataforma, segmentada por perfis de usuário para garantir a separação de responsabilidades (Separation of Concerns):

* **Ambiente do Cliente:**

  * `ui-client`: Aplicativo mobile nativo (iOS/Android).

  * `web-client`: Aplicação web (cliente.wecareu.app).

* **Ambiente do Artista:**

  * `ui-worker`: Aplicativo mobile nativo (Ferramenta de produtividade principal).

  * `web-worker`: Aplicação web (artista.wecareu.app).

* **Ambiente de Locais (Salões/Empresas):**

  * `ui-business`: Aplicativo mobile nativo.

  * `web-business`: Aplicação web para gestão operacional e analítica (empresa.wecareu.app).

* **Ambiente Interno (WeCareU):**

  * `web-admin`: Painel de controle de acessos, moderação, banimentos e feature flags (admin.wecareu.app).

  * `web-wiki`: Base de conhecimento para guias de estilo e processos (wiki.wecareu.app).

## 3. Motor de Monetização (Zero Commission Model)

A WeCareU opera sob o modelo de **Zero Comissão** sobre os serviços prestados. A escalabilidade financeira provém de três fontes principais (Upsell e B2B2C):

1. **Planos Premium (Artistas/Locais):** Assinaturas que oferecem algoritmos de destaque no ranking orgânico e liberam funcionalidades críticas, como a ativação do modo "Atendimento Imediato" (para preenchimento de buracos na agenda).

2. **Microtransações (Pontos Avulsos):** Venda de pacotes de pontos (em lotes de 100) para desempate no ranqueamento regional. Estratégia restrita: Apenas usuários já assinantes do Plano Premium podem adquirir pontos avulsos.

3. **Publicidade B2B (Marcas Parceiras):** O alvo de longo prazo. Monetização de espaços na plataforma para marcas de cosméticos (Natura, Avon, O Boticário, L'Oréal), vendendo:

   * Filtros patrocinados no motor de busca (ex: "Especialistas Natura").

   * Banners nativos injetados no feed de ranqueamento.

   * Missões/competições patrocinadas.

## 4. Estratégia de Go-To-Market e MVP (Shadow Testing)

Devido ao modelo B2B2C, a plataforma enfrenta o problema do "ovo ou a galinha". Para prospectar marcas B2B de forma baseada em dados sem parcerias ativas no dia zero, o MVP adotará a estratégia de **Shadow Testing (Coleta Silenciosa)**:

* **Mapeamento de Oferta (Inventário Espontâneo):** Durante o onboarding do `ui-worker`, o Artista declara espontaneamente quais marcas utiliza. Isso cria o banco de dados de uso geolocalizado.

* **Mapeamento de Demanda (Filtros Sombra):** O `ui-client` oferecerá filtros orgânicos como "Produtos Veganos", "Hipoalergênicos" ou tags de marcas específicas ("Usa Truss"). O Analytics rastreará essas interações para provar a intenção de consumo.

* **Métrica de Validação Pós-Serviço:** O checkout do cliente incluirá a pergunta: "Gostou dos produtos utilizados hoje?", gerando NPS de produtos para compor o *Pitch Deck* de vendas B2B.

* **Validação de CTR Nativo:** Banners institucionais (ex: "Indique um amigo e ganhe pontos") ocuparão o espaço dos futuros anúncios para medir a Taxa de Clique (CTR) e precificar o inventário de mídia.

* **Expansão Controlada:** O lançamento será focado em uma única cidade/região para validar a densidade de mercado e a carga na infraestrutura técnica antes da escala nacional.

## 5. Gamificação, Retenção e Experiência do Usuário

O aplicativo deve atuar como uma ferramenta de retenção orgânica constante, reduzindo o *churn* e o custo de aquisição de clientes (CAC).

* **Tags de Endosso Ágil:** Substituição de avaliações longas e obrigatórias por "Tags de Endosso" em 1 clique durante o checkout (ex: "Mão leve", "Pontual"), gerando *badges* no perfil do Artista.

* **Consentimento de Imagem (1-Click LGPD):** Funcionalidade jurídica nativa no fluxo de finalização do serviço, permitindo que o cliente autorize o uso de fotos do "Antes e Depois" para o portfólio do Artista via app.

* **Agenda Inteligente (Buffer Obrigatório):** O sistema de agendamento impõe automaticamente um tempo de buffer entre serviços e limita a capacidade para evitar overbooking e garantir a qualidade (cuidado/care).

## 6. Backlog Estratégico (Roadmap Mapeado)

Itens de negócio documentados para iterações pós-MVP:

* Integração social: Sincronismo nativo com Instagram buscando fotos com a hashtag `#wecareu`.

* Check-in auditado: Geração de senha aleatória no aplicativo do Cliente para que o Artista realize o check-in presencial no `ui-worker`.

* Gateways de pagamento transparentes: Avaliação contínua (ênfase na Erede devido ao protocolo 3DS).

* Mapas de calor de conversão e rastreamento de links profundos (Deep Linking) de notificações Push.

* E-commerce P2P: Opção para o Artista revender produtos físicos diretamente pelo seu perfil na plataforma.