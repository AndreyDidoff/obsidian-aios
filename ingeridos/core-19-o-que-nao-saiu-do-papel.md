> Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do repositório BPT-Core, os microserviços por trás do BFF da WeCareU, no momento da extração (21/10/2026). Descreve o que esses serviços já fazem e em que pé está cada parte, em linguagem de produto, e fecha a cadeia até o projeto, o host `*.bptsoftware.com.br` e a tabela. Não é o aplicativo e não é o BFF: é a camada em que a regra de negócio mora. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# O que não saiu do papel

## Onde isso mora

Dois achados neste repositório. Os dois ficam fora do aplicativo do cliente, fora do aplicativo do artista e fora dos microserviços do BFF. Os dois fecham sem tabela e sem arquivo banco-*.

Br.Ticket.Nuget mora no projeto Br.Ticket.Nuget, pasta Br.Login.API/Br.Ticket.Nuget. A única classe é Class1, vazia. Não há API. Não há host `*.bptsoftware.com.br`. O projeto de endereço aponta para este pacote e não usa a classe. A compilação do repositório chega a gerar o projeto. Não há arquivo banco-* de chamado.

A consola web Vue mora na pasta Br.Login.API/Br.Login.Front/br.login.vue. As telas desta nota são App.vue e os componentes Login, Signup, Systems e Home, em src. O package.json chama o pacote de client-app. Esse nome não faz desta pasta o aplicativo do cliente. A consola não se publica num host `*.bptsoftware.com.br`. O entrar e o sair chamam https://loginapimicroservice.bptsoftware.com.br. O esqueci a senha chama https://localhost:7161. O e-mail seuemail@bptsoftware.com.br aparece só como texto de exemplo na página inicial. Não há tabela.

## O que isso é

Br.Ticket.Nuget é um pacote vazio. O nome do projeto fala em ticket. O código não descreve chamado, fila, suporte nem atendimento. A classe pública não tem campo nem ação.

A consola Vue é um site desenhado dentro do repositório de login. Mostra uma página institucional da BPT, uma tela de entrar, um cartão de cadastro vazio e, depois do acesso, uma grade de sistemas. Não guarda a regra de negócio. Não é microserviço do BFF.

## O que já se consegue fazer

No pacote de ticket, nada. Não há ação para chamar.

Na consola, o que cada tela mostra:

A moldura (App) mostra a rota da vez, o rodapé com a marca BPT e o texto Desenvolvido por BPT, um carregamento e uma faixa que diz Salvo com Sucesso, e o título da aba fica My | Titulo.

A tela de entrar mostra um cartão com foto, o campo E-mail, o campo Senha, o botão esqueci a senha e o botão Login.

A tela de cadastro mostra um cartão com o título Sign Up, o miolo em branco, o botão Cancel e o botão Sign In.

A grade de sistemas mostra a foto, o nome e o e-mail de quem entrou, o botão logout e um cartão por sistema, só com a foto.

A página inicial mostra a marca BPT software, os atalhos Home, Beneficios, Performance, Evolução, Contato e Login, frases de sistemas de gestão, um celular de exemplo com o painel Produção, Cadastro, Finanças, Relatórios, SAC e Configurações no nome Gabriela e no e-mail seuemail@bptsoftware.com.br, e um formulário de contato com Nome, Celular, Email, Empresa e Mensagem.

O botão Login só segue quando o e-mail e a senha passam na regra da tela. A senha não sai como foi digitada. Se o login responde, a tela pede a grade de sistemas. O esqueci a senha só dispara com o e-mail preenchido e pede o token no endereço local, não no host publicado. O cartão Sign Up não tem campo, o Cancel não tem ação e o Sign In chama uma ação que a tela não define. Na grade, o sistema inativo aparece apagado e o clique ainda abre o endereço `https://` mais o endereço daquele sistema. Editar a pessoa, no menu, não faz nada. O logout pede a saída e abre de novo a tela de entrar. Na página inicial, os gráficos usam números fixos da própria tela. O formulário de contato manda a mensagem para fora desta consola, por e-mail, e não passa por host `*.bptsoftware.com.br`.

## Em que pé está

Casca, os dois.

O pacote de ticket entra na solução e na compilação com uma classe vazia. Sem API, sem host, sem tabela.

A consola tem tela desenhada neste repositório e continua casca de produto: não é o aplicativo do cliente, não é o aplicativo do artista e não é microserviço do BFF. Não tem host próprio nem tabela. O cadastro é cartão vazio. O entrar depende do serviço de login, que mora em outro projeto.

## O que esta nota não cobre

Senha e credencial de pacote. O aplicativo do cliente e o do artista. O contrato do BFF. A regra de negócio de entrar, de senha e de sistemas, que mora no serviço de login. Chamado de suporte: este código não o descreve. A conta e o destino do formulário de contato. O texto já gravado de tradução.

## Incertezas

Não dá para saber, por esta pasta, se um pacote Br.Ticket.Nuget já publicado noutro feed carrega código que este repositório não tem. Aqui a classe está vazia.

A grade de sistemas só segue se a checagem do acesso devolver isValid, com i minúsculo. O mesmo retorno, ao guardar a pessoa, é lido como IsValid, com I maiúsculo. As duas leituras não são a mesma chave. Sem o cookie de acesso, a checagem devolve falso e a leitura de isValid estoura, em vez de só voltar à tela de entrar. Não dá para fechar, por esta pasta, se uma sessão boa abre a grade.

Há nesta pasta um cliente de traduções apontando https://i18napimicroservice.bptsoftware.com.br. Nenhuma das telas desta nota o usa. Esse host não é o endereço da consola.
