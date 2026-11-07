---
tipo: fonte
arquivo: "ingeridos/Espera e carregamento.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório library-design-system; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-21
atualizado: 2026-10-21
aliases: ["Espera e carregamento"]
---

# Espera e carregamento

Volta para [[panorama-do-design-system]]. A peça pronta para quando uma tela precisar esperar. Não é o carregamento de uma tela específica do app.

**Pé:** Pronto. `@wecareu/loading` **0.4.4**. Demonstração no navegador. Teste no celular.

## O que a pessoa vê

Os dois ao mesmo tempo: uma cortina por cima da tela inteira e, no centro, a animação de pontos de [[vocabulario-visual]] (`dots`). Pontos brancos, grandes, que começam sozinhos e repetem. No claro, véu preto pela metade. No escuro, o mesmo preto, mais fechado. Ver [[identidade-visual]]. Não há frase, título nem botão de cancelar.

Enquanto a cortina está no ar, o toque fica nela. O que está por baixo não recebe o toque. Celular e navegador mostram a mesma espera.

## Como liga

O guarda-chuva precisa estar por cima das telas. Uma tela de fora não consegue ligar a espera. Começa desligada. Quem mostrou é que precisa pedir para esconder. Pedir para mostrar de novo não apaga.

A demonstração tem um botão que liga a espera e ela se apaga sozinha depois de três segundos. O teste confirma que o conteúdo continua lá, que a cortina aparece, e que uma tela fora do guarda-chuva não controla a espera. Lugares e aviso, as outras animações do vocabulário, não entram aqui.

Ver [[kit-visual]].
