### **Q.1 What do you mean by Inheritance? What are the advantages of Inheritance?**

**Answer**:
**Inheritance** is a mechanism in Java that allows one class (subclass) to inherit the properties (fields) and methods of another class (superclass).
**Advantages**:

* **Code Reusability**: You can reuse existing code in the subclass.
* **Extensibility**: It allows extending the behavior of a class.
* **Maintainability**: Changes to the superclass affect all subclasses.

**Real-life Example**:
A **Car** class (subclass) inherits from a **Vehicle** class (superclass), so it can reuse properties like `speed` and methods like `accelerate()`.

---

### **Q.2 Which class is by default parent class of all Java classes? Why?**

**Answer**:
The default parent class of all Java classes is **`Object`**.
**Why?**: Every class in Java implicitly inherits from `Object`, which is the root of the class hierarchy. It provides essential methods like `toString()`, `equals()`, and `hashCode()`.

---

### **Q.3 How many types of Inheritance are possible? Explain each and which type of inheritance is not supported in Java?**

**Answer**:

* **Single Inheritance**: A class inherits from one superclass.
* **Multilevel Inheritance**: A class inherits from a class, which is already a subclass of another class.
* **Hierarchical Inheritance**: Multiple classes inherit from a single superclass.
* **Hybrid Inheritance**: A combination of two or more types of inheritance (not supported in Java due to ambiguity in method inheritance).

**Not Supported in Java**: **Multiple Inheritance** through classes is not supported because it can cause ambiguity.

---

### **Q.4 What do you mean by multiple Inheritance?**

**Answer**:
**Multiple inheritance** occurs when a class inherits from more than one superclass. It is not allowed in Java through classes because it can cause ambiguity.

---

### **Q.5 Why Java doesn’t support multiple inheritance?**

**Answer**:
Java doesn’t support multiple inheritance through classes to avoid the **Diamond Problem**, where a class can inherit conflicting methods from multiple classes, causing ambiguity.

---

### **Q.6 What is an ambiguity problem or diamond problem regarding inheritance in Java?**

**Answer**:
The **diamond problem** occurs when a class inherits from two classes that have a common ancestor, leading to ambiguity in method resolution. In Java, this is avoided by not allowing multiple inheritance through classes.

---

### **Q.7 Why does the ambiguity problem not arise in the case of interfaces in Java?**

**Answer**:
In Java, the ambiguity problem doesn’t arise with interfaces because **interfaces cannot have method implementations** (prior to Java 8). If two interfaces have the same method, the class implementing them must explicitly define the method, resolving any ambiguity.

---

### **Q.8 What do you mean by a HAS-A relationship?**

**Answer**:
A **HAS-A relationship** indicates that one class contains or has an instance of another class. This is also known as **composition** or **aggregation**.

**Real-life Example**:
A **Car** has an **Engine** — the car "has" an engine, but the engine is not necessarily part of the car in all scenarios (e.g., engine replacement).

---

### **Q.9 What do you mean by composition and aggregation in Java?**

**Answer**:

* **Composition**: A form of **strong association** where the lifetime of the contained object depends on the container object. If the container object is destroyed, the contained object is also destroyed.
* **Aggregation**: A form of **weaker association** where the contained object can exist independently of the container.

**Real-life Example**:

* **Composition**: A **House** has **Rooms**. If the house is destroyed, rooms are also destroyed.
* **Aggregation**: A **University** has **Departments**, but a department can exist without the university.

---

### **Q.10 Give practical example of composition and aggregation in Java?**

**Answer**:

```java
// Composition Example: House -> Rooms
class Room {
    // Room properties and methods
}

class House {
    private Room room; // Composition: House has a Room
    public House() {
        this.room = new Room();  // Room is created with the House
    }
}

// Aggregation Example: University -> Departments
class Department {
    // Department properties and methods
}

class University {
    private List<Department> departments; // Aggregation: University has Departments
}
```

---

### **Q.11 What do you mean by method signature?**

**Answer**:
A **method signature** consists of the method's **name** and **parameter types** (but not the return type or method body). It uniquely identifies a method.

---

### **Q.12 What do you mean by method overloading?**

**Answer**:
**Method overloading** is defining multiple methods with the same name but different parameters (either by type, number, or both).

**Real-life Example**:
A **`print()`** method can be overloaded to print different types of messages (e.g., `print(String)` and `print(int)`).

---

### **Q.13 What do you mean by method overriding?**

**Answer**:
**Method overriding** is when a subclass provides a specific implementation for a method that is already defined in its superclass. The method signature must remain the same.

**Real-life Example**:
A **Dog** class overrides the `sound()` method from an **Animal** class to provide a specific implementation (barking).

---

### **Q.14 What do you mean by method hiding?**

**Answer**:
**Method hiding** occurs when a subclass defines a static method with the same signature as a static method in the superclass. Unlike method overriding, this doesn’t involve polymorphism.

---

### **Q.15 Explain the differences between method overriding and method hiding in Java?**

**Answer**:

| Aspect          | **Method Overriding**                  | **Method Hiding**                           |
| --------------- | -------------------------------------- | ------------------------------------------- |
| **Type**        | Dynamic (runtime polymorphism)         | Static (compile-time polymorphism)          |
| **Inheritance** | Occurs in instance methods.            | Occurs in static methods.                   |
| **Binding**     | Method binding happens at runtime.     | Method binding happens at compile time.     |
| **Example**     | Overriding `toString()` in a subclass. | Hiding static method `print()` in subclass. |

