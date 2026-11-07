> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório service_api, o backend de apoio ao aplicativo da WeCareU, no momento da extração. Descreve em linguagem de produto o que o aplicativo já pode pedir a este backend e em que pé está cada capacidade. Não descreve telas. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Preparado e ainda não oferecido

## O que isso é para o app

Parte do que este backend já conhece ainda não chega ao aplicativo como ação. O banco local sobe junto e não é o lugar onde o negócio mora.

## O que a pessoa já consegue fazer por este backend

Estas capacidades param antes do aplicativo.

O arranque já conhece auditoria, dados da empresa, idiomas, assinatura, modelos de mensagem e e-mail. Não há porta para o aplicativo pedir essas ações.

O canal de e-mail tem um arquivo de porta. Ele está vazio e fora da compilação. O construtor ainda pede dois identificadores soltos, incompatíveis com o vínculo único de empresa e aplicativo (CompanyData) que o restante do backend usa. O canal de e-mail não está disponível neste backend. O cliente de e-mail, esse sim, está ligado no arranque, sem ação exposta.

O banco local está declarado e não mapeia informação de negócio. Comentários antigos de atualização estão desligados: idiomas, bloqueio, auditoria, usuário de sistema e redefinição de senha. Esses dados não moram aqui. O bloqueio e a redefinição de senha que o aplicativo já pede seguem para os serviços ligados, em [[07-bloqueio]] e [[03-entrar-sair-e-senha]].

## Quem pode

Ninguém, por estas capacidades. Não há ação exposta ao aplicativo. A porta de e-mail não entra na compilação.

## Em que pé está

Só preparado — auditoria, dados da empresa, idiomas, assinatura e modelos de mensagem. O cliente de e-mail também está só preparado: ligado no arranque, sem ação para o aplicativo.

Fora de uso — o canal de e-mail. Há código, e ele está desligado da compilação.

O banco local fica fora dessa escala de porta. Ele existe no arranque e não oferece informação de negócio ao aplicativo.

Planos e cupons são outra situação, porta sem ligação, e estão em [[06-planos-e-cupons]].

## O que esta nota não cobre

Telas, endereços dos serviços e segredos. Também fica de fora o que já está no ar: entrar, cadastro, serviços, bloqueio, endereços, telefones, fotos, relatos, documentos, permissões e grupos. O repositório não mostra o que a pessoa faria com auditoria, idiomas, assinatura ou modelos de mensagem.

## Ligações

[[01-o-que-e-este-backend]] [[02-cliente-e-profissional]] [[03-entrar-sair-e-senha]] [[06-planos-e-cupons]] [[07-bloqueio]]

## Incertezas

"Dados da empresa", nesta nota, é o serviço de empresa conhecido no arranque, sem porta. O vínculo de uma empresa e um aplicativo já sobe com o backend e entra no cadastro do profissional, em [[02-cliente-e-profissional]]. O que o serviço de empresa devolveria não aparece neste repositório.

"Assinatura" é o nome do serviço conhecido no arranque. O repositório não diz se isso é aceite de documento ou outro tipo de assinatura.

A configuração nomeia um serviço de registro de falhas. O arranque não registra esse cliente. O canal de e-mail fora de uso ainda o pede.

Várias portas no ar recebem o cliente de auditoria e não o chamam. Dessas ações não sai registro de auditoria.

Os comentários do banco local citam idiomas, bloqueio, auditoria, usuário de sistema e redefinição de senha, e estão desligados. O código atual não mapeia essas informações. Não dá para afirmar, por este repositório, que esse banco um dia as gravou.
