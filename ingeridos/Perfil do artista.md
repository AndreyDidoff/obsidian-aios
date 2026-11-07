---
tipo: extração
tema: Perfil do artista
fonte: ui_worker
extraido_em: 2026-10-21
idioma: pt-BR
pé: Construído como menu; destinos mistos.
---

Aviso de versionamento (extração via IA — Cursor): Este documento é um retrato do aplicativo do artista (repositório ui_worker) no momento da extração. Descreve, em linguagem de produto, o que já está construído e em que pé está cada parte. Pode estar à frente ou atrás da base de conhecimento principal. Se divergir do repositório oficial ou de uma decisão da empresa, vale a fonte oficial.

# Perfil do artista

Volta para [[Mapa do app do artista]].

**Pé:** Construído como menu; destinos mistos.

O Perfil é a última aba. A barra, da esquerda para a direita, é Início, Pedidos, Agenda, Planos e Perfil. A primeira é [[Início do artista]]. Dentro da aba, o título da tela é **Meu Perfil**.

O menu está inteiro e dá para percorrer. Os destinos não estão no mesmo pé: senha, biometria, notificações, sobre, termos, privacidade e sair funcionam; editar perfil e endereços só avisam que vem depois; a central de ajuda abre o site.

O sentido de cada pé está em [[Mapa do app do artista]].

## O que a pessoa vê

| Seção | Item | Subtítulo | Para onde vai | Pé do destino |
|-------|------|-----------|---------------|---------------|
| Dados Pessoais | Editar Perfil | Nome, foto, documento e outros dados | Tela com a frase de em breve | Casca |
| Segurança | Alterar Senha | Mude sua senha de acesso | Fluxo de troca de senha | Construído |
| Segurança | Biometria | Ativada ou Desativada | Interruptor nesta mesma tela | Construído |
| Endereços | Gerenciar Endereços | Adicionar, editar ou remover endereços | Tela com a frase de em breve | Casca |
| Notificações | Configurações de Notificação | Gerencie como você recebe notificações | Tela de preferências | Construído |
| Suporte | Central de Ajuda | Encontre respostas para suas dúvidas | O site, fora do app | Parcial |
| Suporte | Sobre o App | Versão e informações do aplicativo | Tela sobre o app | Construído |
| Legal | Termos de Uso | Leia nossos termos de uso | Texto dos termos | Construído |
| Legal | Política de Privacidade | Como protegemos seus dados | Texto da privacidade | Construído |

A biometria só entra nessa lista se o aparelho tem. O detalhe está na seção Segurança.

No fim da lista, fora das seções, há o texto **Sair da sua conta**.

## Dados Pessoais

**Editar Perfil** abre uma tela cujo título é **Dados Pessoais**. O único texto é: "Em breve você poderá editar seus dados pessoais aqui." No topo há um botão de fechar, sem rótulo, que volta ao perfil.

Os dados foram pedidos em [[Cadastro do artista]] e não voltam para edição. O que falta está em [[O que ainda não está no app do artista]].

## Segurança

**Alterar Senha** existe no menu, com o subtítulo "Mude sua senha de acesso". Abre um fluxo de verdade para trocar a senha, com o texto Voltar para o perfil. O passo a passo está em [[Entrar, senha e biometria do artista]].

**Biometria** também existe no menu, com um interruptor. O subtítulo mostra **Ativada** ou **Desativada**, conforme a escolha atual. O item só aparece se o aparelho tem digital ou reconhecimento facial e já existe um cadastro disso no próprio telefone. Sem isso, a linha some. O que acontece ao ligar e ao desligar está em [[Entrar, senha e biometria do artista]].

Alterar e-mail aparece nos textos do app ("Alterar Email", "Mude seu email de acesso") e não entra neste menu.

## Endereços

**Gerenciar Endereços** abre uma tela com o mesmo título. O único texto é: "Em breve você poderá gerenciar seus endereços aqui." O fechar do topo, sem rótulo, volta ao perfil.

O endereço em si está em [[Endereços do artista]].

## Notificações, ajuda, sobre, termos e privacidade

Estes cinco itens saem deste menu e o conteúdo de cada um está em [[Avisos, ajuda e regras do artista]].

- **Configurações de Notificação** abre a tela de preferências. Há o texto Voltar.
- **Central de Ajuda** não abre tela nenhuma. Abre o site `https://wecareu.app/suporte`. Se o navegador não abrir, o app avisa "Erro" e "Não foi possível abrir o link".
- **Sobre o App**, **Termos de Uso** e **Política de Privacidade** abrem tela própria, cada uma com o texto Voltar.

## Sair

O texto no fim da tela é **Sair da sua conta**. Ao tocar, o app pede confirmação:

- Título: **Sair da WeCareU**
- Mensagem: **Tem certeza que deseja sair da sua conta WeCareU?**
- **Cancelar** fica na conta
- **Sair** encerra

Ao confirmar, a pessoa sai das abas e volta para a entrada de quem não está na conta. A sessão deste aparelho acaba mesmo se a saída no serviço falhar. A biometria que estava ligada para esta conta neste aparelho deixa de valer.
