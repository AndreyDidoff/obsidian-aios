> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um *snapshot* do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Termos Legais, LGPD e Segurança

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Atuar como Single Source of Truth (SSoT) para as políticas legais, conformidade com a Lei Geral de Proteção de Dados (LGPD) e diretrizes de segurança da informação e anti-fraude do ecossistema WeCareU.

## 1. Termos de Uso e Natureza do Serviço

A WeCareU opera sob um modelo jurídico rigoroso de intermediação tecnológica.

* **Isenção de Responsabilidade Técnica:** A plataforma atua exclusivamente como conectora entre Clientes e "Artistas" (ou Locais de Beleza). A WeCareU não se responsabiliza pela qualidade, execução ou eventuais danos decorrentes dos serviços físicos prestados.
* **Modelo Zero Comissão:** Os Termos de Uso devem deixar explícito que não há cobrança de taxas de corretagem sobre o serviço prestado. A relação financeira ocorre via Planos Premium e Pontos Avulsos.
* **Idade Mínima:** O uso é restrito a maiores de 18 anos, exigindo autorização expressa de responsáveis legais para menores (aplicável especialmente a clientes finais).
* **Suspensão de Contas:** A WeCareU reserva-se o direito de suspensão unilateral e sem aviso prévio de usuários que violem diretrizes morais, legais ou o código de conduta da plataforma.

## 2. Conformidade com a LGPD (Lei nº 13.709/2018)

O tratamento de dados sensíveis exige conformidade arquitetural desde a base de código (*Privacy by Design*).

* **Coleta Estrita:** O sistema coleta apenas o necessário: Identificação, Agendamento, Localização, Dispositivo e Dados de Pagamento (tokenizados).
* **Consentimento de Imagem (1-Click LGPD):** Funcionalidade jurídica nativa no fluxo de checkout. Permite que o cliente autorize, com um único clique, o uso de fotos do serviço ("Antes e Depois") no portfólio público do Artista. Isso resolve o passivo jurídico do autônomo sem atrito na interface.
* **Anonimização e Criptografia:** Dados sensíveis devem ser criptografados em trânsito (HTTPS/SSL) e em repouso. O tráfego de dados de pagamento não passa descriptografado pelos nossos servidores (uso de gateways).
* **Geolocalização Transparente:** O compartilhamento de localização em tempo real ocorre **apenas** entre as partes envolvidas (Cliente e Artista) e **apenas** durante a janela de tempo do serviço agendado.

## 3. Segurança de Dados e Infraestrutura

As regras de segurança devem ser validadas tanto na infraestrutura quanto na esteira de CI/CD.

* **Testes Automatizados (Quality Gates):** A pipeline de automação (Jest + Maestro) possui a obrigação de validar a existência de máscaras de dados sensíveis na interface e confirmar que os fluxos de solicitação de permissões (GPS, Câmera, Galeria) estão operando corretamente antes de qualquer deploy.
* **Gateways de Pagamento Seguros:** A arquitetura financeira exige parceiros que cumpram o protocolo 3DS (ex: Erede) para prevenção de chargebacks e fraudes transacionais. A WeCareU não armazena dados completos de cartão de crédito no banco de dados.
* **Segurança de API e MFA:** A `service_api` (.NET) deve proteger rotas sensíveis via OAuth 2.0 / JWT. Ambientes administrativos (`web-admin`) exigem Autenticação Multi-Fator (MFA/2FA) para acesso da equipe interna.

## 4. Moderação e Estratégia Anti-Fraude (Shadowban)

Para manter a integridade do ecossistema e evitar engenharia reversa por parte de usuários mal-intencionados, adotamos estratégias ativas de mitigação técnica:

* **Shadowban (Mentir para o Mentiroso):** Em casos de detecção de fraude, tentativas de scraping ou violações graves, o sistema não deve alertar o infrator com um erro claro de "Conta Banida". Em vez disso, aplica-se o Shadowban: o usuário acredita que sua ação foi concluída com sucesso (ex: "Dados enviados"), mas no backend a requisição é isolada e descartada (Sinkhole). Isso atrasa a adaptação do golpista.
* **Validação de Dispositivo (Device Fingerprinting):** Mapeamento de identificadores de hardware para cruzar contas. Se múltiplos perfis de "Artistas" acessarem simultaneamente do mesmo dispositivo (sem pertencerem a um `web-business` corporativo), o sistema sinaliza a anomalia para revisão manual no `web-admin`.