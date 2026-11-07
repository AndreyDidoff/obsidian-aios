> **Aviso de Versionamento (Extração via IA - Gemini):** Este documento foi gerado a partir da consolidação do histórico e representa um *snapshot* do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# WeCareU: SSoT de Design System e Redação de Interface (LyraUI)

**Data de Atualização:** 20 de Outubro de 2026
**Objetivo do Documento:** Atuar como Single Source of Truth (SSoT) para a conceituação, o status de desenvolvimento e as diretrizes de Voz e Tom da LyraUI, o futuro Design System do ecossistema WeCareU.

## 1. Definição Arquitetural: LyraUI vs. WeCareU

Para garantir o alinhamento de todos os colaboradores, é imperativo separar o produto final da infraestrutura interna:

*   **WeCareU (O Produto):** É a plataforma bilateral voltada para o mercado (composta pelos apps `ui-client`, `ui-worker`, `ui-business` e suas contrapartes web). É o que o cliente final e o prestador de serviço ("Artista") acessam.
*   **LyraUI (A Ferramenta Interna):** É o nome oficial do futuro Design System e biblioteca de componentes da empresa. **A LyraUI não é um produto voltado ao cliente.** Ela é uma infraestrutura estrita e exclusiva para o uso interno dos times de Design, Produto e Engenharia da WeCareU.

## 2. Status Atual (Fase de Discovery)

**Atenção:** A LyraUI encontra-se, no momento, estritamente em **fase de Discovery**. 

*   **Paralelismo:** O planejamento da LyraUI corre em uma esteira paralela ao desenvolvimento atual dos aplicativos.
*   **Código:** Até o presente momento, **nenhuma linha de código** foi escrita ou refatorada oficialmente sob o escopo ou nomenclatura da LyraUI. 
*   **Transição Futura:** Atualmente, os apps utilizam componentes locais e pacotes utilitários iniciais (`library-design-system`). No futuro, quando a fase de Discovery e documentação (via ZeroHeight) for concluída, a LyraUI absorverá, padronizará e substituirá essas bibliotecas, tornando-se a Única Fonte da Verdade (SSoT) visual e de componentes em código de todo o ecossistema.

## 3. Guia de Voz e Tom (A Fundação Textual)

Enquanto os componentes visuais estão em planejamento, a **Redação de Interface (UI Copy)** já possui diretrizes estabelecidas que a LyraUI fornecerá para os apps. Toda palavra exibida nos aplicativos deve respeitar os pilares: *O profissional como artista, estética, cuidado (care), eficiência e simplicidade.*

### A Voz (Nossa Personalidade Imutável)
A voz da LyraUI é sempre especialista, elegante, polida e acolhedora.
*   **Focada em estética:** Valoriza o polimento visual e o respeito à arte nos textos (ex: usa-se "Portfólio" em vez de "Fotos de trabalho").
*   **Acolhedora (Care):** O sistema prevê o erro humano e ajuda a corrigi-lo. **Nunca culpa o usuário.** (ex: "Preencha o campo de e-mail" em vez de "Erro do usuário: E-mail não inserido").
*   **Dignifica o profissional:** Trata cada prestador de serviço como um talento único e indispensável.

### Os Tons (Nosso Contexto Variável)
O tom muda conforme o estado do componente e a ansiedade do usuário. O jeito que a interface comemora um agendamento confirmado (Tom Celebrativo) é diferente da forma como avisa sobre uma falha de rede (Tom Tranquilizador/Instrutivo).

### Regra da Perspectiva (1ª Pessoa)
*   **Nós somos o ambiente:** A interface assume a responsabilidade em interações de feedback.
*   ✅ **Correto:** "Encontramos 5 Artistas perto de você." ou "Preparamos a sua agenda de hoje."
*   ❌ **Incorreto:** "A WeCareU encontrou 5 artistas." (Evitar referir-se à marca na 3ª pessoa).

## 4. Perfis de Audiência na Redação

A LyraUI orientará os textos dos componentes dependendo de qual aplicativo os consumirá:

1.  **Clientes (`ui-client` / `web-client`):** A comunicação foca em confiança, facilidade e segurança na hora da escolha e do agendamento de serviços de beleza e bem-estar.
2.  **Artistas (`ui-worker` / `web-worker`):** A interface é a ferramenta de trabalho (o "ganha-pão"). O texto deve ser direto, focado em produtividade e dignificar a profissão como arte.
3.  **Empresas (`ui-business` / `web-business`):** Foco em gestão, dados analíticos e controle operacional de forma objetiva.
4.  **Equipe Interna (`web-admin` / `web-wiki`):** O texto abdica de qualquer tom comercial. Foca 100% no rigor técnico, moderação e clareza de processos do sistema.

## 5. Regras Práticas de UI Copy

*   **Verbos de Ação Fortes:** Botões e chamadas para ação (CTAs) devem ser literais e eficientes. Use "Confirmar agendamento" em vez de "Clique aqui para realizar a confirmação".
*   **Pontuação (O Uso do Ponto Final):** 
    *   **Proibido na Interface (UI):** Não se usa ponto final em rótulos de botões, títulos, itens de lista curtos, *tooltips* ou *Toasts* rápidos.
    *   **Obrigatório em Textos Longos:** O uso do ponto final é exigido apenas em parágrafos de tutoriais, Central de Ajuda, Termos de Uso (LGPD), e-mails transacionais e comunicados de atualização extensos.
*   **Formatação Visual:** É expressamente proibido combinar negrito e itálico na mesma frase para evitar poluição visual.