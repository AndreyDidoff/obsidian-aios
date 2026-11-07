---
tipo: extração
tema: Vocabulário visual
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/icons"]
pé: "Pronto nos desenhos; bandeira e animações parciais"
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Vocabulário visual

Volta para o [[Panorama do design system]].

É o conjunto de desenhos que as telas podem usar. Não é uma tela. São desenhos de linha: a cor pinta o traço.

## Quantos

A lista real tem **69** desenhos. O texto do pacote também conta 69. Os dois batem.

| Grupo | Quantos |
|-------|---------|
| Navegação | 16 |
| Pessoa e perfil | 7 |
| Dinheiro e pagamento | 6 |
| Lugar e deslocamento | 5 |
| Tempo e calendário | 2 |
| Comunicação | 9 |
| Imagem e captura | 4 |
| Avaliação e status | 11 |
| Cuidado e beleza | 2 |
| Sistema | 7 |
| **Total** | **69** |

Imagem e captura ficou de fora dos grupos sugeridos. Câmera, imagem, galeria e envio de arquivo não cabem em comunicação sem misturar o sentido.

## Navegação

| Desenho |
|---------|
| adicionar (plus) |
| buscar (search) |
| chevron para a direita (chevronRight) |
| chevron para a esquerda (chevronLeft) |
| chevron para baixo (chevronDown) |
| chevron para cima (chevronUp) |
| fechar (close) |
| início (home) |
| lista (list) |
| lista, outra variação (listAlt) |
| menu (menu) |
| seta em giro (arrowSpin) |
| seta para a direita (arrowRight) |
| seta para a esquerda (arrowLeft) |
| seta para baixo (arrowDown) |
| seta para cima (arrowUp) |

## Pessoa e perfil

| Desenho |
|---------|
| avatar (avatar) |
| avatar preenchido (avatarFill) |
| caderno de perfil (bookProfile) |
| digital (fingerPrint) |
| pessoa (user) |
| pessoa bloqueada (userBlock) |
| pessoa preenchida (userFilled) |

## Dinheiro e pagamento

| Desenho |
|---------|
| banco (bank) |
| cartão (card) |
| cartão com cédula (moneyCard) |
| cédula (money) |
| cédula, outra variação (money1) |
| pix (pix) |

## Lugar e deslocamento

| Desenho |
|---------|
| a pé (walk) |
| carro (car) |
| distância (distance) |
| lugar (location) |
| ponto de ônibus (busStop) |

## Tempo e calendário

| Desenho |
|---------|
| calendário (calendar) |
| relógio (time) |

## Comunicação

| Desenho |
|---------|
| aviso desligado (notificationOff) |
| aviso ligado (notificationOn) |
| central de ajuda (supportCenter) |
| compartilhar (share) |
| conversa encerrada (chatClose) |
| correio (mail) |
| denúncia (denounce) |
| enviar (paperPlane) |
| robô (bot) |

## Imagem e captura

| Desenho |
|---------|
| câmera (camera) |
| enviar arquivo (upload) |
| galeria (imageGallery) |
| imagem (image) |

## Avaliação e status

| Desenho |
|---------|
| confirmação (correct) |
| coroa (crown) |
| coração (heart) |
| coração preenchido (heartFilled) |
| diamante (diamond) |
| estrela (star) |
| estrela preenchida (starFilled) |
| estrelas (stars) |
| etiqueta (tag) |
| informação (information) |
| máscara triste (maskSad) |

Coroa e diamante são marcas de destaque. Etiqueta é um rótulo. Nenhum dos três é meio de pagamento.

## Cuidado e beleza

| Desenho |
|---------|
| secador (dryer) |
| unha (fingernail) |

## Sistema

| Desenho |
|---------|
| cadeado (lock) |
| configurar (config) |
| editar (edit) |
| filtrar (filter) |
| lixeira (trash) |
| mostrar (eyeOn) |
| ocultar (eyeOff) |

## O que o desenho não prova

Ter o desenho na biblioteca só prova que a tela pode mostrá-lo.

Pix, cartão, banco e cédula não significam que o app cobra. Secador, unha, carro, ponto de ônibus e a pé não significam que esse serviço está no catálogo. Aviso, central de ajuda, denúncia e robô não significam que o fluxo correspondente já existe no produto.

## Bandeiras

A peça de bandeira existe, no mesmo pacote dos desenhos.

Uma tela usa quando já tem o código do país, com duas letras, e quer mostrar a bandeira. O pacote cita Brasil, Estados Unidos e Portugal como exemplos. Não há lista fechada de países aqui: qualquer código de duas letras serve. Não há ligação pronta com telefone, endereço ou idioma.

No celular, a bandeira é o emoji do país, desenhado no aparelho. No navegador, é uma imagem buscada na hora para aquele código, então depende de rede. O tamanho muda. O padrão é pequeno. No navegador a largura fica uma vez e meia a altura. A cor não se escolhe.

Quem usa leitor de tela ouve o código do país, não o nome.

## Animações

Há três. O sentido vem do desenho e do nome interno, não do nome do arquivo.

| Nome | O que sugere |
|------|----------------|
| dots | Pontos de carregamento. O desenho interno se chama Loading Dots. São brancos. |
| locations | Lugares. Vários pinos surgindo. O desenho interno não tem nome legível. A cor gravada é roxa. |
| notification | Aviso. Um sino que balança. O desenho interno se chama notificacion. A cor gravada é o mesmo roxo. |

A peça de [[Espera e carregamento]] usa só os pontos. Lugares e aviso existem no vocabulário e não entram nessa espera.

Dá para mudar o tamanho, a velocidade, se a animação começa sozinha e se fica repetindo. O padrão é começar sozinha, repetir, velocidade normal. A cor já vem gravada: pontos brancos; lugares e aviso em roxo.

## O que dá para mudar na hora

No desenho: tamanho e cor. O tamanho vale igual para altura e largura. Sem cor escolhida, vale a cor de texto do tema, no claro e no escuro. Ver [[Identidade visual]]. Sem tamanho pedido, o desenho fica no tamanho natural do arquivo.

Na bandeira: só o tamanho.

Na animação: tamanho, velocidade, início automático e repetição. A cor, não.

## Versão, demonstração, teste, pé

Versão marcada de `@wecareu/icons`: **1.3.3**. Vale para desenhos, bandeira e animações.

| Peça | Demonstração | Teste | Pé |
|------|--------------|-------|----|
| Desenhos | Catálogo com tamanho pequeno, grande, cor escolhida, e exemplos de navegação, ação, status e comunicação | O desenho aparece, o tamanho pedido entra, a cor pedida entra, sem cor vale o tema, e dá para trocar o desenho | Pronto |
| Bandeira | Não há | Não há | Parcial |
| Animações | Não há neste pacote. Os pontos aparecem na demonstração de [[Espera e carregamento]] | Não há | Parcial |

## Como ler o pé

| Pé | Significado |
|----|-------------|
| Pronto | Existe, usável numa tela, com demonstração e teste. |
| Parcial | Existe com buraco. |
| Previsto | Não construído. |
