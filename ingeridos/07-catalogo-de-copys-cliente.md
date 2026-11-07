# WeCareU — Catálogo de copys do app do cliente (C)

Fonte única das copys aprovadas do app do cliente. O `05-lista-funcoes-e-telas.md` descreve o comportamento e aponta para os blocos "Textos finais aprovados" deste arquivo; o `06` registra as divergências em relação aos congelados. **Valem para implementação somente os blocos "Textos finais aprovados"**; as tabelas "Texto atual (literal)" de cada fluxo são histórico da revisão (textos copiados do `05` antes da revisão, com os problemas encontrados).

**Legenda da coluna "Marca" (tabelas históricas):**
- **provisória**: o `05` marca a copy como provisória, rascunho, proposta ou "texto em revisão de copy".
- **a revisar**: o `05` diz "a revisar" / "cópia a revisar" / "copy a revisar".
- **definida**: sem marca de provisória no trecho, na época da revisão. Todas essas marcas foram superadas pelos blocos "Textos finais aprovados" (16 fluxos aprovados).
- **exemplo**: o `05` apresenta o texto como "ex." / "do tipo" (indicativo, não final).

**Legenda da coluna "Tom":** Celebrativo (sucesso), Instrutivo (welcome/cadastro/primeiros acessos), Operacional (menus/listas/configurações/cartões), Tranquilizador (erro/falha do sistema com saída).

"Problemas detectados": só problemas objetivos; "—" quando nenhum. Violações das regras aprovadas anotadas com `[R1]`…`[R9]`.

---

## Regras de copy aprovadas

1. Voz única e vários tons. A marca fala em primeira pessoa do plural ("Encontramos 5 Artistas perto de você", nunca "A WeCareU encontrou"); tratamento "você" para a pessoa, imperativo de "você". Nome da marca só onde é o nome do app.
2. "Artista" e "Portfólio" com inicial maiúscula em todo o app. Nunca "prestador"/"profissional" na interface. "Região" (nunca "zona"; "bairro" só como rótulo do campo do endereço postal digitado pelo cliente, onde continua "Bairro"). "Agendamento" (nunca reserva). "e-mail" com hífen e sem itálico. Vocabulário fixo: "Agendar", "Já tenho conta", "Denunciar Artista", "Falar com a gente" (suporte), "Tentar de novo". "Listagem" vira "Artistas" (nome da aba). "Ver meus agendamentos" leva à Agenda.
3. Sem ponto final em nada dentro da tela (título, aviso, botão, corpo de modal, erro, push, toast, mensagem do robô). Ponto final só em Central de Ajuda, tutoriais, comunicados, e-mail transacional, marketing fora do app e texto jurídico. Exclamação, interrogação e reticências só quando o tom pede (pergunta ou comemoração de sucesso).
4. Botão diz a ação ("Confirmar agendamento"). O botão de destaque é sempre o caminho seguro ou o avanço do fluxo, nunca a ação destrutiva (ex.: em "Sair da conta" o destaque é "Cancelar" e "Sair" fica em texto; idem "Excluir minha conta").
5. Formatos: data "25 de maio, quarta" (minúscula); hora "15h" ou "15h30"; tempo "10 s", "60 s", "5 min"; moeda sempre com "R$" ("R$ 10 a R$ 150").
6. Erro nunca culpa a pessoa: assume a falha do sistema, explica com transparência e oferece saída (tom Tranquilizador). Celebrativo: sucesso (agendamento confirmado, avaliação enviada). Instrutivo: welcome, cadastro, primeiros acessos. Operacional: menus, configurações, listas, cartões.
7. Sem caixa alta em frase inteira; siglas reconhecidas em maiúsculas (CPF, FAQ, LGPD); negrito no máximo 5 palavras por parágrafo; sem itálico exceto estrangeirismo; se a frase precisou de parênteses ou aspas para se explicar, reescrever.
8. A frase "Sempre tem um Artista perto de você" é válida e deve ser mantida (é a mensagem que a empresa quer), mesmo não refletindo a realidade do MVP.
9. **"Ofício" é termo interno, nunca aparece na interface (nos dois apps)**, como "listagem" (decisão do dono: pessoas com menos estudo não entendem a palavra). Na tela, o agrupamento de Artistas por tipo de trabalho se chama **"categoria"** (ex.: Cabeleireiro, Manicure); "profissional" continua proibido pela regra 2. Vale para qualquer texto de qualquer fluxo, inclusive o bloco "ofícios e serviços" do perfil do Artista (fluxo 7).
10. Processo: revisão faseada por fluxo, qualidade acima de velocidade; textos aprovados ficam só no 07; o 05 aponta para o bloco aprovado ("texto aprovado em `07` (bloco)").

## Status de aprovação por fluxo

| # | Fluxo | Status |
|---|---|---|
| 1 | Welcome (slides 1-5) | **Aprovado** (textos finais no bloco "Textos finais aprovados" da seção 1) |
| 2 | Cadastro (chat do bot) | Parte A **aprovada** (bloco "Textos finais aprovados do Cadastro, parte A"); parte B (foto, confirmação de e-mail) **aprovada**; fluxo 2 **Aprovado** |
| 3 | Login e recuperação de senha | **Aprovado** (bloco "Textos finais aprovados do Login e recuperação de senha") |
| 4 | Sessão | **Aprovado** (bloco "Textos finais aprovados da Sessão") |
| 5 | Home | **Aprovado** |
| 6 | Listagem de artistas, filtros e "Pesquisar" | Partes A, B e C **aprovadas** (fluxo fechado) |
| 7 | Perfil do artista visto pelo cliente | **Aprovado** (parte A; textos do bloqueio no bloco "Textos finais aprovados da Denúncia", C-12-15, C-12-15B e C-12-15C) |
| 8 | Agendamento em chat (robô) | Aprovado |
| 9 | Agenda e cartão de agendamento | Aprovado |
| 10 | Avaliação | Aprovado |
| 11 | Notificações | Aprovado |
| 12 | Denúncia e bloqueio | Aprovado |
| 13 | Perfil / engrenagem | Aprovado |
| 14 | Excluir conta | Aprovado |
| 15 | Estados gerais | Aprovado |
| 16 | SMS de convite | Aprovado |

---


