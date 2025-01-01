
# 1. Spring vs Spring Boot vs Spring MVC

# 1.1 Spring: 
Spring Framework is the most popular application development framework of Java. 
The main feature of the Spring Framework is dependency Injection or Inversion of Control (IoC). 
With the help of Spring Framework, we can develop a loosely coupled application. 
It is better to use if application type or characteristics are purely defined.

**Summary of Key Features:**
1. IoC & DI for loose coupling and easier testing
2. AOP for handling cross-cutting concerns
3. Spring MVC for building web applications
4. Transaction management and data access support
5. Spring Boot for rapid development with minimal configuration
6. Spring Security for authentication and authorization
7. Spring Cloud for cloud-native and microservices architectures
8. WebFlux for reactive programming and non-blocking apps
9. Spring Batch for batch processing

**Inversion of Control (IoC)** is a core concept in Spring, where the framework manages the 
creation and lifecycle of objects.

**Dependency Injection (DI)** is the mechanism through which Spring injects dependencies 
into objects, rather than the objects creating or managing their own dependencies. 
This promotes loose coupling, making applications easier to test and maintain.

**Aspect-Oriented Programming (AOP)**
Spring provides support for AOP, which allows the separation of cross-cutting concerns 
(such as logging, security, and transaction management) from the business logic.
With AOP, developers can define aspects (such as logging or security) and apply 
them across different parts of the application without modifying the core business logic.

**Spring MVC (Model-View-Controller)**
Spring MVC is a comprehensive framework for building web applications based on the 
Model-View-Controller (MVC) pattern.
It provides features like request mapping, view resolution, form handling, validation, 
and more, allowing the development of flexible and clean web applications
**DispatcherServlet** is at the heart of Spring MVC, coordinating HTTP requests 
and forwarding them to appropriate handlers.

**Transaction Management**
Transaction Management in Spring ensures that a series of operations (usually involving a database) 
are executed as a single unit. If any operation fails, the transaction can be rolled back, 
ensuring consistency and integrity of data
The transaction is managed using annotations like **@Transactional** or **XML configuration**, 
which is the preferred method as it is simpler and less error-prone.

**Data Access and ORM Integration**
Spring simplifies database interactions by providing support for JDBC, JPA (Java Persistence API), 
Hibernate, MyBatis, and JDBC Templates.
The Spring JDBC module offers a lightweight, powerful alternative to using raw JDBC code directly.

**Spring Security**
Spring Security is a comprehensive and customizable authentication and authorization framework.
It supports a wide range of security features, including authentication, authorization, 
CSRF protection, OAuth2, JWT, and more.
secure against various types of security threats (e.g., SQL injection, cross-site scripting).

**Spring Boot (Convention over Configuration)**
1. Spring Boot (as an extension of the Spring Framework) simplifies Spring application development 
by providing auto-configuration, eliminating the need for XML configurations and boilerplate code.
2. Spring Boot allows you to run applications in an embedded server (like Tomcat, Jetty, or Undertow), 
making it easy to deploy standalone applications without needing an external application server.
3. It also provides starter dependencies that bundle commonly used configurations 
4. (e.g., for web apps, databases, messaging, etc.).

**Spring Data**
Spring Data simplifies database interactions by providing abstractions for a wide variety of 
data stores, including relational databases (through Spring Data JPA) and NoSQL databases 
(like MongoDB, Cassandra, etc.).
It allows you to use repositories for common CRUD (Create, Read, Update, Delete) 
operations and provides advanced functionality like pagination and sorting.

**Spring Batch**
Spring Batch is a framework for building batch processing applications, 
handling large volumes of data in a reliable and scalable manner.

**Spring Integration**
It supports different integration patterns (e.g., messaging, routing, transformation) 
and integrates with external systems, databases, messaging queues, and more.
It allows you to build ETL pipelines, data flows, and event-driven applications

**Spring Cloud**
Spring Cloud provides tools for building cloud-native applications, 
especially for microservices architectures.
Key components of Spring Cloud include Spring Cloud Config, Spring Cloud Netflix (for microservices patterns), 
and Spring Cloud Gateway.

**Spring Actuator**
Spring Actuator provides production-ready features such as monitoring, metrics, health checks, and logging.

**Spring Test**
Spring Test is a testing framework that supports writing unit tests 
and integration tests for Spring-based applications.


