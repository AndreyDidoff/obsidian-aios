---
tipo: extração
tema: Primeira entrada
fonte: ui_client
extraido_em: 2026-10-21
idioma: pt-BR
pé: construído, com falha na permissão de localização
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do app do cliente (repositório ui_client) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Primeira entrada

Volta para o [[Mapa do app do cliente]].

Esta é a porta de quem ainda não está dentro da conta. Há duas saídas na abertura, um carrossel de três passos e, no fim, a lista de artistas como visitante. Quem já tem conta pula isso e vai para o [[Entrar, senha e biometria|login]].

**Pé:** construído. A pessoa consegue sair da abertura, passar o carrossel e chegar na lista sem criar conta. A permissão de localização não se comporta como o texto da tela promete. Detalhe abaixo.

## Abertura

A primeira tela mostra o logo da WeCareU e dois caminhos:

- **Vamos começar?** Abre o carrossel.
- **Já tenho uma conta.** Abre o login.

Se a pessoa já ligou digital ou reconhecimento facial, o aparelho tem esse recurso e a credencial ainda vale, o app tenta entrar sozinho assim que termina de carregar. Se essa tentativa falha, cai no login. Os dois botões continuam na tela enquanto isso acontece. O restante da biometria está em [[Entrar, senha e biometria]].

## O carrossel

Três passos, com bolinhas de progresso. O botão de baixo diz **Próximo** nos dois primeiros e **Finalizar!** no último. Dá para arrastar para o lado. Arrastar não pede permissão: só o botão pede. O leitor de tela anuncia o passo atual, o título e, quando existe, o texto de apoio.

Não há botão de voltar para a abertura. **Já tenho uma conta** continua embaixo e leva ao login.

### 1. Localização

Título: **Permitir localização.** Texto: "Para descobrir artistas que atendem em sua região."

O que acontece de fato ao tocar em **Próximo**:

- Se a pessoa **recusa**, o carrossel avança e o endereço não é preenchido.
- Se a pessoa **permite**, o carrossel avança e o app tenta completar o endereço com o GPS. Se já houver um ponto salvo, não busca de novo. Se a busca falhar, volta para este primeiro passo.

O app também grava no aparelho se a localização foi permitida, mas nenhuma tela lê esse registro. E o registro fica invertido: recusa é gravada como permitida, e permissão como recusada. Isso não muda o que a pessoa vê hoje.

### 2. Notificações

Título: **Permitir Notificações.** Texto: "Para acompanhar seus agendamentos e receber atualizações."

Aceitar ou recusar não trava o fluxo. O carrossel sempre segue para o endereço. Se a permissão já tinha sido dada antes, o sistema não pergunta de novo.

### 3. Endereço

Título: **Preencha seu endereço.** O formulário tem:

- **Usar minha localização.** Tenta de novo o GPS e preenche rua e CEP. Número e complemento que a pessoa já digitou são mantidos. Se o aparelho não devolver um endereço, o carregamento some e o formulário fica como estava, sem uma frase de erro.
- **CEP.** Ao sair do campo com oito dígitos, o app busca a rua. Se a busca falhar, o campo entra em estado de erro, sem texto explicando o motivo. O endereço que aparece não pode ser digitado: vem do CEP ou do GPS.
- **Número.** É o único campo que trava o fim do carrossel.
- **Complemento.** Opcional.

O CEP aparece com asterisco, como se fosse obrigatório. Para concluir, o app só exige o número. Sem número, **Finalizar!** não avança e mostra "Campos obrigatórios". Com número, a pessoa entra como visitante.

O endereço fica guardado no aparelho e reaparece se ela voltar a este formulário. Não entra sozinho no [[Criar conta|cadastro da conta]], que guarda um rascunho separado.

## Visita sem conta

Ao finalizar, abre a lista de [[Encontrar profissionais|artistas]]. A pessoa não está logada. Fechar a lista sai da visita e volta para a abertura.

Existe outra tela, "Qual é seu endereço?", com a pergunta e um atalho **Entrar ou Cadastrar**. Ela está no app e não faz parte deste caminho. O endereço da primeira entrada é o terceiro passo do carrossel.

## O que esta entrada ainda não faz

- Não explica, na tela, o que acontece se a localização for recusada. O texto fala em descobrir artistas da região, e recusar simplesmente avança.
- Não impede seguir sem notificações, e também não impede seguir sem um CEP válido.
- Não leva a pessoa a criar a conta. Isso fica para o convite dentro da lista, ou para **Já tenho uma conta**.
- Não usa uma tela antiga de visitante ("Encontre os melhores artistas perto de você"), que existe no projeto e não entra neste fluxo. Ver [[O que ainda não está no app]].
