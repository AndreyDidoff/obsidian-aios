---
tipo: fonte
arquivo: "ingeridos/core-19-o-que-nao-saiu-do-papel.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["O que não saiu do papel"]
---

# O que não saiu do papel

Dois achados no repositório BPT-Core, retrato de 21/10. Os dois ficam fora do aplicativo do cliente, fora do aplicativo do artista e fora dos microserviços do BFF. Os dois fecham sem tabela e sem arquivo `banco-*`.

Foto desse repositório. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

`Br.Ticket.Nuget` mora no projeto `Br.Ticket.Nuget`, pasta `Br.Login.API/Br.Ticket.Nuget`. A única classe, `Class1`, está vazia. Não há API. Não há host `*.bptsoftware.com.br`. O projeto de endereço aponta para este pacote e não usa a classe. A compilação do repositório chega a gerar o projeto. Não há arquivo `banco-*` de chamado.

A consola web Vue mora na pasta `Br.Login.API/Br.Login.Front/br.login.vue`. O `package.json` chama o pacote de `client-app`. Esse nome não faz desta pasta o `ui_client` de [[app-do-cliente]]. A consola não se publica num host `*.bptsoftware.com.br`. O entrar e o sair chamam `https://loginapimicroservice.bptsoftware.com.br`. O esqueci a senha chama `https://localhost:7161`. Não há tabela.

## O que isso é

`Br.Ticket.Nuget` é um pacote vazio. O nome do projeto fala em ticket. O código não descreve chamado, fila, suporte nem atendimento. A classe pública não tem campo nem ação.

A consola Vue é um site desenhado dentro do repositório de login. Mostra uma página institucional da BPT, uma tela de entrar, um cartão de cadastro vazio e, depois do acesso, uma grade de sistemas. Não guarda a regra de negócio. Não é microserviço do BFF. Não é [[app-do-cliente]] nem [[app-do-artista]].

## O que já se consegue fazer

No pacote de ticket, nada. Não há ação para chamar.

Na consola, o entrar chama o host do serviço de login e a senha não sai como foi digitada. O esqueci a senha pede o token em `https://localhost:7161`, não no host publicado. O cadastro é um cartão vazio. O sair pede a saída no serviço de login e abre de novo a tela de entrar. A página inicial usa números fixos da própria tela. O formulário de contato manda a mensagem para fora desta consola, por e-mail, e não passa por host `*.bptsoftware.com.br`.

A regra de entrar, de senha e de sistemas mora no serviço de login, em [[core-01-conta]].

## Em que pé está

Casca, os dois.

O pacote de ticket entra na solução e na compilação com uma classe vazia. Sem API, sem host, sem tabela.

A consola tem tela desenhada neste repositório e continua casca de produto. Não é o aplicativo do cliente, não é o aplicativo do artista e não é microserviço do BFF. Não tem host próprio nem tabela. O cadastro é cartão vazio. O entrar depende do serviço de login, que mora em outro projeto.

## O que esta nota não cobre

Senha e credencial de pacote. O contrato do BFF, [[beautiful-api]]. A regra de negócio de entrar, de senha e de sistemas. Chamado de suporte: este código não o descreve. A conta e o destino do formulário de contato. O texto já gravado de tradução.

## Incertezas

Não dá para saber, por esta pasta, se um pacote `Br.Ticket.Nuget` já publicado noutro feed carrega código que este repositório não tem. Aqui a classe está vazia.

A grade de sistemas só segue se a checagem do acesso devolver `isValid`, com i minúsculo. O mesmo retorno, ao guardar a pessoa, é lido como `IsValid`, com I maiúsculo. As duas leituras não são a mesma chave. Sem o cookie de acesso, a checagem devolve falso e a leitura de `isValid` estoura, em vez de só voltar à tela de entrar. Não dá para fechar, por esta pasta, se uma sessão boa abre a grade.

Há nesta pasta um cliente de traduções apontando `https://i18napimicroservice.bptsoftware.com.br`. Nenhuma das telas desta nota o usa. Esse host não é o endereço da consola.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
