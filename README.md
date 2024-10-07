# Projeto Web Services com Spring Boot, JPA e Hibernate

Este projeto é uma aplicação desenvolvida em **Java** utilizando o **Spring Boot** para construção de APIs REST, junto com **JPA** e **Hibernate** para o mapeamento objeto-relacional e persistência de dados. O projeto visa exemplificar a construção de um serviço web completo, com entidades, relacionamentos e interações entre objetos que representam um domínio de vendas de produtos.

## Tecnologias Utilizadas
- **Java 21 (LTS)**: Linguagem de programação utilizada para construir a aplicação.
- **Spring Boot**: Framework que simplifica o desenvolvimento de aplicações Java, especialmente na criação de APIs REST.
- **Spring Data JPA**: Facilita o acesso a dados e a persistência com o banco de dados, utilizando a especificação JPA.
- **Hibernate**: Implementação do JPA, responsável pelo mapeamento objeto-relacional (ORM) entre entidades Java e tabelas no banco de dados.
- **H2 Database**: Banco de dados em memória utilizado durante o desenvolvimento.
- **Maven**: Gerenciador de dependências e automação de build.

## Funcionalidades da Aplicação

A aplicação simula um sistema de vendas, onde é possível gerenciar **usuários**, **pedidos**, **produtos** e **pagamentos**. A seguir estão algumas das funcionalidades implementadas:

- **Gerenciamento de Usuários**:
  - Listar todos os usuários cadastrados.
  - Adicionar novos usuários ao sistema.

- **Gerenciamento de Pedidos**:
  - Listar todos os pedidos realizados.
  - Associar pedidos aos usuários cadastrados.
  - Informar status do pedido (pendente, entregue, cancelado).

- **Gerenciamento de Produtos**:
  - Listar todos os produtos disponíveis.
  - Adicionar produtos ao sistema.
  - Relacionar produtos aos pedidos.

## Arquitetura

A aplicação é organizada em camadas, de forma a garantir modularidade e manutenção:

- **Entidades de Domínio**: Representam os objetos principais do sistema, como `User`, `Order`, `Product`, `OrderItem` e `Payment`. Essas entidades estão mapeadas para tabelas no banco de dados utilizando anotações do **JPA**.

- **Serviços REST**: A API é implementada utilizando controladores REST para expor as funcionalidades do sistema. Por exemplo, o endpoint `/users` permite listar todos os usuários e `/orders` cria novos pedidos.

### Diagrama UML

O projeto conta com um **diagrama UML** que descreve os relacionamentos entre as entidades do sistema, ilustrando como **usuários**, **pedidos**, **itens de pedidos** e **produtos** interagem entre si. O diagrama mostra as seguintes entidades principais:
- **User**: Representa o cliente que faz pedidos no sistema.
- **Order**: Representa o pedido feito pelo cliente.
- **Product**: Produtos disponíveis no catálogo.
- **OrderItem**: Detalhes de cada item presente em um pedido.
- **Payment**: Representa o pagamento de um pedido.

### Exemplo de Endpoints REST

- **GET /users**: Lista todos os usuários cadastrados no sistema.
- **POST /orders**: Cria um novo pedido vinculado a um usuário.
- **GET /products**: Lista todos os produtos disponíveis.

### Persistência de Dados

A aplicação faz uso do **JPA** para realizar a persistência de dados. A classe `EntityManager` é utilizada para gerenciar as operações de inserção, atualização e exclusão de dados no banco. Um exemplo de persistência de dados:

```java
EntityManagerFactory emf = Persistence.createEntityManagerFactory("exemplo-jpa");
EntityManager em = emf.createEntityManager();
em.getTransaction().begin();
em.persist(novoUsuario);
em.getTransaction().commit();
em.close();
```

Esse exemplo mostra como um novo usuário é persistido no banco de dados por meio do **EntityManager**.

## Considerações Finais

Este projeto foi desenvolvido com o objetivo de demonstrar como construir um serviço web robusto e modular utilizando **Spring Boot**, **JPA** e **Hibernate**, explorando conceitos de persistência, mapeamento objeto-relacional e boas práticas de desenvolvimento em Java.
