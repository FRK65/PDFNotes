* **List, Set, Queue, Map**
* **Common implementations:** `ArrayList`, `LinkedList`, `Vector`, `Stack`, `PriorityQueue`, `Deque`, `HashSet`, `LinkedHashSet`, `TreeSet`, `HashMap`, `LinkedHashMap`, `TreeMap`, `Hashtable`, etc.
* Properties like **Thread-Safe**, **Ordering**, **Duplicates Allowed**, **Null Allowed**, and **Performance Notes**.

---

## ✅ **Java Collections Comparison Table**

| Class / Interface        | Type        | Thread-Safe               | Ordered (Insertion/Sorted)  | Duplicates Allowed | Null Allowed                             | Backed By / Notes                                     |
| ------------------------ | ----------- | ------------------------- | --------------------------- | ------------------ | ---------------------------------------- | ----------------------------------------------------- |
| **ArrayList**            | List        | ❌                         | Insertion Order             | ✅                  | ✅                                        | Fast random access; resizing array                    |
| **LinkedList**           | List/Deque  | ❌                         | Insertion Order             | ✅                  | ✅                                        | Doubly-linked list; good for insert/delete            |
| **Vector**               | List        | ✅ (synchronized)          | Insertion Order             | ✅                  | ✅                                        | Legacy class; slower than `ArrayList`                 |
| **Stack**                | List (LIFO) | ✅ (inherited from Vector) | Insertion Order             | ✅                  | ✅                                        | Legacy; use `Deque` instead                           |
| **CopyOnWriteArrayList** | List        | ✅ (thread-safe)           | Insertion Order             | ✅                  | ✅                                        | Safe in concurrent read-heavy cases                   |
| **HashSet**              | Set         | ❌                         | No                          | ❌                  | ✅                                        | Backed by `HashMap`; no duplicates                    |
| **LinkedHashSet**        | Set         | ❌                         | Insertion Order             | ❌                  | ✅                                        | Maintains order                                       |
| **TreeSet**              | Set         | ❌                         | Sorted                      | ❌                  | ❌\* (null disallowed if Comparator used) | Backed by TreeMap                                     |
| **CopyOnWriteArraySet**  | Set         | ✅                         | Insertion Order             | ❌                  | ✅                                        | Good for read-heavy concurrent applications           |
| **PriorityQueue**        | Queue       | ❌                         | Sorted (Natural/Comparator) | ✅ (in queue logic) | ❌                                        | Min-heap by default                                   |
| **ArrayDeque**           | Deque       | ❌                         | Insertion Order             | ✅                  | ❌                                        | Faster than Stack and LinkedList for Deque operations |
| **HashMap**              | Map         | ❌                         | No                          | Keys: ❌, Values: ✅ | Keys: 1 null, Values: many nulls         | Key-value store; fast lookup                          |
| **LinkedHashMap**        | Map         | ❌                         | Insertion Order             | Keys: ❌, Values: ✅ | ✅                                        | Maintains order                                       |
| **TreeMap**              | Map         | ❌                         | Sorted by key               | Keys: ❌, Values: ✅ | ❌ (null keys not allowed)                | Red-Black tree                                        |
| **Hashtable**            | Map         | ✅                         | No                          | Keys: ❌, Values: ✅ | ❌                                        | Legacy; synchronized                                  |
| **ConcurrentHashMap**    | Map         | ✅ (Concurrent)            | No                          | Keys: ❌, Values: ✅ | ❌                                        | High-performance thread-safe map                      |

---

### 🟨 **Legend and Key Notes:**

* ✅ = Yes
* ❌ = No
* * \= TreeSet/TreeMap allow `null` only if comparator permits — which is generally discouraged

---

### 🔄 **Synchronized vs Concurrent:**

* **Synchronized Collections** (e.g., `Vector`, `Hashtable`) block the entire structure for every operation (less efficient).
* **Concurrent Collections** (e.g., `ConcurrentHashMap`, `CopyOnWriteArrayList`) allow better performance through finer locking or snapshot isolation.

---
