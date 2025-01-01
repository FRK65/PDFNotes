
Most asked Java interview Questions:

**1. Can an interface have a constructor? Why or why not?**
**Ans :**  
No, interfaces cannot have constructors because they are not meant to represent specific 
object instances or manage state. They are simply a blueprint for classes to implement. 

**2. What is the significance of the default keyword in Java 8 interfaces?**
**Ans :**

- The default keyword in Java 8 introduced the ability to define default methods in interfaces. 
- Prior to Java 8, we can declare only method signatures (abstract methods) in interface.
and the class which is implementing this interface, was required to provide an implementation 
for those methods. 

However, with the introduction of **default methods**, interfaces can now provide a default 
implementation for some of their methods, thereby improving code **reusability and flexibility.**

```java
interface MyInterface {
    
    // Default method with an implementation
    default void defaultMethod() {
    System.out.println("This is a default method");
    }

    // Abstract method that must be implemented by implementing classes
    void doSomething();
}
```
**3. Can a class implement multiple interfaces in Java? If yes, explain how.**
- Yes, a class can implement multiple interfaces in Java. 
- This is one of the key features of **Java's interface** inheritance mechanism and 
it enables a class to inherit behaviors from multiple sources, which is particularly useful 
for achieving multiple inheritance of behavior.

**4. Can an interface extend another interface? If so, what is the use case?**
- Yes, in Java, an interface can extend another interface. This is similar to how classes can extend other 
classes. But with interfaces, this is a form of interface inheritance. 
- When one interface extends another, the extending interface inherits all the abstract methods 
from the parent interface, and can also declare additional methods of its own.
- It's commonly used when you need to build a contract-based system with shared functionality, 
or when you want to add more specific capabilities to a base interface.

**5. What happens if a class implements two interfaces with conflicting default methods?**
- When a class implements two interfaces with conflicting default methods in Java, the compiler will raise 
a compilation error. 
- This happens because Java cannot decide which default method to invoke and creating ambiguity. 
- However, the class can resolve the conflict by overriding the conflicting method, 
and providing its own implementation.

**6. Can you explain the difference between public, private, protected, and package-private access modifiers?**

- **public**: Accessible from anywhere.
- **private**: Accessible only within the same class.
- **protected**: Accessible within the same package and by subclasses.
- **Package-private (default)**: Accessible only within the same package (no modifier specified).

**7. In conetex of two different package explain public, private, protected, and default access modifier behaviour.** 

We have two package, package A and package B. 
- package A has 4 variable : publicA, privateA, protectedA and defaultA and 
- similarly package B has 4 variable publicB, priavteB, protectedB and defaultB.  

Now tell package A can access how many variable of B and package B can access how many variable of A.

| Modifier         | **Package A Accessing Package B** | **Package B Accessing Package A** |
|------------------|-----------------------------------|-----------------------------------|
| **`public`**      | Yes (`publicB`)                   | Yes (`publicA`)                   |
| **`private`**     | No (`privateB`)                   | No (`privateA`)                   |
| **`protected`**   | Yes (only if subclass in Package A) | Yes (only if subclass in Package B)|
| **default**       | No (`defaultB`)                   | No (`defaultA`)                   |



**8. What is the purpose of the protected access modifier? Can you access a protected method from another package?**

The **`protected`** access modifier allows access to a class member within the **same package** and 
by **subclasses**, even if they are in **different packages**.

So, **yes**, a **protected** method can be accessed from another package, 
but only if the accessing class is a **subclass** of the class that defines the `protected` method. 
Other classes in the different package, which are not subclasses, cannot access the `protected` method.

**8. What is the default access level for a class, method, or variable if no access modifier is specified?** 

The default access level (also known as package-private). 
in Java it is applied when no access modifier is specified. 
Here's how it works:
- **For a class:** If no access modifier is specified, the class is accessible only within its own package. 
It cannot be accessed from outside the package.
- **For a method or variable**: If no access modifier is specified, it is accessible only within its own package, 
just like the class. It cannot be accessed from classes in other packages

