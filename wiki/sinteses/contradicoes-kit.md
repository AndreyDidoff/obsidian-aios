---
tipo: sintese
criado: 2026-11-07
atualizado: 2026-11-07
fontes: ["[[contradicoes-e-lacunas]]"]
---

Este tema não é o produto do MVP. Os outros temas saem de [[contradicoes-e-lacunas]]. Os números são os daquela página.

## Contradições

| # | Tema | Conflito | Status |
| --- | --- | --- | --- |
| 20 | Catálogo do kit | [[lyraui-06-catalogo-legado]] lista 13 pacotes `@wecareu/*`, com `image-upload`. [[panorama-do-design-system]] lista 12 e não cita `image-upload` | **Aberto.** O catálogo de 20/10 permanece |
| 21 | Livvic | O alvo reserva Livvic ao título grande e deixa o corpo entre Plus Jakarta Sans e DM Sans ([[lyraui-09-fundamentos-visuais]]). O kit pinta corpo, rótulo e botão em Livvic ([[identidade-visual]]) | Aberto |
| 22 | Cor secundária | O alvo nomeia Secondary coral `#D85A30` e Tertiary `#FF0098` ([[lyraui-09-fundamentos-visuais]]). No kit, a ação no claro é o roxo `#712fc1` e a ação secundária é o lilás `#817eb9`. O texto de instalação ainda cita `#2E6BE6`. O retrato não cita coral nem o rosa terciário entre os papéis de marca ([[identidade-visual]]) | Aberto |
| 23 | Tema por app | [[lyraui-05-sistema-de-tema]] fixa CLIENT em light e WORKER em dark, sem a pessoa escolher. O kit abre no claro se ninguém escolhe e permite alternar com a tela aberta; o interruptor do app do cliente não está nesse repositório ([[identidade-visual]]). O catálogo tem um controle Tema que regrava o claro ao abrir ([[como-o-time-revisa-a-interface]]) | Aberto |
| 24 | Auth-flow e os apps | [[lyraui-06-catalogo-legado]] trata `@wecareu/auth-flow` como peça da biblioteca ao lado das telas dos apps. O retrato de 21/10 do repositório `library-components` não evidencia publicação nem instalação, e o inventário interno de 7 de maio de 2026 não descreve o disco de 21/10: dizia que a pasta de build não existia (hoje existe) e citava um componente de carregamento que o pacote atual não declara ([[library-components-em-que-pe-esta]], [[library-components-o-que-entrega]]). A extração do cliente não cita `@wecareu/auth-flow` ([[entrar-senha-e-biometria]]). A extração do artista não cita `@wecareu/auth-flow` ([[entrar-senha-e-biometria-do-artista]]). O cruzamento de 21/10 lê os três percursos juntos: a peça 0.1.0 existe desenhada e não está ligada a nenhum dos dois apps ([[cruzamento-entrar-senha-e-biometria]], [[cruzamento-como-ler]]) | **Aberto, como retrato.** Os dois apps têm percurso próprio e a peça compartilhada não está instalada. Cliente e artista estão mais perto um do outro do que da peça. Não é decisão de manter os percursos separados. As extrações de cada app não citam o pacote. O repositório `library-components` não evidencia instalação. Quem fala com o backend, hoje, é o próprio app, não a peça compartilhada ([[cruzamento-bff-como-ler]]). Telas de login pedidas em [[board-conta-e-acesso]] não provam que o pacote está em uso. Biblioteca e design system pedidos em [[board-estrutura-dos-apps]] não instalam `@wecareu/auth-flow` |
| 27 | Pé da escolha e dos ícones | [[cruzamento-como-ler]] diz que, quando o panorama e a nota da peça divergem, o cruzamento fica com a nota da peça e registra a divergência. Isso acontece na escolha em lista e nos ícones. [[cruzamento-kit-visual]] registra: na tabela de áreas do [[panorama-do-design-system]], a [[escolha-em-lista]] está como Pronto; a nota da peça diz Parcial; neste cruzamento vale o pé da peça, Parcial (busca vazia sem frase, textos prontos em inglês). O mesmo panorama marca os ícones como Parcial. A nota [[vocabulario-visual]] diz que os desenhos estão prontos, e que a bandeira e as animações ficam parciais. Neste cruzamento vale essa nota | **Aberto.** Divergência de retrato entre o panorama e a nota da peça. Não é decisão da empresa |

## Lacunas

- **Telas e pagamento no kit:** o retrato de 21/10 não cobre telas dos apps nem pagamento. Ícone e máscara de cartão não cobram. → [[panorama-do-design-system]]
- **Peça só, como direção deste retrato:** [[cruzamento-o-que-deveria-ser-uma-peca-so]] pede cara da tela no kit e percurso igual numa peça de fluxo, e cadastro só depois de alinhar as jornadas. É direção de manutenção deste retrato de 21/10. A empresa não tomou essa decisão. Não é alvo do MVP. Se conflitar com uma decisão oficial, vale a oficial. → [[kit-visual]], [[fluxo-de-entrada]], [[cadastro]]
