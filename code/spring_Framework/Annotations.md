
# 1. Spring annotation 

# 1. @RestController 
It is used to define a controller where every method is capable of handling 
HTTP requests, and the response is automatically converted to JSON or XML 
(depending on the configuration). 
It is a specialized version of the **@Controller** annotation, 
typically used for building RESTful APIs.

It combines the behavior of @Controller and @ResponseBody
It Automatically serializes objects to JSON or XML

**@RestController = @Controller + @ResponseBody**

# 2. @Controller
It is one of the core annotations in Spring MVC (Model-View-Controller) architecture.
It is used to define a Spring MVC controller that processes incoming HTTP 
requests and returns a response, often in the form of a view 
(such as a JSP or Thymeleaf template) or other resources. 

The @Controller annotation marks the class as a Spring MVC controller.
It require @ResponseBody for  serializes objects to JSON or XML
~~~
@Controller
public class MyController {

    @GetMapping("/json")
    @ResponseBody
    public MyObject getJsonResponse() {
        return new MyObject("John", 30); // Automatically serialized to JSON
    }
}
~~~

# 3. @RequestBody 
- The @RequestBody annotation tells Spring to deserialize the incoming 
JSON into a User object.
- It tells Spring to bind the incoming HTTP request body to a Java object 
(e.g., JSON or XML).
- Ex. Accepting JSON data from a client and converting it into a Java object
(e.g., POST request)

# 4. @ResponseBody 
- The @ResponseBody annotation tells Spring to serialize the returned 
User object into JSON and send it back in the response body.
- it Tells Spring to write the return value of a method directly to 
the response body (e.g., JSON or XML)
- Returning a Java object as JSON to the client (e.g., GET request)

# 5. @Autowired 
- @Autowired is used for dependency injection
- it is used to inject dependencies automatically into Spring beans
- It can be used with constructor injection, field injection, or setter injection.
- Spring can inject dependencies via constructor, field, or setter injection.
- When you annotate a field, constructor, or setter method with @Autowired, 
Spring will look for a matching bean in the Spring context 
(i.e., the Spring ApplicationContext). 
If it finds a bean that matches, it will inject it automatically.

# 6. @Resource

- @Resource is a standard Java annotation for dependency injection, 
defined in the **javax.annotation package**
- @Resource injects a bean by name by default. This means that it looks for a bean in the Spring context that matches the name of the field or method parameter being annotated
- It allows Spring to inject beans into a class either by name (default) or type (fallback).
- It is similar to @Autowired but prioritizes name-based injection, making it more useful when you need to specify a particular bean by its name.

| **Feature**                  | **@Autowired**                                                              | **@Resource**                                                               |
|------------------------------|-----------------------------------------------------------------------------|----------------------------------------------------------------------------|
| **Injection Criteria**        | Injects by type (unless `@Qualifier` is used)                                | Injects by name first, then by type if needed                               |
| **Name Matching**             | No default name matching, relies on type                                    | Defaults to matching bean by name (name attribute)                          |
| **Bean Lookup**               | Can inject beans of the same type (via `@Qualifier`)                         | No need for `@Qualifier`, relies on name first                              |
| **Flexibility**               | More flexible when dealing with multiple beans of the same type             | Less flexible for type-based injection                                      |

# 7. @GetMapping, @PostMapping, @PutMapping, @DeleteMapping

In Spring, the @GetMapping, @PostMapping, @PutMapping, @DeleteMapping, etc., 
are specialized versions of the @RequestMapping annotation, 
designed to handle HTTP requests for the corresponding HTTP methods 
(GET, POST, PUT, DELETE, etc.) in a cleaner, more semantic way.

# 8. HTTP Method Mappings in Spring

In Spring, annotations like `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, and `@PatchMapping` are used to map HTTP requests to controller methods. These annotations are more specific and readable alternatives to `@RequestMapping` for handling HTTP methods.

| Annotation         | HTTP Method | Use Case                          | Example Endpoint         | Example Action                                |
|--------------------|-------------|-----------------------------------|--------------------------|-----------------------------------------------|
| **`@GetMapping`**   | GET         | Retrieve data (Read)              | `/users`                 | Fetch all users                              |
| **`@PostMapping`**  | POST        | Create a new resource             | `/users`                 | Create a new user                            |
| **`@PutMapping`**   | PUT         | Update an existing resource       | `/users/{id}`            | Update user with ID                          |
| **`@DeleteMapping`**| DELETE      | Delete a resource                 | `/users/{id}`            | Delete user with ID                          |
| **`@PatchMapping`** | PATCH       | Partially update a resource      | `/users/{id}`            | Partially update user with ID                |

### Example Usage in a Spring Controller

```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/users")
public class UserController {