**9.Can you access a private variable from a subclass?**
**Ans :** No, you cannot access a private variable from a subclass in Java.

**10.  What is a functional interface? Can you give an example?**

- A functional interface in Java is an interface that has exactly one abstract method. 
- It may also contain multiple default or static methods, but it can only have one abstract method 
to be considered a functional interface. 
- Functional interfaces are primarily used in the context of lambda expressions and method references, 
- It introduced in Java 8, to represent single-method interfaces in a concise manner.

**11.  Explain the concept of Lambda Expressions in Java 8. How do they improve code readability?**
**Ans :** Lambda expressions is introduced in Java 8 and provide a concise way to write anonymous functions, 
allowing you to pass behavior as arguments. 
- They are used primarily with functional interfaces and are a key feature of functional programming in Java
- Syntax: **(parameters) -> expression or (parameters) -> { statements; }**
- They allow you to focus directly on the business logic without worrying about 
implementation details like anonymous classes.
- Functional Programming: It Enables use of streams, higher-order functions, and operations like 
- filter, map, and reduce on collections.

```java
// Traditional approach
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
Collections.sort(names, new Comparator<String>() {
    @Override
    public int compare(String o1, String o2) {
        return o1.compareTo(o2);
    }
});

// Using Lambda Expression
Collections.sort(names, (o1, o2) -> o1.compareTo(o2));

```



**12.  What is the Stream API in Java 8, and how is it different from a collection?**

**Ans :** The Stream API in Java 8 allows you to process sequences of elements (e.g., collections, arrays) 
in a functional and declarative style. 
It supports operations like filtering, mapping, and reducing to make data processing more concise and readable.

| Feature             | **Collection**                              | **Stream**                                 |
|---------------------|---------------------------------------------|--------------------------------------------|
| **Storage**         | Stores data (e.g., `List`, `Set`)           | Does not store data; processes data on demand |
| **Modification**    | Can be modified (add/remove elements)       | Does not modify the underlying data (immutable) |
| **Evaluation**      | Eager evaluation (immediate processing)     | Lazy evaluation (operations are deferred until terminal operation) |
| **Multiple Traversals** | Can be traversed multiple times            | Can be traversed only once                  |
| **Operations**      | Direct operations on data (e.g., `add()`, `remove()`) | Supports functional-style operations (e.g., `map()`, `filter()`, `reduce()`) |
| **Purpose**         | Used for data storage and retrieval         | Used for processing data in a pipeline     |



**13.  What is the difference between map() and flatMap() in Java 8 Streams?**

In Java 8 Streams, both map() and flatMap() are intermediate operations that transform the 
elements of a stream, but they differ in how they handle the transformation and the structure of the 
resulting stream.

| **Feature**          | **`map()`**                                                | **`flatMap()`**                                      |
|----------------------|------------------------------------------------------------|------------------------------------------------------|
| **Operation**        | Transforms each element to one element.                   | Transforms each element to a stream of elements.     |
| **Return Type**      | Produces a new stream where each element is the result of applying a function to the original element. | Produces a new stream where each element is flattened into the stream (i.e., elements are merged into one stream). |
| **Transformation**   | Applies a function that returns a single element for each input. | Applies a function that returns a **stream** of elements, which is then flattened into a single stream. |
| **Usage Scenario**   | Used when you want to **map** each element to exactly one output element. | Used when you want to **flatten** multiple sub-streams into a single stream of elements. |
| **Resulting Stream** | A stream of transformed elements.                         | A single, flattened stream of all the elements from multiple streams. |

