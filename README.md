# 📝 Roteiro da Atividade: Definição de Tarefas e Planejamento de Sprint — Connexa (Etapa 2) 

## 🎯 Objetivo da Atividade

Dar continuidade ao projeto **Connexa**, detalhando as **tarefas técnicas associadas às User Stories** definidas no backlog (Etapa 1), organizando um **planejamento inicial de Sprint** no **Azure DevOps Boards** e explorando o uso de ferramentas de IA para otimizar o processo.

-----

## 🔄 Continuidade do Cenário Fictício

**Produto:** *Connexa*
**Etapa Anterior (Etapa 1):** O backlog do produto foi criado com User Stories priorizadas, descrevendo as funcionalidades sob a ótica do usuário.
**Etapa Atual (Etapa 2):** Transformar as User Stories em **tarefas técnicas** executáveis e planejar a primeira Sprint do projeto, que representa o primeiro ciclo de desenvolvimento.

-----

## 👥 Organização da Atividade

  * **Grupos:** 3 a 5 alunos.
  * **Ferramenta:** Azure DevOps Boards.
  * **Duração sugerida da Sprint:** 1 a 2 semanas (para fins de exercício acadêmico).

-----

## 🚀 Criação das Tarefas a partir das User Stories

Cada **User Story** deve ser detalhada em **tarefas menores** e mais específicas, que serão atribuídas aos membros do time. As tarefas descrevem **ações técnicas** que precisam ser realizadas para que a funcionalidade da User Story seja completamente implementada.

**Boas práticas para criar tarefas:**

  * **Especificidade:** A tarefa deve descrever uma ação clara (Ex: "Criar componente de botão" em vez de "Fazer a tela").
  * **Granularidade:** Deve ser pequena o suficiente para ser concluída por uma pessoa em um ou dois dias.
  * **Independência:** Sempre que possível, tarefas devem ser independentes para facilitar o trabalho paralelo.

### Exemplo Prático

#### 📌 User Story: Cadastro de Usuário

**Descrição:**
*Como um aluno universitário, quero me cadastrar na plataforma Connexa usando meu e-mail institucional, para que eu possa criar, buscar e participar de grupos de estudo com segurança e legitimidade.*

**Critérios de Aceitação (já definidos na Etapa 1):**

  * Campos obrigatórios: nome completo, e-mail institucional, curso, período/semestre e senha.
  * Validação de domínio do e-mail.
  * Senha com regras de complexidade (mínimo 8 caracteres, maiúscula, minúscula e número).
  * Mensagens de erro claras.
  * Envio de e-mail de confirmação.

**Tarefas técnicas derivadas da User Story:**

1.  **Front-end:** Criar a tela (View) de cadastro de usuário com os campos necessários.
2.  **Front-end:** Implementar a validação dos campos obrigatórios no formulário.
3.  **Front-end:** Implementar a validação de domínio do e-mail institucional.
4.  **Front-end:** Implementar a validação das regras de complexidade da senha em tempo real.
5.  **Back-end:** Criar o endpoint `POST /api/usuarios/cadastro` para receber os dados.
6.  **Back-end:** Implementar a lógica de negócio para validar os dados recebidos (regras de e-mail e senha).
7.  **Banco de Dados:** Modelar e criar a tabela `usuarios` no banco de dados.
8.  **Back-end:** Integrar o endpoint de cadastro para persistir os dados do novo usuário na tabela `usuarios`.
9.  **Back-end:** Implementar o serviço de envio de e-mail de confirmação de cadastro.
10. **Testes:** Criar testes unitários para o endpoint de cadastro no back-end.

-----

### Exemplo de Detalhamento de uma Tarefa Técnica

Apenas o título de uma tarefa pode não ser suficiente. Uma boa prática é detalhar a tarefa dentro da ferramenta (Azure DevOps), garantindo que quem for executá-la saiba exatamente o que precisa ser feito. Veja um exemplo para a tarefa 5:

**------------------------------------------------------------------**

**Item de Trabalho: Tarefa (Task)**

  * **User Story Pai:** Cadastro de Usuário

  * **Título:** Back-end: Criar endpoint POST `/api/usuarios/cadastro`

  * **Responsável:** `[Nome do Integrante do Grupo]`

  * **Esforço Estimado:** `[Ex: 4 Horas]`

  * **Descrição:**
    Desenvolver o endpoint inicial na API que será responsável por receber os dados do formulário de cadastro do front-end. O objetivo desta tarefa é criar a "porta de entrada" dos dados, sem ainda implementar as lógicas complexas de validação e salvamento no banco, que serão tratadas em tarefas subsequentes.

      * **Método HTTP:** `POST`
      * **URL:** `/api/usuarios/cadastro`
      * **Corpo da Requisição (Request Body):** O endpoint deve esperar um objeto JSON com a seguinte estrutura:
        ```json
        {
          "nomeCompleto": "string",
          "email": "string",
          "curso": "string",
          "semestre": "integer",
          "senha": "string"
        }
        ```

  * **Critérios de Aceitação (da Tarefa):**

      * ✅ O endpoint está funcional e acessível na rota `/api/usuarios/cadastro`.
      * ✅ O endpoint aceita requisições utilizando o método `POST`.
      * ✅ Ao receber uma requisição com o corpo JSON no formato correto, o endpoint deve retornar uma resposta de sucesso (`HTTP 201 Created`).
      * ✅ Ao receber uma requisição com o corpo malformado ou faltando campos essenciais, o endpoint deve retornar uma resposta de erro (`HTTP 400 Bad Request`).

