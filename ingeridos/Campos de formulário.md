---
tipo: extração
tema: Campos de formulário
fonte: library-design-system
extraido_em: 2026-10-21
idioma: pt-BR
pacotes: ["@wecareu/input-text", "@wecareu/input-masked"]
pé: Pronto. Campo livre 0.2.7 e campo com máscara 0.2.4, com demonstração e teste.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato da biblioteca visual do app (repositório library-design-system) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está. Pode estar à frente ou atrás da base de conhecimento principal. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Campos de formulário

Volta para o [[Panorama do design system]].

Um campo de formulário é o que uma tela pede por escrito. Quando a resposta é uma opção da lista, a peça é [[Escolha em lista]].

São duas peças. O campo livre escreve texto, e-mail, senha, número, endereço web ou telefone. A máscara brasileira é outra peça, vestida em cima do mesmo campo. As duas estão usáveis.

**Pé:** Pronto. O campo livre é `@wecareu/input-text`, versão **0.2.7**. O campo com máscara é `@wecareu/input-masked`, versão **0.2.4**. Os dois têm demonstração e teste.

## Campo livre

A borda é arredondada, na cor da marca, e o texto fica no centro. Cores, raio e letra vêm da [[Identidade visual]].

A peça não desenha um título acima do campo. A ajuda fica dentro, enquanto está vazio. A tela escreve essa frase. Na demonstração, a frase comum é **Digite seu texto**.

### Erro

O erro balança. O campo vai para o lado e volta, uma vez, no momento em que o erro aparece. A borda passa para a cor de erro. Se a tela mandou uma frase, ela aparece embaixo, na cor de erro, e o leitor de tela anuncia.

Há dois caminhos. A tela liga o erro na hora. Na demonstração, a frase é **Campo obrigatório**. Ou a pessoa sai do campo e a checagem falha. Aí a frase é a que a tela preparou. Na demonstração, texto curto usa **Digite ao menos 3 caracteres**.

A checagem ao sair está ligada. Por baixo, o usual é ter pelo menos 3 caracteres e no máximo 255. Se a tela não mandou frase, o campo ainda balança e a borda muda, e nenhuma frase aparece. Campo desabilitado e somente leitura não passam por essa checagem.

### Ícone e senha

Cabe um ícone à esquerda e outro à direita, do [[Vocabulário visual]]. O ícone pode só aparecer, ou responder ao toque. Na demonstração, a esquerda é uma busca, com a ajuda **Buscar**. A direita, num e-mail, é um envelope.

Senha nasce escondida. O olho para mostrar e esconder está na demonstração, não nasce sozinho com o tipo senha. Olho fechado fala **Mostrar senha**. Olho aberto fala **Ocultar senha**. O toque troca.

### Desabilitado e somente leitura

A tela pode chamar o campo de desabilitado ou de somente leitura. Nos dois casos ele fica apagado e não aceita digitação.

### O que se pode pedir

O tipo lista seis, e cada um troca o teclado:

- **Texto.** Teclado comum. Sem formato próprio.
- **E-mail.** Teclado de e-mail. Ao sair, vale se houver texto, um @, mais texto, um ponto e mais texto. A demonstração avisa **Informe um email válido**. O campo não verifica se a caixa existe.
- **Senha.** Texto escondido. Sem regra de força.
- **Número.** Teclado numérico. Por baixo ficam só dígitos. Com o agrupamento ligado, o português mostra **1.234.567** e o inglês mostra **1,234,567**. Sem o agrupamento, a tela mostra os dígitos crus.
- **Endereço web.** Teclado de endereço. Ao sair, precisa começar com http:// ou https://.
- **Telefone.** Teclado de telefone. A forma muda com o idioma, abaixo.

E-mail, senha, endereço e telefone também avisam o aparelho do que é aquele campo, para ele oferecer o que já guardou.

O idioma do campo livre é português ou inglês. O padrão é português.

No telefone em português, o teste com 5511987654321 aparece como **+55 (11) 98765-4321**. Por baixo ficam os dígitos, no máximo 13. Vale com 12 ou 13. No inglês, a forma é um dígito de país, área de três e o resto, no molde +0 (000) 000-0000, com 11 dígitos por baixo. Esse telefone não é a máscara nacional da outra peça.

