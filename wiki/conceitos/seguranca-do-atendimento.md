---
tipo: conceito
criado: 2026-10-20
atualizado: 2026-11-05
fontes: ["[[decisoes-2026-10-20]]", "[[decisoes-2026-10-21]]", "[[decisoes-2026-11-03]]", "[[decisoes-2026-11-05]]", "[[mvp-final]]", "[[mvp-funcoes-e-telas]]", "[[mvp-alteracoes-pos-congelamento]]", "[[ssot-backlog]]", "[[ssot-termos-legais]]", "[[lyraui-03-estado-atual]]", "[[lyraui-06-catalogo-legado]]", "[[brainstorming-wecareu]]", "[[planos]]", "[[planos-para-o-futuro]]", "[[seguranca-e-protecao-de-dados]]", "[[library-components-o-que-entrega]]", "[[library-components-entrar-na-conta]]", "[[library-components-biometria-e-sessao]]", "[[library-components-em-que-pe-esta]]", "[[conversa-do-agendamento]]", "[[o-que-ainda-nao-esta-no-app-do-artista]]", "[[bff-bloqueio]]", "[[bff-documentos-para-validacao]]", "[[bff-relatos]]", "[[board-bloqueio]]", "[[board-denuncia]]", "[[core-07-bloqueio]]"]
---

# Segurança do atendimento

Segurança física e contra fraude entre cliente e [[artista]], sobretudo em atendimento a domicílio. Para dados e LGPD, ver [[protecao-de-dados]].

## Alvo do cliente

O cliente bloqueia o artista e não desbloqueia. Não há tela de bloqueados. O desbloqueio é da equipe, pelo suporte. A sanção do MVP é só a suspensão por tempo indeterminado, por conta e por app, até a pessoa falar com o suporte. Não há advertência nem banimento permanente neste release. ([[mvp-alteracoes-pos-congelamento]])

Cadastro e agendamento do cliente são chatbot. Chat livre continua fora. ([[mvp-funcoes-e-telas]])

O endereço que o artista vê continua o de 03/11. A tela do artista espera o detalhe desse lado. ([[mvp-final]])

## Validação do Artista ([[brainstorming-wecareu]])

- Upload de documentos e de foto/vídeo, com ou sem documento.
- Foto/vídeo usados pelo cliente para reconhecer o Artista.
- Check-in ao chegar, com senha aleatória.
- Validador de dispositivo: detecta vários perfis de Artista no mesmo aparelho sem serem da mesma empresa.

## Proteção do cliente ([[brainstorming-wecareu]])

- **Quando o endereço do cliente aparece para o artista:** antes de 00:00:01 do dia anterior ao atendimento, só nome, foto e região. A partir dessa hora, os dados de todos os clientes daquele dia. Marcação já dentro da janela libera na hora. ([[mvp-final]]) A tela espera o arquivo de detalhe.
- Sem chat livre: cliente e Artista interagem apenas pela plataforma, via chatbot (ver abaixo).

## Outros

- Check-in também valida o [[atendimento-imediato]] e pune o uso indevido. ([[planos]])
- Rastreamento do Artista em tempo real: **fora do [[mvp]]**, fica para versão futura ([[decisoes-2026-10-20]]). Quando existir, a localização deve ser compartilhada só entre as partes do serviço ([[seguranca-e-protecao-de-dados]]).
- Shadowban: a ação parece concluída e o backend descarta (sinkhole). Vários perfis de Artista no mesmo aparelho, sem serem da mesma empresa, vão para revisão manual no `web-admin`. ([[planos-para-o-futuro]], [[ssot-termos-legais]], [[brainstorming-wecareu]])
- Sessão: a mesma conta pode estar no CLIENT e no WORKER ao mesmo tempo, até no mesmo aparelho, mas não em dois aparelhos do mesmo app. ([[lyraui-03-estado-atual]])

## Comunicação: sempre mediada por bot

Decidido em [[decisoes-2026-10-20]]: há chat, mas é um **chatbot** com três fluxos (cadastro, finalização do cadastro, agendamento com o Artista). O Artista nunca tem chat livre direto com o cliente; sempre há um bot no meio. Isso concilia o "sem chat" do [[brainstorming-wecareu]] com o chatbot de atendimento que já aparecia ali, e torna obsoleta a frase "antes do cliente e Artista se falarem" ([[planos]]).