**------------------------------------------------------------------**

-----

## 🤖 (Opcional) Usando IA para Geração de Tarefas com Agentes (GitHub Copilot)

Ferramentas de IA, como o **GitHub Copilot**, podem ser usadas como assistentes para acelerar o brainstorming e a criação de tarefas técnicas. Elas podem sugerir uma lista inicial de trabalho com base na descrição de uma User Story.

### Como usar:

1.  Abra um editor de texto ou o próprio campo de descrição no Azure DevOps.
2.  Escreva um "prompt" claro, fornecendo o contexto da User Story e dos Critérios de Aceitação.
3.  Peça à IA para gerar uma lista de tarefas.

#### Exemplo de Prompt para uma Nova User Story:

```prompt
Com base na seguinte User Story e seus Critérios de Aceitação para a plataforma "Connexa", sugira uma lista de tarefas técnicas detalhadas para a sua implementação. Separe as tarefas por área (Front-end, Back-end, Banco de Dados).

**User Story: Criação de Grupo de Estudos**
*Como um usuário cadastrado, eu quero criar um novo grupo de estudos, para que eu possa organizar sessões de estudo com outros alunos.*

**Critérios de Aceitação:**
- O formulário de criação deve incluir os campos: matéria, objetivo (ex: prova, projeto), local (online/presencial) e um limite de participantes.
- O sistema deve validar que todos os campos são de preenchimento obrigatório.
- O limite de participantes deve ser um número entre 2 e 20.
- O usuário que cria o grupo é automaticamente definido como o administrador do grupo.
- Após a criação, o grupo deve ser exibido na lista "Meus Grupos" do usuário.
```

**⚠️ Atenção:** A lista gerada pela IA é um **ponto de partida**. O time é responsável por revisar, refinar, adicionar ou remover tarefas com base no conhecimento técnico da equipe e na arquitetura do projeto. A IA é um copiloto, não o piloto.

-----

## 🗂 Planejamento do Sprint

No **Azure Boards → Sprints**:

1.  **Criação da Sprint:** Crie a sua primeira Sprint (ex: `Sprint 1 - Cadastro, Login e Criação de Grupos`).

2.  **Definição da Duração:** Configure a duração da Sprint (sugestão: 1 a 2 semanas).

3.  **Seleção de Itens:** Arraste as **User Stories mais prioritizadas** do Backlog para dentro da Sprint que você criou.

4.  **Detalhamento das Tarefas (Tasking):** Dentro da Sprint, quebre cada User Story em tarefas técnicas, como detalhado nos exemplos acima.

5.  **Atribuição de Responsáveis:** Distribua as tarefas entre os membros do grupo. É fundamental que cada integrante tenha ao menos duas tarefas atribuídas.

6.  **Definição de "Pronto" (Definition of Done - DoD):** Antes de iniciar o trabalho, o time deve concordar sobre o que significa "Pronto". Uma tarefa ou história só é considerada concluída quando atende a todos os critérios do DoD.

    **Exemplo de "Definition of Done" para o projeto Connexa:**

      * O código foi desenvolvido e submetido ao repositório central.
      * Os testes unitários foram criados e estão passando com sucesso.
      * A funcionalidade atende a todos os Critérios de Aceitação da User Story.
      * O código foi revisado por pelo menos um outro membro do time (Code Review).
      * Não há débitos técnicos conhecidos introduzidos pela nova funcionalidade.

-----

## ✅ Critérios de Entrega (via Microsoft Teams)

Cada grupo deverá realizar uma única entrega na plataforma Microsoft Teams, contendo:

1.  **URL do Projeto no Azure DevOps:* No painel do seu projeto, copie a URL completa do navegador.
2.  **Print da Sprint Ativa no Azure Boards:** A captura de tela deve exibir o quadro da Sprint, mostrando as User Stories selecionadas e suas respectivas tarefas distribuídas nas colunas (Ex: *To Do*, *In Progress*, *Done*).
3.  **Print de uma User Story Expandida:** Uma captura de tela que mostre claramente uma das User Stories dentro da Sprint com sua lista de tarefas técnicas associadas.


-----

## 📖 Referências e Recursos Complementares

  * **Microsoft Learn -- Azure DevOps:**
      * [Organizar trabalho em sprints](https://learn.microsoft.com/pt-br/azure/devops/boards/sprints/define-sprints)
      * [Criar e gerenciar tarefas no Azure Boards](https://learn.microsoft.com/pt-br/azure/devops/boards/backlogs/add-tasks)
  * **Agile/Scrum:**
      * [Scrum.org -- O Guia do Scrum (oficial, PT-BR)](https://www.scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-Portuguese-Brazilian.pdf)
  * **IA em Desenvolvimento:**
      * [GitHub Copilot - Documentação](https://docs.github.com/pt/copilot)
  * **Vídeos:**
      * [Azure DevOps -- Criando e gerenciando Sprints (YouTube, PT-BR)](https://www.youtube.com/watch?v=7e-wAwj8fGo)
