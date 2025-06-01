
**Q.1: What do you mean by interface?**

* An interface is a **collection of abstract methods** (plus default/static methods) used to define a **contract** that implementing classes must follow.
* Example:

  ```java
  interface Drawable {
      void draw();
  }
  ```

---

**Q.2: Explain about `extends` and `implements` keywords?**

* `extends`: Used for class-to-class or interface-to-interface inheritance.

  ```java
  class B extends A {}
  interface Y extends X {}
  ```
* `implements`: Used when a class implements an interface.

  ```java
  class Circle implements Drawable {}
  ```

---

**Q.3: What is the purpose of `import`?**

* `import` brings external or built-in classes/packages into scope.
* Example:

  ```java
  import java.util.Scanner;
  ```

---

**Q.4: Explain about interface methods and interface variables?**

* **Methods**: Implicitly `public` and `abstract` (except `default` and `static` methods).
* **Variables**: Implicitly `public`, `static`, and `final`.
* Example:

  ```java
  interface Test {
      int x = 10; // public static final
      void show(); // public abstract
  }
  ```

---

**Q.5: Is multiple inheritance possible in Java?**

* **Not via classes**, but **possible with interfaces**.
* Example:

  ```java
  interface A {}
  interface B {}
  class C implements A, B {}
  ```

---

**Q.6: Why is multiple inheritance not supported in classes but supported in interfaces?**

* Java avoids multiple inheritance in classes to prevent ambiguity (like Diamond Problem).
* Interfaces don't have implementation conflicts (unless default methods are involved).

---

**Q.7: How many interfaces can a Java class implement simultaneously?**

* A Java class can implement **multiple interfaces**.
* Example:

  ```java
  class Demo implements A, B, C {}
  ```

---

**Q.8: What do you mean by marker interface?**

* An interface with **no methods or fields**, used for metadata purposes.
* Example:

  ```java
  interface Serializable {}
  ```

---

**Q.9: What do you mean by Adapter class?**

* A class that provides **default (empty) implementation** of all methods in an interface.
* Mostly used with **listener interfaces**.
* Example:

  ```java
  class MouseAdapter implements MouseListener {
      public void mouseClicked(MouseEvent e) {}
      // Other methods empty
  }
  ```

---

**Q.10: Differences between abstract class & interface?**

| Feature      | Abstract Class              | Interface                          |
| ------------ | --------------------------- | ---------------------------------- |
| Methods      | Abstract + Concrete allowed | Abstract (default/static optional) |
| Variables    | Instance/static allowed     | Always `public static final`       |
| Inheritance  | Single only                 | Multiple allowed                   |
| Constructors | Yes                         | No                                 |

---

**Q.11: What do you mean by default method in Interface?**

* A method in an interface with a **default implementation** using the `default` keyword.
* Example:

  ```java
  interface A {
      default void display() {
          System.out.println("Default method");
      }
  }
  ```

---

**Q.12: What do you mean by static method in Interface?**

* A method defined with `static` inside an interface; **belongs to the interface**, not implementing classes.
* Example:

  ```java
  interface Utility {
      static void show() {
          System.out.println("Static method");
      }
  }
  ```
---