## 1. Welcome (slides 1-5)

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-01-01 | Todos os slides (exceto o último), botão | "Próximo" | definida | Operacional | Welcome do cliente: estrutura [DEFINIDO] | — |
| C-01-02 | Último slide, botão | "Ver artistas" | definida | Operacional | Welcome do cliente: estrutura [DEFINIDO] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-01-03 | Abaixo do carrossel, link fixo | "Já tenho conta" | definida | Operacional | Welcome do cliente: estrutura [DEFINIDO] | Varia com "Já tenho conta" (tela de bloqueio, C-06-C07) para a mesma ação. |
| C-01-04 | Slide 1, título | "Aqui, quem atende você é um artista" | provisória | Instrutivo | Welcome: slides de apresentação [DEFINIDO, copy provisória] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-01-05 | Slide 1, subtítulo | "Profissionais (artistas) prontos para transformar sua vida e seu bem-estar" | provisória | Instrutivo | Welcome: slides de apresentação [DEFINIDO, copy provisória] | Sem ponto final, enquanto os subtítulos dos slides 2, 3 e 4 têm ponto. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R2] "prestador"/"profissional" proibido na interface (usar "Artista") |
| C-01-06 | Slide 2, título | "Agendar é fácil" | provisória | Instrutivo | Welcome: slides de apresentação [DEFINIDO, copy provisória] | — |
| C-01-07 | Slide 2, subtítulo | "Escolha o artista, o serviço e o horário. Ele vai até você." | provisória | Instrutivo | Welcome: slides de apresentação [DEFINIDO, copy provisória] | "Ele" presume artista do gênero masculino (a denúncia usa "assediada(o)": tratamento de gênero inconsistente). [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-01-08 | Slide 3, título | "Artistas em quem você pode confiar" | provisória | Instrutivo | Welcome: slides de apresentação [DEFINIDO, copy provisória] | — |
| C-01-09 | Slide 3, subtítulo | "Cada artista passa por aprovação antes de atender na WeCareU." | provisória | Instrutivo | Welcome: slides de apresentação [DEFINIDO, copy provisória] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-01-10 | Slide 4 (localização), título | "Vamos até você!" | provisória | Instrutivo | Welcome: slide 4 (localização) [DEFINIDO, copy provisória] | "Vamos" atribui o deslocamento à WeCareU; no slide 2 quem vai é o artista ("Ele vai até você"). |
| C-01-11 | Slide 4, subtítulo | "Usamos sua localização para ajudar você a encontrar um artista perto de você." | provisória | Instrutivo | Welcome: slide 4 (localização) [DEFINIDO, copy provisória] | Repetição "você ... você". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-01-12 | Slide 5 (endereço), título | "Confirme seu endereço" | provisória | Instrutivo | Welcome: slide 5 (endereço) [DEFINIDO, copy provisória] | — |
| C-01-13 | Slide 5, rótulos de campo | CEP, rua, número, bairro, cidade, estado (UF), complemento e nome do local | provisória (nomes de campo, não copy final) | Operacional | Welcome: slide 5 (endereço) [DEFINIDO, copy provisória] | Capitalização dos rótulos não definida. [R2] "bairro"/"zona" (usar "Região") |
| C-01-14 | Slide 5, sugestão do campo nome do local | "Casa" (exemplos: "Casa", "Trabalho") | provisória | Operacional | Welcome: slide 5 (endereço) [DEFINIDO, copy provisória] | — |
| C-01-15 | Slide 5, observação ao lado do número 0 (também em "Meus endereços" e na cópia do endereço do agendamento) | "(ver complemento)" | a revisar | Operacional | Welcome: slide 5 (endereço) [DEFINIDO, copy provisória] | Tela citada como "Meus endereços"; no menu chama-se "Gerenciar Endereços". |
| C-01-16 | Slide 5, erro de CEP inválido ou não encontrado | SEM TEXTO DEFINIDO ("mensagem no campo (copy a revisar)") | a revisar | Tranquilizador | Welcome: slide 5 (endereço) [DEFINIDO, copy provisória] | Falta o texto. |

### Textos finais aprovados do Welcome (substituem os da tabela acima; tom Instrutivo)

| Id | Onde aparece | Texto final |
|---|---|---|
| C-01-01 | Botão dos slides 1 a 4 | Próximo |
| C-01-02 | Botão do último slide | Ver Artistas |
| C-01-03 | Link fixo abaixo do carrossel | Já tenho conta |
| C-01-04 | Slide 1, título | Aqui, quem atende você é um Artista |
| C-01-05 | Slide 1, subtítulo | Talentos que transformam seu visual e seu bem-estar |
| C-01-06 | Slide 2, título | Agendar é fácil |
| C-01-07 | Slide 2, subtítulo | Escolha o Artista, o serviço e o horário e receba o atendimento no endereço que você escolher |
| C-01-08 | Slide 3, título | Artistas em quem você pode confiar |
| C-01-09 | Slide 3, subtítulo | Todo Artista é aprovado por nós antes de começar a atender |
| C-01-10 | Slide 4, título | Encontre Artistas perto de você |
| C-01-11 | Slide 4, subtítulo | Usamos sua localização para mostrar quem atende na sua região |
| C-01-12 | Slide 5, título | Onde você quer ser atendido? |
| C-01-13 | Slide 5, rótulos dos campos | CEP, Rua, Número, Bairro, Cidade, Estado, Complemento, Nome do endereço |
| C-01-14 | Slide 5, sugestão do nome do local | Casa |
| C-01-15 | Aviso ao lado do número 0 (slide 5, Meus endereços e cópia do endereço do agendamento) | Ver complemento |
| C-01-16 | Slide 5, erro de CEP inválido ou não encontrado | Não encontramos esse CEP |

Observações: a aprovação do Artista é da pessoa, e o texto C-01-09 deixa isso explícito ("Todo Artista é aprovado por nós"). Nos itens C-01-07 e C-01-11 não há ponto final, conforme a regra 3.

## 2. Cadastro (chat do bot)

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-02-01 | Tela de login, botão para ir ao cadastro | "Cadastrar" | provisória | Operacional | Cadastro do cliente: formato e dados [DEFINIDO] | — |
| C-02-02 | Erro acima do campo de mensagem (exemplo) | "CPF inválido" | exemplo | Tranquilizador | Cadastro do cliente: formato e dados [DEFINIDO] | Sem ponto final; outras mensagens de erro têm ponto. |
| C-02-03 | Perguntas do bot para cada dado (CPF, nome completo, celular, sexo, nome social, data de nascimento, foto, endereço, complemento, nome do endereço, e-mail, senha, repetir senha) | SEM TEXTO DEFINIDO | — | Instrutivo | Cadastro do cliente: formato e dados [DEFINIDO] | Faltam todas as perguntas do bot, a saudação inicial e a pergunta "quer cadastrar aquele endereço" (vindo do welcome). |
| C-02-04 | Botões do passo sexo | "Masculino", "Feminino", "Não binário", "Prefiro não dizer" | provisória | Operacional | Cadastro do cliente: formato e dados [DEFINIDO] | — |
| C-02-05 | Botão do passo nome social | "pular" | provisória | Operacional | Cadastro do cliente: formato e dados [DEFINIDO] | Em minúscula, enquanto os demais botões começam com maiúscula. |
| C-02-06 | Botões do passo foto | "Depois" e "Sim" | provisória | Operacional | Cadastro do cliente: formato e dados [DEFINIDO] | — |
| C-02-07 | Aviso do passo foto, título | "Importante!" | provisória | Instrutivo | Cadastro do cliente: foto [DEFINIDO, copy provisória] | — |
| C-02-08 | Aviso do passo foto, texto | "Antes de agendar, precisamos da sua foto. Ela ajuda o artista a te encontrar, te reconhecer e lembrar de você quando chegar no seu endereço." | provisória | Instrutivo | Cadastro do cliente: foto [DEFINIDO, copy provisória] | Mistura "te" e "você" na mesma frase; "chegar no" (regência culta: "chegar ao"). [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-02-09 | Modal "Enviar foto", título | "Enviar foto" | provisória | Operacional | Cadastro do cliente: foto [DEFINIDO, copy provisória] | — |
| C-02-10 | Modal "Enviar foto", texto | "Escolha a foto que o artista vai ver. Ela ajuda o artista a te encontrar, te reconhecer e lembrar de você no atendimento." | provisória | Instrutivo | Cadastro do cliente: foto [DEFINIDO, copy provisória] | Mistura "te"/"você"; repetição "o artista". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-02-11 | Modal "Enviar foto", dica | "Use uma foto do seu rosto, com boa luz." | provisória | Instrutivo | Cadastro do cliente: foto [DEFINIDO, copy provisória] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-02-12 | Modal "Enviar foto", botões | "Salvar" e "Cancelar" | provisória | Operacional | Cadastro do cliente: foto [DEFINIDO, copy provisória] | — |
| C-02-13 | Modal "Enviar foto", opções de origem | "Escolher da galeria" e "Tirar foto" | provisória | Operacional | 6. Permissão de câmera ou galeria na foto [DEFINIDO; copy provisória] | — |
| C-02-14 | Passo endereço, nome sugerido | "Casa" | provisória | Operacional | Cadastro do cliente: formato e dados [DEFINIDO] | — |
| C-02-15 | Passo senha, checklist de critérios | mínimo 8 caracteres, 1 número, 1 letra minúscula, 1 letra maiúscula, 1 símbolo (! @ # $ % * ( ) } { + = \| / ? \ -) | provisória (critério, não copy final) | Instrutivo | Cadastro do cliente: formato e dados [DEFINIDO] | Texto exato dos itens do checklist não definido. |
| C-02-16 | Passo aceite, caixa obrigatória com links | "Termos de Uso" e "Política de Privacidade" (frase da caixa: SEM TEXTO DEFINIDO) | provisória | Instrutivo | Cadastro do cliente: formato e dados [DEFINIDO] | Falta a frase da caixa de aceite. |
| C-02-17 | Erro de menor de 18 anos (no campo) | SEM TEXTO DEFINIDO ("copy na etapa de copys") | — | Tranquilizador | Cadastro do cliente: formato e dados [DEFINIDO] | Falta o texto. |
| C-02-18 | Modal CPF/e-mail já cadastrado, título | "Atenção!!" | provisória | Tranquilizador | Cadastro do cliente: formato e dados [DEFINIDO] | Pontuação dupla "!!". |
| C-02-19 | Modal CPF/e-mail já cadastrado, texto | "Vimos que esse CPF (ou e-mail) já foi cadastrado na WeCareU. Se está tentando entrar clique em entrar no botão abaixo." | provisória | Tranquilizador | Cadastro do cliente: formato e dados [DEFINIDO] | Falta vírgula após "entrar"; "clique em entrar no botão" redundante; "clique" (no app: "toque"); "(ou e-mail)" é marcação de spec, a versão real deve citar só um dos dois. [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) [R7] Parênteses para se explicar (reescrever sem parênteses) |
| C-02-20 | Modal CPF/e-mail já cadastrado, texto secundário | SEM TEXTO LITERAL (conteúdo: por questões de segurança só é possível cadastrar com um CPF (ou e-mail) que não foi usado na plataforma e, se achar que é um erro, entrar em contato com o suporte) | — | Tranquilizador | Cadastro do cliente: formato e dados [DEFINIDO] | O 05 só parafraseia; o texto precisa ser escrito. |
| C-02-21 | Modal CPF/e-mail já cadastrado, botões | "Entrar" (destaque) e "Tentar novamente" (texto) | provisória | Operacional | Cadastro do cliente: formato e dados [DEFINIDO] | "Tentar novamente" vs "Tentar de novo" em outras telas. [R2] "Tentar/Tente novamente" (vocabulário fixo: "Tentar de novo") |
| C-02-22 | Retomada do cadastro, cumprimento do bot ao reabrir | SEM TEXTO DEFINIDO | — | Instrutivo | Cadastro do cliente: retomada e conclusão [DEFINIDO] | Falta o texto. |
| C-02-23 | Conclusão, mensagem final de boas-vindas do bot | SEM TEXTO DEFINIDO | — | Celebrativo | Cadastro do cliente: retomada e conclusão [DEFINIDO] | Falta o texto. |
| C-02-24 | Modal de e-mail confirmado (link válido, logado) | SEM TEXTO DEFINIDO (mensagem de e-mail confirmado) + botão "OK" | provisória | Celebrativo | Confirmação de e-mail do cliente [DEFINIDO] | Falta o texto da mensagem. |
| C-02-25 | Modal de link expirado, botão | "Reenviar e-mail de confirmação" (texto da modal: SEM TEXTO DEFINIDO) | provisória | Tranquilizador | Confirmação de e-mail do cliente [DEFINIDO] | Falta o texto da modal. |
| C-02-26 | Home, aviso fixo de e-mail não confirmado | SEM TEXTO DEFINIDO + botão "Reenviar e-mail" | provisória | Tranquilizador | Confirmação de e-mail do cliente [DEFINIDO] | Falta o texto do aviso e do estado de espera de 60 s. |

### Textos finais aprovados do Cadastro, parte A (conversa do bot, erros de campo, modal "já cadastrado")
Substituem os da tabela acima. Tom Instrutivo na conversa, Celebrativo na conclusão, Tranquilizador nos erros e na modal.

**Conversa do bot, na ordem do fluxo**

| Id | Passo | Texto final |
|---|---|---|
| C-02-A01 | Saudação | Oba, que bom ter você aqui! Vamos fazer seu cadastro |
| C-02-A02 | CPF | Qual é o seu CPF? |
| C-02-A03 | Nome completo | Qual é o seu nome completo? |
| C-02-A04 | Celular | Qual é o seu celular com DDD? |
| C-02-A05 | Sexo | Como você se identifica? Botões: Masculino, Feminino, Não binário, Prefiro não dizer |
| C-02-A06 | Nome social | Você usa nome social? Se usar, é ele que os Artistas vão ver. Botão: Pular |
| C-02-A07 | Data de nascimento | Qual é a sua data de nascimento? |
| C-02-A08 | Endereço vindo do welcome | Quer usar este endereço para os seus atendimentos? (endereço mascarado). Botões: Sim, Usar outro |
| C-02-A09 | Endereço sem welcome ou "Usar outro": CEP | Qual é o CEP do endereço onde você quer ser atendido? |
| C-02-A10 | CEP encontrado | Encontramos Rua [nome], [região], [cidade], com o link "Alterar CEP" |
| C-02-A11 | CEP não encontrado | Não encontramos esse CEP |
| C-02-A12 | Rua, quando o CEP não a traz (vem antes do número) | Qual é a rua? |
| C-02-A13 | Bairro, quando o CEP não o traz (vem antes do número) | Qual é o bairro? |
| C-02-A14 | Número | Qual é o número? Botão: Sem número (salva 0; o complemento ganha o aviso "Ver complemento") |
| C-02-A15 | Complemento | Tem complemento? Por exemplo, apto 12 ou bloco B. Botão: Não tem |
| C-02-A16 | Nome do endereço | Que nome quer dar a este endereço? Por exemplo, Casa ou Trabalho |
| C-02-A17 | E-mail | Qual é o seu e-mail? Vamos usá-lo para você entrar na conta |
| C-02-A18 | Senha, pergunta | Crie uma senha para entrar na conta |
| C-02-A19 | Senha, lista de critérios (título e itens, marcados ao cumprir) | Sua senha precisa ter: Pelo menos 8 caracteres; Um número; Uma letra minúscula; Uma letra maiúscula; Um símbolo: ! @ # $ % * ( ) } { + = \| / ? \ - |
| C-02-A20 | Repetir senha | Digite a senha de novo para confirmar |
| C-02-A21 | Aceite (caixa obrigatória, na mesma mensagem da senha, sem passo separado) | Li e aceito os Termos de Uso e a Política de Privacidade (links para as duas telas). Botão: Continuar, habilitado só com a caixa marcada |
| C-02-A22 | Retomada | Que bom que você voltou, vamos continuar de onde parou |
| C-02-A23 | Conclusão | Boas-vindas à WeCareU! Você já pode começar a agendar seus Artistas preferidos |

**Erros de campo (Tranquilizador)**

| Id | Campo | Texto final |
|---|---|---|
| C-02-A24 | CPF | Confira o CPF digitado |
| C-02-A25 | Nome | Digite nome e sobrenome |
| C-02-A26 | Celular | Digite o celular com DDD |
| C-02-A27 | Data de nascimento inválida | Digite uma data válida |
| C-02-A28 | E-mail | Confira o e-mail digitado |
| C-02-A29 | Senha, critérios pendentes | Complete os critérios da senha |
| C-02-A30 | Senha, repetição diferente | As senhas precisam ser iguais |
| C-02-A31 | Menor de 18 anos | Só é possível se cadastrar com 18 anos ou mais, mas seus responsáveis podem agendar por você |

**Modal "já cadastrado" (Tranquilizador)**

| Id | Parte | Caso CPF | Caso e-mail |
|---|---|---|---|
| C-02-A32 | Título | Opa, você já tem uma conta | Opa, você já tem uma conta |
| C-02-A33 | Texto | Esse CPF já tem cadastro. Quer entrar? | Esse e-mail já tem cadastro. Quer entrar ou usar outro e-mail? |
| C-02-A34 | Texto secundário | Por segurança, cada CPF e cada e-mail só podem ter uma conta. Se acha que é um engano, fale com a gente (link para o WhatsApp do suporte) | igual |
| C-02-A35 | Botões | Entrar (destaque) e Tentar de novo | Entrar (destaque) e Usar outro e-mail |

**Regras de comportamento decorrentes (já no `05`):** no cadastro, "Depois" segue o fluxo sem nova insistência; a foto só é cobrada de novo ao agendar.
- O endereço do cadastro é coletado em campos separados (CEP como busca, rua, bairro, número, complemento, nome), salvos separadamente no backend; "Usar outro" e o cadastro sem welcome seguem o mesmo fluxo por CEP. Rua e bairro à mão só aparecem quando o CEP não os traz, e sempre antes do número.
- Sem marcar a caixa de aceite, o cliente não conclui o cadastro (botão Continuar desabilitado). A caixa fica na mesma mensagem da senha. Validar a formulação com o advogado.
- "Tentar de novo" na modal de CPF volta ao campo do CPF; "Usar outro e-mail" volta ao campo do e-mail.

### Textos finais aprovados do Cadastro, parte B (foto e confirmação de e-mail)
Todos aprovados. Tom Instrutivo na foto, Celebrativo no e-mail confirmado, Tranquilizador nos erros e Operacional no aviso da Home.

**Foto**

| Id | Onde aparece | Texto final |
|---|---|---|
| C-02-B01 | Mensagem do bot no passo da foto. O aviso fica **visível na mesma mensagem, acima dos botões**, antes de o cliente escolher "Depois" ou "Sim" | Título: Sua foto é necessária para agendar. Texto: Ela ajuda o Artista a reconhecer você quando chegar ao seu endereço. Pergunta: Quer enviar sua foto agora? Botões: Depois, Sim |
| C-02-B02 | **Só no momento de agendar**, para quem escolheu "Depois" no cadastro (no cadastro, "Depois" segue o fluxo sem insistir). Primeira mensagem do bot no chat de agendamento, sem opção "Depois" | Para agendar, precisamos da sua foto, ela ajuda o Artista a reconhecer você quando chegar ao seu endereço. Botão: Enviar foto |
| C-02-B03 | Modal "Enviar foto", título | Enviar foto |
| C-02-B04 | Modal "Enviar foto", texto | Escolha a foto que o Artista vai ver, ela ajuda a reconhecer você no atendimento |
| C-02-B05 | Modal "Enviar foto", dica | Use uma foto do seu rosto, com boa luz |
| C-02-B06 | Modal, origem da foto | Escolher da galeria; Tirar foto |
| C-02-B07 | Modal, **sem foto escolhida** | Área de envio com ícone e o texto "Toque para escolher uma foto". Botão "Salvar" desabilitado. Botão "Cancelar" ativo (volta à pergunta do bot, com "Depois" e "Sim") |
| C-02-B08 | Modal, **com foto escolhida** | Prévia da foto e o link "Trocar foto". Botão "Salvar" habilitado (destaque). Botão "Cancelar" ativo (descarta a foto escolhida) |
| C-02-B09 | Modal, foto inválida (formato ou tamanho não aceito), erro dentro da modal acima dos botões | Essa foto não pode ser usada, escolha outra |
| C-02-B10 | Modal, falha ao salvar (erro de rede ou servidor), erro dentro da modal acima dos botões; "Salvar" volta a habilitar | Não conseguimos salvar sua foto, tente de novo |
| C-02-B11 | Bot, depois de salvar a foto (Celebrativo) | Foto salva, vamos continuar |

**Confirmação de e-mail**

| Id | Onde aparece | Texto final |
|---|---|---|
| C-02-B12 | Modal e-mail confirmado | Título: E-mail confirmado. Texto: Pronto, seu e-mail está confirmado. Botão: OK |
| C-02-B13 | Modal link expirado | Título: Esse link expirou. Texto: Por segurança, esse link expirou, mas não se preocupe, você pode pedir de novo. Botão: Reenviar e-mail de confirmação |
| C-02-B14 | Aviso fixo na Home, sem o e-mail do cliente (quem quiser vê em Perfil, Configurações) | Confirme seu e-mail pelo link que enviamos. Botão: Reenviar e-mail |
| C-02-B15 | Toast de reenvio feito | Enviamos um novo e-mail, confira sua caixa de entrada |
| C-02-B16 | Botão durante o intervalo de 60 s | Reenviar em 45 s (contagem regressiva em segundos; botão desabilitado) |

**Regras de comportamento decorrentes (para o `05`):** quando o cliente confirma o e-mail, o aviso da Home, o botão de reenvio e a contagem de espera **somem por completo**. O aviso não exibe o e-mail do cliente.

## 3. Login e recuperação de senha

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-03-01 | Login, título | "Vamos entrar com sua conta:" | provisória | Instrutivo | Login e recuperação de senha do cliente [DEFINIDO] | Título termina em dois-pontos. |
| C-03-02 | Login, botões e links | "Entrar", "Esqueci minha senha", "Cadastrar", "Voltar" | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | Rótulos dos campos e-mail/senha sem texto escrito. |
| C-03-03 | Login, erro acima do campo | "E-mail ou senha inválidos" | a revisar (exemplo) | Tranquilizador | Login e recuperação de senha do cliente [DEFINIDO] | Sem ponto final, enquanto C-03-11 tem ponto. |
| C-03-04 | Recuperação passo 1, texto | "Poxa, que pena! Vou te enviar um email com um código para continuarmos. Para isso me informe seu e-mail cadastrado." | provisória | Instrutivo | Login e recuperação de senha do cliente [DEFINIDO] | "email" e "e-mail" na mesma frase; falta vírgula após "Para isso"; 1ª pessoa do singular ("Vou") vs plural no resto do app. [R1] 1ª pessoa do singular ("Vou"/"achei"); voz da marca é 1ª do plural [R2] mistura "email" e "e-mail" [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-03-05 | Recuperação passo 1, botões | "Enviar e-mail", "Cancelar", "Voltar" | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | — |
| C-03-06 | Recuperação passo 2, texto | "Se seu e-mail estiver em nosso sistema você receberá um código. Coloque ele abaixo:" | provisória | Instrutivo | Login e recuperação de senha do cliente [DEFINIDO] | Falta vírgula após "sistema"; "Coloque ele" (norma: "Digite-o"). |
| C-03-07 | Recuperação passo 2, erro e legenda | "Código inválido"; "Código válido por 5m00" | provisória | Tranquilizador | Login e recuperação de senha do cliente [DEFINIDO] | Formato "5m00" fora do padrão de tempo do app. Mensagem de bloqueio após 5 erros: SEM TEXTO DEFINIDO. [R5] Formato de tempo "5m00" (usar "5 min") |
| C-03-08 | Recuperação passo 2, botões | "Enviar código novamente", "Validar código", "Cancelar", "Voltar" | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | Contador dos 60 s até liberar o reenvio: SEM TEXTO DEFINIDO. |
| C-03-09 | Recuperação passo 3, título | "Vamos mudar sua senha:" | provisória | Instrutivo | Login e recuperação de senha do cliente [DEFINIDO] | Dois-pontos em título. |
| C-03-10 | Recuperação passo 3, botões | "Mudar Senha", "Cancelar", "Voltar" | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | "Mudar Senha" vs "Alterar Senha" (menu) para a mesma ação. |
| C-03-11 | Login, bloqueio após 5 senhas erradas | "Muitas tentativas. Tente novamente em alguns minutos." | provisória | Tranquilizador | Login e recuperação de senha do cliente [DEFINIDO] | [R2] "Tentar/Tente novamente" (vocabulário fixo: "Tentar de novo") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-03-12 | Modal de ativar biometria, título | "Entrar com biometria?" | provisória | Instrutivo | Login e recuperação de senha do cliente [DEFINIDO] | — |
| C-03-13 | Modal de ativar biometria, texto | "Use sua digital ou seu rosto para abrir a WeCareU mais rápido e com segurança, sem digitar a senha." | provisória | Instrutivo | Login e recuperação de senha do cliente [DEFINIDO] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-03-14 | Modal de ativar biometria, botões | "Ativar" (destaque) e "Agora não" (texto) | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | — |
| C-03-15 | Modal de desativar biometria, título | "Desativar a biometria?" | provisória | Tranquilizador | Login e recuperação de senha do cliente [DEFINIDO] | — |
| C-03-16 | Modal de desativar biometria, texto | "Com ela você entra mais rápido, não precisa lembrar da senha a cada acesso e mantém sua conta mais protegida se alguém pegar seu celular." | provisória | Tranquilizador | Login e recuperação de senha do cliente [DEFINIDO] | "não precisa lembrar da senha" promete mais que a regra: a biometria "não substitui o login" e a senha volta a ser exigida em vários casos (troca de senha, Sair, biometria alterada). [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-03-17 | Modal de desativar biometria, botões | "Manter ativada" (destaque) e "Desativar" (texto) | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | — |
| C-03-18 | Falha da biometria, opção | "Usar senha" | provisória | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | — |
| C-03-19 | Biometria alterada no aparelho, pedido para reativar após o login | SEM TEXTO DEFINIDO | — | Tranquilizador | Login e recuperação de senha do cliente [DEFINIDO] | Falta o texto. |

### Textos finais aprovados do Login e recuperação de senha
Todos aprovados. Sem ponto final dentro da tela. Substituem os textos da tabela do fluxo 3 acima.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-03-A01 | Login, título | Instrutivo | Vamos entrar na sua conta |
| C-03-A02 | Login, rótulos dos campos | Operacional | E-mail; Senha |
| C-03-A03 | Login, botões e links | Operacional | Entrar; Esqueci minha senha; Criar conta (substitui "Cadastrar", faz par com "Já tenho conta"); Voltar |
| C-03-A04 | Login, erro acima do campo (mensagem única, sem dizer qual dado falhou) | Tranquilizador | E-mail ou senha não conferem, tente de novo |
| C-03-A05 | Login, bloqueio após 5 senhas erradas | Tranquilizador | Por segurança, bloqueamos o login por alguns minutos, tente de novo depois |
| C-03-A06 | Recuperação, passo 1, título | Instrutivo | Vamos recuperar sua senha |
| C-03-A07 | Recuperação, passo 1, texto | Instrutivo | Vamos enviar um código para o seu e-mail, informe o e-mail do seu cadastro |
| C-03-A08 | Recuperação, passo 1, botões | Operacional | Enviar código; Cancelar (**sem "Voltar" neste passo**) |
| C-03-A09 | Recuperação, passo 2, texto | Instrutivo | Se esse e-mail estiver cadastrado, enviamos um código, digite-o abaixo |
| C-03-A10 | Recuperação, passo 2, legenda do tempo (contagem regressiva) | Operacional | Código válido por [mm:ss] (exemplo de contagem regressiva; valor inicial 5 min, configurável no backend) |
| C-03-A11 | Recuperação, passo 2, erro de código | Tranquilizador | Esse código não confere, tente de novo |
| C-03-A12 | Recuperação, passo 2, código expirado | Tranquilizador | Esse código expirou, peça um novo |
| C-03-A13 | Recuperação, passo 2, bloqueio após 5 erros de código | Tranquilizador | Por segurança, pausamos as tentativas por alguns minutos |
| C-03-A14 | Recuperação, passo 2, botões | Operacional | Validar código; Reenviar código (nos 60 s de espera: "Reenviar em 45 s", desabilitado); Cancelar; Voltar |
| C-03-A15 | Recuperação, passo 3, título | Instrutivo | Crie sua nova senha |
| C-03-A16 | Recuperação, passo 3, botão principal (vale também para o menu do perfil, que passa a "Alterar senha") | Operacional | Alterar senha |
| C-03-A17 | Recuperação, passo 3, botões secundários | Operacional | Cancelar; Voltar |
| C-03-A18 | Toast após alterar a senha (o cliente é levado ao login) | Celebrativo | Senha alterada, entre com a nova senha |
| C-03-A19 | Modal de ativar biometria, título e texto | Instrutivo | Entrar com biometria? / Use sua digital ou seu rosto para abrir a WeCareU mais rápido e com segurança |
| C-03-A20 | Modal de ativar biometria, botões | Operacional | Ativar (destaque); Agora não (texto) |
| C-03-A21 | Modal de desativar biometria, título e texto | Tranquilizador | Desativar a biometria? / Com a biometria você abre o app mais rápido e mantém sua conta mais protegida se alguém pegar seu celular |
| C-03-A22 | Modal de desativar biometria, botões | Operacional | Manter ativada (destaque); Desativar (texto) |
| C-03-A23 | Falha da biometria | Operacional | Usar senha |
| C-03-A24 | Biometria alterada no aparelho, modal após o login, título e texto | Tranquilizador | Sua biometria mudou / Notamos que a biometria do aparelho mudou, por isso desativamos por segurança, quer ativar de novo? |
| C-03-A25 | Biometria alterada, botões | Operacional | Ativar (destaque); Agora não (texto) |

## 4. Sessão

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-04-01 | Login, mensagem acima do campo após expiração | "Sua sessão expirou. Entre novamente." | a revisar (exemplo) | Tranquilizador | Sessão do cliente [DEFINIDO] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |

### Textos finais aprovados da Sessão
Aprovado. O backend devolve um **401 genérico** em qualquer perda de sessão (expiração, troca de senha em outro aparelho, bloqueio, suspensão), sem informar o motivo. Por isso existe **uma única mensagem** de sessão.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-04-A01 | Login, acima do campo, após deslogar por qualquer 401 | Tranquilizador | Sua sessão expirou, entre de novo |

A mensagem de conta suspensa ou banida aparece **somente na tentativa de login** (fluxo 15, Estados gerais); ao deslogar por 401 não há mensagem diferente.

## 5. Home

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-05-01 | Cabeçalho, saudação | "Olá, <nome>!" | definida | Celebrativo | Registro de detalhamento: Home do cliente [DEFINIDO] | — |
| C-05-02 | Títulos de seção | "Vamos agendar", "Aguardando avaliação", "Próximos agendamentos" | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | A Home mostra só o próximo, mas o título está no plural; o singular "Próximo agendamento" só foi definido para a Agenda. |
| C-05-03 | Bloco "Vamos agendar", campo | "Endereço" | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | Placeholder do campo de pesquisa: SEM TEXTO DEFINIDO. |
| C-05-04 | Bloco "Vamos agendar", link | "Ver todos" | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | — |
| C-05-05 | Nome de endereço salvo (exemplo) | "Casa" | exemplo | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | — |
| C-05-06 | Botão com vários agendamentos futuros | "Ver mais agendamentos" | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | — |
| C-05-07 | Erro de endereço pesquisado inválido | SEM TEXTO DEFINIDO | — | Tranquilizador | Endereço de atendimento e troca pela listagem [DEFINIDO] | Falta o texto (vale para home e modal da listagem). |
| C-05-08 | Aviso fixo de push negado | "Ative as notificações para não perder avisos dos seus agendamentos" | provisória | Tranquilizador | Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO] | Sem ponto final. Rótulo do botão que abre os ajustes: SEM TEXTO DEFINIDO. |
| C-05-09 | Pergunta de salvar endereço novo no fim do agendamento | SEM TEXTO DEFINIDO | — | Instrutivo | Endereço de atendimento e troca pela listagem [DEFINIDO] | Faltam também os pedidos de complemento e nome no chat. |
| C-05-10 | Navegação inferior | "Início", "Artistas", "Agenda", "Perfil" | definida | Operacional | Registro de detalhamento: Navegação inferior do cliente [DEFINIDO] | — |

### Textos finais aprovados da Home
Todos aprovados. A pesquisa de endereço é por CEP, igual ao welcome e ao cadastro.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-05-A01 | Cabeçalho, saudação ([nome] = nome social quando existir, senão o primeiro nome) | Celebrativo | Olá, [nome]! |
| C-05-A02 | Título da seção de agendar | Operacional | Vamos agendar |
| C-05-A03 | Título da seção de avaliação pendente | Operacional | Avalie seu atendimento |
| C-05-A04 | Título da seção do próximo agendamento (singular) | Operacional | Próximo agendamento |
| C-05-A05 | Campo de endereço | Operacional | Campo fictício que abre o formulário. Rótulo: Endereço. Placeholder: Onde você quer ser atendido? |
| C-05-A06 | Links e botões | Operacional | Ver mais (dentro da caixa de endereços, carrega mais 5); Ver mais agendamentos |
| C-05-A07 | Navegação inferior | Operacional | Início; Artistas; Agenda; Perfil |
| C-05-A08 | Erro de CEP inválido ou não encontrado na pesquisa (Home e modal da listagem; mesmo texto de C-01-16) | Tranquilizador | Não encontramos esse CEP |
| C-05-A09 | Aviso fixo de push negado | Tranquilizador | Ative as notificações para não perder avisos dos seus agendamentos. Botão: Abrir ajustes |
| C-05-A10 | Chat de agendamento, endereço | — | **Removido:** o chat não pergunta nada sobre endereço (nem complemento, nome ou "quer salvar?"). Todo endereço novo do cliente logado é salvo pelo formulário |

**Formulário de endereço (Home e folha da listagem) e aviso de endereço repetido. Aprovados (textos finais):**

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-05-A11 | Formulário, título | Instrutivo | Novo endereço |
| C-05-A12 | Formulário, campos | Operacional | CEP, Rua, Número, Bairro, Cidade, Estado, Complemento, Nome do endereço (mesmo rótulo do welcome, C-01-13; substitui "Nome do local"); sugestão do nome: Casa |
| C-05-A13 | Formulário, botões (logado) | Operacional | Salvar (destaque); Cancelar |
| C-05-A14 | Formulário, botão (deslogado, sem campo de nome) | Operacional | Usar este endereço (destaque); Cancelar |
| C-05-A15 | Formulário, endereço repetido, erro dentro do formulário acima dos botões | Tranquilizador | Você já tem este endereço salvo |

**Prioridade das mensagens fixas (já no `05`):** uma por vez na região de alertas: 0 mensagem pontual, 1 push negado, 2 e-mail não confirmado.

## 6. Listagem de artistas, filtros e "Pesquisar"

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-06-01 | Lista vazia, região sem artista, mensagem | "Ainda estamos chegando na sua região" | provisória | Tranquilizador | Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono] | Sem ponto final. |
| C-06-02 | Lista vazia, região sem artista, frase | "Você pode buscar no bairro do trabalho ou de alguém da família." | provisória | Instrutivo | Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono] | "bairro" em vez de "região" (o próprio 05 manda trocar). [R2] "bairro"/"zona" (usar "Região") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-06-03 | Lista vazia, região sem artista, ação | "Tentar outro bairro" | provisória | Operacional | Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono] | "bairro" em vez de "região" (o 05 manda trocar). [R2] "bairro"/"zona" (usar "Região") |
| C-06-04 | Sem horário na data, com grupo B | "Não encontramos artistas para a data escolhida, mas você pode ver abaixo artistas com datas próximas." | provisória | Tranquilizador | Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono] | Promete "datas próximas", mas o card do grupo B não mostra data. Repetição "artistas ... artistas". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-06-05 | Sem horário na data nem em 14 dias | "Ops! Não encontramos horários livres no dia selecionado e nos próximos dias. Que tal escolher outra data?" | provisória | Tranquilizador | Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono] | "dia selecionado" vs "data escolhida" para o mesmo conceito. Rótulo do botão: SEM TEXTO DEFINIDO. |
| C-06-06 | Falha de conexão ou servidor | "Não foi possível carregar os artistas." | provisória | Tranquilizador | Registro de detalhamento: M05 Busca e listagem, estados da listagem [DEFINIDO pelo dono] | Ação descrita em minúscula ("tentar de novo"); assume-se "Tentar de novo". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-06-07 | Rodapé, falha ao carregar próxima página | "Não foi possível carregar mais artistas" + ação "Tentar de novo" | definida | Tranquilizador | Registro de detalhamento: M05 Scroll infinito [DEFINIDO pelo dono] | Sem ponto final, enquanto C-06-06 tem ponto. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-06-08 | Rodapé, fim da lista | "Você viu todos os artistas disponíveis" | exemplo | Operacional | Registro de detalhamento: M05 Scroll infinito [DEFINIDO pelo dono] | Sem ponto final. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-06-09 | Card, preço | "10 à 150" (rótulo "à") | definida | Operacional | Registro de detalhamento: M05 Card de artista na listagem [DEFINIDO pelo dono] | Erro de português: crase indevida em intervalo ("10 a 150"). [R5] Intervalo com "à" e sem "R$" (formato: "R$ 10 a R$ 150") |
| C-06-10 | Card, tags | "Premium", "Novo" | exemplo / definida | Operacional | Registro de detalhamento: M05/M02 Foto de divulgação e tag no card [DEFINIDO pelo dono] | — |
| C-06-11 | Card e perfil, com menos de 3 avaliações | "Poucas avaliações" | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | — |
| C-06-12 | Topo, data filtrada | "Data: 25 de maio" | provisória (formato provisório) | Operacional | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | Mês em minúscula aqui, maiúscula no chat ("25 de Maio"). |
| C-06-13 | Topo, chips de filtro (exemplos) | "Faz unhas das mãos", "Faz unhas dos pés", "Escova" | exemplo | Operacional | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | O 05 diz que o chip segue o texto de "Filtros selecionados", cujo exemplo tem outro formato ("Cabelereiro - Luzes"). |
| C-06-14 | Topo, endereço atual (exemplos) | "Casa"; região "Santana" | exemplo | Operacional | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | — |
| C-06-15 | Tela "Pesquisar": título, área, calendário, botão, link | "Pesquisar"; "Filtros selecionados"; "Data do atendimento"; "Aplicar filtros"; "Limpar filtros" | definida ("Limpar filtros": provisória) | Operacional | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | Placeholder do campo de texto: SEM TEXTO DEFINIDO. |
| C-06-16 | "Pesquisar", chip selecionado (exemplo) | "Cabelereiro - Luzes" | exemplo | Operacional | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | Erro de grafia: "Cabelereiro" (correto "Cabeleireiro"). |
| C-06-17 | "Pesquisar", texto sem correspondência | "Não encontramos esse serviço" | provisória | Tranquilizador | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | Sem ponto final. A busca também cobre ofício, que "serviço" não abrange. |
| C-06-18 | Modal artista indisponível | "Este artista não está mais disponível" | provisória | Tranquilizador | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | Botão da modal: SEM TEXTO DEFINIDO. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-06-19 | Modal artista que também é cliente | "Você não pode agendar com você mesmo" | provisória | Tranquilizador | Registro de detalhamento: M05 Filtros e tela "Pesquisar" (como existe hoje) [DEFINIDO pelo dono] | Botão da modal: SEM TEXTO DEFINIDO. |
| C-06-20 | Balão de cadastro 1 | "Na WeCareU você escolhe quem vai te atender! Sempre teremos um artista perfeito para você! Cadastra-se!" | provisória | Instrutivo | Registro de detalhamento: M05 Balões de incentivo de cadastro [DEFINIDO pelo dono] | Erro: "Cadastra-se!" (correto "Cadastre-se!"). Mistura "te"/"você". Promessa "Sempre teremos um artista" contradiz "Ainda estamos chegando na sua região". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-06-21 | Balão de cadastro 2 | "Você sabia que a plataforma WeCareU é grátis até mesmo para o artista? Isso mesmo aqui todos são bem vindos." | provisória | Instrutivo | Registro de detalhamento: M05 Balões de incentivo de cadastro [DEFINIDO pelo dono] | Falta vírgula ("Isso mesmo, aqui"); "bem vindos" sem hífen ("bem-vindos"). "grátis para o artista" conflita com os planos pagos de ranqueamento citados no 05. [R1] "a plataforma WeCareU" (terceira pessoa / nome da marca fora do necessário) [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-06-22 | Balão de cadastro 3 | "Cadastre-se na WeCareU agora mesmo e tenha acesso a todos os artistas da plataforma de forma 100% gratuita!" | provisória | Instrutivo | Registro de detalhamento: M05 Balões de incentivo de cadastro [DEFINIDO pelo dono] | "acesso a todos os artistas": o deslogado já vê a listagem inteira; promessa sem efeito real. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-06-23 | Balões, botão | "Cadastrar" | provisória | Operacional | Registro de detalhamento: M05 Balões de incentivo de cadastro [DEFINIDO pelo dono] | — |
| C-06-24 | Tela de bloqueio do deslogado, título | "Encontre os melhores artistas perto de você." | provisória (em revisão de copy) | Instrutivo | Registro de detalhamento: Navegação inferior do cliente [DEFINIDO] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-06-25 | Tela de bloqueio, subtexto | "Agende, favorite e descubra talentos agora mesmo." | provisória (em revisão de copy) | Instrutivo | Registro de detalhamento: Navegação inferior do cliente [DEFINIDO] | Promete "favorite": Favoritos fora do MVP. "talentos" em vez de "artistas". [R2] "talentos" (usar "Artistas") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-06-26 | Tela de bloqueio, botão e link | "Cadastrar"; "Já sou cadastrado" | provisória | Operacional | Registro de detalhamento: Navegação inferior do cliente [DEFINIDO] | "Já sou cadastrado" (masculino) vs "Já tenho conta" no welcome. [R2] "Já sou cadastrado" (vocabulário fixo: "Já tenho conta") |
| C-06-27 | Modal de troca de endereço (listagem) | SEM TEXTO DEFINIDO (título, placeholder do campo, marcação do endereço atual) | — | Operacional | Endereço de atendimento e troca pela listagem [DEFINIDO] | Faltam os textos. |

### Textos finais aprovados da Listagem, parte A (estados, rodapé e card)
Todos aprovados. As partes B (filtros, "Pesquisar", modais) e C (balões e tela de bloqueio) têm seus próprios blocos de textos finais abaixo.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-06-A01 | Região sem Artista | Tranquilizador | Título: Ainda estamos chegando na sua região. Frase: Você pode buscar o endereço do seu trabalho ou de alguém da família. Botão: Trocar endereço (abre o formulário de endereço) |
| C-06-A02 | Sem horário na data, com lista do grupo B | Tranquilizador | Nenhum Artista tem horário nessa data, mas estes têm nos próximos dias |
| C-06-A03 | Sem horário na data nem em 14 dias | Tranquilizador | Ops, não encontramos horários livres nessa data nem nos próximos dias. Botão: Escolher outra data (abre "Pesquisar") |
| C-06-A04 | Falha ao carregar a lista | Tranquilizador | Não conseguimos carregar os Artistas. Botão: Tentar de novo |
| C-06-A05 | Rodapé, falha ao carregar a próxima página | Tranquilizador | Não conseguimos carregar mais Artistas. Botão: Tentar de novo |
| C-06-A06 | Rodapé, fim da lista (duas linhas) | Operacional | Esses são todos os Artistas perto de você / Em breve chegarão mais Artistas |
| C-06-A07 | Card, faixa de preço | Operacional | R$ 10 a R$ 150 |
| C-06-A08 | Card e perfil, com menos de 3 avaliações (texto no lugar das estrelas, não é tag) | Operacional | Poucas avaliações |
| C-06-A09 | Card, tags | Operacional | Premium; Novo |

### Textos finais aprovados da Listagem, parte B (filtros, "Pesquisar" e modais)
Todos aprovados. Em nenhum texto aparece "ofício" (ver regra 9): usa-se "categoria".

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-06-B01 | Topo da listagem, data filtrada (ícone de calendário, sem rótulo "Data:") | Operacional | 25 de maio, quarta |
| C-06-B02 | Chips de filtro (topo e área "Filtros selecionados"); a faixa do topo é um campo **rolável para a direita, com os chips que vazam cortados na borda**, para sugerir que dá para rolar | Operacional | Categoria: Cabeleireiro. Serviço: Cabeleireiro - Luzes (grafia corrigida) |
| C-06-B03 | Tela "Pesquisar" | Operacional | Pesquisar; Filtros selecionados; Data do atendimento; Aplicar filtros; Limpar filtros |
| C-06-B04 | "Pesquisar", placeholder do campo de texto | Operacional | Busque por categoria ou serviço |
| C-06-B05 | "Pesquisar", texto sem correspondência | Tranquilizador | Não encontramos essa categoria ou serviço |
| C-06-B06 | Modal de Artista indisponível | Tranquilizador | Título: Este Artista não está mais disponível. Botão: Ver Artistas (volta à listagem recarregada) |
| C-06-B07 | Modal do próprio perfil | Tranquilizador | Título: Este é o seu perfil. Texto: Você não pode agendar com você mesmo, escolha outro Artista. Botão: Entendi |
| C-06-B08 | Folha de troca de endereço da listagem | Instrutivo | Título: Onde você quer ser atendido? Campo fictício e formulário iguais aos da Home (C-05-A05, C-05-A11 a A15); sem marcação do endereço atual |

### Textos finais aprovados da Listagem, parte C (balões de cadastro e tela de bloqueio)
Todos aprovados. Substituem os textos provisórios C-06-20 a C-06-26 da tabela acima. Os planos pagos do ranqueamento não contradizem "grátis": o Artista usa o app sem pagar e aparece na listagem, só não no topo, e compra funções se quiser.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-06-C01 | Balão de cadastro 1 | Instrutivo | Sempre tem um Artista perto de você, crie sua conta e escolha quem atende você |
| C-06-C02 | Balão de cadastro 2 | Instrutivo | Agendar na WeCareU é grátis, todo mundo é bem-vindo |
| C-06-C03 | Balão de cadastro 3 | Instrutivo | Crie sua conta agora e agende com Artistas perto de você, é grátis! |
| C-06-C04 | Botão dos balões | Operacional | Criar conta |
| C-06-C05 | Tela de bloqueio do deslogado, título | Instrutivo | Encontre Artistas perto de você |
| C-06-C06 | Tela de bloqueio, subtexto | Instrutivo | Agende e acompanhe seus atendimentos em um só lugar |
| C-06-C07 | Tela de bloqueio, botão e link | Operacional | Criar conta; Já tenho conta |

### Textos finais aprovados do Perfil do Artista (visão do cliente), parte A
Itens aprovados do fluxo 7. Textos do bloqueio: C-12-15, C-12-15B e C-12-15C, no bloco "Textos finais aprovados da Denúncia".

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-07-A01 | Cabeçalho, seta de voltar | Operacional | Voltar |
| C-07-A02 | Botão principal | Operacional | Agendar agora |
| C-07-A03 | Bloco "Sobre mim" | Operacional | Sobre mim; Ler mais; Regiões que atende; botão Ver mais (expande de 10 em 10) |
| C-07-A04 | Lista longa de regiões | Operacional | Botão Ver mais; sem "entre outros" e sem reticências |
| C-07-A05 | Bloco de serviços | Operacional | Título: Serviços. 5 categorias com 5 serviços cada; cada categoria tem o seu próprio "Ver mais" (mais 5 serviços), e o fim do bloco tem "Ver mais" para mais 5 categorias. Cada serviço mostra nome, duração ("2h30", "45 min") e preço ("R$ 180") |
| C-07-A06 | Rodapé de data | Operacional | Na WeCareU desde maio de 2020 (mês e ano da aprovação) |
| C-07-A07 | Rodapé de ações | Operacional | Denunciar Artista; Bloquear Artista (mesmo fluxo do "Bloquear também"; textos em C-12-15) |
| C-07-A08 | Avaliação no cabeçalho | Operacional | Somente estrelas, sem contagem; com poucas avaliações: Poucas avaliações (C-06-A08) |
| C-07-A09 | Falha ao carregar o perfil | Tranquilizador | Não conseguimos carregar este perfil. Botão: Tentar de novo |
| C-07-A10 | Artista indisponível | Tranquilizador | Reutiliza a modal C-06-B06 |

### Textos finais aprovados do Agendamento em chat, parte A
Itens aprovados do fluxo 8. Mensagens do robô que interrompem o fluxo (extensão, expiração, revalidação) aparecem no fim do chat mesmo que o cliente esteja em outro passo.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-08-A01 | Pedido de foto, no agendamento | Instrutivo | C-02-B02, agora com o motivo: "Para agendar, precisamos da sua foto, ela ajuda o Artista a reconhecer você quando chegar ao seu endereço". Botão: Enviar foto |
| C-08-A02 | Pedido de notificações, **início do chat, antes do passo 1**, se a permissão não foi concedida (aprovada) | Instrutivo | "Antes de começar, ative as notificações para receber os avisos do seu agendamento". Botões: Ativar notificações (destaque) e Agora não; com a permissão negada no aparelho, o primeiro botão vira Abrir ajustes |
| C-08-A02B | Resposta do robô a "Agora não" no pedido de notificações | Tranquilizador | "Sem problema, os avisos do seu agendamento só aparecerão aqui dentro do app" |
| C-08-A03 | Passo 1 | Instrutivo | Pergunta: Quais serviços você quer agendar? Campo: Pesquisar serviços. Aviso: Tempo total estimado: 1h30. Botão: Pronto. Serviços selecionados (inclusive o pré-selecionado) aparecem como chips com "×", sem copy extra |
| C-08-A04 | Passo 2 | Instrutivo | Pergunta: Para quando você quer agendar? Cartão de data: 25 de maio, quarta. Link: Ver mais datas |
| C-08-A05 | Barra do topo do chat (elemento fixo, não é mensagem) | Operacional | Menu de três pontos: Preciso de ajuda; "×" fecha o fluxo |
| C-08-A06 | Passo 2, aviso fixo (duas linhas) | Instrutivo | Não garantimos a disponibilidade do Artista, o horário pode mudar conforme a agenda dele / Se o Artista não comparecer, você poderá avisar pela Agenda |
| C-08-A07 | Data sem horário, com datas próximas | Tranquilizador | Não encontramos horários nessa data para os serviços escolhidos, mas estas são as datas mais próximas |
| C-08-A08 | Nada na data nem nos próximos 14 dias | Tranquilizador | Ops, não encontramos horários livres para esses serviços nessa data nem nos próximos dias. Que tal remover algum serviço ou escolher outra data? Botões: Alterar serviços; Escolher outra data |
| C-08-A09 | Artista sem horários | Tranquilizador | Ops, este Artista não tem horários livres no momento. Que tal ver outros Artistas? Botão: Ver Artistas |
| C-08-A10 | Contador do pré-agendamento, **faixa fixa abaixo do topo do chat**, que não rola com a conversa e **sem "×"** | Operacional | Horário pré-reservado por 09:41 |
| C-08-A11 | Oferta de extensão, mensagem do robô 2 min antes de expirar, interrompe o fluxo | Instrutivo | Seu horário pré-reservado está acabando. Quer mais 10 min para terminar? Só é possível estender uma vez. Botão: Estender por 10 min |
| C-08-A12 | Expiração (depois ou sem extensão), mensagem do robô, interrompe o fluxo; desativa os botões anteriores que dependiam do horário | Tranquilizador | O tempo para confirmar acabou e liberamos o horário, mas você pode escolher outro. Botão: Escolher horário |
| C-08-A13 | Antes do resumo | Instrutivo | Falta pouco, confira seu agendamento |
| C-08-A14 | Resumo | Operacional | Rótulos: Preço estimado; Região de atendimento. Data: 25 de maio, quarta. Hora: 12h. Botão: Confirmar agendamento. Legenda: Agendamento confirmado |
| C-08-A21 | Resumo, legenda sob o Preço estimado | Operacional | O pagamento é feito direto com o Artista |
| C-08-A15 | Revalidação, horário ocupado | Tranquilizador | Ops, este horário acabou de ser ocupado. Botão: Escolher outro horário |
| C-08-A16 | Revalidação, preço mudou | Tranquilizador | O Artista mudou o preço do serviço Luzes durante seu agendamento, o valor que era R$ 150 agora é R$ 180 (resumo atualizado logo abaixo, sem segunda confirmação) |
| C-08-A17 | Revalidação, serviço removido | Tranquilizador | "O Artista deixou de oferecer o serviço Luzes, você pode continuar sem ele ou escolher outros serviços". Botões: Continuar sem este serviço (destaque); Alterar serviços |
| C-08-A18 | Revalidação, Artista indisponível | Tranquilizador | Este Artista não está mais disponível (como C-06-B06). Botão: Ver Artistas |
| C-08-A19 | Falha ao confirmar | Tranquilizador | Não conseguimos confirmar seu agendamento agora. Botão: Tentar de novo |
| C-08-A20 | Mensagem final | Celebrativo | Tudo certo, seu agendamento está confirmado. Botão: Ver meus agendamentos (leva à Agenda) |

### Textos finais aprovados da Agenda e do cartão de agendamento
Todos aprovados (fluxo 9). "Cancelado" e "Sem avaliação" ocupam o lugar das estrelas de avaliação no cartão, não são tags no topo. O menu dos cartões passados tem "Preciso de ajuda" e "Denunciar Artista" como itens separados.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-09-A01 | Títulos de seção da Agenda | Operacional | Avalie seu atendimento; Próximo agendamento (um); Próximos agendamentos (vários); Agendamentos anteriores |
| C-09-A02 | Cartão, número | Operacional | #1234 |
| C-09-A03 | Menu do cartão futuro | Operacional | Cancelar agendamento; Preciso de ajuda |
| C-09-A04 | Menu do cartão passado, aguardando avaliação ou cancelado pelo Artista | Operacional | Preciso de ajuda; Denunciar Artista (itens separados) |
| C-09-A05 | Mensagem pré-preenchida do WhatsApp | Operacional | Com cartão: "Olá, preciso de ajuda com meu agendamento #1234 na WeCareU". Sem cartão (Central de Ajuda): "Olá, preciso de ajuda com o app da WeCareU" |
| C-09-A06 | Modal de cancelamento | Tranquilizador | Título: Cancelar agendamento. Texto: O Artista reservou esse horário para você e pode não conseguir atender outra pessoa. Quer mesmo cancelar? Botões: Não cancelar (destaque); Cancelar agendamento (texto) |
| C-09-A07 | Modal de cancelamento, erro dentro da modal acima dos botões | Tranquilizador | Não conseguimos cancelar agora. Botão: Tentar de novo |
| C-09-A08 | No lugar das estrelas do cartão | Operacional | Cancelado; Sem avaliação |
| C-09-A09 | Rodapé dos anteriores | Operacional | Carregando: indicador sem texto. Erro: Não conseguimos carregar mais agendamentos / Tentar de novo. Fim: Esses são todos os seus agendamentos |
| C-09-A10 | Agenda vazia | Instrutivo | Título: Você ainda não tem agendamentos. Texto: Que tal agendar com um Artista perto de você? Botão: Agendar agora |
| C-09-A11 | Falha ao carregar a Agenda | Tranquilizador | Não conseguimos carregar seus agendamentos. Botão: Tentar de novo |
| C-09-A12 | Modal "Como denunciar", aberta pela exclusão de conta | Instrutivo | Título: Como denunciar um Artista. Texto: Procure o atendimento com o Artista, toque nos três pontos do cartão, depois em "Denunciar Artista". Botão: Entendi |

## 7. Perfil do artista visto pelo cliente

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-07-01 | Cabeçalho, voltar | "Listagem" | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | A aba chama-se "Artistas"; "Listagem" é jargão interno. [R2] "Listagem" (aba/nome: "Artistas") |
| C-07-02 | Botão principal | "Agende agora!" | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | Varia com "Agendar agora" (estado vazio da Agenda). |
| C-07-03 | Bloco "Sobre mim" | "Sobre mim"; "Ler mais"; "Regiões que atende"; "entre outros..." | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | Rótulos "Cidade"/"Região" não escritos. |
| C-07-04 | Bloco de serviços | "Serviços"; "Ver mais" | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | O bloco vai virar "ofícios e serviços": título novo SEM TEXTO DEFINIDO. |
| C-07-05 | Rodapé | "Perfil criado em Maio de 2020" | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | Mês com maiúscula (norma: minúscula). A data é da aprovação, não da criação: "criado" é impreciso. [R5] Mês com maiúscula (formato com mês em minúscula) |
| C-07-06 | Rodapé, botão | "Denunciar Perfil" | definida | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | Title case inconsistente. [R2] variante de denúncia (vocabulário fixo: "Denunciar Artista") |
| C-07-07 | Itens do Figma removidos no MVP | "23 Anos"; "Compartilhar"; aba "Favoritos" | removidos | Operacional | Registro de detalhamento: M05/M02-F05 Perfil do artista visto pelo cliente [DEFINIDO] | Não devem aparecer no MVP. |
| C-07-08 | Botão de bloqueio no perfil | SEM TEXTO DEFINIDO | — | Operacional | Bloqueio (M12-F02) [DEFINIDO] | Falta o rótulo. |

## 8. Agendamento em chat (robô)

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-08-01 | Primeira mensagem para quem não tem foto | SEM TEXTO DEFINIDO (pedido de foto, sem opção "Depois") | — | Instrutivo | Cadastro do cliente: foto [DEFINIDO, copy provisória] | Falta o texto. |
| C-08-02 | Passo 1, pergunta | "Quais serviços pretende realizar?" | definida | Instrutivo | Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO] | Tom mais formal que o resto do app. |
| C-08-03 | Passo 1, campo | "Pesquisar serviços" | definida | Instrutivo | Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO] | — |
| C-08-04 | Passo 1, aviso | "Tempo total estimado" | definida | Instrutivo | Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO] | — |
| C-08-05 | Botão dos passos 1 e 2 | "Pronto" | definida | Instrutivo | Registro de detalhamento: M06 Agendamento do cliente [DEFINIDO] | — |
| C-08-06 | Passo 2, pergunta | "Para quando quer o serviço?" | definida | Instrutivo | M06 Passo 2: data e horário [DEFINIDO] | Singular "o serviço" quando podem ser vários. |
| C-08-07 | Passo 2, cartão de data (exemplo) | "25 de Maio, Quarta" | exemplo | Instrutivo | M06 Passo 2: data e horário [DEFINIDO] | Maiúsculas em mês e dia da semana (diverge de "25 de maio" na listagem). [R5] Mês com maiúscula (formato: "25 de maio, quarta") |
| C-08-08 | Passo 2, link | "Ver mais datas" | definida | Instrutivo | M06 Passo 2: data e horário [DEFINIDO] | — |
| C-08-09 | Passo 2, aviso fixo | "A disponibilidade do Artista não é garantida pela WeCareU, o agendamento pode variar conforme a agenda do Artista. Caso o Artista não te atenda no horário combinado você poderá mais tarde avaliá-lo na aba de agendamentos." | a revisar | Instrutivo | M06 Passo 2: data e horário [DEFINIDO] | "Artista" com maiúscula; vírgula unindo orações independentes; falta vírgula após "combinado"; "te"/"você"; longo para aviso fixo; "aba de agendamentos" não existe (é "Agenda"); diz que poderá avaliar quem não atendeu, mas sem check-out não há estrelas (só "O artista não compareceu"). [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-08-10 | Menu de três pontos | "Preciso de ajuda" | definida | Instrutivo | M06 Passo 2: data e horário [DEFINIDO] | — |
| C-08-11 | Data sem horário, com datas próximas | "Não encontramos horários nessa data para os serviços escolhidos, mas veja abaixo as datas mais próximas." | definida | Tranquilizador | M06 Passo 2: ordem das datas e situações sem horário | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-08-12 | Nada na data nem em 14 dias | "Ops! Não encontramos horários livres para esses serviços na data escolhida nem nos próximos dias. Que tal remover algum serviço ou escolher outra data?" | definida | Tranquilizador | M06 Passo 2: ordem das datas e situações sem horário | — |
| C-08-13 | Ações do item anterior | "Alterar serviços" e "Escolher outra data" | definida | Operacional | M06 Passo 2: ordem das datas e situações sem horário | — |
| C-08-14 | Sem data e sem horário | "Ops! Este artista não tem horários livres no momento. Que tal ver outros artistas?" | definida | Tranquilizador | M06 Passo 2: ordem das datas e situações sem horário | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-08-15 | Ação do item anterior | "Voltar à listagem" | definida | Operacional | M06 Passo 2: ordem das datas e situações sem horário | "listagem" é jargão; a aba é "Artistas". [R2] "Listagem" (aba/nome: "Artistas") |
| C-08-16 | Contador do pré-agendamento (10 min) | SEM TEXTO DEFINIDO | — | Operacional | M06 Pré-agendamento [DEFINIDO pelo dono] | Falta a legenda do contador. |
| C-08-17 | Oferta de extensão (+10 min, aviso de extensão única) e botão | SEM TEXTO DEFINIDO | — | Instrutivo | M06 Aviso de extensão única e endereço | Falta o texto; precisa dizer que só é possível estender 1 vez. |
| C-08-18 | Mensagem de expiração (horário liberado) | SEM TEXTO DEFINIDO | — | Tranquilizador | M06 Pré-agendamento [DEFINIDO pelo dono] | Falta o texto (inclusive o fim após a extensão). |
| C-08-19 | Mensagem antes do resumo | "Vamos continuar seu agendamento." | definida | Instrutivo | M06 Confirmação do agendamento [DEFINIDO] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-08-20 | Resumo, nota/data/horário (exemplos) | "4,5"; "25 de Maio, Quarta"; "12h00" | exemplo | Instrutivo | M06 Confirmação do agendamento [DEFINIDO] | Rótulos de preço total e região de atendimento: SEM TEXTO DEFINIDO. [R5] Hora "12h00" (preferir "12h" quando minutos zero) [R5] Mês com maiúscula (formato: "25 de maio, quarta") |
| C-08-21 | Resumo, botão | "Confirmar agendamento" | definida | Operacional | M06 Confirmação do agendamento [DEFINIDO] | — |
| C-08-22 | Legenda após confirmar | "Agendamento confirmado" | definida | Celebrativo | M06 Confirmação do agendamento [DEFINIDO] | — |
| C-08-23 | Revalidação, horário/artista indisponível | "Algo mudou" | provisória | Tranquilizador | M06 Regras de consistência do agendamento [DEFINIDO; copys provisórias] | Só o gancho; texto completo e ação: SEM TEXTO DEFINIDO. |
| C-08-24 | Revalidação, preço mudou | "O artista mudou o preço do serviço [nome] durante seu agendamento: o valor que era R$ [antes] agora é R$ [depois]." | provisória | Tranquilizador | M06 Regras de consistência do agendamento [DEFINIDO; copys provisórias] | Usa "R$", mas o card não usa símbolo de moeda ("app mais internacional"). [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-08-25 | Revalidação, serviço removido | SEM TEXTO DEFINIDO | — | Tranquilizador | M06 Regras de consistência do agendamento [DEFINIDO; copys provisórias] | Falta o texto. |
| C-08-26 | Mensagem final do robô, ação | "Ver meus agendamentos" | definida | Operacional | M06 Confirmação do agendamento [DEFINIDO] | Leva à Home (não à Agenda nem a um detalhe, que não existe no MVP): o rótulo promete outra coisa. Texto da mensagem final: SEM TEXTO DEFINIDO. [R2] "Ver meus agendamentos" deve levar à Agenda (hoje leva à Home / destino indefinido) |
| C-08-27 | Pedido de permissão de push após confirmar | SEM TEXTO DEFINIDO | — | Instrutivo | M06 Confirmação do agendamento [DEFINIDO] | — |
| C-08-28 | Falha de rede ao confirmar | SEM TEXTO DEFINIDO (padrão de estados gerais) | — | Tranquilizador | M06 Regras de consistência do agendamento [DEFINIDO; copys provisórias] | — |

## 9. Agenda e cartão de agendamento

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-09-01 | Agenda, títulos de seção | "Aguardando avaliação", "Próximo agendamento" / "Próximos agendamentos", "Agendamentos anteriores" | definida | Operacional | Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO] | — |
| C-09-02 | Cartão, número | "#" + número | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | — |
| C-09-03 | Cartão, menu de três pontos | "Cancelar" e "Preciso de ajuda" | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | "Cancelar" é ação destrutiva aqui e botão de fuga em outras modais (ex.: C-13-13, C-14-20). |
| C-09-04 | "Preciso de ajuda" em cartão passado, escolha | "Falar com a WeCareU" e "Denunciar o artista" | definida | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | "Denunciar o artista" vs "Denunciar artista" (C-14-15). [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R2] variante de denúncia (vocabulário fixo: "Denunciar Artista") [R2] "Falar com a WeCareU" (vocabulário fixo suporte: "Falar com a gente") |
| C-09-05 | Mensagem pré-preenchida no WhatsApp (com #) | SEM TEXTO DEFINIDO | — | Operacional | Registro de detalhamento: Home do cliente [DEFINIDO] | Falta o texto (também no chat de agendamento, Central de Ajuda e "Falar com a gente"). |
| C-09-06 | Modal de cancelamento, título | "Cancelar agendamento" | definida | Operacional | Cancelamento pelo cliente (M06-F05) [DEFINIDO] | — |
| C-09-07 | Modal de cancelamento, texto | "O artista pode não conseguir encaixar outro cliente nesse horário e separou esse horário só para você. Quer mesmo cancelar?" | definida | Tranquilizador | Cancelamento pelo cliente (M06-F05) [DEFINIDO] | Repetição "horário ... horário". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-09-08 | Modal de cancelamento, botões | "Não cancelar" (destaque) e "Cancelar" (texto) | definida | Operacional | Cancelamento pelo cliente (M06-F05) [DEFINIDO] | — |
| C-09-09 | Modal de cancelamento, erro | "Não foi possível cancelar. Tente novamente." | definida | Tranquilizador | Cancelamento pelo cliente (M06-F05) [DEFINIDO] | Difere do exemplo do aviso embutido para o mesmo erro (C-15-05). [R2] "Tentar/Tente novamente" (vocabulário fixo: "Tentar de novo") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-09-10 | Tag do cartão | "Cancelado" | definida | Operacional | Cancelamento pelo cliente (M06-F05) [DEFINIDO] | — |
| C-09-11 | Cartão anterior sem avaliação no prazo | "Você não avaliou" | definida | Operacional | Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO] | — |
| C-09-12 | Rodapé dos anteriores | "Tentar de novo" (carregando, erro e fim: "mesmos estados da listagem de artistas") | definida | Operacional | Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO] | Os textos da listagem citam "artistas" e não servem para agendamentos: texto próprio SEM TEXTO DEFINIDO. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-09-13 | Estado vazio, mensagem | SEM TEXTO DEFINIDO ("mensagem curta e amigável (texto provisório)") | provisória | Instrutivo | Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO] | Falta o texto. |
| C-09-14 | Estado vazio, botão | "Agendar agora" | definida | Operacional | Registro de detalhamento: Aba Agenda do cliente (M06-F03) [DEFINIDO] | Varia com "Agende agora!". |
| C-09-15 | Modal explicativa, título | "Como denunciar um artista" | provisória | Instrutivo | Excluir conta do cliente [DEFINIDO, copy provisória] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-09-16 | Modal explicativa, texto | "Escolha o atendimento com o artista, toque nos três pontos do cartão e selecione \"Preciso de ajuda\". Depois, escolha \"Denunciar o artista\"." | provisória | Instrutivo | Excluir conta do cliente [DEFINIDO, copy provisória] | As barras invertidas são escape do markdown do 05 e não vão ao app. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-09-17 | Modal explicativa, botão | "Entendi" | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | — |

