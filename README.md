# 📝 Roteiro da Atividade: Definição de Tarefas e Planejamento de Sprint — Connexa (Etapa 2) 

## 🎯 Objetivo da Atividade

Dar continuidade ao projeto **Connexa**, detalhando as **tarefas técnicas associadas às User Stories** definidas no backlog (Etapa 1), organizando um **planejamento inicial de Sprint** no **Azure DevOps Boards** e explorando o uso de ferramentas de IA para otimizar o processo.

## 🔄 Continuidade do Cenário Fictício

**Produto:** *Connexa*
**Etapa Anterior (Etapa 1):** O backlog do produto foi criado com User Stories priorizadas, descrevendo as funcionalidades sob a ótica do usuário — conforme o roteiro disponível em [03-DefinicaoRequisitos](https://github.com/EngSoftwareFatecRL/03-DefinicaoRequisitos).
**Etapa Atual (Etapa 2):** Transformar as User Stories em **tarefas técnicas** executáveis e planejar a primeira Sprint do projeto, que representa o primeiro ciclo de desenvolvimento.

## 👥 Organização da Atividade

  * **Grupos:** 3 a 5 alunos (os mesmos grupos formados na Etapa 1).
  * **Ferramenta:** Azure DevOps Boards — utilize o **mesmo projeto** criado na Etapa 1 (ex: `Connexa-Grupo01`). Não crie um novo projeto.
  * **Duração sugerida da Sprint:** 1 a 2 semanas (para fins de exercício acadêmico).

## 🚀 Criação das Tarefas a partir das User Stories

Cada **User Story** deve ser detalhada em **tarefas menores** e mais específicas, que serão atribuídas aos membros do time. As tarefas descrevem **ações técnicas** que precisam ser realizadas para que a funcionalidade da User Story seja completamente implementada.

**Boas práticas para criar tarefas:**

  * **Especificidade:** A tarefa deve descrever uma ação clara (Ex: "Criar componente de botão" em vez de "Fazer a tela").
  * **Granularidade:** Deve ser pequena o suficiente para ser concluída por uma pessoa em um ou dois dias.
  * **Baixo acoplamento:** Sempre que possível, mantenha as tarefas o mais desacopladas possível para facilitar o trabalho paralelo. Quando houver dependências reais entre tarefas, registre-as no Azure DevOps usando os campos de relacionamento (`Predecessor`/`Successor` ou `Related`).
  * **Estimativa de esforço:** Defina uma unidade de estimativa para a equipe (horas, story points ou T-shirt sizing) e aplique-a de forma consistente. Veja sugestões de leitura na seção de Referências.

### 🗂️ Hierarquia de Work Items no Azure DevOps (processo Agile)

O processo Agile do Azure DevOps organiza o trabalho em uma hierarquia: **Epic → Feature → User Story → Task**. Como o backlog da Etapa 1 já contém as **User Stories**, nesta etapa vamos criar **Tasks** como filhas dessas User Stories. Ao criar uma Task, sempre vincule-a à sua User Story usando o campo **Parent** (ou criando-a a partir do botão `+` dentro da própria User Story).

### Exemplo Prático

#### 📌 User Story: Cadastro de Usuário

**Descrição:**
*Como um aluno universitário, quero me cadastrar na plataforma Connexa usando meu e-mail institucional, para que eu possa criar, buscar e participar de grupos de estudo com segurança e legitimidade.*

**Critérios de Aceitação (já definidos na Etapa 1):**

  * Campos obrigatórios: nome completo, e-mail institucional, curso, período/semestre e senha.
  * Validação de domínio do e-mail.
  * Senha com regras de complexidade (mínimo 8 caracteres, maiúscula, minúscula e número).
  * O sistema não deve permitir o cadastro de um e-mail que já exista na base de dados.
  * Mensagens de erro claras.
  * Após o preenchimento correto dos dados, o usuário deve ser redirecionado para a tela de login ou para uma página de sucesso.
  * Envio de e-mail de confirmação.

**Tarefas técnicas derivadas da User Story:**

1.  **Front-end:** Criar a tela (View) de cadastro de usuário com os campos necessários
2.  **Front-end:** Implementar a validação dos campos obrigatórios no formulário
3.  **Front-end:** Implementar a validação de domínio do e-mail institucional
4.  **Front-end:** Implementar a validação das regras de complexidade da senha em tempo real
5.  **Front-end:** Implementar o redirecionamento para a tela de login (ou página de sucesso) após cadastro bem-sucedido
6.  **Back-end:** Criar o endpoint `POST /api/usuarios/cadastro` para receber os dados
7.  **Back-end:** Implementar a lógica de negócio para validar os dados recebidos (regras de e-mail e senha)
8.  **Back-end:** Implementar a verificação de e-mail duplicado na base de dados, retornando erro adequado (`HTTP 409 Conflict`) caso já exista
9.  **Banco de Dados:** Modelar e criar a tabela `usuarios` no banco de dados
10. **Back-end:** Integrar o endpoint de cadastro para persistir os dados do novo usuário na tabela `usuarios`
11. **Back-end:** Implementar o serviço de envio de e-mail de confirmação de cadastro
12. **Testes (sugerido):** Criar testes unitários para o endpoint de cadastro no back-end

> **Sobre testes:** Para cada tarefa de back-end ou regra de negócio, considere planejar uma tarefa correspondente de testes. Embora os testes não sejam obrigatórios nesta etapa, sua inclusão é fortemente recomendada como boa prática de engenharia.

### Exemplo de Detalhamento de uma Tarefa Técnica (Back-end)

Apenas o título de uma tarefa pode não ser suficiente. Uma boa prática é detalhar a tarefa dentro da ferramenta (Azure DevOps), garantindo que quem for executá-la saiba exatamente o que precisa ser feito. Veja um exemplo para a tarefa 6:

> **Item de Trabalho: Tarefa (Task)**
>
> * **User Story Pai:** Cadastro de Usuário
> * **Título:** Back-end: Criar endpoint POST `/api/usuarios/cadastro`
> * **Responsável:** `[Nome do Integrante do Grupo]`
> * **Esforço Estimado:** `[Ex: 4 Horas]`
> * **Descrição:**
>   Desenvolver o endpoint inicial na API que será responsável por receber os dados do formulário de cadastro do front-end. O objetivo desta tarefa é criar a "porta de entrada" dos dados, sem ainda implementar as lógicas complexas de validação e salvamento no banco, que serão tratadas em tarefas subsequentes.
>
>     * **Método HTTP:** `POST`
>     * **URL:** `/api/usuarios/cadastro`
>     * **Corpo da Requisição (Request Body):** O endpoint deve esperar um objeto JSON com a seguinte estrutura:
>       ```json
>       {
>         "nomeCompleto": "string",
>         "email": "string",
>         "curso": "string",
>         "semestre": "integer",
>         "senha": "string"
>       }
>       ```
>     * **Observação sobre a senha:** O tratamento seguro da senha (hash, política de armazenamento) será abordado em tarefa subsequente. Nesta tarefa, apenas validar a presença do campo no payload.
> * **Critérios de Aceitação (da Tarefa):**
>
>     * ✅ O endpoint está funcional e acessível na rota `/api/usuarios/cadastro`
>     * ✅ O endpoint aceita requisições utilizando o método `POST`
>     * ✅ Ao receber uma requisição com o corpo JSON no formato correto, o endpoint deve retornar uma resposta de sucesso (`HTTP 201 Created`)
>     * ✅ Ao receber uma requisição com o corpo malformado ou faltando campos essenciais, o endpoint deve retornar uma resposta de erro (`HTTP 400 Bad Request`)

### Exemplo de Detalhamento de uma Tarefa Técnica (Front-end)

Veja agora um exemplo para a tarefa 1 (front-end):

> **Item de Trabalho: Tarefa (Task)**
>
> * **User Story Pai:** Cadastro de Usuário
> * **Título:** Front-end: Criar tela de cadastro de usuário
> * **Responsável:** `[Nome do Integrante do Grupo]`
> * **Esforço Estimado:** `[Ex: 6 Horas]`
> * **Descrição:**
>   Desenvolver a interface gráfica do formulário de cadastro, contendo os campos definidos nos critérios de aceitação da User Story. Esta tarefa cobre apenas a estrutura visual e a maqueteção dos campos; validações e integração com o back-end serão tratadas em tarefas subsequentes.
>
>     * **Campos do formulário:** nome completo, e-mail institucional, curso, período/semestre, senha, confirmação de senha
>     * **Componentes:** inputs com labels, botão "Cadastrar", link para tela de login
> * **Critérios de Aceitação (da Tarefa):**
>
>     * ✅ Todos os campos da User Story estão presentes na tela
>     * ✅ O layout está responsivo (desktop e mobile)
>     * ✅ O botão "Cadastrar" está visível e desabilitado por padrão (será habilitado em tarefa de validação)
>     * ✅ Há um link funcional para a tela de login

## 🤖 (Opcional) Usando IA para Geração de Tarefas com Agentes (GitHub Copilot)

> **Nota sobre a mudança em relação à Etapa 1:** Na Etapa 1, o uso de IA e a análise crítica dos seus outputs eram obrigatórios e avaliados, pois o foco era aprender a formular prompts e questionar os resultados gerados. Nesta etapa, o ponto central é o **produto gerado pelo grupo** — o planejamento do Sprint com tarefas bem definidas. O uso de IA é oferecido como recurso de apoio, mas o domínio do processo de tasking é responsabilidade do time.

Ferramentas de IA, como o **GitHub Copilot**, podem ser usadas como assistentes para acelerar o brainstorming e a criação de tarefas técnicas. Elas podem sugerir uma lista inicial de trabalho com base na descrição de uma User Story.

### Como usar:

1.  Abra um editor de texto ou o próprio campo de descrição no Azure DevOps.
2.  Escreva um "prompt" claro, fornecendo o contexto da User Story e dos Critérios de Aceitação.
3.  Peça à IA para gerar uma lista de tarefas.

#### Exemplo de Prompt para uma User Story do seu Backlog:

> **Importante:** Use as User Stories e Critérios de Aceitação **do backlog que o seu grupo criou na Etapa 1**, não os do exemplo abaixo. O template abaixo mostra apenas a estrutura do prompt; substitua o conteúdo pelos dados reais do seu projeto.

```text
Com base na seguinte User Story e seus Critérios de Aceitação para a plataforma "Connexa", sugira uma lista de tarefas técnicas detalhadas para a sua implementação. Separe as tarefas por área (Front-end, Back-end, Banco de Dados).

**User Story: [Título da sua User Story do backlog da Etapa 1]**
*[Descrição da sua User Story no formato "Como um... quero... para que..."]*

**Critérios de Aceitação:**
- [Critério 1 definido pelo grupo na Etapa 1]
- [Critério 2 definido pelo grupo na Etapa 1]
- [demais critérios...]
```

**⚠️ Atenção:** A lista gerada pela IA é um **ponto de partida**. O time é responsável por revisar, refinar, adicionar ou remover tarefas com base no conhecimento técnico da equipe e na arquitetura do projeto. A IA é um copiloto, não o piloto.

### ⛔ Antipadrões a evitar

  * **Tarefa monolítica:** "Fazer a tela de login inteira" — muito grande, abrange múltiplas ações técnicas.
  * **Tarefa atribuída ao grupo todo:** cada tarefa deve ter **um único responsável**, mesmo que outros colaborem.
  * **Tarefa sem critério de aceitação:** sem critérios objetivos não há como verificar se a tarefa está concluída.
  * **Tarefa que descreve fim em vez de meio:** "Funcionalidade de cadastro pronta" descreve o resultado final da User Story, não uma ação técnica.
  * **Estimativas emícas:** "vai ficar pronto quando ficar". Sempre registre uma estimativa, mesmo que aproximada.

## 🗂 Planejamento da Sprint

No **Azure Boards → Sprints**:

1.  **Criação da Sprint:** Crie a sua primeira Sprint (ex: `Sprint 1 - Cadastro, Login e Criação de Grupos`).

2.  **Definição da Duração:** Configure a duração da Sprint (sugestão: 1 a 2 semanas).

3.  **Seleção de Itens:** Arraste as **User Stories mais prioritizadas** do Backlog para dentro da Sprint que você criou.

4.  **Detalhamento das Tarefas (Tasking):** Dentro da Sprint, quebre cada User Story em tarefas técnicas, como detalhado nos exemplos acima.

5.  **Atribuição de Responsáveis:** Distribua as tarefas entre os membros do grupo. É fundamental que cada integrante tenha ao menos duas tarefas atribuídas.

6.  **Definição de "Pronto" (Definition of Done - DoD):** O planejamento da Sprint é o momento certo para formalizar o DoD — antes de qualquer linha de código ser escrita, o time precisa ter um acordo explícito sobre o que significa "terminado". Isso evita ambiguidades durante a execução e garante qualidade consistente entre as entregas. Uma tarefa ou história só é considerada concluída quando atende a todos os critérios do DoD.

    **Exemplo de "Definition of Done" para o projeto Connexa:**

      * O código foi desenvolvido e submetido ao repositório central no **Azure Repos** (vinculado ao mesmo projeto Azure DevOps utilizado para o Boards).
      * (Sugerido) Testes unitários criados e passando com sucesso para as tarefas de back-end e regras de negócio.
      * A funcionalidade atende a todos os Critérios de Aceitação da User Story.
      * O código foi revisado por pelo menos um outro membro do time (Code Review).
      * Não há débitos técnicos conhecidos introduzidos pela nova funcionalidade.

### 🔄 Ciclo de vida de uma Task no Azure Boards

No processo Agile do Azure DevOps, cada Task transita pelos estados **New → Active → Closed** (ou *Removed*, quando descartada). No quadro Kanban da Sprint, esses estados aparecem comumente como as colunas **To Do**, **In Progress** e **Done**. Ao longo do exercício, o time deve mover os cards entre as colunas conforme o trabalho avança, mantendo o quadro como reflexo fiel do estado real das tarefas.

## ✅ Critérios de Entrega (via Microsoft Teams)

Cada grupo deverá realizar uma única entrega na plataforma Microsoft Teams, contendo:

1.  **URL do Projeto no Azure DevOps:** No painel do seu projeto, copie a URL completa do navegador. Deve ser o **mesmo projeto** utilizado na Etapa 1 (`Connexa-Grupo01` ou equivalente), com o backlog de User Stories já criado anteriormente visível.
2.  **Captura de tela (screenshot) da Sprint Ativa no Azure Boards:** Deve exibir o quadro da Sprint, mostrando as User Stories selecionadas e suas respectivas tarefas distribuídas nas colunas (Ex: *To Do*, *In Progress*, *Done*).
3.  **Captura de tela (screenshot) de uma User Story Expandida:** Deve mostrar claramente uma das User Stories dentro da Sprint com sua lista de tarefas técnicas associadas.

## 📒 Glossário Rápido

| Termo | Significado |
|---|---|
| **Backlog** | Lista priorizada de User Stories pendentes do produto. |
| **User Story** | Descrição de uma funcionalidade sob a ótica do usuário (criada na Etapa 1). |
| **Task** | Ação técnica executável derivada de uma User Story. |
| **Sprint** | Ciclo curto e de prazo fixo (timebox) para entregar um conjunto de User Stories. |
| **Tasking** | Atividade de quebrar uma User Story em Tasks técnicas. |
| **DoD (Definition of Done)** | Acordo do time sobre o que significa uma tarefa/história estar "pronta". |
| **Code Review** | Revisão do código por outro membro do time antes de integrá-lo ao repositório. |
| **Kanban Board** | Quadro visual com colunas que representam o estado das tarefas (To Do, In Progress, Done). |

## 🔜 Próxima Etapa

A Etapa 3 (final) envolverá a **implementação efetiva da primeira Sprint** planejada aqui: cada grupo executará as tarefas definidas, integrará o código no Azure Repos e moverá os cards no Kanban até sua conclusão, exercitando o ciclo completo de desenvolvimento iterativo.

## 📖 Referências e Recursos Complementares

  * **Microsoft Learn -- Azure DevOps:**
      * [Organizar trabalho em sprints](https://learn.microsoft.com/pt-br/azure/devops/boards/sprints/define-sprints)
      * [Criar e gerenciar tarefas no Azure Boards](https://learn.microsoft.com/pt-br/azure/devops/boards/backlogs/add-tasks)
      * [Vincular work items (Parent/Child, Predecessor/Successor)](https://learn.microsoft.com/pt-br/azure/devops/boards/queries/link-work-items-support-traceability)
      * [Azure Repos — visão geral](https://learn.microsoft.com/pt-br/azure/devops/repos/get-started/what-is-repos)
  * **Agile/Scrum:**
      * [Scrum.org -- O Guia do Scrum (oficial, PT-BR)](https://www.scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-Portuguese-Brazilian.pdf)
  * **Estimativas de esforço:**
      * [Atlassian — Story Points and Estimation](https://www.atlassian.com/agile/project-management/estimation)
      * [Mountain Goat Software — What are Story Points? (Mike Cohn)](https://www.mountaingoatsoftware.com/blog/what-are-story-points)
      * [Microsoft Learn — Estimating work in Azure Boards](https://learn.microsoft.com/pt-br/azure/devops/boards/sprints/best-practices-scrum)
  * **IA em Desenvolvimento:**
      * [GitHub Copilot - Documentação](https://docs.github.com/pt/copilot)
      * [Azure DevOps MCP Server (repositório oficial)](https://github.com/microsoft/azure-devops-mcp)
  * **Vídeos:**
      * [Azure DevOps -- Criando e gerenciando Sprints (YouTube, PT-BR)](https://www.youtube.com/watch?v=7e-wAwj8fGo)
      * [Azure DevOps -- Plan your work with Azure Boards (YouTube, EN)](https://www.youtube.com/watch?v=SbFKi6Hflc0)

## 🔗 Integração Avançada: Azure DevOps MCP (Opcional)

Assim como na Etapa 1, grupos que desejarem podem utilizar o **Azure DevOps MCP Server** para criar e gerenciar Tasks diretamente a partir do chat com a IA, integrando o GitHub Copilot ao seu projeto Azure DevOps. Configuração no [repositório oficial](https://github.com/microsoft/azure-devops-mcp). Esta etapa é opcional e não será cobrada na avaliação.
