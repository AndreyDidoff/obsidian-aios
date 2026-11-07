> **Aviso de Versionamento (Extração via IA - Claude):** Este documento foi gerado a partir da consolidação do histórico e representa um snapshot do projeto no momento de sua extração. O conteúdo aqui presente pode divergir (estando mais atualizado ou defasado) em relação à base de conhecimento principal. Recomenda-se a validação das diretrizes arquiteturais caso haja conflito com o repositório oficial.

# 11 · Escrita e ortografia

Tags: #lyraui #ortografia #pontuacao #estilos-de-escrita #ux-writing

---

## 1. Status

- **LyraUI (alvo, em discovery, não implementada no código):** estas regras definem como os textos das interfaces devem ser escritos quando a LyraUI entrar no app.
- **WeCareU (app em produção):** as regras valem para os "projetos WeCareU" (apps, e-mails, documentação). Os textos já em produção podem não seguir tudo isto.
- A voz e os tons que orientam o conteúdo estão em [[10-voz-e-tons]]. Contexto em [[01-visao-geral-lyraui]].

---

## 2. Pontuação: regra base

**Nas interfaces, não usar ponto final (.)**, mesmo em frases mais longas.

### Por que

| Motivo | Explicação |
|---|---|
| Consistência com a interface | A maioria das mensagens nas telas é curta, imperativa ou descritiva. Todas sem ponto final cria um padrão único no app do Cliente e na ferramenta do Artista |
| Redução de ruído (estética) | Títulos e avisos com ponto, ao lado de botões, tags e cards sem ponto, quebram o ritmo visual |
| Foco na ação (eficiência) | Telas são de interação rápida, não de leitura contemplativa. Comandos diretos não precisam ser "finalizados" |
| Leitura dinâmica | O Artista no `ui-worker` escaneia a interface em segundos. Sem ponto, não há pausas desnecessárias no fluxo do olhar |
| Alinhamento digital | A ausência do ponto soa menos engessada e mais acolhedora (Care) |

### Pontuações finais permitidas

- Ponto de exclamação (`!`), interrogação (`?`) e reticências (`…`).
- Usar **apenas** quando absolutamente necessário para o tom correto: uma pergunta à pessoa usuária ou a comemoração de um sucesso.

Exemplo de comando direto do guia: `Confirmar agendamento` (sem ponto).

---

## 3. Quando manter o ponto final

Exigido em **textos explicativos mais densos**, com várias frases formando parágrafos.

| Contexto | Observação |
|---|---|
| Central de Ajuda e Tutoriais | Respostas longas que explicam processos (configurar a agenda de serviços, resgatar pontos) |
| Textos de Atualizações | Comunicados na plataforma sobre novas funcionalidades, para Empresas ou Artistas |
| E-mails transacionais | Mensagens fora do app (confirmação de agendamento, redefinição de senha) |
| Comunicações de marketing | Redes sociais, e-mails promocionais, argumentos para marcas parceiras |
| Documentações internas | Guias do `web-wiki`, manuais do `web-admin` e o próprio Design System no ZeroHeight |
| Textos jurídicos e LGPD | Termos de Uso, Políticas de Privacidade e modais de consentimento. A pontuação tradicional é exigência de segurança legal para a WeCareU |

**Exceção importante:** banner de marketing que roda **dentro do aplicativo** segue a regra da interface (sem ponto final).

Regra prática: se está **dentro da tela do app**, sem ponto. Se é **texto corrido fora da tela** ou longo, com ponto.

---

## 4. Estilos de escrita

### Itálico

- Usar **exclusivamente** para termos estrangeiros ainda não incorporados ao vocabulário técnico brasileiro.
- Se o termo já faz parte do dialeto técnico (e-mail, online, dashboard), **não** usar itálico.
- Exemplo de uso correto: expressões latinas ou estrangeiras muito específicas, como *status quo*.

### Negrito

- Usar para destacar informações essenciais que exigem atenção imediata. É a ferramenta principal para guiar o olhar.
- Aplicar em trechos curtos, destacando o "o quê" de uma tarefa.
- **Limite de 1 a 5 palavras em negrito por parágrafo.**
- Em listas e passo a passo, aplicar negrito **apenas no termo-chave** de cada item.

### Formatações a evitar

| Evitar | Regra | Alternativa |
|---|---|---|
| **Aspas e parênteses** | Se precisa de parênteses para explicar, a frase precisa ser reescrita para ser mais assertiva | Reescrever a frase ou usar negrito para destaque |
| **Sublinhado** | Nunca sublinhar texto que não seja link clicável. O sublinhado é gatilho de navegação | Negrito |
| **Caixa alta** | Não escrever frases inteiras em maiúsculas: reduz a velocidade de leitura e cria tom autoritário, em desacordo com a persona acolhedora | Caixa normal |
| **Múltiplas formatações** | Nunca combinar negrito e itálico na mesma sequência de caracteres | Escolher uma única ênfase |

**Exceção da caixa alta:** siglas e abreviações técnicas reconhecidas, como FAQ, CPF, LGPD, API e CLI.

---

## 5. Aplicação rápida: antes e depois

Exemplos montados a partir das regras. Não são exemplos oficiais do guia.

| Contexto | Evitar | Preferir |
|---|---|---|
| Botão | `Confirmar agendamento.` | `Confirmar agendamento` |
| Aviso curto na tela | `Seu agendamento foi confirmado.` | `Seu agendamento foi confirmado` |
| Celebração | `Parabéns, você alcançou a meta.` | `Parabéns, você alcançou a meta!` |
| Pergunta | `Deseja cancelar o agendamento.` | `Deseja cancelar o agendamento?` |
| Ênfase | `ATENÇÃO: revise seus dados` | `Revise seus dados` com **revise** em negrito, se necessário |
| Explicação | `Cancele (se preferir) até 24h antes` | Reescrever sem parênteses |
| E-mail transacional | Frases soltas sem ponto | Parágrafos com ponto final |

---

## 6. Divergências e pontos em aberto

- **Os próprios documentos-fonte** usam parênteses, aspas e ponto final em textos longos. Isso é coerente com a exceção de documentação interna, mas deve ser considerado ao copiar trechos deles para telas.
- **Limite de negrito** (1 a 5 palavras por parágrafo): vale para texto corrido. Não está definido como tratar títulos e rótulos de componentes.
- **Reticências:** a fonte cita `…` como caractere. Definir se o padrão é o caractere único ou três pontos.
- **Banners dentro do app:** a regra de interface prevalece sobre a de marketing. Garantir que a revisão de marketing conheça a exceção.
- **Textos de erro, vazios e de confirmação:** não há catálogo de exemplos por tom. Ver [[10-voz-e-tons]].

---

## Links

Anterior: [[10-voz-e-tons]] · Próximos: [[12-principios-de-design]] · [[13-glossario]]
