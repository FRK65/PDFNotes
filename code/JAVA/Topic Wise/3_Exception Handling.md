### **Q.1 What do you mean by Exception?**

**Answer**:
An **exception** in Java is an **event** that disrupts the normal flow of a program's execution. It occurs during the runtime and indicates that something went wrong (like trying to divide by zero or accessing an invalid index in an array). Exceptions are objects that represent errors or unexpected conditions in the program.

* **Key Concept**: Exceptions are objects that are derived from the `Throwable` class in Java.

**Real-life Example**:
Imagine you are trying to open a file that doesn't exist. This results in an **IOException**.

```java
FileReader file = new FileReader("non_existent_file.txt");  // Throws FileNotFoundException
```

---

### **Q.2 What is the main objective of Exception Handling?**

**Answer**:
The main objective of **exception handling** in Java is to handle runtime errors (exceptions) in a graceful manner, preventing the program from crashing and allowing it to recover or provide meaningful feedback to the user.

* **Key Concept**: It improves the program’s reliability, readability, and maintainability by allowing the code to handle errors efficiently.

**Real-life Example**:
Instead of the program crashing when trying to divide by zero, exception handling ensures the program can handle it and display a message like "Cannot divide by zero."

```java
try {
    int result = 10 / 0; // Throws ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Error: Cannot divide by zero");
}
```

---

### **Q.3 What is the meaning of Exception Handling?**

**Answer**:
**Exception handling** in Java refers to the process of responding to exceptional conditions or runtime errors that occur during the execution of a program. It uses specific constructs (like `try`, `catch`, `finally`, etc.) to catch and handle exceptions.

* **Key Concept**: It ensures that the program continues executing even if an exception occurs, or it handles the error appropriately.

**Real-life Example**:
In an online shopping cart, if a product’s price cannot be fetched due to an issue with the server, the program can show a friendly error message to the user without crashing.

```java
try {
    // Code that might throw an exception
} catch (Exception e) {
    // Handle the exception
} finally {
    // Clean-up code, will always execute
}
```

---

### **Q.5 Which is the root class for Java Exception Hierarchy and why?**

**Answer**:
The root class for Java's exception hierarchy is **`Throwable`**. It is the superclass of all errors and exceptions in Java.

* **Key Concept**: Both **`Exception`** and **`Error`** inherit from `Throwable`. While `Exception` is used for runtime exceptions and checked exceptions, `Error` is used for critical errors that usually can't be handled, such as **OutOfMemoryError**.

**Real-life Example**:
An **Exception** might represent a user input error, while an **Error** could indicate an **OutOfMemoryError** due to excessive memory use.

---

### **Q.6 What are the differences between checked exceptions & unchecked exceptions?**

**Answer**:

| **Aspect**               | **Checked Exceptions**                                                                                     | **Unchecked Exceptions**                                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Definition**           | Exceptions that the compiler requires to be handled at compile time (e.g., `IOException`, `SQLException`). | Exceptions that don't need to be explicitly handled (e.g., `NullPointerException`, `ArrayIndexOutOfBoundsException`). |
| **Handling Requirement** | Must be handled using `try-catch` or declared in the method signature using `throws`.                      | No need to handle or declare.                                                                                         |
| **Examples**             | `IOException`, `FileNotFoundException`.                                                                    | `ArithmeticException`, `NullPointerException`.                                                                        |

**Real-life Example**:

* **Checked**: Opening a file without checking if it exists (`IOException`).
* **Unchecked**: Dividing a number by zero (`ArithmeticException`).

---

### **Q.7 What are the differences between partially checked exceptions & fully checked exceptions?**

**Answer**:

* **Partially Checked Exceptions**: These are exceptions that are not strictly enforced by the compiler. You can choose to handle them or not (e.g., `RuntimeException`).
* **Fully Checked Exceptions**: These exceptions must either be caught in a `try-catch` block or declared with `throws`. The compiler forces you to handle them (e.g., `IOException`, `SQLException`).

**Real-life Example**:

* **Partially Checked**: A `NullPointerException` will not force you to handle it explicitly.
* **Fully Checked**: An `IOException` when reading from a file must be handled or declared.

---

### **Q.8 What is the purpose of try and catch block?**

**Answer**:
The `try` and `catch` blocks are used to handle exceptions in Java:

* **`try` block**: Contains code that might throw an exception.

* **`catch` block**: Catches and handles the exception if one occurs.

* **Key Concept**: The `try` block tries to execute code, and if an exception occurs, it’s caught by the corresponding `catch` block.

**Real-life Example**:
Attempting to divide by zero is enclosed in a `try` block. If an exception occurs, the `catch` block handles it.

```java
try {
    int result = 10 / 0;  // Throws ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Error: Cannot divide by zero");
}
```

---

### **Q.9 Explain about methods to print exception information to the console?**

**Answer**:
Java provides several methods to print exception details:

* **`getMessage()`**: Returns a detailed message about the exception.
* **`printStackTrace()`**: Prints the stack trace (method calls leading to the exception).
* **`toString()`**: Returns a string representation of the exception.

**Real-life Example**:
To print the exception message and stack trace for debugging:

```java
try {
    int result = 10 / 0;  // ArithmeticException
} catch (ArithmeticException e) {
    System.out.println("Exception Message: " + e.getMessage());
    e.printStackTrace();  // Prints stack trace for debugging
}
```

---

### **Q.10 What is the main purpose of try with multiple catch blocks?**

**Answer**:
The main purpose of **multiple `catch` blocks** is to handle different types of exceptions separately and specifically. Each `catch` block is designed to handle a particular type of exception, allowing more granular control over error handling.

* **Key Concept**: This allows the program to handle various types of exceptions in different ways.

**Real-life Example**:
A program might want to handle a `FileNotFoundException` differently than a `NumberFormatException`.

```java
try {
    // Some code that may throw exceptions
} catch (FileNotFoundException e) {
    System.out.println("File not found!");
} catch (NumberFormatException e) {
    System.out.println("Invalid number format!");
}
```

---

### **Q.11 What is the main purpose and specialty of finally block?**

**Answer**:
The **`finally` block** is used to **execute code** that must run regardless of whether an exception is thrown or not. This is typically used for cleaning up resources (e.g., closing files or releasing database connections).

* **Key Concept**: The `finally` block always executes after the `try` block and its associated `catch` blocks, even if an exception is thrown.

**Real-life Example**:
When opening a file, the `finally` block ensures that the file is closed, even if an exception occurs.

```java
try {
    // Open file
} catch (Exception e) {
    // Handle exception
} finally {
    // Close file (important cleanup)
}
```

---

### **Q.13 What is the purpose of the throw keyword?**

**Answer**:
The **`throw`** keyword is used to explicitly **throw an exception** from a method or block of code. It’s mainly used when a certain condition is met that requires throwing an exception.

* **Key Concept**: Allows custom exception throwing for specific error conditions.

**Real-life Example**:
Throwing an exception if a user input is invalid:

```java
if (age < 18) {
    throw new IllegalArgumentException("Age must be 18 or older");
}
```

---

### **Q.14 What is the purpose of the throws keyword?**

**Answer**:
The **`throws`** keyword is used in a method signature to **declare that a method may throw one or more exceptions**. It informs the caller that they must handle the exceptions or declare them in their own method.

* **Key Concept**: It is used to propagate exceptions up the call stack.

**Real-life Example**:
If a method might throw an `IOException`, it needs to declare it using `throws`.

```java
public void readFile() throws IOException {
    // Code that might throw IOException
}
```

---

### **Q.15 How many types of exceptions are available in Java?**

**Answer**:
There are two main types of exceptions in Java:

1. **Checked Exceptions**: Exceptions that must be either caught or declared (e.g., `IOException`, `SQLException`).
2. **Unchecked Exceptions**: Exceptions that are not required to be caught or declared (e.g., `NullPointerException`, \`ArrayIndexOutOf