## 10. Avaliação

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-10-01 | Contador abaixo das estrelas | "Enviaremos a avaliação em 10s" | provisória | Operacional | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | "10s" sem espaço (vs "60 s"); sem ponto final. [R5] Tempo sem espaço ("10s"; formato: "10 s") |
| C-10-02 | Após envio | "Obrigado pela avaliação" | definida | Celebrativo | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | — |
| C-10-03 | Falha no envio | "Não foi possível enviar sua avaliação. Toque nas estrelas para tentar de novo." | provisória | Tranquilizador | M10 Falha no envio da avaliação [DEFINIDO; copy provisória] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-10-04 | Link no rodapé do cartão | "O artista não compareceu" | definida | Operacional | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-10-05 | Modal, título | "O artista não compareceu?" | definida | Tranquilizador | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-10-06 | Modal, texto | "Vamos analisar o que aconteceu com o artista. Confirma que ele não compareceu?" | definida | Tranquilizador | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | "ele" assume gênero masculino. "Vamos analisar" sugere retorno, mas o cliente nunca recebe o resultado. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-10-07 | Modal, botões | "Voltar" (destaque) e "Sim, não compareceu" (texto) | definida | Operacional | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | — |
| C-10-08 | Modal, erro | "Não foi possível enviar. Tente novamente." | definida | Tranquilizador | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | [R2] "Tentar/Tente novamente" (vocabulário fixo: "Tentar de novo") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-10-09 | Modal de agradecimento, texto | "Obrigado pelo seu aviso! Continue sempre nos avisando quando ocorrido!" | definida | Celebrativo | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | Erro de português: "quando ocorrido" (frase incompleta); "aviso ... avisando". Título: SEM TEXTO DEFINIDO. |
| C-10-10 | Modal de agradecimento, botão | "Fechar" | definida | Operacional | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | — |

