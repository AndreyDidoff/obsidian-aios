---
tipo: fonte
arquivo: "ingeridos/14-preparado-e-ainda-nao-oferecido.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório service_api (Beautiful.API); o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Preparado e ainda não oferecido"]
---

# Preparado e ainda não oferecido

Parte do que este backend já conhece ainda não chega ao aplicativo como ação. O banco local sobe junto e não é o lugar onde o negócio mora. Porta desta leva: [[bff-o-que-e-este-backend]]. Foto de 21/10 do repositório `service_api`. O alvo continua o [[mvp]]. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

O arranque já conhece auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem e e-mail. Não há porta para pedir essas ações.

O canal de e-mail tem um arquivo de porta. Ele está vazio e fora da compilação. O construtor pede dois identificadores soltos, incompatíveis com CompanyData, o vínculo único de empresa e aplicativo que o restante do backend usa. O canal de e-mail não está disponível neste backend. O cliente de e-mail está ligado no arranque, sem ação exposta.

O banco local está declarado e não mapeia informação de negócio. Comentários antigos de atualização estão desligados: idiomas, bloqueio, auditoria, usuário de sistema e redefinição de senha. Esses dados não moram aqui. O bloqueio e a redefinição de senha que estão no ar seguem para os serviços ligados. A redefinição de senha está em [[bff-entrar-sair-e-senha]]. O bloqueio está em [[bff-bloqueio]].

## Quem pode

Ninguém, por estas capacidades. Não há ação exposta. A porta de e-mail não entra na compilação.

## Em que pé está

| Pé | O que esta nota nomeia |
|---|---|
| Só preparado | auditoria, dados da empresa, idiomas, assinatura e modelos de mensagem. O cliente de e-mail também: ligado no arranque, sem ação para o aplicativo |
| Fora de uso | o canal de e-mail. Há código, e ele está desligado da compilação |

O banco local fica fora dessa escala de porta. Existe no arranque e não oferece informação de negócio ao aplicativo.

Planos e cupons são porta sem ligação: a porta existe, exige sessão, e o serviço de planos não está registrado no arranque. O detalhe está em [[bff-planos-e-cupons]].

## O que esta nota não cobre

Telas, endereços dos serviços e segredos. O que já está no ar está nomeado em [[bff-o-que-e-este-backend]]. O repositório não mostra o que a pessoa faria com auditoria, idiomas, assinatura ou modelos de mensagem.

## Incertezas

"Dados da empresa", nesta nota, é o serviço de empresa conhecido no arranque, sem porta. O vínculo de uma empresa e um aplicativo já sobe com o backend e entra no cadastro do profissional, em [[bff-cliente-e-profissional]]. O que o serviço de empresa devolveria não aparece neste repositório.

"Assinatura" é o nome do serviço conhecido no arranque. O repositório não diz se isso é aceite de documento ou outro tipo de assinatura.

A configuração nomeia um serviço de registro de falhas. O arranque não registra esse cliente. O canal de e-mail fora de uso ainda o pede.

Várias portas no ar recebem o cliente de auditoria e não o chamam. Dessas ações não sai registro de auditoria.

Os comentários do banco local citam idiomas, bloqueio, auditoria, usuário de sistema e redefinição de senha, e estão desligados. O código atual não mapeia essas informações. Não dá para afirmar, por este repositório, que esse banco um dia as gravou.

A lacuna de e-mail e a da sessão seguem abertas em [[contradicoes-e-lacunas]]. Ver [[beautiful-api]].
