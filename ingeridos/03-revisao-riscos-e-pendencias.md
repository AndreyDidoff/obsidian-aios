# WeCareU — Revisão crítica, pendências e regras de trabalho

## 1. Pontos críticos levantados na revisão do documento de MVP (por impacto)

1. **R3 x R4 deixam o prestador sem endereço do próximo cliente.** O endereço só aparece após o check-out anterior, mas o prestador precisa ir ao local durante o deslocamento. Recomendação: liberar o endereço do próximo cliente no mesmo dia, a partir de um intervalo antes do horário (tempo de deslocamento configurado). Além disso, o prestador que esquece o check-out trava o próprio dia: o botão "encerrar atendimento" (P8) entra no MVP. **[DEFINIDO e confirmado pelo dono: regra de 1 dia antes; o prestador vê todos os clientes do dia para planejar rotas]**
2. **Contradição na seção 1.3.** Separar "cliente do app" de "cliente trazido pelo prestador" foi dito como não métrica, mas a H3 só é verificável com essa separação. Recomendação: registrar a origem do cliente (convite do prestador, indicação, orgânico) como dado e usá-la só na H3.
3. **Falta gatilho para o marketing de clientes.** O critério de saída do Release 1 depende de H3, que depende de um marketing sem condição de início. Recomendação: dividir em 1a (oferta, H1 e H2) e 1b (demanda, H3), com o gatilho de 1b por prestadores aprovados e com agenda ativa, por bairro e ofício (limiares [PENDENTE]). "Todos os ofícios" dilui a liquidez, que é medida por bairro e ofício: cadastro aberto, mas marketing de clientes com 1 ou 2 ofícios âncora e poucas zonas.
4. **Prestador exposto no MVP.** Reserva instantânea sem aceite, cliente desconhecido, cancelamento sem prazo e sem reputação do cliente. Mitigação: prestador vê nome e tempo de conta do cliente no perfil; cancelamento com motivo e contestação (H2.3 da spec). A penalidade da spec continua valendo.
5. **Convite por SMS sem teto.** Custo da empresa, sem limite: prestador pode disparar para qualquer número. Recomendação: limite diário por prestador. A caixa "o cliente autorizou" é autodeclaração; validade é ponto para o advogado.
6. Aprovação manual não escala para cadastro aberto em qualquer cidade. Recomendação: aprovar só São Paulo no início; demais cidades em lista de espera, com mensagem clara no cadastro.
7. Risco 16 (equipe, orçamento e capacidade de entrega) sem resposta.

## 2. Pendências com o dono do produto

- Definir a data de `LANCAMENTO_PUBLICO_EM` de São Paulo (= quando o marketing de clientes liga).
- Confirmar D-00, D-04, D-05 (avaliação mínima, nota bayesiana, exibição) para virarem [DEFINIDO].
- Aprovações e denúncias: Andrey e Bruno no início; responsável dedicado no futuro.
- Parecer do advogado: termos, LGPD, convite SMS/WhatsApp, caixa de autorização, relação autônomo x plataforma, publicidade patrocinada (CDC, art. 36).

## 3. Próximas etapas do processo

- Etapa 2 (discovery em rodadas de até 5 perguntas, cada uma com resposta recomendada): lacunas ainda abertas — segmento inicial e liquidez (quantos prestadores por bairro/ofício), jornada de suporte e mediação, comunicação (push/SMS/WhatsApp), instrumentação.
- Etapa 6: gerar o documento final consolidado (tese, escopo, inventário, releases, métricas, riscos, decisões, mudanças na spec) quando as decisões críticas estiverem fechadas.

## 4. Regras de trabalho com o dono (Andrey)

- Respostas diretas e objetivas, sem introdução, bajulação ou enrolação.
- Corrigir diretamente quando estiver errado; apontar riscos antes de continuar.
- Não repetir contexto estabelecido. Não reabrir [DEFINIDO] sem argumento.
- Ao dar opções, indicar a melhor e por quê.
- Separar fato (dito pelo dono), recomendação (do consultor) e hipótese (a validar). Sem números de mercado inventados.
- Sem datas e sem estimativas de prazo; esforço só em P/M/G se for pedido.
- Avisar ao final, em linha separada: "💾 Hora de salvar contexto — [motivo]" só quando uma decisão for fechada, etapa concluída, documento definido ou houver definições acumuladas cuja perda causaria retrabalho.

## 5. Equipe e restrições [DEFINIDO pelo dono]

- Equipe: 2 devs. Andrey (frontend, Expo/React) e Bruno (backend, .NET), com apoio de IA. Sem outras pessoas por enquanto.
- Aprovações de prestadores e mediação: feitas por eles no início; alguém dedicado no futuro.
- Orçamento: sem valores definidos; o projeto está em fase de desenvolvimento.
- Exigência: construir de forma profissional, como uma empresa de grande porte faria.
- Implicações recomendadas: backend .NET e dois apps Expo precisam de contrato de API versionado, ambientes separados (dev/homologação/produção), CI com testes automáticos e observabilidade desde o Release 1; o painel de administração mínimo e o convite por SMS (com teto diário) são os itens de maior risco de sobrecarga operacional.

## 6. Rodada 2 de discovery (decisões do dono)

- Foco atual: definir o MVP do app. Marketing fica fora desta fase.
- Só aparecem ao cliente ofícios e serviços com pelo menos 1 prestador aprovado na região dele. [DEFINIDO]
- Aprovação de prestador: nome real, foto adequada e telefone verificado por SMS. Sem indicação de outro prestador (talvez no futuro, como gamificação). [DEFINIDO]
- Verificação por SMS (OTP) entra no MVP. [DEFINIDO]
- Reenvio de push quando o prestador não visualiza o agendamento. [DEFINIDO] Prazo e número de reenvios: [PENDENTE].
- Medição/eventos: dono pediu explicação; ver resposta no chat. Lista de eventos [PENDENTE].
- Princípio de arquitetura: regra de negócio só no backend; frontend só apresentação e dados de uso. [DEFINIDO]
- Analytics de uso do app (mapas de calor, funil, abandono) fora do MVP, em release posterior. [DEFINIDO]
- Lista de fatos de negócio a gravar no backend: [PENDENTE], fechar antes do Release 1.
- P1, P3, P4, P6, P7, P8, P9, P10, P11, P12 fechadas [DEFINIDO] (detalhe em R19 do arquivo 01). Filtro de horário na busca: nunca. Encerramento automático à meia-noite no lugar do botão manual; estado final [RECOMENDADO] "concluído, encerrado automaticamente".
- Abertas: ordem dos releases (analytics como Release 2?), prazo de reenvio de push, limiares de métricas, P13 (pós-MVP), data de lançamento em São Paulo, parecer do advogado.
- [DEFINIDO] Encerramento à meia-noite = fechado às 00:00:00, igual ao manual, nunca tratado como ausência. Penalização/avaliação futura.
- [DEFINIDO] Push: um único reenvio, prazo fixo. Configurável só no futuro.
- Ordem dos releases após o MVP: fora de foco agora; será discutida depois.
