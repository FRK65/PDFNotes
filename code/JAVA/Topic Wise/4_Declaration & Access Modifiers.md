### **Q.1 How many classes can a Java program contain?**

**Answer**:
A **Java program** can contain **multiple classes**, but there can only be **one public class** with the same name as the filename. Other classes can be defined as **non-public** or **inner classes**.

* **Key Concept**: While only one class can be public and match the filename, Java allows multiple classes in the same file, but the program is typically structured with a primary class that contains the `main` method.

**Real-life Example**:
A program could have one main class, and several helper classes.

```java
public class MainClass { 
    public static void main(String[] args) {
        // main method
    }
}

class HelperClass {
    // non-public helper class
}
```

---

### **Q.2 What do you mean by fully qualified name and what is the problem in using a fully qualified name?**

**Answer**:
A **fully qualified name** (FQN) in Java is the complete name of a class, including its package name, which uniquely identifies it in the Java runtime environment.

* **Key Concept**: It’s essentially the **package path + class name**, e.g., `java.util.ArrayList`.

**Real-life Example**:
Using the fully qualified name to refer to `ArrayList`:

```java
java.util.ArrayList<String> list = new java.util.ArrayList<>();
```

* **Problem**: Using FQN can make the code **verbose** and harder to read. This is why imports are generally preferred.

---

### **Q.3 What is the purpose of import?**

**Answer**:
The **`import`** statement in Java is used to bring in external classes or entire packages so that you can use them without specifying their fully qualified names.

* **Key Concept**: **Simplifies code** by making it easier to reference classes in other packages.

**Real-life Example**:
Without import, you'd need to use the full class name, but with import, you can reference it directly.

```java
import java.util.ArrayList;
ArrayList<String> list = new ArrayList<>();
```

---

### **Q.4 Explain types of import statement?**

**Answer**:
There are two main types of **import statements** in Java:

1. **Single Class Import**:
   Imports a specific class from a package.

   ```java
   import java.util.ArrayList;  // Importing a specific class
   ```

2. **Wildcard Import**:
   Imports all classes from a package.

   ```java
   import java.util.*;  // Importing all classes from the java.util package
   ```

* **Key Concept**: Wildcard imports reduce typing, but it's better to import specific classes to avoid naming conflicts and improve code clarity.

---

### **Q.6 What do you mean by static import?**

**Answer**:
**Static import** allows you to directly access **static members** (fields and methods) of a class without having to use the class name.

* **Key Concept**: Static import makes the code cleaner, especially when you use static constants or methods frequently.

**Real-life Example**:
Using `Math.PI` directly by importing it statically:

```java
import static java.lang.Math.PI;

public class Circle {
    public double area(double radius) {
        return PI * radius * radius;
    }
}
```

---

### **Q.7 What are the advantages and disadvantages of using static import?**

**Answer**:

* **Advantages**:

  * Makes the code more readable and concise, especially when working with **constants** or **static methods**.
  * Reduces redundancy by not needing to repeatedly reference the class name for static members.
* **Disadvantages**:

  * **Naming conflicts**: If multiple classes have static members with the same name, it can lead to ambiguity.
  * **Readability**: Overuse can make it unclear where static methods or constants are coming from.

**Real-life Example**:

* **Good**: Using `Math.PI` for a cleaner code.
* **Bad**: Overusing static imports leading to unclear code where members are being referenced.

```java
import static java.lang.Math.*;
double result = sqrt(25);  // It’s unclear whether `sqrt` is from Math class or elsewhere
```

---

### **Q.8 What do you mean by package?**

**Answer**:
A **package** in Java is a **namespace** that groups related classes and interfaces. It helps organize the code, prevents naming conflicts, and provides access protection.

* **Key Concept**: Packages also allow code modularization and better management of large codebases.

**Real-life Example**:
A package for database operations might contain classes like `DBConnection`, `DBQuery`, etc.

```java
package com.example.database;
public class DBConnection { 
    // Database connection logic
}
```

---

### **Q.9 What do you mean by public modifier?**

**Answer**:
The **`public`** modifier is an **access modifier** that allows a class, method, or variable to be accessible from any other class.

* **Key Concept**: It's the broadest access level, meaning **no access restriction**.

**Real-life Example**:
The `main()` method in a Java application is `public` so it can be accessed by the Java runtime to start the program.

```java
public class MyClass {
    public void display() {
        System.out.println("Hello, World!");
    }
}
```

---

### **Q.10 What do you mean by private modifier?**

**Answer**:
The **`private`** modifier restricts access to a class, method, or variable to **within the same class only**.

* **Key Concept**: It provides **encapsulation**, ensuring that data is protected and cannot be accessed or modified directly from outside the class.

**Real-life Example**:
Private variables in a class ensure that sensitive data is only accessible through getter and setter methods.

```java
public class Account {
    private double balance;  // private variable

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}
```

---

### **Q.11 What do you mean by <default> modifier?**

**Answer**:
The **`default`** modifier (also called **package-private**) is the **default access level** when no access modifier is specified. It means the class, method, or variable is accessible **only within the same package**.

* **Key Concept**: It’s used when you want to restrict access to the class, method, or variable within the same package but keep it hidden from other packages.

**Real-life Example**:
A method that should only be accessed within the same package, but not from outside.

```java
class MyClass {
    void display() {  // default access level
        System.out.println("This is a package-private method");
    }
}
```

---

### **Q.12 What do you mean by protected modifier?**

**Answer**:
The **`protected`** modifier allows a class, method, or variable to be accessed by:

* The **same package**.

* **Subclasses**, even if they are in different packages.

* **Key Concept**: It allows **inheritance** while still providing some level of encapsulation.

**Real-life Example**:
A subclass in a different package can access a **protected** method from its parent class.

```java
package package1;
public class Parent {
    protected void display() {
        System.out.println("Protected Method");
    }
}

package package2;
public class Child extends Parent {
    public void show() {
        display();  // Accessing protected method from Parent class
    }
}
```

---

### **Q.13 What do you mean by final modifier?**

**Answer**:
The **`final`** modifier is used to indicate that a class, method, or variable cannot be changed:

* **Final class**: Cannot be subclassed.

* **Final method**: Cannot be overridden.

* **Final variable**: Its value cannot be changed once initialized.

* **Key Concept**: The `final` modifier enforces immutability or restricts modification of methods and classes.

**Real-life Example**:
You might have a constant value in your application that should never change.

```java
final double PI = 3.14159;  // A constant that cannot be changed
```

---

### **Q.14 Explain abstract class and abstract method?**

**Answer**:

* **Abstract Class**: A class that cannot be instantiated directly and may have both abstract methods (methods without implementation) and non-abstract methods (methods with implementation).

* **Abstract Method**: A method without a body, meant to be overridden by subclasses.

* **Key Concept**: Abstract classes allow the definition of common behavior while leaving the implementation details to subclasses.

**Real-life Example**:
A **Shape** class might be abstract, and subclasses like **Circle** and **Rectangle** implement the abstract method `draw()`.

```java
abstract class Shape {
    abstract void draw();  // abstract method
}
```

---

### **Q.15 What is the purpose of strictfp modifier?**

**Answer**:
The **`strictfp`** modifier is used to **restrict floating-point calculations** to a strict standard, ensuring consistent results across different platforms. It ensures that floating-point operations adhere to the IEEE 754 standard.

* **Key Concept**: Used to ensure that floating-point arithmetic is consistent and portable.

**Real-life Example**:
When performing **scientific** calculations where precision across different platforms