### Textos finais aprovados da Avaliação
Todos aprovados (fluxo 10). Os pushes de avaliação ficam no fluxo 11. Comportamento em `05`, "Registro de detalhamento: Fluxo de avaliação do cliente (M10)".

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-10-A01 | Contador abaixo das estrelas | Operacional | Enviaremos sua avaliação em 10 s, toque nas estrelas para alterar |
| C-10-A02 | Após o envio, no cartão | Celebrativo | Obrigado pela avaliação |
| C-10-A03 | Falha no envio da avaliação | Tranquilizador | Não conseguimos enviar sua avaliação, toque nas estrelas para tentar de novo |
| C-10-A04 | Link no rodapé do cartão | Operacional | O Artista não compareceu |
| C-10-A05 | Modal de não comparecimento | Tranquilizador | Título: O Artista não compareceu? Texto: Vamos analisar o que aconteceu. Você confirma que ele não compareceu? Botões: Voltar (destaque); Sim, não compareceu (texto) |
| C-10-A06 | Erro dentro da modal, acima dos botões | Tranquilizador | Não conseguimos enviar seu aviso agora, tente de novo |
| C-10-A07 | Modal de agradecimento | Tranquilizador | Título: Recebemos seu aviso. Texto: Obrigado por nos contar, avisar quando algo assim acontece ajuda a cuidar de quem usa a WeCareU. Botão: Fechar |

