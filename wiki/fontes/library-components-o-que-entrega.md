---
tipo: fonte
arquivo: ingeridos/library-components-o-que-entrega.md
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-components, pacote @wecareu/auth-flow; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["O que o library-components entrega"]
---

# O que o library-components entrega

Porta desta leva. O repositório `library-components` não é o app. A única experiência de produto construída é entrar e recuperar senha, com biometria opcional. Pacote `@wecareu/auth-flow` **0.1.0**. A descrição oficial é fluxo de autenticação centralizado para os aplicativos da WeCareU.

O visual não nasce aqui. Vem de [[kit-visual]], no repositório `library-design-system`. Aqui ficam o percurso e os textos. Peças declaradas hoje: botão de fechar, degradê, link, ícones, campo de texto, texto e tema. Não declara data, lista, máscara nem espera. ([[library-components-em-que-pe-esta]])

## O que a pessoa já faz

A tela de entrada se chama "Entre na sua conta". E-mail e senha. A falha de login tem frase na tela. Se o aparelho oferecer biometria, dá para entrar, ligar e desligar. Para ligar, e-mail e senha precisam estar preenchidos. ([[library-components-entrar-na-conta]], [[library-components-biometria-e-sessao]])

Quem esqueceu a senha percorre três telas. Quando a senha nova é aceita, volta para a entrada. Os textos já estão prontos em português e em inglês. O idioma é o que o app já escolheu. Esta peça não escolhe idioma. ([[library-components-recuperar-senha]])

A sessão fica no aparelho e é retomada ao abrir. Este repositório não chama a API sozinho. Quem fala com o servidor é o serviço de conta do app consumidor. Sem esse serviço, as telas não concluem login nem recuperação.

Depois que a pessoa entra, o app consumidor escolhe a tela. Ao sair, escolhe o retorno. Esses destinos não estão neste repositório.

## O que o texto promete e o código não faz

O texto de apresentação promete renovação automática de acesso. O que está construído: a sessão é guardada e renovar fica com o app. Nada aqui dispara a renovação sozinho.

O link "Não tem uma conta? Cadastrar" está visível e o toque não abre nada. Não há tela de troca de senha para quem já está logado. Não há home, pedidos nem perfil.

Trocar a senha de quem já está logado, invalidar sessões e buscar a pessoa entram no serviço que o app precisa ligar. Não há tela aqui para essas três.

Ver [[fluxo-de-entrada]], [[library-components-em-que-pe-esta]].