map()
```java
List<String> words = Arrays.asList("hello", "world1");
List<Integer> lengths = words.stream()
                              .map(String::length)  // Converts each string to its length
                              .collect(Collectors.toList());

System.out.println(lengths); // Output: [5, 5]

```
flatmap()
```java
List<List<String>> listOfLists = Arrays.asList(
    Arrays.asList("a", "b", "c"),
    Arrays.asList("d", "e", "f")
);

List<String> flattenedList = listOfLists.stream()
                                        .flatMap(List::stream) // Flattens each List into a stream of strings
                                        .collect(Collectors.toList());

System.out.println(flattenedList); // Output: [a, b, c, d, e, f]

```

**14.  How to use the Optional class in Java 8 to avoid NullPointerException?**
**Ans:** Optional in Java 8 is a container object that may or may not contain a value. 
It’s used to avoid NullPointerException by providing a more expressive and safe way of 
handling null values.
- Avoids explicit null checks and Helps in functional programming

Common Methods:

**of(): Creates an Optional with a non-null value.**
```java
Optional<String> optional = Optional.of("Hello");
```

**ofNullable(): Creates an Optional that can hold a null value.**
```java
Optional<String> optional = Optional.ofNullable(null); // Empty Optional
```

**isPresent(): Checks if a value is present.**

```java
optional.isPresent(); // true if value is present
```

**ifPresent(): Executes a lambda if the value is present.**
```java
optional.ifPresent(val -> System.out.println(val)); // Will execute if value is present
```

**orElse(): Returns the value if present, or a default if not.**
```java
String result = optional.orElse("Default Value");
```

**orElseThrow(): Throws an exception if no value is present.**
```java
optional.orElseThrow(() -> new IllegalArgumentException("No value present"));
```

Example:
```java

Optional<String> optionalValue = Optional.ofNullable(null);

// Using orElse to provide a default value
String result = optionalValue.orElse("Default Value");
System.out.println(result); // Output: Default Value

// Using ifPresent to safely handle the value
optionalValue.ifPresent(value -> System.out.println(value)); // Will not print anything
```


**15.  What are the major improvements introduced in java.time package in Java 8?**

The java.time package in Java 8 improves upon the old Date and Calendar API by providing an 
immutable, thread-safe, and ISO-8601 compliant API that offers clear separation of date and 
time, better handling of time zones, and easier manipulation of date and time values. 
It is designed for modern, functional-style date-time programming
```java
// Create a LocalDate
LocalDate date = LocalDate.of(2024, 12, 25);

// Create a LocalTime
LocalTime time = LocalTime.of(15, 30);

// Combine into LocalDateTime
LocalDateTime dateTime = LocalDateTime.of(date, time);

// Get the current time in a specific time zone
ZonedDateTime zonedDateTime = ZonedDateTime.now(ZoneId.of("America/New_York"));

// Format a date
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
String formattedDate = date.format(formatter);

```

**16.  Can you create an instance of a class with only static methods? How to call the methods?**

**Ans:**  Yes, But You don't need to create an instance of a class with only static methods 
to call those methods. The recommended way is to call them directly on the class using **ClassName.methodName()**


**17.  What is the difference between a static method and a non-static method?**

- **Static Method**: Belongs to the class and can be called without creating an instance of the class.

- **Non-static Method**: Belongs to an instance of the class and requires an object to be called.


**18.  Can you access a non-static variable from a static method? Why or why not?**
**Ans :** No, you cannot access a non-static variable from a static method because static methods 
belong to the class, not an instance, and non-static variables are tied to specific instances.

**19.  What is a static block in Java, and when is it executed?**
**Ans :** 
A static block in Java is a block of code inside a class that is marked with the static keyword. 
It is executed once when the class is loaded into memory, before any objects of the class are created 
or any static methods are called.

**20.  How can you call a static method in another class?**
**Ans :** You can call a static method in another class using the class name followed by the method name, 
like this: ClassName.methodName()