## 11. Notificações

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-11-01 | Push de avaliação no check-out | "[Nome do artista] te atendeu bem? Avalie agora" (ex.: "Ricardo te atendeu bem? Avalie agora") | provisória | Instrutivo | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | Sem pontuação final; "te" vs "você". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-11-02 | Push agrupado do dia seguinte às 10:00 | "Você tem atendimentos para avaliar" | provisória | Instrutivo | Registro de detalhamento: Fluxo de avaliação do cliente (M10) [DEFINIDO] | Plural fixo mesmo com 1 pendente. |
| C-11-03 | Pushes de lembrete (antecipado às 18:00 e 2h antes) | SEM TEXTO DEFINIDO | — | Operacional | Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO] | Faltam os 2 textos. |
| C-11-04 | Push de cancelamento pelo artista (artista, data, hora; tom de desculpa) | SEM TEXTO DEFINIDO | provisória | Tranquilizador | Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO] | Falta o texto; também serve ao cancelamento automático por bloqueio/sanção do artista. |
| C-11-05 | Push de lembrete mensal de reagendamento | SEM TEXTO DEFINIDO | provisória | Instrutivo | Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO] | Falta o texto. |
| C-11-06 | Aviso de permissão negada (home e Configurações de Notificação) | ver C-05-08 | provisória | Tranquilizador | Registro de detalhamento: Notificações do cliente (M11) [DEFINIDO] | — |
| C-11-07 | Configurações de Notificação, grupos e itens | "Gerais/Sistema"; "Serviços": "Agendamentos" e "Avaliações"; "Marketing": "Promoções e Ofertas" (oculto no MVP) | definida | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | "Gerais/Sistema" ambíguo (qual é o rótulo final?). |
| C-11-08 | Configurações de Notificação, aviso | "algumas notificações essenciais de segurança não podem ser desativadas" | definida | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | Começa em minúscula, sem ponto; "Agendamentos" também é travado e não é de segurança: aviso incompleto. |
| C-11-09 | Item removido | "Artistas que você segue" | removido no MVP | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | Não deve aparecer (Favoritos fora do MVP). |

