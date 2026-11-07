---
tipo: extração
tema: Como o time revisa a interface
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["storybook-web", "playground"]
pé: Parcial — o catálogo no navegador mostra as peças com página; o app no celular só mostra o botão de link e não abre o catálogo
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Como o time revisa a interface

Volta para o [[Panorama do design system]].

Há dois lugares previstos para olhar as peças. Um é o catálogo no navegador, o pacote `storybook-web`, na porta 6006. O outro é um app de demonstração no celular, o pacote `playground`, chamado Design System Playground (versão marcada 1.0.0). Nenhum dos dois usa o escopo `@wecareu`. Esse app também tem um catálogo preparado para abrir dentro do aparelho, na porta 7007. Hoje a tela do app não abre esse catálogo.

O lugar que mostra as peças é o catálogo do navegador. O app no celular ainda não é uma vitrine.

## Como ler o pé

| Pé | Significado |
|----|-------------|
| Pronto | A peça existe, dá para colocar numa tela, tem demonstração e teste automático. |
| Parcial | Existe e dá para usar, mas demonstração, teste ou texto interno está incompleto, ou o comportamento cobre só parte do que o nome promete. |
| Previsto | Citado e não construído neste repositório. |

Pé desta área: **Parcial**.

## O que a pessoa vê no catálogo

O catálogo procura as páginas de demonstração das peças e abre cada uma dentro do tema. Dá para alternar claro e escuro por um controle chamado Tema, com as opções Claro e Escuro. A abertura é o claro.

A escolha é gravada no navegador. Na abertura, o controle volta para o claro e grava o claro de novo. Quem tinha deixado o escuro não reencontra essa escolha ao abrir o catálogo.

Cada página também fica dentro da camada de espera, a mesma da nota [[Espera e carregamento]]. O véu só aparece quando a página pede.

Páginas que existem:

- [[Vocabulário visual]]
- [[Textos da interface]]
- [[Ações]] — botão em degradê, botão de link e botão de fechar, cada um com a sua página
- [[Campos de formulário]] — campo livre e campo com máscara
- [[Escolha em lista]]
- [[Datas]]
- [[Espera e carregamento]] — um botão com o texto "Mostrar Loading" mostra o véu por alguns segundos

Sem página própria:

- [[Identidade visual]] — medidas, cores e tema. O claro e o escuro aparecem em volta das outras peças, não numa página só deles

## O que a pessoa vê no celular

A tela que abre não é um mostruário do kit. O título diz "Design System Playground". O subtítulo diz para testar os componentes. Embaixo há uma seção só do botão de link, com cinco exemplos:

- "Link Pequeno"
- "Link Médio"
- "Link Grande"
- "Link Desabilitado" — o botão não responde
- "Link Sem Sublinhado"

Os três primeiros só mudam o texto. O botão de link não tem tamanho pequeno, médio ou grande. Nenhuma outra peça aparece: nem o degradê, nem o fechar, nem o texto, nem os campos, nem a lista, nem a data, nem a espera, nem os ícones.

O tema dessa tela fica preso no claro.

O catálogo dentro do aparelho está preparado na porta 7007, com a moldura de catálogo no celular. Ele só registraria a página do botão de link. As outras páginas não entram. E a tela do app não troca para esse catálogo. O sinal que deveria abrir o catálogo no aparelho não é lido pela tela que abre.

## O que esta nota não cobre

- Como ligar o catálogo ou o app. Isso fica com quem desenvolve
- Telas do app de quem procura o serviço, e o app de quem atende
- Se o teste automático passa ou falha neste momento. A nota só registra que o teste existe, ou não, em cada peça. O mapa está no [[Panorama do design system]]