**21.  Can a static variable be overridden by a subclass? Why or why not?**
**Ans:** No, a static variable cannot be overridden by a subclass because static variables belong to 
the class, not instances, and are not subject to polymorphism. They can be **hidden** but not overridden.

**22. What are the four pillars of OOP?**
1. Encapsulation
2. Abstraction 
3. Polymorphism
4. Inheritance

**23. What is the difference between an abstract class and an interface?**

**Abstract class** = Shared implementation for related classes.
**Interface** = Defines a contract that can be implemented by any class.

- Abstract classes can have both abstract methods (without implementation) and 
concrete methods (with implementation). 
- Interfaces can only have abstract methods (until Java 8), but from Java 8 onwards, 
they can also have default methods (with a body) and static methods
- Abstract classes can have **instance** fields, **static** fields, and **constants**.
- Interfaces can only have static final fields (constants) and all fields are implicitly **public, static, and final.**
- A class can extend only one abstract class (Java supports single inheritance for classes).
- A class can implement multiple interfaces (Java supports multiple inheritance for interfaces).
- Abstract classes can have constructors for initializing state.
- Interfaces cannot have constructors.
- Abstract classes can have methods with any access modifier (public, private, protected).
- Interface methods are implicitly public, and you cannot use other access modifiers.


24. Explain method overloading and method overriding.

**Method Overloading**: Defining multiple methods with the same name but 
different parameters (number, type, or order) within the same class.

**Method Overriding:** A specific implementation of a method in child class that 
is already defined in a superclass, using the same method signature.

25. What is polymorphism?
**Polymorphism** in real life is like a **person** who can be a **teacher**, 
a **driver**, or a **chef**, depending on the situation, 
even though they are the same person.

**26. What are the differences between encapsulation and abstraction?**

**Encapsulation** = Hiding the object's internal state and requiring all 
interactions to be done through methods.

**Abstraction** = Hiding complex details and exposing only necessary parts 
of an object.


**27. What is the use of the virtual, sealed, and override keywords?**

**virtual**: Used to define a method, property, or event in a base class that 
can be overridden in a derived class.

Example: **public virtual void Method() { }**

**sealed**: Prevents further overriding of a method or class in derived classes.

Example: **public sealed void Method() { } or public sealed class MyClass { }**

**override**: Used to provide a new implementation of a virtual or abstract method 
in a derived class.

Example: **public override void Method() { }**

**28. Can a class inherit multiple interfaces ?**

Yes

**29. What is the difference between composition and inheritance?**

**Inheritance**: Represents a "**is-a**" relationship where a subclass inherits 
properties and behaviors from a superclass, establishing a hierarchical relationship. 
It promotes code reuse but can lead to tight coupling between classes.

~~~
Example: A Car class inherits from a Vehicle class. (A Car is a Vehicle)
~~~
**Composition**: Represents a "**has-a**" relationship where a class contains 
instances of other classes as its fields. 
It allows for greater flexibility and loose coupling, enabling code reuse by 
combining simpler components.
~~~
Example: A Car class has a Engine (a Car contains an Engine).
~~~


**30. Explain the SOLID principles.**

The SOLID principles are a set of five design principles in object-oriented programming 
that help create more maintainable, flexible, and scalable software. 
Here's a brief explanation of each:

**S - Single Responsibility Principle (SRP):**

A class should have only one reason to change, meaning it should only have one responsibility or job.

Example: A User class should not handle both user data management and email notifications.

**O - Open/Closed Principle (OCP):**

Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.

Example: You should be able to add new functionality (e.g., a new shape) 
without changing the existing code by using polymorphism.

**L - Liskov Substitution Principle (LSP):**

Objects of a base class should be replaceable with objects of derived classes 
without affecting the correctness of the program.

Example: If a Bird class has a method fly(), 
a Penguin class should not inherit from Bird if it cannot fly, 
as it violates the principle.
when we use bird class object to reperesent Penguin class Object.

**I - Interface Segregation Principle (ISP):**