### Textos finais aprovados das Notificações
Todos aprovados (fluxo 11). Cada push tem título e corpo; nomes, serviços e horários abaixo são exemplos. O aviso fixo de push negado é o C-05-A09. Comportamento em `05`, "Registro de detalhamento: Notificações do cliente (M11)".

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-11-A01 | Push de avaliação, no check-out | Instrutivo | Título: Avalie seu atendimento. Corpo: Como foi o atendimento com Ricardo? Toque para avaliar |
| C-11-A02 | Push de avaliação agrupado, às 10h do dia seguinte (1 ou mais pendentes) | Instrutivo | Título: Avalie seu atendimento. Corpo: Conte como foi, leva só um toque |
| C-11-A03 | Lembrete antecipado, às 18h | Operacional | Título: Seu agendamento é quinta, 10h. Corpo: Ricardo vai atender você: Corte feminino e mais 2 serviços. Sem menção a cancelamento: o push só lembra, não instiga. Com um serviço só: "Ricardo vai atender você: Corte feminino" |
| C-11-A04 | Lembrete de 2h antes | Operacional | Título: Seu atendimento é hoje, 10h. Corpo: Ricardo vai até você, confira se o endereço está certo |
| C-11-A05 | Cancelamento pelo Artista (serve também ao cancelamento por bloqueio ou sanção) | Tranquilizador | Título: Agendamento cancelado. Corpo: Sentimos muito, seu agendamento com Ricardo de quinta, 10h foi cancelado |
| C-11-A06 | Lembrete de reagendamento, 25 dias após o último atendimento | Celebrativo | Título: Que tal agendar de novo? Corpo: Escolha um Artista perto de você |
| C-11-A07 | Configurações de Notificação, grupos e itens | Operacional | Serviços: Agendamentos (sempre ligado) e Avaliações. Geral: Segurança e manutenção (sempre ligado). Promoções e Ofertas: oculto no MVP |
| C-11-A08 | Configurações de Notificação, aviso fixo | Operacional | Alguns avisos, como os de agendamento, segurança e manutenção, não podem ser desativados |

