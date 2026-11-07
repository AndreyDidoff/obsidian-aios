---
tipo: fonte
arquivo: "ingeridos/Primeira entrada.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório ui_client; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Primeira entrada"]
---

# Primeira entrada

Volta para [[mapa-do-app-do-cliente]].

Porta de quem ainda não está na conta. Duas saídas na abertura, um carrossel de três passos e, no fim, a lista como visitante. Quem já tem conta pula isso e vai para o login. ([[entrar-senha-e-biometria]])

**Pé:** construído, com falha na permissão de localização. A pessoa sai da abertura, passa o carrossel e chega na lista sem criar conta. A permissão não se comporta como o texto da tela promete.

## Abertura

Logo da WeCareU. **Vamos começar?** abre o carrossel. **Já tenho uma conta** abre o login.

Se a pessoa já ligou digital ou reconhecimento facial, o aparelho tem o recurso e a credencial ainda vale, o app tenta entrar sozinho assim que termina de carregar. Os dois botões continuam na tela enquanto isso. Se a tentativa falha, cai no login.

## O carrossel

Três passos, com bolinhas. **Próximo** nos dois primeiros e **Finalizar!** no último. Arrastar não pede permissão: só o botão pede. Não há botão de voltar para a abertura. **Já tenho uma conta** continua embaixo.

**Permitir localização.** Texto: "Para descobrir artistas que atendem em sua região." Recusar avança, e o endereço não é preenchido. Permitir avança e o app tenta completar o endereço com o GPS. Se já houver um ponto salvo, não busca de novo. Se a busca falhar, volta a este passo. O app grava no aparelho se a localização foi permitida, mas nenhuma tela lê esse registro, e o registro fica invertido: recusa é gravada como permitida, e permissão como recusada. Isso não muda o que a pessoa vê hoje.

**Permitir Notificações.** Texto: "Para acompanhar seus agendamentos e receber atualizações." Aceitar ou recusar não trava. O carrossel segue para o endereço.

**Preencha seu endereço.** **Usar minha localização** tenta o GPS de novo e preenche rua e CEP; número e complemento já digitados são mantidos. Se o aparelho não devolver um endereço, o carregamento some e o formulário fica como estava, sem frase de erro. O CEP, com oito dígitos, busca a rua. Se a busca falhar, o campo entra em erro, sem texto explicando. A rua que aparece não se digita: vem do CEP ou do GPS. O CEP aparece com asterisco. Para concluir, o app só exige o **número**. Sem número, **Finalizar!** não avança e mostra "Campos obrigatórios". Com número, a pessoa entra como visitante. Complemento é opcional. O endereço fica no aparelho e reaparece neste formulário. Não entra sozinho no rascunho de [[criar-conta]].

## Visita sem conta

Ao finalizar, abre a lista. ([[encontrar-profissionais]]) A pessoa não está logada. Fechar a lista sai da visita e volta para a abertura.

A tela "Qual é seu endereço?", com **Entrar ou Cadastrar**, está no app e não faz parte deste caminho. O endereço desta entrada é o terceiro passo do carrossel.

Esta entrada não explica, na tela, o que acontece se a localização for recusada. Não impede seguir sem notificações nem sem um CEP válido. Não leva a criar a conta: isso fica no convite da lista, ou em **Já tenho uma conta**. Não usa a tela antiga de visitante ("Encontre os melhores artistas perto de você"). Ver [[o-que-ainda-nao-esta-no-app]].