Clients should not be forced to depend on interfaces they do not use. 
Instead, create smaller, more specific interfaces.

Example: A Printer interface should not include methods for both scan() and print() if a class only implements one functionality.

**D - Dependency Inversion Principle (DIP):**

High-level modules should not depend on low-level modules. 
Both should depend on abstractions (e.g., interfaces). 
Additionally, abstractions should not depend on details; details should depend on abstractions.

Example: A PaymentService should not depend directly on a CreditCard class but rather on 
a PaymentMethod interface, allowing for easier extension to other payment methods.

31. How to implement encapsulation?

**Encapsulation** is achieved by using private fields and public methods (getters and setters) 
to control access to the internal state of an object.

Steps to Implement Encapsulation:

**Declare class variables as private** so they can't be accessed directly from outside the class.

**Provide public getter and setter methods** to access and modify the values of the private variables.

**32. What is the difference between public, private, and protected access modifiers?**

- public: Accessible from everywhere.
- private: Accessible only within the same class.
- protected: Accessible within the same package and by subclasses.

**33. What is a constructor, and how is it different from a method?**

**Constructor**: It Used for object initialization, no return type, and same name as the class.
while
**Method**: Used to perform actions on objects, has a return type, and can be called explicitly.


**34. Can you explain the concept of a static class and its use?**

**Static Class in Java :** also known as inner class or nested class
-  In Java, the term static class typically refers to a static nested class 
(a class defined inside another class and marked as static).
- **No Instantiation**: A static class cannot be instantiated from outside the Outer class.
- Static members of a static class can be accessed without creating an instance of the outer class.
- Since it does not hold a reference to the outer class instance, 
it is more memory-efficient when compared to non-static nested classes

CASE : I have **static** **class A** and  other **static class B**, can B inherit class A.
also i have another **class C** which is simple non static class, can C inherit class A
- Yes, a static class (B) can inherit from another static class (A). class B extends A 

**35. What is the difference between is-a and has-a relationships in OOP?**

**Is-a**: Represents inheritance, where one class is a type of another (e.g., a Dog is a Animal).

**Has-a**: Represents composition, where one class contains or is composed of another class (e.g., a Car has an Engine)



1.    Tell me about yourself and your experience working with Microservices.
2.    How have you implemented Microservices in your past projects, and what challenges did you face?
3.    In your projects, you’ve worked with Microservices. 
4.    Could you explain the key architectural decisions you took when designing Microservices-based systems?
4.    How to handle inter-service communication between Microservices? Can you explain your experience with patterns like Circuit Breaker and Service Discovery?
5.    What design patterns do you use in .NET for building scalable applications? Can you provide examples from your current project?
6.    You mentioned Test Driven Development (TDD) in your projects. Could you explain your approach to TDD and give an example of how to write unit tests for a Microservice or an API in .NET Core?
7.    Suppose we need to design a high-traffic web application using ASP.NET Core and SQL Server. What architecture and design patterns would you recommend?
8.    How have you utilized Azure DevOps and Kubernetes in your previous projects?
9.    What is the difference between Task, async, and await in C#? Can you explain how these work together for asynchronous programming?
10. What are the benefits of asynchronous programming in .NET Core, especially in web applications?
11. Write a LINQ query to find the highest value in a list of insurance premium values.
12. What are the differences between LINQ to Objects, LINQ to SQL, and LINQ to Entities?
13. How to manage dependencies in a .NET Core application? Can you explain the concept of dependency injection in .NET Core?
14. Explain how routing works in ASP.NET Core Web API. Can you show how you would define a simple route for a GET request in a controller?
15. How to manage the lifecycle of services (Transient, Scoped, Singleton) in .NET Core? Can you give an example of when you would use each type?
16. What is a DbContext in EF Core, and what role does it play in data access?

17. You have a Policy model with fields such as Id, PolicyNumber, PremiumAmount, and IsActive. 