---
tipo: fonte
arquivo: "ingeridos/core-02-servicos.md"
origem: "extração via IA (Cursor), retrato de 2026-10-21 do repositório BPT-Core, microserviços por trás do BFF; o arquivo avisa que, em conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial"
criado: 2026-10-22
atualizado: 2026-10-22
aliases: ["Serviços"]
---

# Serviços

Retrato de 21/10 do projeto `Br.User.Service.API`. Host `https://serviceapimicroservice.bptsoftware.com.br/`. Banco [[banco-sql-systemservice]], SQL `SystemService`, tabelas `SystemService` e `UserService`.

Agenda e empresa moram neste mesmo projeto, neste mesmo host e neste mesmo banco. O miolo está em [[core-03-agenda]] e [[core-04-empresa-e-colaboradores]]. Esta nota não escreve o miolo delas.

Foto desse serviço. O alvo continua o [[mvp]] já decidido. Onde conflitar, valem [[decisoes-2026-10-20]] e [[decisoes-2026-10-21]].

## Onde isso mora

1. No app. O cadastro de serviços do profissional ainda é pedido de trabalho ([[board-servicos]]), não tela em uso nos apps de 21/10.
2. No BFF. [[bff-servicos]]. O aplicativo fala com `api.wecareu.app`. Nessa porta, listar e apagar recusam sem pessoa reconhecida; criar e editar não conferem. Este serviço é outra camada. Esta nota não apaga esse retrato e não resolve uma pela outra.
3. Neste serviço: `Br.User.Service.API`. O aplicativo não fala com ele. Fala com o BFF.

## O que isso é

O cadastro do que se oferece. São duas listas no mesmo serviço.

A lista da empresa, na tabela `SystemService`, é o serviço disponível naquele sistema: um nome, se ainda está em uso, quando nasceu, quando mudou e quem mudou. Cada linha carrega um sistema e uma empresa. `SystemId` e `EnterpriseId` apontam por nome, com força forte, em [[banco-sql-relacoes]]; não é constraint.

A lista da pessoa, na tabela `UserService`, é o serviço ligado a ela: um valor numérico, se ainda está em uso, as mesmas datas e quem mudou, mais a pessoa, o sistema e a empresa. `UserId` aponta por nome, com força fraca, para a pessoa, em [[banco-sql-relacoes]]; não é constraint. `ServiceId` está sem destino único em [[banco-sql-relacoes]]. A gravação aceita o identificador que vier e não procura esse serviço na lista da empresa.

As duas listas só devolvem o que continua ativo.

## O que já se consegue fazer

Listar os serviços ativos de uma pessoa, dentro de um sistema e de uma empresa. Listar os serviços ativos da empresa naquele sistema.

Incluir um serviço da pessoa e incluir um serviço da empresa. Identificador vazio faz a linha nascer. Identificador preenchido substitui a linha. Na pessoa, viajam o valor, quem mudou, as datas, a pessoa e o `ServiceId`. Não há regra de nome, de valor mínimo nem de serviço repetido. Incluir grava antes da trilha.

Editar os dois. O pedido manda a linha inteira e cai na mesma gravação da inclusão. Editar grava antes da trilha. Se a trilha quebra, a linha já foi gravada.

Apagar um serviço da pessoa e apagar um serviço da empresa. A linha permanece, fica fora de uso e some das listas. A trilha roda depois que a linha já mudou. A trilha da pessoa grava a tabela `UserService` e um banco com outro nome. A trilha do catálogo não grava a tabela `SystemService`.

Nas quatro ações a checagem está invertida: token aceito pelo login vira recusa, e token recusado deixa listar, incluir, editar e apagar. A autenticação preparada na subida não entra no pedido.

## Em que pé está

| Pé | O que esta nota mostra |
|---|---|
| Feito com ressalva | Listar o que está ativo, da pessoa e da empresa. Incluir e apagar, no dado. A checagem está invertida nas quatro ações |
| Pela metade | Incluir e editar gravam antes da trilha. Essa trilha, nas duas listas, grava banco e tabela de endereço. A trilha do catálogo não grava `SystemService`. Na edição, a diferença de empresa ou de sistema só é recusada quando o cabeçalho de gestão vem preenchido |
| Casca | A autenticação preparada na subida. Ela não entra no caminho do pedido |
| Operação interna | Falha ao listar, gravar ou apagar. O ocorrido vai para a operação e a chamada devolve o erro |

## O que esta nota não cobre

O aplicativo. O cadastro de serviços do profissional segue como pedido de trabalho em [[board-servicos]]. O miolo de agenda e de empresa está em [[core-03-agenda]] e [[core-04-empresa-e-colaboradores]]. O miolo de [[bff-servicos]], além do contraste de sessão entre as duas camadas. O que o valor numérico representa, duração, descrição e foto do serviço. Senha, string de conexão e identificador de empresa ou de aplicativo. O desenho do banco além do necessário: [[banco-sql-systemservice]] e [[banco-sql-relacoes]].

## Incertezas

No Windows e no Linux a subida troca o marcador de catálogo por `UserLogin`. O compose deste repositório aponta `Database` para `SystemService`. Por este repositório não dá para fechar qual banco o host publicado está usando agora. O wikilink permanece [[banco-sql-systemservice]].

A conferência manda o cabeçalho de sessão inteiro com outro prefixo na frente. No formato usual, o login recusa e esta camada deixa passar. Quem chamar com o token cru, e o login aceitar, recebe recusa. Não há, neste serviço, um contrato único do formato da sessão.

O valor é um número. Não dá para fechar se é preço.

Ver [[bpt-core]] e [[core-00-o-que-e-este-nucleo]].