Ao concluir, o foco pode ir para o campo seguinte. A demonstração mostra os dois, **Primeiro campo** e **Segundo campo**.

### Máscara dentro da demonstração do campo livre

A demonstração do campo livre também veste um CPF. Os dígitos 12345678901 aparecem como **123.456.789-01**. Por baixo ficam só os dígitos. Isso é um exemplo montado na história, no mesmo campo livre.

Os nomes prontos (CPF, CNPJ, CEP, telefone, cartão, data) moram na peça de máscara. Essa peça usa o campo livre por baixo. As duas convivem: a tela pode montar um formato no campo livre, ou pedir um preset já nomeado.

## Máscaras brasileiras

Peça à parte, `@wecareu/input-masked`, versão **0.2.4**. Enquanto a pessoa digita, os pontos, traços, barras e espaços entram sozinhos. O que a tela guarda é o miolo, sem esses sinais.

Se a tela mandar um formato livre e um preset ao mesmo tempo, vale o formato livre. Sem os dois, o campo volta a ser texto livre.

### O que aparece e o que fica por baixo

Os exemplos saem do preset e dos testes.

- **CPF.** Na tela, **123.456.789-01**. Por baixo, **12345678901**. No começo, 1234 já aparece como **123.4**.
- **CNPJ.** Na tela, **12.345.678/0001-99**. Por baixo, **12345678000199**.
- **CEP.** Na tela, **01310-100**. Por baixo, **01310100**.
- **Telefone.** Até 10 dígitos, **(11) 3333-4444**. No 11º, troca para **(11) 98765-4321**. Por baixo, só os dígitos. É o telefone nacional, sem o +55 do campo livre.
- **Cartão.** Na tela, **1234 5678 9012 3456**. Por baixo, **1234567890123456**.
- **Data.** Na tela, **31/12/2025**. Por baixo, **31122025**. A ajuda na demonstração é **DD/MM/AAAA**. Digitar 3112 aparece como **31/12**.
- **Máscara livre.** A demonstração é a placa, no molde de três letras, hífen e quatro números. **ABC1234** aparece como **ABC-1234**. Por baixo fica **ABC1234**. O hífen só existe na tela.

CPF, CNPJ, CEP, cartão e data abrem o teclado numérico. O telefone abre o teclado de telefone. A placa, por ter letras, abre o teclado comum.

Num formato livre, o desenho pede dígito, letra, ou letra e dígito. Qualquer outro sinal é desenhado sozinho.

### O que a máscara confere

Ela não confere se o CPF é verdadeiro, se o CNPJ existe, se o CEP é de uma rua, se o cartão é de uma bandeira, nem se 31/02 é um dia. Ela só dá forma.

A checagem do campo livre continua valendo ao sair: tamanho do miolo, e a frase que a tela mandar. A demonstração de erro já nasce ligada, com **CPF inválido**, e o campo balança.

Data mascarada é digitar o dia. Escolher no calendário é [[Datas]].

### O que isto não é

Ter máscara de CPF não significa que o cadastro do app já pede CPF. Ter cartão não significa que o app cobra. A data digitada não abre um calendário. A peça está pronta para quando uma tela precisar.

## Demonstração e teste

A revisão visual está em [[Como o time revisa a interface]].

O campo livre mostra o uso comum, o erro, o desabilitado, o somente leitura, o ícone à esquerda, o ícone à direita, a senha com olho, o CPF de exemplo e a passagem para o campo seguinte. Os testes cobrem a ajuda, o miolo sem máscara, o erro com borda e balanço, o ícone que responde, o campo que não edita, a checagem ao sair, o e-mail, o telefone com +55 e o número **1.234.567**.

A máscara mostra CPF, CNPJ, CEP, telefone, cartão, data, placa, erro e desabilitado. Os testes confirmam o CPF **123.456.789-01** com miolo **12345678901**, a placa **ABC-1234** com miolo **ABC1234**, e a forma de CNPJ, CEP, cartão e data.