    // GET request to retrieve all users
    @GetMapping
    public List<User> getAllUsers() {
        return userService.getAllUsers();
    }

    // POST request to create a new user
    @PostMapping
    public User createUser(@RequestBody User user) {
        return userService.createUser(user);
    }

    // PUT request to update a user
    @PutMapping("/{id}")
    public User updateUser(@PathVariable Long id, @RequestBody User user) {
        return userService.updateUser(id, user);
    }

    // DELETE request to remove a user
    @DeleteMapping("/{id}")
    public void deleteUser(@PathVariable Long id) {
        userService.deleteUser(id);
    }
}
```
# 9. @Component 

In Spring Framework, @Component is an annotation that marks a Java class as a Spring bean. 
When a class is annotated with @Component, Spring will automatically detect it during component 
scanning and register it as a bean in the Spring ApplicationContext. 
This means that Spring will manage the lifecycle of that class, and you can inject it into 
other components (e.g., other beans or controllers) using dependency injection.

# 10. @Service
In Spring, the @Service annotation is a specialization of the @Component annotation, 
which is used to mark a class as a service-layer bean. 
It is part of Spring's stereotype annotations, and it indicates 
that the class contains business logic or services. While @Component
is a generic annotation for any Spring-managed bean, @Service is more 
semantically meaningful, suggesting that the class is intended to perform service-related tasks.

# 11. Spring Annotations Overview

This table summarizes some commonly used Spring annotations, their purpose, and typical use cases:

| Annotation        | Purpose                                          | Use Case                                                       |
|-------------------|--------------------------------------------------|---------------------------------------------------------------|
| **`@Component`**   | Generic Spring bean definition.                 | Used for any class you want Spring to manage.                  |
| **`@Service`**     | Specialized version of `@Component` for business logic. | Used for service layer beans containing business logic.        |
| **`@Repository`**  | Specialized version of `@Component` for DAO classes. | Used for data access layer (e.g., interacting with databases). |
| **`@Controller`**  | Specialized version of `@Component` for web controllers. | Used for handling HTTP requests in Spring MVC applications.    |
| **`@RestController`** | Combination of `@Controller` and `@ResponseBody`. | Used for REST APIs to automatically serialize return values as JSON/XML. |

### Summary
- **`@Component`** is used for generic Spring beans.
- **`@Service`** is used for beans that contain business logic.
- **`@Repository`** is used for data access objects (DAOs) interacting with databases.
- **`@Controller`** is used for handling web requests in Spring MVC.
- **`@RestController`** is used for creating RESTful web services with automatic JSON/XML serialization.


# 12. 

# Spring Annotations Overview

This table summarizes various Spring annotations, their purpose, and typical use cases:

| Annotation                    | Purpose                                                              | Use Case                                                                 |
|-------------------------------|----------------------------------------------------------------------|--------------------------------------------------------------------------|
| **`@Autowired`**               | Automatically injects dependencies into Spring beans.                | Used to autowire dependencies in Spring-managed beans (fields, setters, or constructors). |
| **`@Component`**               | Marks a class as a Spring bean for component scanning.               | Used for any class you want Spring to manage.                            |
| **`@Service`**                 | Specialized version of `@Component` for service-layer beans.         | Used for business logic/service-layer classes.                          |
| **`@Repository`**              | Specialized version of `@Component` for DAO classes.                 | Used for data access objects (e.g., interacting with databases).         |
| **`@Controller`**              | Specialized version of `@Component` for Spring MVC controllers.      | Used for handling HTTP requests in Spring MVC applications.             |
| **`@RestController`**          | Combination of `@Controller` and `@ResponseBody`.                    | Used for creating REST APIs and automatically serializing return values to JSON/XML. |
| **`@Configuration`**           | Indicates that the class contains Spring configuration.             | Used to define beans and Spring configuration classes.                  |
| **`@Bean`**                     | Defines a bean that Spring should manage.                            | Used within a `@Configuration` class to define beans explicitly.        |
| **`@Value`**                    | Injects values into fields or methods.                               | Used to inject property values or expressions into fields or method parameters. |
| **`@Qualifier`**                | Resolves ambiguity when multiple beans of the same type exist.      | Used with `@Autowired` to specify which bean to inject when there are multiple candidates. |
| **`@Scope`**                    | Defines the scope of a Spring bean (e.g., singleton, prototype).     | Used to specify the lifecycle scope of a bean.                          |
| **`@PostConstruct`**            | Marks a method to be executed after the bean's initialization.       | Used to perform tasks after a bean is initialized.                      |
| **`@PreDestroy`**               | Marks a method to be executed before the bean is destroyed.         | Used to perform cleanup tasks before a bean is destroyed.              |
| **`@Transactional`**            | Manages transactions in Spring beans.                               | Used to mark methods that should run within a transactional context.    |
| **`@RequestMapping`**           | Maps HTTP requests to handler methods.                              | Used to map HTTP requests to methods in controller classes.             |
| **`@GetMapping`**               | Shorthand for `@RequestMapping(method = RequestMethod.GET)`.         | Used to map HTTP GET requests to methods.                               |
| **`@PostMapping`**              | Shorthand for `@RequestMapping(method = RequestMethod.POST)`.        | Used to map HTTP POST requests to methods.                              |
| **`@PutMapping`**               | Shorthand for `@RequestMapping(method = RequestMethod.PUT)`.         | Used to map HTTP PUT requests to methods.                               |
| **`@DeleteMapping`**            | Shorthand for `@RequestMapping(method = RequestMethod.DELETE)`.      | Used to map HTTP DELETE requests to methods.                            |
| **`@PatchMapping`**             | Shorthand for `@RequestMapping(method = RequestMethod.PATCH)`.       | Used to map HTTP PATCH requests to methods.                             |
| **`@PathVariable`**             | Binds method parameters to URI template variables.                   | Used to extract variables from the URI path in request mappings.        |
| **`@RequestParam`**             | Binds method parameters to request parameters.                       | Used to extract query parameters from the HTTP request.                 |
| **`@RequestBody`**              | Binds the body of an HTTP request to a method parameter.             | Used to extract and bind the request body to a method parameter (typically in REST APIs). |
| **`@ResponseBody`**             | Indicates that the return value of a method should be the response body. | Used to serialize return values directly to the HTTP response (e.g., JSON/XML). |
| **`@CrossOrigin`**              | Enables Cross-Origin Resource Sharing (CORS) support.                | Used to allow or configure cross-origin requests in REST APIs.          |
| **`@EnableAutoConfiguration`**  | Enables Spring Boot’s auto-configuration mechanism.                  | Used in Spring Boot to automatically configure beans based on classpath settings. |
| **`@Import`**                   | Imports additional configuration classes.                           | Used to import other configuration classes into a Spring context.      |
| **`@PropertySource`**           | Specifies locations of property files for Spring's Environment.      | Used to load external properties into the Spring environment.           |
| **`@EnableAspectJAutoProxy`**   | Enables AspectJ-based proxy support in Spring.                       | Used to enable Aspect-Oriented Programming (AOP) in Spring applications. |
| **`@EnableScheduling`**         | Enables scheduling in a Spring application.                          | Used to enable support for task scheduling in Spring.                   |
| **`@EnableTransactionManagement`** | Enables Spring's annotation-driven transaction management.         | Used to enable declarative transaction management in Spring.          |
| **`@Profile`**                  | Specifies profiles for bean definitions.                             | Used to define beans that should only be active for specific profiles (e.g., `dev`, `prod`). |
| **`@EnableWebSecurity`**        | Enables Spring Security's web security configuration.                | Used to enable security features in Spring-based web applications.     |
| **`@EnableJpaRepositories`**    | Enables Spring Data JPA repositories.                               | Used to enable JPA repository support for accessing data from a database. |
| **`@EnableCaching`**            | Enables Spring’s caching abstraction.                                | Used to enable caching in Spring applications.                          |

### Summary

- **Annotations like `@Component`, `@Service`, `@Repository`, `@Controller`, `@RestController`** are used for defining beans in Spring and signify the role of a class within the application (business logic, data access, controllers, etc.).
- **Annotations like `@Autowired`, `@Value`, `@Qualifier`, `@Scope`** are used for managing dependencies and the lifecycle of beans.
- **Annotations like `@Transactional`, `@PostConstruct`, `@PreDestroy`** handle transactional behavior and bean initialization/destroy tasks.
- **Annotations like `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@PatchMapping`** are used to define HTTP request mappings in web applications.
- **Annotations like `@EnableAutoConfiguration`, `@EnableAspectJAutoProxy`, `@EnableScheduling`** enable specific features or configurations in Spring (e.g., auto-configuration, AOP, scheduling).
