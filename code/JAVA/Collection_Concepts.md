
**✅ What is Map in Java?**

Map is an Interface in Java. 

In Java, the Map Interface is part of the **java.util package** and represents a mapping between a key and a value. 
The Java Map interface is not a subtype of the Collections interface. 
So, it behaves differently from the rest of the collection types.

**Key Features:**

1. **No Duplicates in Keys**: Keys should be unique, but values can be duplicated.
2. **Null Handling**: It allows one null key in implementations like HashMap and LinkedHashMap Only, and allows multiple null values in most implementations.
3. **Thread-Safe Alternatives**: It Use Concurrent **HashMap** for thread-safe operations. Also, wrap an existing map using **Collections.synchronizedMap()** for synchronized access.

**The Map data structure in Java is implemented by two interfaces:**

- Map Interface
- SortedMap Interface

The three primary classes that implement these interfaces are,

- HashMap
- TreeMap
- LinkedHashMap

**We must know that why and when to use Maps.**

Maps are perfect to use for key-value mapping such as dictionaries. Some common scenarios are as follows: 

- A map of error codes and their descriptions.
-  A map of pin codes and cities.
- A map of managers and employees. Each manager (key) is associated with a list of employees (value).
- A map of classes and students.

**Creating Map Objects**

Since Map is an interface, objects cannot be created of the type map. 
We always need a class that extends this map in order to create an object. 
And also, after the introduction of Generics in Java 1.5, it is possible to restrict the type of object that can be stored in the Map. 

Syntax: Defining Type-safe Map:
```java
Map<String, Integer> hm = new HashMap<>();  // Type-safe map storing String keys and Integer values
```

**Characteristics of a Map Interface:**
- A map cannot contain duplicate keys and each key can map to at most one value.
- Some implementations allow null key and null values like the **HashMap and LinkedHashMap**, but some do not like the **TreeMap**.
- The order of a map depends on the specific implementations. For example, TreeMap and LinkedHashMap have predictable orders, while HashMap does not.

  