## 12. Denúncia e bloqueio

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-12-01 | Topo da tela | "Escolha um motivo para a Denúncia:" | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | "Denúncia" com maiúscula indevida; dois-pontos. |
| C-12-02 | Aviso | "Todas as denúncias serão analisadas e poderão gerar desligamento da plataforma." | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | "desligamento" vs "suspensão" (única sanção do MVP). [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-12-03 | Botões | "Reportar" e "Cancelar" | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | "Reportar" vs "Denunciar" na mesma tela. |
| C-12-04 | Campo de descrição | "Descreva..." | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | — |
| C-12-05 | Grupo 1, título | "Informações diferentes" (Figma: "Informação diferentes", a corrigir) | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | Erro de concordância no Figma (já apontado no 05). |
| C-12-06 | Grupo 1, descrição | "Toda e qualquer informação que não seja condizente com o informado no anúncio. Ex.: número de telefone de terceiros, endereço de atendimento incorreto, não prestação de serviços informados pelo anunciante etc." | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | "anúncio"/"anunciante" em vez de "perfil"/"artista"; o perfil não mostra telefone. [R2] "anúncio"/"anunciante" (usar perfil/Artista) [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-12-07 | Grupo 1, motivos | "Perfil usado por mais de uma pessoa"; "Propaganda no perfil"; "Divulgação de outras mídias"; "Fingindo ser eu ou minha empresa"; "Pessoa do agendamento diferente do WeCareU"; "Fotos" | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | "do WeCareU" (no resto é feminino: "na WeCareU"); "diferente do WeCareU" sem sentido claro (diferente do perfil). |
| C-12-08 | Grupo 2, título | "Problemas com atendimento" | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | — |
| C-12-09 | Grupo 2, motivos | "Me atendeu de forma rude"; "Quis fazer o agendamento por fora da WeCareU"; "Cancelou de última hora"; "Fez Check-in sem mim"; "Me obrigou a dar nota alto"; "Me obrigou a fazer meu review na sua frente" | provisória ("Quis fazer o agendamento por fora da WeCareU": definida) | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | "nota alto" (concordância: "nota alta"); "Check-in" com maiúscula; "review" (no app é "avaliação"); "na sua frente" (deveria ser "na frente dele"). |
| C-12-10 | Grupo 3, título | "Comportamento indesejado" | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | — |
| C-12-11 | Grupo 3, motivos | "Fui assediada(o)"; "Fui vítima de bullying"; "Fui agredida(o)"; "Fui roubada(o)"; "Conteúdo inadequado"; "Outros" | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | Flexão "(o)" aqui vs masculino genérico no resto do app. |
| C-12-12 | Modal pós-denúncia, título | "Denúncia realizada" (Figma sem acento) | provisória | Celebrativo | Denúncia do cliente (M12-F01) [DEFINIDO] | Figma sem acento. |
| C-12-13 | Modal pós-denúncia, textos | "Obrigado pelas informações!"; "Os dados enviados serão analisados pela nossa equipe e tomaremos as medidas necessárias." | provisória | Celebrativo | Denúncia do cliente (M12-F01) [DEFINIDO] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-12-14 | Modal pós-denúncia, botões | "Voltar" (destaque) e "Bloquear também" (texto) | provisória | Operacional | Denúncia do cliente (M12-F01) [DEFINIDO] | — |
| C-12-15 | Modal de bloqueio, confirmação | Título: Bloquear Artista. Texto: "Sentimos muito que tenha chegado a esse ponto" / "Se algo errado aconteceu, recomendamos denunciar primeiro, pois depois do bloqueio o perfil deste Artista some da sua lista" / "O bloqueio é permanente e seus agendamentos futuros com este Artista serão cancelados" / "Você tem certeza de que quer bloquear?". Botões: Cancelar (destaque) e Bloquear Artista (texto) | aprovada (texto final no bloco "Textos finais aprovados da Denúncia") | Tranquilizador | Bloqueio (M12-F02) [DEFINIDO] | Mantém a abertura empática do Figma. |
| C-12-15B | Modal de bloqueio, resultado | Título: Artista bloqueado. Texto: "Pronto, este Artista não vai mais aparecer para você" / "Seus agendamentos futuros com ele foram cancelados". Secundário: "Os atendimentos que você já teve com ele continuam no seu histórico". Botão: Entendi. Sem "Desfazer" | aprovada (texto final no bloco "Textos finais aprovados da Denúncia") | Tranquilizador | Bloqueio (M12-F02) [DEFINIDO] | Só promete o que controlamos. |
| C-12-15C | Modal de bloqueio, falha | "Não conseguimos bloquear agora", dentro da modal, acima dos botões. Botão: Tentar de novo | aprovada (texto final no bloco "Textos finais aprovados da Denúncia") | Tranquilizador | Bloqueio (M12-F02) [DEFINIDO] | — |

### Textos finais aprovados da Denúncia
Aprovados (fluxo 12), **padrão: cada grupo tem título e descrição (C-12-A05 e A05B)**. O bloqueio (C-12-15, C-12-15B e C-12-15C) está no fim da tabela abaixo. Comportamento em `05`, "Denúncia do cliente (M12-F01)". "Fez check-in sem mim" foi removido (é o "O Artista não compareceu").

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-12-A01 | Topo da tela | Instrutivo | Qual é o motivo da denúncia? |
| C-12-A02 | Aviso | Operacional | Nossa equipe analisa todas as denúncias e pode suspender o Artista |
| C-12-A03 | Botões | Operacional | Denunciar (destaque; desabilitado até marcar um motivo); Cancelar (texto) |
| C-12-A04 | Campo de descrição (opcional; obrigatório só em "Outros"; limite de 500 caracteres) | Operacional | Placeholder: Conte o que aconteceu |
| C-12-A05 | Grupo 1, título e descrição | Operacional | Título: Problemas com o perfil. Descrição: Algo no perfil do Artista que não é real ou não confere |
| C-12-A05B | Grupos 2 e 3, descrição (aprovada) | Operacional | Grupo 2: Algo que aconteceu durante ou por causa do atendimento. Grupo 3: Situações que colocaram sua segurança ou seu bem-estar em risco |
| C-12-A06 | Grupo 1, motivos | Operacional | Perfil usado por mais de uma pessoa; Propaganda no perfil; Divulgação de outras redes sociais; Fingindo ser eu ou minha empresa; Pessoa do atendimento diferente da do perfil; Fotos |
| C-12-A07 | Grupo 2, título e motivos | Operacional | Problemas com o atendimento: Me atendeu de forma rude; Quis fazer o agendamento por fora da WeCareU; Cancelou de última hora; Me obrigou a dar nota alta; Me obrigou a avaliar na frente dele |
| C-12-A08 | Grupo 3, título e motivos | Operacional | Comportamento indesejado: Sofri assédio; Sofri bullying; Sofri agressão; Sofri roubo; Conteúdo inadequado; Outros |
| C-12-A09 | Modal pós-denúncia | Tranquilizador | Título: Denúncia enviada. Texto: Obrigado por nos contar / Vamos analisar o que você enviou e tomar as medidas necessárias. Botões: Voltar (destaque); Bloquear também (texto) |
| C-12-A10 | Falha ao enviar, dentro da tela, acima do botão "Denunciar" | Tranquilizador | Não conseguimos enviar sua denúncia agora, tente de novo |
| C-12-15 | Modal de bloqueio, confirmação ("Bloquear também" e "Bloquear Artista" no perfil) | Tranquilizador | Título: Bloquear Artista. Texto: Sentimos muito que tenha chegado a esse ponto / Se algo errado aconteceu, recomendamos denunciar primeiro, pois depois do bloqueio o perfil deste Artista some da sua lista / O bloqueio é permanente e seus agendamentos futuros com este Artista serão cancelados / Você tem certeza de que quer bloquear? Botões: Cancelar (destaque); Bloquear Artista (texto) |
| C-12-15B | Modal de bloqueio, resultado | Tranquilizador | Título: Artista bloqueado. Texto: Pronto, este Artista não vai mais aparecer para você / Seus agendamentos futuros com ele foram cancelados. Secundário: Os atendimentos que você já teve com ele continuam no seu histórico. Botão: Entendi. Sem "Desfazer" |
| C-12-15C | Modal de bloqueio, falha (dentro da modal, acima dos botões) | Tranquilizador | Não conseguimos bloquear agora. Botão: Tentar de novo |

## 13. Perfil / engrenagem

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-13-01 | Aba Perfil | "Sobre mim"; "Cidade"; "Região"; "Perfil criado em [mês/ano]" | definida | Operacional | Registro de detalhamento: Aba Perfil do cliente [DEFINIDO] | O Figma ainda mostra "Bairro"/"Zona" (05 manda trocar). |
| C-13-02 | Engrenagem, título | "Meu Perfil" | definida | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | "Meu Perfil" vs aba "Perfil". |
| C-13-03 | Engrenagem, grupos e itens | "Dados Pessoais" > "Editar Perfil"; "Segurança" > "Alterar Senha"; "Endereços" > "Gerenciar Endereços"; "Notificações" > "Configurações de Notificação"; "Suporte" > "Central de Ajuda" e "Sobre o App"; "Legal" > "Termos de Uso" e "Política de Privacidade"; "Sair da sua conta"; "Excluir conta" | definida (todos passam por revisão de copy) | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | Title case inconsistente ("Excluir conta" e "Sair da sua conta" em minúscula). |
| C-13-04 | Editar Perfil, botão | "Salvar" | definida | Operacional | Editar Perfil do cliente e troca de e-mail [DEFINIDO] | Rótulos de campos, botão de troca de e-mail e aviso de confirmação do novo e-mail: SEM TEXTO DEFINIDO. |
| C-13-05 | Editar Perfil, e-mail já em uso | modal de e-mail já cadastrado sem "Entrar" (ver C-02-18 a C-02-21) | provisória | Tranquilizador | Editar Perfil do cliente e troca de e-mail [DEFINIDO] | O texto C-02-19 manda clicar em entrar no botão abaixo, que não existe nesta variante. |
| C-13-06 | E-mails transacionais (aviso ao e-mail antigo, confirmação do novo, verificação do cadastro, código) | SEM TEXTO DEFINIDO | — | Operacional | Editar Perfil do cliente e troca de e-mail [DEFINIDO] | Fora da interface do app, mas são copys do cliente. |
| C-13-07 | Alterar Senha, tela | "Verificar Email" | definida | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | "Email" sem hífen. [R2] "email"/"Email" sem hífen (usar "e-mail") |
| C-13-08 | Modal de último endereço, título | "Não dá para excluir ainda" | provisória | Tranquilizador | Endereço de atendimento e troca pela listagem [DEFINIDO] | — |
| C-13-09 | Mesma modal, texto | "Você precisa ter pelo menos um endereço salvo. Adicione outro para poder excluir este." | provisória | Tranquilizador | Endereço de atendimento e troca pela listagem [DEFINIDO] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-13-10 | Mesma modal, botão | "Entendi" | provisória | Operacional | Endereço de atendimento e troca pela listagem [DEFINIDO] | — |
| C-13-11 | Segurança, interruptor de biometria | SEM TEXTO DEFINIDO (modais: C-03-12 a C-03-17) | — | Operacional | Login e recuperação de senha do cliente [DEFINIDO] | Falta o rótulo. |
| C-13-12 | Modal de sair, título | "Sair da conta?" | provisória | Tranquilizador | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | Item do menu é "Sair da sua conta". |
| C-13-13 | Modal de sair, botões | "Sair" (destaque) e "Cancelar" (texto) | provisória | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | Ação de saída em destaque, ao contrário do padrão "caminho seguro em destaque" das modais de cancelamento e "não compareceu". [R4] Botão de destaque é a ação destrutiva "Sair" (deve ser "Cancelar" em destaque) |
| C-13-14 | Sobre o App, links | "Nosso Site", "Central de Ajuda", "Contato por Email" | definida | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | "Email" sem hífen. Descrição do app: SEM TEXTO DEFINIDO. [R2] "email"/"Email" sem hífen (usar "e-mail") |
| C-13-15 | Termos de Uso e Política de Privacidade | texto legal defasado (dez/2024) | a revisar (entrega com o advogado) | Operacional | Registro de detalhamento: Engrenagem / "Meu Perfil" do cliente [DEFINIDO] | Texto novo pendente. |

### Textos finais aprovados do Perfil e da engrenagem (Configurações)
Aprovados (fluxo 13), todos os textos aprovados. Comportamento em `05`, "Aba Perfil do cliente", "Engrenagem / 'Meu Perfil' do cliente" e "Editar Perfil do cliente e troca de e-mail". Os e-mails transacionais ficam fora deste catálogo (ver o fim do bloco).

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-13-A01 | Aba Perfil | Operacional | Sobre mim; Cidade; Região; Endereço (com o olho para revelar); Na WeCareU desde maio de 2020 |
| C-13-A02 | Título da tela da engrenagem (substitui "Meu Perfil") | Operacional | Configurações |
| C-13-A03 | Menu | Operacional | Dados pessoais > Editar perfil; Segurança > Alterar senha e interruptor "Entrar com biometria"; Endereços > Meus endereços; Notificações > Notificações; Ajuda > Central de Ajuda e Sobre o app; Legal > Termos de Uso e Política de Privacidade; no fim: Sair da conta; Excluir conta (em vermelho) |
| C-13-A04 | Editar perfil, título e campos | Operacional | Título: Editar perfil. Campos: Nome completo (bloqueado); CPF (bloqueado); Nome social; Celular; Sexo; Data de nascimento; E-mail. Foto: Trocar foto. Botão: Salvar |
| C-13-A05 | Editar perfil, aviso sob os campos bloqueados | Instrutivo | Nome completo e CPF só podem ser alterados pela nossa equipe. Link: Falar com a gente |
| C-13-A06 | Troca de e-mail, botão | Operacional | Alterar e-mail |
| C-13-A07 | Troca de e-mail, após o toque | Instrutivo | Enviamos um e-mail para o seu endereço atual, abra e confirme para trocar |
| C-13-A08 | Troca de e-mail, e-mail já em uso (modal, sem "Entrar") | Tranquilizador | Título: E-mail já cadastrado. Texto: Este e-mail já tem uma conta na WeCareU, use outro. Botão: Entendi |
| C-13-A09 | Modal de último endereço | Tranquilizador | Título: Não dá para excluir ainda. Texto: Você precisa ter pelo menos um endereço salvo, adicione outro para poder excluir este. Botão: Entendi |
| C-13-A10 | Alterar senha logado, passo 1 | Instrutivo | Título: Vamos confirmar que é você. Texto: Enviaremos um código para m***@gmail.com (exemplo, e-mail mascarado). Botões: Enviar código; Cancelar. Passos seguintes: C-03-A09 a A18 |
| C-13-A11 | Modal de sair (aprovada; também serve de retenção leve e espaço de marketing) | Tranquilizador | Título: Sair da conta? Texto: Não vá embora, tem Artistas esperando por você. Botões: Cancelar (destaque); Sair (texto) |
| C-13-A12 | Sobre o app | Operacional | Versão 1.0.0 (exemplo); A WeCareU leva Artistas de beleza e bem-estar até o seu endereço; links: Nosso site; Central de Ajuda; Contato por e-mail |
| C-13-A13 | Termos de Uso e Política de Privacidade | Operacional | Títulos: Termos de Uso; Política de Privacidade. Linha: Atualizado em 25 de maio de 2026 (exemplo). Conteúdo legal: entrega com o advogado |
| C-13-A14 | E-mails transacionais (aviso ao e-mail antigo, confirmação do novo, verificação do cadastro, código) | Operacional | **Fora do catálogo do app:** já existem modelos prontos, que serão revisados num bloco próprio no fim da revisão de copy, com as regras de e-mail (ponto final permitido) |

## 14. Excluir conta

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-14-01 | Modal 1, título | "Opa, achei agendamentos abertos" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | 1ª pessoa do singular ("achei") vs "podemos" no texto da mesma modal. [R1] 1ª pessoa do singular ("Vou"/"achei"); voz da marca é 1ª do plural |
| C-14-02 | Modal 1, texto | "Você tem agendamentos não concluídos e, por isso, ainda não podemos excluir sua conta. Assim que cancelar ou concluir cada um deles, é só voltar aqui e continuar." | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | "abertos" (título) vs "não concluídos" (texto). [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-14-03 | Modal 1, botões | "Ver meus agendamentos" (destaque) e "Voltar" (texto) | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | Mesmo rótulo de C-08-26, que leva à Home; destino aqui não definido. [R2] "Ver meus agendamentos" deve levar à Agenda (hoje leva à Home / destino indefinido) |
| C-14-04 | Modal 2, título | "Poxa, vai mesmo embora?" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-05 | Modal 2, texto | "A gente ficaria muito feliz em continuar cuidando de você. Se algo não saiu como esperava, conta pra gente pelo nosso suporte. (link para o suporte) Lembre-se: Sempre tem um novo artista perto de você!" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | "conta pra gente" (imperativo de "tu") com "você"; "Sempre" com maiúscula após dois-pontos; "Sempre tem um novo artista perto de você" contradiz "Ainda estamos chegando na sua região"; longo para modal. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R7] Parênteses para se explicar (reescrever sem parênteses) |
| C-14-06 | Modal 2, botões e link | "Quero ficar" (destaque); "Continuar com a exclusão" (texto); "Falar com a gente" (link WhatsApp) | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | "Falar com a gente" vs "Falar com a WeCareU" para o mesmo destino; link de suporte duplicado na modal. |
| C-14-07 | Tela de motivo, título | "Pode nos contar o motivo?" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-08 | Tela de motivo, opções | "Não uso mais o app"; "Não encontrei artistas na minha região"; "Tive um problema com um artista"; "Prefiro agendar por outros meios"; "Outro motivo" | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |
| C-14-09 | Tela de motivo, botão | "Continuar" | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-10 | Opção 2, modal, título | "Estamos chegando aos poucos" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-11 | Opção 2, modal, texto | "A WeCareU está chegando aos poucos em várias regiões, e usar o app não custa nada. Vale a pena esperar por um artista perto de você." | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | Repete "chegando aos poucos" do título. [R1] Terceira pessoa: "A WeCareU ..." (voz deve ser 1ª do plural) [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-14-12 | Opção 2, botões | "Vou esperar" (destaque) e "Continuar com a exclusão" (texto) | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | [R1] 1ª pessoa do singular ("Vou"/"achei"); voz da marca é 1ª do plural |
| C-14-13 | Opção 3, modal, título | "Poxa, sentimos muito" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | Título e texto repetem "sentimos muito". |
| C-14-14 | Opção 3, modal, texto | "Sentimos muito que isso tenha acontecido. Você pode denunciar e bloquear o artista, e não precisa ir embora por causa disso." | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-14-15 | Opção 3, botões | "Denunciar artista" (destaque) e "Continuar com a exclusão" (texto) | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | "Denunciar artista" vs "Denunciar o artista". [R2] "artista(s)" com minúscula (deve ser "Artista(s)") [R2] variante de denúncia (vocabulário fixo: "Denunciar Artista") |
| C-14-16 | Opções 4 e 5, modal, título | "Quer contar mais?" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | Texto explicativo e placeholder do campo (máx. 500): SEM TEXTO DEFINIDO. |
| C-14-17 | Opções 4 e 5, botão | "Continuar com a exclusão" | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-18 | Modal 3, título | "Só mais um passo" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-19 | Modal 3, texto | "Ao excluir, você perde o acesso à sua conta, aos seus endereços e ao seu histórico. Para garantir que é você mesmo, digite sua senha." | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-14-20 | Modal 3, botões | "Excluir minha conta" (destaque) e "Cancelar" (texto) | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | Ação destrutiva em destaque (padrão invertido). Erro de senha: SEM TEXTO DEFINIDO. [R4] Botão de destaque é a ação destrutiva "Excluir minha conta" (deve ser "Cancelar" em destaque) |
| C-14-21 | Modal 4, título | "Sua conta será excluída" | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | — |
| C-14-22 | Modal 4, texto | "Sentiremos sua falta! Se mudar de ideia, é só entrar novamente em até 30 dias e recuperamos sua conta como ela estava. Depois desse prazo, sua conta será encerrada." | provisória | Tranquilizador | Excluir conta do cliente [DEFINIDO, copy provisória] | "excluída" (título) vs "encerrada" (texto). [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-14-23 | Modal 4, botão | "Entendi" | provisória | Operacional | Excluir conta do cliente [DEFINIDO, copy provisória] | — |

### Textos finais aprovados de Excluir conta
Aprovados (fluxo 14). Voz do cliente em botões e opções ("Quero ficar", "Vou esperar") é permitida; a voz da marca continua no plural. Comportamento em `05`, "Excluir conta do cliente". O link de suporte vai dentro do texto (padrão de duas opções por modal). Termos: nas ações o app diz "excluir"; o aviso final diz "desativada", pois a exclusão só vale após 30 dias e o app não promete remoção física dos dados.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-14-A01 | Modal 1, agendamentos em aberto | Tranquilizador | Título: Você tem agendamentos em aberto. Texto: Ainda não podemos excluir sua conta, cancele ou conclua cada agendamento e volte aqui para continuar. Botões: Ver meus agendamentos (destaque, leva à Agenda); Voltar (texto) |
| C-14-A02 | Modal 2, retenção | Tranquilizador | Título: Poxa, vai mesmo embora? Texto: Ficaríamos muito felizes em continuar cuidando de você / Se algo não saiu como esperado, [fale com a gente] (link para o WhatsApp dentro do texto) / Sempre tem um Artista perto de você. Botões: Quero ficar (destaque); Continuar com a exclusão (texto) |
| C-14-A03 | Tela de motivo | Operacional | Título: Pode nos contar o motivo? Opções: Não uso mais o app; Não encontrei Artistas na minha região; Tive um problema com um Artista; Prefiro agendar por outros meios; Outro motivo. Botão: Continuar (desabilitado até escolher) |
| C-14-A04 | Opção "Não encontrei Artistas", modal | Tranquilizador | Título: Ainda não chegamos à sua região. Texto: Estamos chegando a mais regiões e usar a WeCareU não custa nada, vale esperar por um Artista perto de você. Botões: Vou esperar (destaque); Continuar com a exclusão (texto) |
| C-14-A05 | Opção "Problema com um Artista", modal | Tranquilizador | Título: Sentimos muito. Texto: Algo errado aconteceu? Você pode denunciar e bloquear o Artista, e não precisa ir embora por causa disso. Botões: Denunciar Artista (destaque); Continuar com a exclusão (texto) |
| C-14-A06 | Opções "Outros meios" e "Outro motivo", modal | Instrutivo | Título: Quer contar mais? Texto: Seu relato ajuda a melhorar a WeCareU, mas é opcional. Placeholder: Escreva aqui o que quiser nos contar. Botão: Continuar com a exclusão |
| C-14-A07 | Modal 3, confirmação com senha | Tranquilizador | Título: Só mais um passo. Texto: Ao excluir, você perde o acesso à sua conta, aos seus endereços e ao seu histórico, digite sua senha para confirmar que é você. Campo: Senha. Botões: Cancelar (destaque); Excluir minha conta (texto vermelho). Erro de senha acima do campo: Essa senha não confere, tente de novo |
| C-14-A08 | Modal 4, aviso final | Tranquilizador | Título: Sua conta será desativada. Texto: Sentiremos sua falta, se mudar de ideia, é só entrar de novo em até 30 dias e recuperamos sua conta como ela estava, depois desse prazo ela deixa de estar disponível. Botão: Entendi |

## 15. Estados gerais

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-15-01 | Overlay offline | "Você está offline, conecte-se para usar o melhor app de agendamentos." | provisória | Tranquilizador | 1. Sem internet [DEFINIDO; copy provisória] | Vírgula unindo orações (melhor ponto); autopromoção numa mensagem de erro. [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-02 | Erro genérico de formulário/ação simples | "Algo deu errado! Tente novamente." | provisória | Tranquilizador | 2. Falhas em ações e padrão de mensagens [DEFINIDO; copy provisória] | Exclamação em erro (os demais erros usam ponto). [R2] "Tentar/Tente novamente" (vocabulário fixo: "Tentar de novo") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-03 | Erros validados no app | CPF inválido, e-mail em formato errado, campo obrigatório (citados como exemplo) | exemplo | Tranquilizador | 2. Falhas em ações e padrão de mensagens [DEFINIDO; copy provisória] | Textos de "e-mail em formato errado" e "campo obrigatório": SEM TEXTO DEFINIDO. |
| C-15-04 | Toast (exemplo) | "Endereço salvo" | exemplo | Celebrativo | 2. Falhas em ações e padrão de mensagens [DEFINIDO; copy provisória] | — |
| C-15-05 | Aviso embutido de erro (exemplo) | "Não foi possível cancelar o agendamento. Tente novamente." | provisória | Tranquilizador | 2. Falhas em ações e padrão de mensagens [DEFINIDO; copy provisória] | Erros embutidos de avaliar e de "Preciso de ajuda": SEM TEXTO DEFINIDO. [R2] "Tentar/Tente novamente" (vocabulário fixo: "Tentar de novo") [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-06 | Tela de versão não suportada | "Atualize o app"; "Há uma nova versão da WeCareU. Atualize para continuar usando."; botão "Atualizar" | provisória (exemplo) | Instrutivo | 3. Versão mínima do app [DEFINIDO; copy provisória] | Texto promocional exigido: SEM TEXTO DEFINIDO. [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-07 | Tela de manutenção | "Estamos em manutenção"; "Voltamos em breve."; botão "Tentar de novo" | provisória | Tranquilizador | 4. Fora do ar e manutenção [DEFINIDO; copy provisória] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-08 | Fora do ar na listagem | ver C-06-06 | provisória | Tranquilizador | 4. Fora do ar e manutenção [DEFINIDO; copy provisória] | — |
| C-15-09 | Login, conta suspensa ou banida | "Não foi possível acessar esta conta. Entre em contato com o suporte." (+ link WhatsApp, rótulo SEM TEXTO DEFINIDO) | provisória | Tranquilizador | 5. Conta suspensa ou banida pelo backoffice [DEFINIDO; copy provisória] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-10 | Modal de câmera negada, título | "Permissão necessária" | provisória | Tranquilizador | 6. Permissão de câmera ou galeria na foto [DEFINIDO; copy provisória] | — |
| C-15-11 | Modal de câmera negada, texto | "Para tirar a foto, precisamos de acesso à câmera. Você pode liberar nos ajustes do aparelho ou escolher uma foto da galeria." | provisória | Tranquilizador | 6. Permissão de câmera ou galeria na foto [DEFINIDO; copy provisória] | [R3] Ponto final dentro da tela (proibido em título/aviso/botão/corpo de modal/erro/push/toast/robô) |
| C-15-12 | Modal de câmera negada, botões | "Abrir ajustes" (destaque) e "Escolher da galeria" (texto) | provisória | Operacional | 6. Permissão de câmera ou galeria na foto [DEFINIDO; copy provisória] | — |
| C-15-13 | Erro por horário recusado pelo backend | SEM TEXTO DEFINIDO (padrão do item 2) | — | Tranquilizador | 7. Hora do servidor como referência [DEFINIDO] | — |

### Textos finais aprovados dos Estados gerais
Todos aprovados (fluxo 15). Sem ponto final. Comportamento em `05`, "Estados gerais do app". Erros de campo do cadastro (CPF, e-mail, etc.) valem em todo o app. Erro de foto: C-02-B09 e B10. Erro de avaliar: C-10-A03. Erro de cancelar: C-09-A07.

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-15-A01 | Overlay offline | Tranquilizador | Título: Você está offline. Texto: Conecte-se à internet para continuar usando a WeCareU |
| C-15-A02 | Erro genérico de formulário ou ação simples | Tranquilizador | Algo deu errado, tente de novo |
| C-15-A03 | Campo obrigatório vazio | Tranquilizador | Preencha este campo |
| C-15-A04 | Toast (padrão: frase curta no passado, sem ponto, some em cerca de 3 s) | Celebrativo | Exemplos: Endereço salvo; Enviamos um novo e-mail, confira sua caixa de entrada |
| C-15-A05 | Aviso embutido, "Preciso de ajuda" quando o WhatsApp não abre | Tranquilizador | Não conseguimos abrir o WhatsApp, confira se ele está instalado |
| C-15-A06 | Tela de versão não suportada | Instrutivo | Título: Atualize o app. Texto: Lançamos uma nova versão da WeCareU, atualize para continuar agendando com Artistas perto de você. Botão: Atualizar |
| C-15-A07 | Tela de manutenção | Tranquilizador | Título: Estamos em manutenção. Texto: Estamos fazendo melhorias para você, voltamos em breve. Botão: Tentar de novo |
| C-15-A08 | Login, conta suspensa ou banida (formal; não revela motivo nem se é temporária) | Tranquilizador | Não foi possível acessar esta conta, [fale com a gente] (link para o WhatsApp dentro do texto) |
| C-15-A09 | Modal de câmera negada | Tranquilizador | Título: Precisamos da câmera. Texto: Para tirar a foto, libere a câmera nos ajustes do aparelho ou escolha uma foto da galeria. Botões: Abrir ajustes (destaque); Escolher da galeria (texto) |
| C-15-A10 | Cancelar recusado por horário (dentro da modal de cancelamento; o cartão recarrega) | Tranquilizador | Não é mais possível cancelar, o horário do agendamento já começou. Botão: Entendi. Outras recusas por horário: C-15-A02 |

## 16. SMS de convite

| Id | Onde aparece | Texto atual (literal) | Marca | Tom | Origem no 05 | Problemas detectados |
|---|---|---|---|---|---|---|
| C-16-01 | SMS ao cliente convidado pela reserva manual | "O artista Ricardo agendou você para dia 28/10 às 15h. Conheça a WeCareU e agende seus próximos atendimentos pelo app." | provisória | Instrutivo | Registro de detalhamento: Convite ao cliente pela reserva manual do artista (M07, lado do cliente) [DEFINIDO] | "para dia" (falta artigo: "para o dia"); "O artista" fixo no masculino; o link da loja permitido não aparece no texto. [R2] "artista(s)" com minúscula (deve ser "Artista(s)") |

### Texto final aprovado do SMS de convite
Aprovado (fluxo 16). SMS é comunicado fora do app: leva ponto final. Comportamento em `05`, "Convite ao cliente pela reserva manual do artista".

| Id | Onde aparece | Tom | Texto final |
|---|---|---|---|
| C-16-A01 | SMS ao cliente convidado pela reserva manual | Instrutivo | [Nome do Artista] agendou você em [dd/mm], às [hh]h. Conheça o app WeCareU: [link curto] |

Regras: o texto precisa ser curto (acento já converte o SMS para Unicode, cerca de 70 caracteres por segmento, e o custo é da empresa); exceção ao padrão de data do app: usa "28/10" por tamanho; hora no padrão ("15h", "15h30"); sem artigo antes do nome, para não errar o gênero; não promete acompanhamento do atendimento nem diz que o horário é de atendimento; um único link curto, que redireciona para a loja certa (iOS ou Android).

---

## Inconsistências transversais (glossário, histórico)

**Histórico da revisão:** as inconsistências abaixo foram encontradas nas copys provisórias e estão **todas resolvidas** nos blocos "Textos finais aprovados" (ex.: "Ver meus agendamentos" leva à Agenda; "Denunciar Artista"; "Tentar de novo"; "Criar conta"; "R$ 10 a R$ 150"). Não usar esta tabela como regra.

| Conceito | Variações encontradas | Onde | Observação |
|---|---|---|---|
| Área geográfica | "região" / "bairro" / "Zona" | C-06-01 vs C-06-02, C-06-03; C-13-01 | O 05 define que "região" substitui "bairro" em toda exibição. |
| Profissional | "artista" / "Artista" / "talentos" / "anunciante" / "prestador" (só interno) | C-08-09, C-06-25, C-12-06 | — |
| Agendamento | "agendamento" / "atendimento" / "serviço" / "reserva" (só interno, M07) | C-11-02, C-08-06, C-09-16 | "atendimento" usado tanto para o evento quanto para o agendamento. |
| Tratamento | "você" / "te" / imperativo de "tu" ("conta pra gente") | C-02-08, C-02-10, C-06-20, C-08-09, C-11-01, C-14-05 | "te" e "você" na mesma frase. |
| Voz da marca | "nós" / "a gente" / "eu" ("Vou", "achei") | C-03-04, C-14-01, C-14-05 | — |
| Repetir ação | "Tentar de novo" / "Tentar novamente" / "Tente novamente" / "Entre novamente" | C-06-07, C-02-21, C-09-09, C-15-02, C-04-01 | — |
| E-mail | "e-mail" / "email" / "Email" | C-03-04, C-13-07, C-13-14 | — |
| CTA de agendar | "Agende agora!" / "Agendar agora" | C-07-02, C-09-14 | — |
| Já tenho conta | "Já tenho conta" / "Já sou cadastrado" | C-01-03, C-06-26 | — |
| Cadastro | "Cadastrar" / "Cadastre-se" / "Cadastra-se" (erro) | C-06-20, C-06-22, C-06-23 | — |
| Denunciar | "Denunciar Perfil" / "Denunciar o artista" / "Denunciar artista" / "Reportar" | C-07-06, C-09-04, C-14-15, C-12-03 | — |
| Suporte | "Falar com a WeCareU" / "Falar com a gente" / "Preciso de ajuda" / "Central de Ajuda" / "suporte" | C-09-04, C-14-06, C-13-03 | Todos levam ao WhatsApp. |
| Senha | "Alterar Senha" / "Mudar Senha" | C-13-03, C-03-10 | — |
| Lista de artistas | aba "Artistas" / "Listagem" / "listagem" | C-05-10, C-07-01, C-08-15 | "Listagem" é jargão interno. |
| Destino "Ver meus agendamentos" | leva à Home (aba "Início"), não à "Agenda" | C-08-26, C-14-03 | — |
| Endereços | "Gerenciar Endereços" / "Meus endereços" | C-13-03, C-01-15 | — |
| Data | "data escolhida" / "dia selecionado"; "25 de maio" / "25 de Maio, Quarta"; "Maio de 2020" | C-06-04, C-06-05, C-06-12, C-08-07, C-07-05 | Mês em maiúscula fere a norma. |
| Tempo | "10s" / "60 s" / "5m00" / "12h00" / "15h" | C-10-01, C-03-07, C-08-20, C-16-01 | — |
| Moeda | sem símbolo ("10 à 150") / "R$" | C-06-09, C-08-24 | — |
| Gênero | masculino genérico ("Ele", "O artista", "Obrigado", "cadastrado") / "(o)" | C-01-07, C-16-01, C-06-26, C-12-11 | — |
| Fim da conta | "excluída" / "encerrada" | C-14-21, C-14-22 | — |
| Pontuação | erros e avisos com e sem ponto final; títulos com ":"; "!!" | C-02-02, C-03-03, C-06-07, C-03-01, C-12-01, C-02-18 | Definir padrão. |
| Capitalização | Title case ("Denunciar Perfil", "Mudar Senha", "Promoções e Ofertas") vs sentence case ("Excluir conta", "Ver mais datas") | vários | — |
| Botão de destaque | caminho seguro ("Não cancelar", "Voltar", "Manter ativada") vs ação destrutiva ("Sair", "Excluir minha conta") | C-09-08, C-10-07, C-13-13, C-14-20 | Padrão invertido entre modais. |
| Promessas acima do MVP | "favorite" (C-06-25); "Sempre teremos/tem um artista" (C-06-20, C-14-05); datas próximas no card do grupo B (C-06-04); avaliar quem não atendeu (C-08-09); "acesso a todos os artistas" (C-06-22); "não precisa lembrar da senha" (C-03-16) | — | Nenhuma copy citada promete reembolso nem chat cliente-artista. |

## Textos sem definição

Nenhum texto pendente no app do cliente: todos os textos de tela estão nos blocos "Textos finais aprovados" (inclui C-08-A21, legenda de pagamento fora do app).

Fora do catálogo de telas, seguem [PENDENTE — diferido] (entram na base de conhecimento; não bloqueiam o Artista):
1. **E-mails transacionais** (aviso ao e-mail antigo, confirmação do novo, verificação do cadastro, código de recuperação, aviso de mudança dos Termos): já há modelos prontos; entram no bloco "E-mails transacionais" no fim deste arquivo.
2. **Termos de Uso e Política de Privacidade** (conteúdo legal, entrega com o advogado) (C-13-A13) e formulação da caixa de aceite a validar com o advogado (C-02-A21).

Fora do catálogo do Cliente:
3. **Lado do Artista:** copys do app do artista, inclusive as modais de "Bloquear cliente".

## E-mails transacionais [PENDENTE — diferido]

Bloco reservado. Os modelos já existem e serão revisados aqui, com as regras de e-mail (ponto final permitido, regra 3).
