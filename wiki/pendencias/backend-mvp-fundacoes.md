---
tipo: pendencia
superficie: backend
criado: 2026-11-05
atualizado: 2026-11-05
fontes: ["[[mvp-funcoes-e-telas]]", "[[mvp]]", "[[mvp-final]]", "[[spec-busca-e-ranqueamento]]"]
---

# Ajustes de backend: fundações

Esta página lista o que o backend precisa mudar nas fundações para chegar ao alvo do MVP. Não é a especificação do produto. Criptografia, Swagger e o disparador antigo de e-mail continuam em [[mvp]].

### API versionada

**Alvo:** A API tem contrato versionado. Cada erro de negócio sai com código e mensagem prontos para o app. (M14-F01, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Versionar o contrato da API e devolver cada erro de negócio com código e mensagem prontos para o app.

### Fatos de negócio

**Alvo:** [RECOMENDADO] A lista de fatos de negócio que o backend grava, na seção 6 de [[mvp-final]], não entra como decisão. O cliente não fechou o esquema. (M14-F02, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Tratar como recomendação o registro dos fatos de negócio da seção 6 de [[mvp-final]]. O cliente não fechou o esquema; a lista não entra como decisão.

### Base de bairros

**Alvo:** A base de bairros vem de CEP e IBGE, na hierarquia cidade, zona e bairro. (M14-F03, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Montar a base de bairros a partir de CEP e IBGE, na hierarquia cidade, zona e bairro.

### LANCAMENTO_PUBLICO_EM só para a tag Novo

**Alvo:** `LANCAMENTO_PUBLICO_EM` controla somente a tag "Novo". Não esconde nem libera Artista: o Artista aparece na listagem assim que é aprovado ou liberado, porque quanto mais Artistas na listagem, melhor. (M14-F04, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Usar `LANCAMENTO_PUBLICO_EM` somente para a tag "Novo". O Artista aprovado ou liberado entra na listagem sem depender dessa data.

### SMS de convite sem código no cliente

**Alvo:** Há provedor de SMS para o convite. No cliente não há código SMS no MVP. O código do artista fica para o detalhe daquele lado. (M14-F05, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Integrar o provedor de SMS do convite. No app do cliente não há código SMS no MVP. Deixar o código do artista para o detalhe daquele lado.

### Provedor de push

**Alvo:** O backend tem um provedor de push. (M14-F06, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Integrar um provedor de push.

### Ranqueamento da spec

**Alvo:** As regras de ranqueamento de [[spec-busca-e-ranqueamento]], spec v0.3.1, continuam: faixas, desempate e sorteio estável na sessão. O cliente não reescreveu a fórmula. (M14-F07, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Aplicar no backend as regras de ranqueamento da spec v0.3.1 em [[spec-busca-e-ranqueamento]]: faixas, desempate e sorteio estável na sessão. O cliente não reescreveu a fórmula.

### Configurações CFG

**Alvo:** As configurações `CFG.*` da spec usadas no MVP ficam no backend. (M14-F08, [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Guardar no backend as configurações `CFG.*` da spec usadas no MVP.

### Versão mínima

**Alvo:** Toda requisição traz a versão do app e a plataforma. A versão mínima é mantida por plataforma. O erro dessa versão é específico e tem prioridade sobre as demais validações. ("Versão mínima do app", [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Exigir versão e plataforma em toda requisição, manter a versão mínima por plataforma e devolver o erro específico com prioridade sobre as demais validações.

### Manutenção

**Alvo:** A equipe liga e desliga a manutenção por configuração. O erro de manutenção é específico e tem prioridade. ("Fora do ar e manutenção", [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Permitir que a equipe ligue e desligue a manutenção por configuração e devolver o erro específico com prioridade.

### Hora do servidor

**Alvo:** [RECOMENDADO] As respostas com prazo devolvem a hora do servidor, a confirmar. As regras de horário são decididas no backend. ("Hora do servidor como referência", [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Como recomendação a confirmar, devolver a hora do servidor nas respostas com prazo. As regras de horário ficam decididas no backend.

### Tempos de carregamento e timeout

**Alvo:** [RECOMENDADO] Os tempos de carregamento e de timeout ficam com o Bruno e não bloqueiam o app. O app usa 30 segundos hoje, para qualquer ação e para o skeleton. Os valores exatos fecham depois, com redução na migração para a nuvem. ("Falhas em ações e padrão de mensagens"; "Carregamento inicial das telas (skeleton)", [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Como recomendação, fechar com o Bruno os tempos de carregamento e de timeout, sem bloquear o app. O app usa 30 segundos hoje, para qualquer ação e para o skeleton. Prever redução desses valores na migração para a nuvem.

### Link curto do SMS

**Alvo:** O SMS de convite leva um único link curto que redireciona para a loja certa, iOS ou Android, sem página de aterrissagem e sem cruzar dados. O Bruno escolhe o encurtador e mede o custo real por segmento. ("Convite ao cliente pela reserva manual do artista", [[mvp-funcoes-e-telas]])

**Hoje:** o retrato lido não descreve este comportamento.

**Ajuste:** O retrato não mostra esta regra. Enviar no SMS de convite um único link curto que redireciona para a loja certa (iOS ou Android), sem página de aterrissagem e sem cruzar dados. Escolher o encurtador e medir o custo real por segmento.