[[ssot-backlog]] registra o oposto como decisão de produto: "não haverá sistema de chat interno". [[lyraui-06-catalogo-legado]] lista a tela `ChatSchedules` nos dois apps. Nenhuma das duas substitui a decisão do chatbot. No app do cliente, em 21/10, a tela é casca: o centro diz "Tab ChatSchedules", nenhuma aba abre e nenhum botão aponta. ([[conversa-do-agendamento]]) No artista, a tela existe, o centro diz "Tab ChatSchedules", não está na barra e nenhum botão do Início, da Agenda ou do perfil a abre. ([[o-que-ainda-nao-esta-no-app-do-artista]]) O alvo continua chatbot sem texto livre.

**Sem texto livre no MVP:** o bot funciona por escolhas ou frases simples. No agendamento, apresenta datas e o usuário escolhe uma; nada é repassado como mensagem entre cliente e Artista. ([[decisoes-2026-10-20]]) Isso também impede, na prática, a troca de contatos para fechar atendimentos fora do app.

## Entrar na conta, neste pacote

Retrato de `@wecareu/auth-flow` 0.1.0 em [[fluxo-de-entrada]]. Não é decisão de produto. O alvo de chatbot e de check-in permanece o que está acima.

A sessão deste fluxo fica no aparelho e é retomada ao abrir. Este repositório não chama a API sozinho. Quem fala com o servidor é o serviço de conta do app. ([[library-components-o-que-entrega]], [[library-components-biometria-e-sessao]])

Entrar com biometria manda um resumo MD5 da senha, não a senha digitada. O login comum manda a senha como foi digitada. O código trata o resumo como exigência de um servidor antigo. Se o serviço esperar a senha original, a entrada falha mesmo com o reconhecimento certo. ([[library-components-biometria-e-sessao]], [[library-components-em-que-pe-esta]])

Sair da conta não apaga a credencial biométrica nem a preferência. O link "Não tem uma conta? Cadastrar" está visível e o toque não abre nada. ([[library-components-biometria-e-sessao]], [[library-components-entrar-na-conta]])

## Bloqueio neste backend

A porta de bloqueio está no ar. O serviço está ligado e a configuração tem endereço de bloqueio. O retrato não diz o efeito na tela, nem se esconde perfil, chat ou agenda, nem motivo e prazo. Relatos estão em [[bff-relatos]]. Shadowban e check-in continuam como estão acima. ([[bff-bloqueio]])

No núcleo, nenhum outro serviço deste repositório lê `BlockUsers` para esconder perfil, conversa ou agenda. ([[core-07-bloqueio]])

## Documentos de validação e relatos neste backend

A porta de documentos para validação está no ar. Dá para consultar um conjunto pelo identificador, enviar, editar e apagar. Não há, nesta porta, o passo em que alguém aprova ou recusa. O alvo de validação do Artista, com upload e check-in, permanece o do início desta página. Esta porta não é esse fluxo. ([[bff-documentos-para-validacao]])

A porta de relatos está no ar. Dá para listar, criar, editar e apagar o relato, e anexar, editar e tirar uma foto desse relato. A porta não declara texto, motivo nem sobre quem é. Shadowban e chatbot continuam como estão acima. ([[bff-relatos]])

## O que o board pede em 21/10

O alvo acima permanece: sem chat livre, validação do artista. Bloqueio e denúncia no board não viram shadowban nem check-in.

O épico 335, Sistema de bloqueio, está New e sem descrição. A história 147, Bloqueio de Artistas e Clientes, está New. A descrição está ausente. ([[board-bloqueio]]) A porta [[bff-bloqueio]] já está no ar como retrato de código. Isso não vem do estado do work item. O board não diz se o bloqueio esconde perfil, chat ou agenda. A porta também não diz.

O épico 336, Sistema de denúncia, está New e sem descrição. A tarefa 368, [BE] Integrar Denuncia do cluster com o WeCareU, está New. A história 242, Criar Fluxo de Denuncia, está Completed e sem pai. Completed é o estado do work item. Não significa no ar, entregue, nem parte do [[mvp]]. ([[board-denuncia]]) A porta [[bff-relatos]] não é esse sistema. O código não diz se o relato é denúncia, avaliação ou atendimento. O pedido de denúncia fica ao lado. A porta não declara o sentido.

Ver [[contradicoes-e-lacunas]].
