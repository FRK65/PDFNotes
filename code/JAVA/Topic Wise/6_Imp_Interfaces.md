## ✅ **Detailed List of Core Java Interfaces (for Interviews)**

---

### **1. Runnable (Functional Interface)**

* **Definition**: `Runnable` is a functional interface in the `java.lang` package used to define a task that can be executed by a thread. It contains a single method `run()` which does not return any result.
* **Key Concept**: Used in **multithreading** to define the code that a thread will execute.
* **Method**: `void run()`
* **Example**:

  ```java
  class MyTask implements Runnable {
      public void run() {
          System.out.println("Task is running...");
      }
  }

  Thread t = new Thread(new MyTask());
  t.start();
  ```
* **Use Case**: When we need to execute code in a new thread without returning a result.

---

### **2. Callable<V> (Functional Interface)**

* **Definition**: `Callable` is a functional interface from `java.util.concurrent` that represents a task which returns a result and may throw a checked exception.
* **Key Concept**: Similar to `Runnable`, but returns a value.
* **Method**: `V call() throws Exception`
* **Example**:

  ```java
  class MyJob implements Callable<Integer> {
      public Integer call() {
          return 42;
      }
  }
  ```
* **Use Case**: For concurrent tasks that **return results**, used with `ExecutorService`.

---

### **3. Comparable<T> (Functional Interface)**

* **Definition**: `Comparable` is an interface in `java.lang` that is used to define **natural ordering** for objects of a class. Classes implementing this interface override `compareTo()` method.
* **Method**: `int compareTo(T o)`
* **Example**:

  ```java
  class Student implements Comparable<Student> {
      int marks;
      public int compareTo(Student s) {
          return this.marks - s.marks;
      }
  }
  ```
* **Use Case**: Sorting using `Collections.sort()` without custom comparator.

---

### **4. Comparator<T> (Functional Interface)**

* **Definition**: `Comparator` is an interface from `java.util` used to define **custom orderings** of objects by implementing `compare()` method externally.
* **Method**: `int compare(T o1, T o2)`
* **Example**:

  ```java
  class SortByName implements Comparator<Student> {
      public int compare(Student a, Student b) {
          return a.name.compareTo(b.name);
      }
  }
  ```
* **Use Case**: When sorting needs to be based on multiple or alternative fields.

---

### **5. Serializable (Marker Interface)**

* **Definition**: `Serializable` is a **marker interface** in `java.io` used to mark a class whose objects can be **converted into byte streams** (i.e., serialized).
* **Methods**: None (marker)
* **Example**:

  ```java
  class Employee implements Serializable {
      int id;
      String name;
  }
  ```
* **Use Case**: For saving object state to file, caching, or transmitting over network.

---

### **6. Cloneable (Marker Interface)**

* **Definition**: `Cloneable` is a marker interface in `java.lang` which indicates that a class allows **object cloning** using the `Object.clone()` method.
* **Methods**: None
* **Example**:

  ```java
  class Person implements Cloneable {
      protected Object clone() throws CloneNotSupportedException {
          return super.clone();
      }
  }
  ```
* **Use Case**: When we want to create a **copy of an object** without creating a new one from scratch.

---

### **7. FunctionalInterface (Annotation)**

* **Definition**: `@FunctionalInterface` is not an interface itself, but an annotation that marks an interface as a **functional interface** (must have exactly one abstract method).
* **Key Concept**: Enables use of **lambda expressions**.
* **Example**:

  ```java
  @FunctionalInterface
  interface Calculator {
      int operate(int a, int b);
  }
  ```
* **Use Case**: Functional programming and method references.

---

### **8. Iterable<T>**

* **Definition**: `Iterable` is the root interface of the **Java Collection traversal mechanism**. Any class that implements it can be iterated using the **enhanced for-loop**.
* **Method**: `Iterator<T> iterator()`
* **Example**:

  ```java
  for (String s : list) {
      System.out.println(s);
  }
  ```
* **Use Case**: Used to iterate over a collection like `List`, `Set`, etc.

---

### **9. Iterator<E>**

* **Definition**: `Iterator` is an interface in `java.util` used to traverse a collection **element by element**.
* **Methods**: `hasNext()`, `next()`, `remove()`
* **Example**:

  ```java
  Iterator<String> it = list.iterator();
  while (it.hasNext()) {
      System.out.println(it.next());
  }
  ```
* **Use Case**: When we need fine-grained control during iteration.

---

### **10. Collection<E>**

* **Definition**: Root interface of the **Collection Framework** in `java.util`. Defines general operations for all types of collections like `List`, `Set`.
* **Methods**: `add()`, `remove()`, `clear()`, `size()`, etc.
* **Example**:

  ```java
  Collection<String> col = new ArrayList<>();
  col.add("Java");
  ```
* **Use Case**: Supertype for working with any collection type generically.

---

### **11. List<E>**

* **Definition**: An ordered collection that **allows duplicate elements** and **index-based access**.
* **Subinterfaces**: `ArrayList`, `LinkedList`, etc.
* **Example**:

  ```java
  List<String> names = new ArrayList<>();
  names.add("A");
  names.add("B");
  ```
* **Use Case**: When insertion order matters and duplicates are allowed.

---

### **12. Set<E>**

* **Definition**: A collection that **does not allow duplicate elements**.
* **Subinterfaces**: `HashSet`, `LinkedHashSet`, `TreeSet`
* **Example**:

  ```java
  Set<String> items = new HashSet<>();
  items.add("A");
  ```
* **Use Case**: When uniqueness of elements is important.

---

### **13. Map\<K, V>**

* **Definition**: A collection that stores **key-value pairs**, where keys are **unique**.
* **Subinterfaces**: `HashMap`, `TreeMap`, `LinkedHashMap`
* **Example**:

  ```java
  Map<Integer, String> map = new HashMap<>();
  map.put(1, "One");
  ```
* **Use Case**: When we need to associate keys with values.

---

### **14. AutoCloseable**

* **Definition**: Interface from `java.lang` that requires a class to implement the `close()` method, which is called automatically when using **try-with-resources**.
* **Method**: `void close() throws Exception`
* **Example**:

  ```java
  class MyResource implements AutoCloseable {
      public void close() {
          System.out.println("Resource closed");
      }
  }
  ```
* **Use Case**: For automatically releasing resources like streams, DB connections.

---

### **15. EventListener**

* **Definition**: A **base interface** in `java.util` for all AWT event listeners in Java GUI programming.
* **Subinterfaces**: `ActionListener`, `MouseListener`, etc.
* **Example**:

  ```java
  class MyListener implements ActionListener {
      public void actionPerformed(ActionEvent e) {
          // Handle button click
      }
  }
  ```
* **Use Case**: Event-driven GUI programming with AWT/Swing.

---

### **16. Observer (Deprecated in Java 9)**

* **Definition**: Used in **Observer Design Pattern**, allows objects to get notified when another object (Observable) changes.
* **Method**: `update(Observable o, Object arg)`
* **Example**:

  ```java
  class MyObserver implements Observer {
      public void update(Observable o, Object arg) {
          System.out.println("Updated!");
      }
  }
  ```
* **Use Case**: Earlier used in MVC designs, now replaced by custom observer systems or reactive APIs.

---

## 📌 Bonus Marker Interfaces (No Methods)

| Interface     | Purpose                                  |
| ------------- | ---------------------------------------- |
| Serializable  | Enables serialization                    |
| Cloneable     | Enables object cloning                   |
| Remote        | Marks class as remotely accessible (RMI) |
| EventListener | Marker for event-handling classes        |

---
