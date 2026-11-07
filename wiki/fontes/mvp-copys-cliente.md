---
tipo: fonte
arquivo: ingeridos/07-catalogo-de-copys-cliente.md
origem: catálogo de copys aprovadas do app do cliente; valem só os blocos Textos finais aprovados
criado: 2026-11-05
atualizado: 2026-11-05
---

# Catálogo de copys do app do cliente

Fonte única das copys aprovadas do app do cliente. O comportamento está em [[mvp-funcoes-e-telas]]. Os deltas estão em [[mvp-alteracoes-pos-congelamento]].

Vale para implementação somente o bloco "Textos finais aprovados" de cada fluxo. Cada bloco substitui a tabela histórica do mesmo fluxo. As tabelas "Texto atual (literal)" são histórico da revisão e não são alvo. As marcas provisória, a revisar, definida e exemplo dessas tabelas foram superadas pelos blocos aprovados.

## Regras

A marca fala em primeira pessoa do plural e trata a pessoa por "você". O nome da marca só entra onde é o nome do app.

"Artista" e "Portfólio" levam inicial maiúscula. Na interface nunca entram "prestador" nem "profissional". O vocabulário fixo usa "Agendamento", "Região", "e-mail" com hífen e sem itálico, "Agendar", "Já tenho conta", "Denunciar Artista", "Falar com a gente" e "Tentar de novo". "Bairro" fica só como rótulo do campo de endereço. A aba de listagem se chama "Artistas". "Ver meus agendamentos" leva à Agenda.

Nada dentro da tela leva ponto final: título, aviso, botão, corpo de modal, erro, push, toast e mensagem do robô. Ponto final fica na Central de Ajuda, em tutoriais, comunicados, e-mail transacional, marketing fora do app e texto jurídico. Exclamação, interrogação e reticências só quando o tom pede.

O botão diz a ação. O destaque é o caminho seguro ou o avanço do fluxo, nunca a ação destrutiva.

Data, hora, duração e moeda têm formato fixo: dia por extenso com o dia da semana em minúscula, hora no padrão "15h" ou "15h30", tempo no padrão "10 s" ou "5 min", valor sempre com "R$".

Erro não culpa a pessoa: a frase assume a falha do sistema, explica e oferece uma saída. Os tons são Celebrativo no sucesso, Instrutivo no welcome, no cadastro e nos primeiros acessos, Operacional em menus, listas, configurações e cartões, e Tranquilizador no erro.

Frase inteira não vai em caixa alta. Siglas reconhecidas ficam em maiúsculas. Negrito cobre no máximo cinco palavras por parágrafo. Itálico só em estrangeirismo. Frase que precisa de parênteses ou aspas para se explicar é reescrita.

A mensagem de marca "Sempre tem um Artista perto de você" permanece, mesmo sem refletir a cobertura do MVP.

"Ofício" é termo interno e não aparece na interface, nos dois apps. Na tela, o agrupamento de Artistas por tipo de trabalho se chama "categoria".

A revisão é faseada por fluxo, com qualidade acima de velocidade. O texto aprovado fica neste catálogo. A lista de funções aponta para o bloco aprovado.

## Fluxos aprovados

Os 16 fluxos estão aprovados:

- Welcome (slides 1-5)
- Cadastro (chat do bot)
- Login e recuperação de senha
- Sessão
- Home
- Listagem de artistas, filtros e "Pesquisar"
- Perfil do artista visto pelo cliente
- Agendamento em chat (robô)
- Agenda e cartão de agendamento
- Avaliação
- Notificações
- Denúncia e bloqueio
- Perfil / engrenagem
- Excluir conta
- Estados gerais
- SMS de convite
