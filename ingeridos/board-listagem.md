> Aviso de versionamento (extração via IA — Azure DevOps): Este documento é um retrato dos épicos, histórias e tarefas do board WeCareU no momento da extração. Conserva o título original de cada item, inclusive os que só têm nome. Não é decisão de produto e não preenche o que o board deixou vazio. Pode estar à frente ou atrás da base de conhecimento. Em caso de conflito com o repositório oficial ou com uma decisão da empresa, vale a fonte oficial.

# Listagem

Extração em 2026-10-21. Organização piresbno1992, projeto WeCareU.

## Épico 330 — Sistema de listagem

**Tipo:** Epic
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** nenhum
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/330
**Tags:** nenhuma

**Descrição:** ausente

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-01T18:19:10.997Z

```
Paired with WECAREU-2 - https://wecareu.atlassian.net/browse/WECAREU-2

 [###getint.io:1|t4df7c9de]
```

### História 145 — Criar Carregamento de Artistas por endereço, sem cadastro

**Tipo:** User Story
**Estado:** New
**Área:** WeCareU\ARTIST
**Responsável:** Bruno Pires de Almeida
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/145
**Tags:** nenhuma

**Descrição:**

Trazer lista de artistas para usuario não logado.

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-08-01T19:25:12.247Z

```
Paired with WECAREU-7 - https://wecareu.atlassian.net/browse/WECAREU-7

 [###getint.io:1|t4df7c9de]
```

sem tarefas

### História 359 — Listagem de delivery 

**Tipo:** User Story
**Estado:** Active
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/359
**Tags:** nenhuma

**sem descrição**

#### Tarefa 362 — [BE] Listagem de serviços dinâmico 

**Tipo:** Task
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** nenhum
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/362
**Tags:** nenhuma

**Descrição:**

Usar o mesmo endpoint com variáveis para geração da lista de atendentes por tipo de atendimento.

fazer a pesquisa pela cadastro de serviços do usuario e subir isso de forma invertida, usando left join para agrupar em ordem

UserService;
Address;
User;
Enterprise;
Forma de Pagamento;

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 446 — [FE] Criação do card de listagem gratuito

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/446
**Tags:** nenhuma

**Descrição:**

Criação do card de listagem gratuito desenvolvidos no figma.

Nesse momento faremos somente cards de listagem gratuita.

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/73422194-970f-40ba-9c9a-85a82da5b4fe?fileName=image.png)

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-04-02T23:33:49.063Z

```
Completing Pull Request 144 and the associated work items.
```

#### Tarefa 447 — [FE] Criação de tag propaganda para se cadastrar

**Tipo:** Task
**Estado:** Completed
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/447
**Tags:** nenhuma

**Descrição:**

Devemos criar uma tag que aparecerá a cada 4 cards aonde teremos uma chamada do cliente para se cadastrar na plataforma.

Ela inicialmente contará com três frases que serão randômicas entre elas.

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/1a76b4d0-852f-4569-b8d0-f5fea20b64e9?fileName=image.png)

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/1caa3503-ee9c-444f-8fbe-49a15734be84?fileName=image.png)

![Image](https://dev.azure.com/piresbno1992/9b3b729e-cf2f-4589-a314-825222b600e6/_apis/wit/attachments/6387c3d3-7248-4577-893d-5700c39bafae?fileName=image.png)

**Critério de aceite:** ausente

**Comentários:**

- Andrey Didoff do Nascimento — 2025-04-02T23:36:09.687Z

```
Completing Pull Request 145 and the associated work items.
```

#### Tarefa 448 — [FE] Integração dos cards de listagem com back-end

**Tipo:** Task
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/448
**Tags:** nenhuma

**Descrição:**

Precisamos criar uma integração com o back-end no qual consumiremos os dados do back via api e exibiremos em tela, respeitando a ordenagem de listagem

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 449 — [FE] Criação dos filtros de listagem

**Tipo:** Task
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/449
**Tags:** nenhuma

**Descrição:**

Precisamos criar os filtros de listagem a serem aplicados para mudar a ordem da listagem.

**Critério de aceite:** ausente

**Comentários:** ausente

#### Tarefa 451 — [FE] Criar campo de troca de endereço no topo da listagem

**Tipo:** Task
**Estado:** New
**Área:** WeCareU\GLOBAL
**Responsável:** Andrey Didoff do Nascimento
**Link:** https://dev.azure.com/piresbno1992/WeCareU/_workitems/edit/451
**Tags:** nenhuma

**sem descrição**
