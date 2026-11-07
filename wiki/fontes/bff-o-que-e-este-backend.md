---
tipo: fonte
arquivo: "ingeridos/01-o-que-e-este-backend.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["O que é este backend"]
---

# O que é este backend

Porta desta leva. Retrato de 21/10 do repositório `service_api`, o backend de apoio ao aplicativo. O nome interno é Beautiful. No catálogo de rotas, o título é "We Care U Service". Os pedidos entram pelo prefixo `beautiful/api/`.

Foto desse repositório. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

Não desenha tela. Encaminha o pedido aos serviços da empresa. A regra de negócio mora nesses serviços.

Está amarrado a uma empresa e a um aplicativo. Esse vínculo sobe com o backend, no dado interno CompanyData. Os identificadores ficam na configuração e não entram nesta nota.

Há um banco local declarado no arranque. Ele não mapeia informação de negócio. Comentários antigos de atualização para idiomas, bloqueio, auditoria, usuário de sistema e redefinição de senha estão desligados. Esses dados não moram aqui.

## Papéis no cadastro

Dois papéis: cliente (User) e profissional (Artist). O profissional recebe, neste backend, a empresa e o aplicativo. O detalhe está em [[bff-cliente-e-profissional]].

Entrar, o fluxo de senha e o cadastro não declaram sessão. O passo está em [[bff-entrar-sair-e-senha]] e [[bff-cadastro]]. Sair, conferir a sessão, bloqueio, endereços, telefones, fotos, relatos, documentos de validação, permissões, grupos e planos declaram sessão. Fora do cadastro, as portas tratam a pessoa da sessão e não escolhem o caminho pelo papel.

## Em que pé está

| Pé | O que significa aqui | O que esta nota nomeia |
|---|---|---|
| No ar | A porta existe e o serviço por trás está ligado no arranque | entrar e sair, senha, cadastro, serviços, bloqueio, endereços, telefones, fotos, relatos, documentos de validação, permissões e grupos |
| Porta sem ligação | A porta existe e o serviço não está registrado no arranque | planos e cupons. A porta exige sessão. A lista de endereços dos serviços não nomeia planos |
| Só preparado | O backend conhece o serviço e não oferece a ação ao aplicativo | auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem, e o cliente de e-mail |
| Fora de uso | Há código de porta, desligado da compilação | o canal de e-mail |

O cliente de e-mail está ligado no arranque, sem ação para o aplicativo: fica em só preparado. O canal de e-mail tem código de porta, vazio, desligado da compilação. O construtor pede dois identificadores soltos, incompatíveis com CompanyData. O detalhe está em [[bff-preparado-e-ainda-nao-oferecido]].

O banco local fica fora dessa escala de porta. Sobe com o backend e não guarda o negócio.

Entrar, sair, senha e cadastro estão em [[bff-entrar-sair-e-senha]] e [[bff-cadastro]]. Serviços, bloqueio, endereços e telefones estão em [[bff-servicos]], [[bff-bloqueio]], [[bff-enderecos]] e [[bff-telefones]]. Planos e cupons, porta sem ligação, estão em [[bff-planos-e-cupons]]. Fotos, relatos, documentos de validação e permissões e grupos estão em [[bff-fotos]], [[bff-relatos]], [[bff-documentos-para-validacao]] e [[bff-o-que-a-pessoa-pode-ver]].

## O que esta nota não cobre

Telas, senha, chave de sessão, identificadores da empresa e do aplicativo, e endereço dos serviços. Os campos de cadastro, plano, endereço, telefone, foto, relato e documento moram em pacotes fora deste repositório.

## Incertezas

O arranque prepara a sessão. A leitura da sessão não entra no caminho do pedido. As portas que declaram sessão podem receber o pedido sem a pessoa preenchida. Fica em aberto até o comportamento em execução ou uma decisão da empresa. Ver [[contradicoes-e-lacunas]].

Várias portas recebem um cliente de auditoria e um cliente de autenticação e não os chamam. A ação oferecida de sessão é entrar, sair e conferir a sessão, pelo serviço de login.

A configuração nomeia um serviço de registro de falhas. O arranque não liga esse cliente. O canal de e-mail fora de uso ainda o pede.

Ver [[beautiful-api]].
