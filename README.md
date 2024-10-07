# Web Services com Spring Boot, JPA e Hibernate

## Objetivos do Projeto

- Criar um projeto Spring Boot em Java.
- Implementar um modelo de domínio baseado em entidades e relacionamentos.
- Estruturar as camadas lógicas do sistema: Resource (controladores REST), Service (lógica de negócios), Repository (acesso a dados) e Entities (modelos de domínio).
- Configurar um banco de dados de teste utilizando H2.
- Implementar as operações básicas de CRUD (Create, Retrieve, Update, Delete).
- Gerenciar o tratamento de exceções e erros.

## Tecnologias Utilizadas

- **Spring Boot**: Framework Java para criar aplicações web modernas e microserviços.
- **JPA (Java Persistence API)**: Especificação de Java para gerenciar persistência de dados, facilitando o mapeamento objeto-relacional (ORM) entre as entidades Java e tabelas no banco de dados.
- **Hibernate**: Implementação de JPA utilizada no projeto para gerenciar o ciclo de vida das entidades e o acesso ao banco de dados.
- **H2 Database**: Banco de dados em memória usado para testes no ambiente de desenvolvimento.
- **Maven**: Ferramenta de gerenciamento de dependências e construção do projeto.
- **Heroku**: Plataforma de cloud computing utilizada para deploy da aplicação (opcional).

## Estrutura do Projeto

O projeto segue uma arquitetura em camadas, separando responsabilidades entre as diferentes áreas do sistema:

1. **Application Layer**: O ponto de entrada da aplicação, onde o Spring Boot é inicializado.
2. **Resource Layer**: Responsável pela comunicação entre o cliente e o servidor através de controladores REST. Exemplo de endpoint: `@GetMapping` para retornar dados de um usuário.
3. **Service Layer**: Onde a lógica de negócios é implementada. Aqui estão os serviços que acessam as regras de negócio e fazem chamadas ao repositório.
4. **Data Access Layer (Repositories)**: Camada responsável pela comunicação com o banco de dados, utilizando interfaces que estendem `JPARepository`.
5. **Entities**: Representam as tabelas do banco de dados mapeadas como classes Java, com atributos que refletem as colunas do banco.

### Modelagem do Domínio

O modelo de domínio inclui classes como `User`, `Order`, `Category`, `Product` e suas respectivas associações. Os relacionamentos são mapeados usando JPA, como:

- **One-to-Many**: Relacionamentos de um para muitos, como entre `User` e `Order`.
- **Many-to-Many**: Exemplo com `Product` e `Category`, utilizando uma `JoinTable`.

### Operações CRUD

O projeto implementa as operações básicas de um CRUD:

- **Create**: Inserção de novos usuários, produtos, pedidos, etc.
- **Retrieve**: Consulta e listagem de dados via endpoints REST.
- **Update**: Atualização de dados existentes.
- **Delete**: Exclusão de registros do banco de dados.

### Povoamento de Dados

Durante a inicialização, a aplicação utiliza classes de configuração para popular o banco de dados com instâncias de objetos (`User`, `Product`, `Order`, etc.). Isso é feito diretamente na camada de repositório com o auxílio do `EntityManager` e transações gerenciadas pelo Hibernate.

### Exceções e Tratamento de Erros

O projeto lida com exceções específicas, como `ResourceNotFoundException` e `DatabaseException`, que são mapeadas para respostas adequadas no lado do cliente. Além disso, uma classe central chamada `ResourceExceptionHandler` gerencia essas exceções e retorna erros estruturados para o cliente.

### Camada de Serviço e Domínio

A camada de serviço implementa a lógica de negócios que interage com as entidades de domínio. Cada entidade, como `User`, `Order`, `Category`, é gerenciada por um serviço que encapsula as regras de negócio e delega a persistência de dados ao repositório.

### Camada de Acesso a Dados

Utilizando a interface `JPARepository`, a camada de repositório acessa e manipula os dados no banco de dados sem a necessidade de escrever SQL manualmente, delegando essa responsabilidade ao Hibernate.