---

### **Q.16 Explain the differences between method overloading and method overriding in Java?**

**Answer**:

| Aspect          | **Method Overloading**                  | **Method Overriding**                             |
| --------------- | --------------------------------------- | ------------------------------------------------- |
| **Definition**  | Same method name, different parameters. | Same method signature in subclass and superclass. |
| **Return Type** | Can have different return types.        | Return type must be the same or covariant.        |
| **Binding**     | Compile-time (static polymorphism).     | Runtime (dynamic polymorphism).                   |

---

### **Q.17 What do you mean by polymorphism? How many types of polymorphism are there?**

**Answer**:
**Polymorphism** means the ability of an object to take many forms. There are two types:

* **Compile-time (Static) Polymorphism**: Achieved through **method overloading** and **operator overloading**.
* **Runtime (Dynamic) Polymorphism**: Achieved through **method overriding** and **inheritance**.

---

### **Q.20 What is the main purpose of the Constructor?**

**Answer**:
The **constructor** initializes a newly created object and sets initial values for its fields. It is called when an object is instantiated.

---

### **Q.23 What do you mean by default constructor?**

**Answer**:
A **default constructor** is a no-argument constructor provided by Java if no other constructor is explicitly defined in the class. It initializes fields to default values.

---

### **Q.24 What are the differences between super(), this() and super, this?**

**Answer**:

* **`super()`**: Refers to the **parent class** constructor.
* **`this()`**: Refers to another constructor in the **same class**.
* **`super`**: Refers to a member of the **parent class**.
* **`this`**: Refers to a member of the **current class**.

---

### **Q.26 What do you mean by object type casting?**

**Answer**:
**Object type casting** is converting an object from one type to another. It can be **upcasting** (subclass to superclass) or **downcasting** (superclass to subclass).

---

### **Q.27 Explain rules for object type casting?**

**Answer**:

* **Upcasting** is implicit and safe.
* **Downcasting** is explicit and requires checking with `instanceof`.
* **Invalid casting** leads to `ClassCastException`.

---

### **Q.28 What do you mean by Data hiding, Abstraction, Encapsulation in Java?**

**Answer**:

* **Data Hiding**: Hiding the internal state of an object by making variables private and providing controlled access through getters/setters.
* **Abstraction**: Hiding unnecessary implementation details and showing only relevant functionality.
* **Encapsulation**: Bundling data and methods together and restricting access to data by using access modifiers.

### **Q.29 What is the purpose of the static block?**

**Answer**:
A **static block** in Java is used to initialize static variables or perform any static initialization tasks when the class is loaded into memory. It runs only once, when the class is first loaded.

* **Purpose**: Used to initialize static data, or to perform some setup operations that need to be done once, such as loading a configuration file or connecting to a database.

**Real-life Example**:
Imagine a **DatabaseManager** class that initializes a database connection when the class is loaded.

```java
class DatabaseManager {
    static Connection conn;
    
    static {
        conn = establishConnection(); // Initialize static database connection
    }
}
```

---

### **Q.30 What is the purpose of the instance block?**

**Answer**:
An **instance block** is a block of code that runs **every time an object of the class is created**. It is used for **initializing instance variables** or performing setup tasks that need to run for every object.

* **Purpose**: To initialize instance variables or perform setup for every object created, before the constructor is executed.

**Real-life Example**:
In a **Student** class, you might use an instance block to calculate the `studentID` whenever a new object is created.

```java
class Student {
    int studentID;
    
    {
        studentID = (int)(Math.random() * 1000); // Initialize studentID for each student
    }
}
```

---

### **Q.31 What do you mean by coupling?**

**Answer**:
**Coupling** refers to the degree of dependence between classes or modules in a system. It measures how closely one class (or module) is related to another.

* **Tight Coupling**: When classes/modules are heavily dependent on each other, it makes the system difficult to maintain and modify.
* **Loose Coupling**: When classes/modules are independent of each other, making the system more flexible and maintainable.

**Real-life Example**:
In a **Car** class, if the engine is directly created within the car class, it’s tightly coupled. If the engine is passed as a dependency (e.g., using dependency injection), the coupling is loose.

```java
// Tight Coupling
class Car {
    Engine engine = new Engine(); // Directly creates Engine

    // Loose Coupling
    class Car {
        Engine engine;
        Car(Engine engine) { this.engine = engine; } // Passes Engine as a dependency
    }
}
```

---

### **Q.32 What do you mean by Cohesion?**

**Answer**:
**Cohesion** refers to how closely related and focused the responsibilities of a class or module are. 
High cohesion means the class/module does one thing well and all of its methods and properties are tightly related to that purpose.

* **High Cohesion**: When a class has methods that are related and serve a single purpose, it's easier to maintain and understand.
* **Low Cohesion**: When a class performs multiple unrelated tasks, it becomes harder to maintain and modify.

**Real-life Example**:
A **Car** class with methods like `start()`, `accelerate()`, and `stop()` has high cohesion because they all relate to a single responsibility: managing car movement. If the class also had a method like `calculateTax()`, it would have low cohesion.

```java
// High Cohesion
class Car {
    void start() { /* start the car */ }
    void accelerate() { /* accelerate the car */ }
    void stop() { /* stop the car */ }
}

// Low Cohesion
class Car {
    void start() { /* start the car */ }
    void accelerate() { /* accelerate the car */ }
    void calculateTax() { /* unrelated to car movement */ }
}
```
---