# 1.2 Spring Boot: 
Spring Boot is a module of Spring Framework. 
It allows us to build a **stand-alone application** with minimal or zero configurations. 
It is better to use if we want to develop a simple Spring-based application or RESTful services.

Spring Boot makes it easy to quickly bootstrap and start developing a Spring-based application. 
It avoids a lot of boilerplate code. It hides a lot of complexity behind the scene so that 
the developer can quickly get started and develop Spring-based applications easily.

**Spring Boot (Convention over Configuration)**
1. Spring Boot (as an extension of the Spring Framework) simplifies Spring application development
   by providing auto-configuration, eliminating the need for XML configurations and boilerplate code.
2. Spring Boot allows you to run applications in an embedded server (like Tomcat, Jetty, or Undertow),
   making it easy to deploy standalone applications without needing an external application server.
3. It also provides starter dependencies that bundle commonly used configurations
4. (e.g., for web apps, databases, messaging, etc.).


# 1.3 Spring MVC 
Spring MVC is a Web MVC Framework for building web applications. 
It contains a lot of configuration files for various capabilities. 
It is an HTTP oriented web application development framework.

Java EE (Java Platform, Enterprise Edition)

# Spring vs. Spring Boot

1. Framework is widely used for Java EE while spring Boot is widely used for develop REST APIs.
2. It aims to simplify JAVA EE developmnet while spring boot aims shorten the code length to develope web application.
3. primary feature Dependency Injection in framework and Autoconfiguration in spring Boot.
4. Framework helps to make loosely coupled application while Spring Boots helps to create Stand Alone application with
minimal configuration.
5. In Framewrok to test the spring project, the server needs to be setup explicitly while spring Boot
offers an embedded server such as tomcat and jetty.
6. Does not provide support for an in-memory databse while it offers several plugins for working
with embedded and im memory databse such as H2.
7. Developers manually define dependencies for the Spring project in pom.xml while Spring 
Boot comes with the concept of starter in pom.xml file that internally takes care of 
downloading the dependencies JARs based on Spring Boot Requirement.

| **Feature**                                                   | **Spring Framework**                                                                         | **Spring Boot**                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Purpose**                                                   | Spring Framework is a widely used Java EE framework for building applications.               | Spring Boot Framework is widely used to develop REST APIs.                                                            |
| **Development Focus**                                         | It Aims to simplify Java EE development, making developers more productive.                  | It Aims to shorten the code length and provide the easiest way to develop Web Applications.                           |
| **Primary Feature**                                           | The primary feature of the Spring Framework is dependency injection.                         | The primary feature of Spring Boot is Autoconfiguration, which automatically configures classes based on requirements. |
| **Application Structure**                                     | It Helps to make things simpler by allowing the development of loosely coupled applications. | It Helps to create stand-alone applications with minimal configuration.                                               |
| **Code Complexity**                                           | The developer writes a lot of boilerplate code for minimal tasks.                            | It Reduces boilerplate code significantly.                                                                            |
| **Server Setup**                                              | To test the Spring project, the server needs to be set up explicitly.                        | Spring Boot offers an embedded server such as Jetty and Tomcat, etc.                                                  |
| **Database Support**                                          | It Does not provide support for an in-memory database.                                       | It Offers several plugins for working with embedded and in-memory databases such as H2.                               |
| **Dependency Management**                                     | Developers manually define dependencies for the Spring project in `pom.xml`.                 | Spring Boot comes with the concept of starter in pom.xml file that internally takes care of downloading the dependencies JARs based on Spring Boot Requirement.                          |

# Spring Boot vs Spring MVC 


| **Feature**               | **Spring Boot**                                                                                         | **Spring MVC**                                                                                        |
|---------------------------|---------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| **Definition**            | Spring Boot is a module of Spring for packaging the Spring-based application with sensible defaults.     | Spring MVC is a model-view-controller-based web framework under the Spring framework.                 |
| **Build configuration**       | There is no need to build configuration manually. | It requires build configuration manually. |
| **Configuration**         | Provides default configurations to build Spring-powered applications.                                   | It provides ready to use features for building a web application..                                                                  |
| **Deployment Descriptor** | No need for a deployment descriptor.                                                                    | A deployment descriptor is required.                                                                  |
| **Boilerplate Code**      | Avoids boilerplate code and wraps dependencies together in a single unit.                               | Specifies each dependency separately.                                                                 |
| **Development Time**      | Reduces development time and increases productivity.                                                    | Takes more time to achieve the same.                                                                   |


