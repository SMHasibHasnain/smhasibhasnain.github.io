---
title: "🍵 Core Collection Interfaces Cheatsheet: Foundations of Java Collections Framework"
date: 2025-07-29
categories: [Java, Cheat Sheet]
tags: [JavaScript, Collection Framework, Reference]
pin: true
toc: true
comments: false
---

![Alt Text](/assets/img/collection.png)

## Java Collection Framework – Overview Table


| Class                      | Interface(s) Implemented           | Also Implements / Extends                     | Ordering                | Duplicates | Null Allowed                     | Thread Safe     | Fail‑Fast Iterator         | Performance (Avg)       | Legacy/Modern     | Typical Use Case                            |
|---------------------------|-------------------------------------|------------------------------------------------|-------------------------|------------|----------------------------------|------------------|-----------------------------|--------------------------|-------------------|---------------------------------------------|
| `ArrayList` 🔴               | `List`                              | `RandomAccess`, `Cloneable`, `Serializable`    | Insertion               | ✅ Yes      | ✅ Multiple nulls                 | ❌ No           | ✅ Yes                      | O(1) get, O(n) remove    | Modern            | Dynamic array, fast random access           |
| `LinkedList` 🟢             | `List`, `Deque`, `Queue`            | `Cloneable`, `Serializable`                     | Insertion               | ✅ Yes      | ✅ Yes                           | ❌ No           | ✅ Yes                      | O(1) add/remove at ends   | Modern            | Frequent insertion/deletion or queue        |
| `Vector` 🔴👴🔐                 | `List`                              | `RandomAccess`, `Cloneable`, `Serializable`    | Insertion               | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ✅ Yes                      | O(1) synchronized        | Legacy            | Thread-safe list (historical use)           |
| `Stack` 🔴👴🔐                  | `List` (via `Vector`)               | extends `Vector`                                | LIFO                    | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ✅ Yes                      | O(1) push/pop             | Legacy            | Classic stack operations                    |
| `CopyOnWriteArrayList` 🔴🔐   | `List`                              | `Cloneable`, `Serializable`                     | Insertion               | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ❌ (snapshot)                | O(n) writes, O(1) read    | Modern (Concurrent) | Thread-safe mostly-read list             |
| `HashSet` 🔵                | `Set`                               | `Cloneable`, `Serializable`                    | Unordered               | ❌ No       | ✅ One null                         | ❌ No           | ✅ Yes                      | O(1) operations           | Modern            | Unique items, high performance              |
| `LinkedHashSet` 🔵🟢          | `Set`                               | extends `HashSet`, `Serializable`               | Insertion               | ❌ No       | ✅ Yes                           | ❌ No           | ✅ Yes                      | O(1) operations           | Modern            | Maintains insertion order                   |
| `TreeSet` 🟣                | `NavigableSet`, `SortedSet`         | `Cloneable`, `Serializable`                     | Sorted                   | ❌ No       | ❌ No                            | ❌ No           | ✅ Yes                      | O(log n) operations       | Modern            | Sorted set, ordered operations              |
| `CopyOnWriteArraySet` 🔴🔐    | `Set`                               | `Cloneable`, `Serializable`                     | Insertion               | ❌ No       | ✅ Yes                           | ✅ Yes          | ❌ (snapshot)                | O(n) writes, O(1) read    | Modern (Concurrent) | Read-heavy thread-safe set             |
| `ConcurrentSkipListSet` 🟣🔐  | `NavigableSet`, `SortedSet`, `Set`  | `Cloneable`, `Serializable`                     | Sorted                   | ❌ No       | ❌ No                            | ✅ Yes          | ❌ (weakly consistent)       | O(log n) concurrent ops   | Modern (Concurrent) | Highly concurrent sorted set            |
| `PriorityQueue` 🟡          | `Queue`                             | `Serializable`                                  | Priority (custom/natural) | ✅ Yes    | ✅ Yes                           | ❌ No           | ✅ Yes                      | O(log n) insertion        | Modern            | Priority-based ordering                     |
| `ArrayDeque` 🔴             | `Deque`                             | `Cloneable`, `Serializable`                     | Insertion               | ✅ Yes      | ❌ No                            | ❌ No           | ✅ Yes                      | O(1) at ends              | Modern            | Efficient stack/queue without blocking      |
| `LinkedBlockingDeque` 🟢🔐    | `BlockingDeque`, `Deque`, `Queue`   | `Serializable`                                  | FIFO or LIFO            | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ❌ (weakly consistent)       | O(1) operations           | Modern (Concurrent) | Thread-safe double-ended queue           |
| `LinkedBlockingQueue` 🟢🔐    | `BlockingQueue`, `Queue`            | `Serializable`                                  | FIFO                    | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ❌                          | O(1) operations           | Modern (Concurrent) | Producer-consumer queue                 |
| `ArrayBlockingQueue` 🔴🔐     | `BlockingQueue`, `Queue`            | `Serializable`                                  | FIFO (bounded)          | ✅ Yes      | ❌ No                            | ✅ Yes          | ❌                          | O(1) operations           | Modern (Concurrent) | Fixed-size blocking queue               |
| `PriorityBlockingQueue` 🟡🔐  | `BlockingQueue`, `Queue`            | `Serializable`                                  | Priority                 | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ❌                          | O(log n) insertion        | Modern (Concurrent) | Concurrent priority queue              |
| `DelayQueue` 🟡🔐             | `BlockingQueue`, `Queue`            | `Serializable`                                  | Delay-ordered            | ✅ Yes      | ❌ No                            | ✅ Yes          | ❌                          | O(log n) operations       | Modern (Concurrent) | Scheduled task queue                   |
| `SynchronousQueue` ⚪🔐       | `BlockingQueue`, `Queue`            | `Serializable`                                  | None (hand-off only)     | ❌ No       | ❌ No                            | ✅ Yes          | ❌                          | O(1)                     | Modern (Concurrent) | Thread rendezvous queue                 |
| `LinkedTransferQueue` 🟢🔐    | `TransferQueue`, `BlockingQueue`, `Queue` | `Serializable`                             | FIFO                    | ✅ Yes      | ✅ Yes                           | ✅ Yes          | ❌                          | O(1) operations           | Modern (Concurrent) | High-throughput producer-consumer handoff |
| `HashMap` 🔵                | `Map`                               | `Cloneable`, `Serializable`                     | Unordered               | ❌ Keys     | ✅ one null key, multiple null values | ❌ No       | ✅ Yes                      | O(1) operations           | Modern            | General-purpose map                        |
| `LinkedHashMap` 🟢🔵          | `Map`                               | extends `HashMap`, `Serializable`               | Insertion               | ❌ No       | ✅ Yes                           | ❌ No           | ✅ Yes                      | O(1) operations           | Modern            | Maintains insertion order                   |
| `TreeMap` 🟣                | `NavigableMap`, `SortedMap`, `Map`  | `Cloneable`, `Serializable`                     | Sorted                   | ❌ No       | ❌ No                            | ❌ No           | ✅ Yes                      | O(log n) operations        | Modern            | Sorted key-value map                        |
| `ConcurrentHashMap` 🔵🔐      | `ConcurrentMap`, `Map`              | `Serializable`, `Cloneable`                     | Unordered               | ❌ No       | ❌ No                            | ✅ Yes          | ❌ (weakly consistent)       | O(1) concurrent access     | Modern (Concurrent) | High-performance concurrent map         |
| `ConcurrentSkipListMap` 🟣🔐  | `ConcurrentNavigableMap`, `Map`     | `Serializable`, `Cloneable`                     | Sorted                   | ❌ No       | ❌ No                            | ✅ Yes          | ❌ (weakly consistent)       | O(log n) concurrent sorted ops | Modern (Concurrent) | Concurrent sorted map               |
| `WeakHashMap` 🔵            | `Map`                               | `Serializable`, `Cloneable`                     | Unordered (GC-based)     | ❌ No       | ✅ Yes                           | ❌ No           | ✅ Yes                      | O(1) (GC-sensitive)        | Modern            | Auto-removable keys on weak reachability  |
| `IdentityHashMap` 🔵        | `Map`                               | `Serializable`, `Cloneable`                     | Unordered               | ❌ No       | ✅ Yes                           | ❌ No           | ✅ Yes                      | O(1) operations           | Modern            | Reference equality-based map               |
| `EnumMap` 🔴                | `Map`                               | `Serializable`, `Cloneable`                     | Enum key order           | ❌ No       | ❌ null keys                     | ❌ No           | ✅ Yes                      | O(1) operations            | Modern            | Efficient enum-key-based map               |
| `Hashtable` 🔵👴🔐              | `Map`                               | `Cloneable`, `Serializable`                     | Unordered               | ❌ No       | ❌ No                            | ✅ Yes          | ✅ Yes                      | O(1) synchronized         | Legacy            | Legacy thread-safe map                      |
| `Dictionary` 👴 (abstract)   | none (abstract legacy)             | —                                               | Unordered               | ❌ No       | ❌ No                            | ❌ No           | —                            | Varies                   | Legacy            | Pre‐`Map` abstract key/value class          |

<div style="text-align: center"> <span style="color:silver; font-style: italic; font-size: 14px;">
🔴Array – 🟢Linked List – 🟣Tree – 🔵Hash Table – 🟡Binary Heap –  
🔐Thread-safe – 👴Legacy
</span></div>

---

## Java Collection Framework — Complete Method Reference

---

### Collection<E> Interface

| Method Name     | Arguments                                                    | Return Type        | Description                                       | Example                                            |
|-----------------|--------------------------------------------------------------|--------------------|-------------------------------------------------|----------------------------------------------------|
| `add`           | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                  | `boolean`          | Adds element to the collection                    | `collection.add("item");`                           |
| `addAll`        | `_Collection<? extends E> c_` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`          | Adds all elements from another collection         | `collection.addAll(otherCollection);`               |
| `clear`         |                                                              | `void`             | Removes all elements                               | `collection.clear();`                               |
| `contains`      | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>              | `boolean`          | Checks if collection contains the element         | `collection.contains("item");`                      |
| `containsAll`   | `_Collection<?> c_` <span style="color:silver; font-style: italic;">(required)</span>       | `boolean`          | Checks if collection contains all elements in c   | `collection.containsAll(otherCollection);`          |
| `equals`        | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>              | `boolean`          | Checks equality with another object                | `collection.equals(anotherCollection);`             |
| `hashCode`      |                                                              | `int`              | Returns hash code                                  | `collection.hashCode();`                            |
| `isEmpty`       |                                                              | `boolean`          | Checks if collection is empty                      | `collection.isEmpty();`                             |
| `iterator`      |                                                              | `Iterator<E>`      | Returns an iterator over elements                   | `Iterator<E> it = collection.iterator();`           |
| `parallelStream`|                                                              | `Stream<E>`        | Returns a parallel Stream of elements               | `collection.parallelStream().forEach(...);`          |
| `remove`        | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>              | `boolean`          | Removes a single instance of specified element     | `collection.remove("item");`                        |
| `removeAll`     | `_Collection<?> c_` <span style="color:silver; font-style: italic;">(required)</span>       | `boolean`          | Removes all elements contained in collection c     | `collection.removeAll(otherCollection);`            |
| `removeIf`      | `_Predicate<? super E> filter_` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`          | Removes all elements matching predicate             | `collection.removeIf(e -> e.isEmpty());`             |
| `retainAll`     | `_Collection<?> c_` <span style="color:silver; font-style: italic;">(required)</span>       | `boolean`          | Retains only elements contained in collection c   | `collection.retainAll(otherCollection);`            |
| `size`          |                                                              | `int`              | Returns number of elements                          | `int size = collection.size();`                     |
| `stream`        |                                                              | `Stream<E>`        | Returns a sequential Stream of elements             | `collection.stream().filter(...);`                   |
| `toArray`       |                                                              | `Object[]`         | Returns an array of all elements                    | `Object[] arr = collection.toArray();`              |
| `toArray`       | `_T[] a_` <span style="color:silver; font-style: italic;">(required)</span>                 | `T[]`              | Returns array containing elements of runtime type | `String[] arr = collection.toArray(new String[0]);`|
| `forEach`       | `_Consumer<? super E> action_` <span style="color:silver; font-style: italic;">(required)</span> | `void`             | Performs given action for each element              | `collection.forEach(System.out::println);`          |
| `spliterator`   |                                                              | `Spliterator<E>`   | Returns a Spliterator over elements                 | `Spliterator<E> spliterator = collection.spliterator();` |

---

### `List<E>` Interface – Full Cheatsheet

| Method Name                                                                 | Arguments                          | Return Type     | Description                                  | Avg. Time ⏱ | Java Version | Example                      |
|-----------------------------------------------------------------------------|------------------------------------|-----------------|----------------------------------------------|-------------|--------------|------------------------------|
| [`add`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#add(int,E))<sup style="color:#d32f2f">★★★</sup> | `int index, E element` (required)  | `void`          | Inserts element at specified position         | O(n)        | 1.2          | `list.add(1, "item");`       |
| [`add`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#add(E))<sup style="color:#d32f2f">★★★</sup> | `E element` (required)             | `boolean`       | Adds element to end of list                   | O(1) amort. | 1.2          | `list.add("item");`          |
| [`addAll`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#addAll(int,java.util.Collection))<sup style="color:#fbc02d">★★</sup> | `int index, Collection<? extends E> c` | `boolean`   | Inserts all elements at specified position    | O(n + m)    | 1.2          | `list.addAll(1, collection);`|
| [`addAll`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#addAll(java.util.Collection))<sup style="color:#d32f2f">★★★</sup> | `Collection<? extends E> c`        | `boolean`       | Adds all elements to end of list              | O(m)        | 1.2          | `list.addAll(collection);`   |
| [`clear`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#clear())<sup style="color:#d32f2f">★★★</sup> |                                    | `void`          | Removes all elements                          | O(n)        | 1.2          | `list.clear();`              |
| [`contains`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#contains(java.lang.Object))<sup style="color:#d32f2f">★★★</sup> | `Object o` (required)              | `boolean`       | Checks if element is present                  | O(n)        | 1.2          | `list.contains("item");`     |
| [`containsAll`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#containsAll(java.util.Collection))<sup style="color:#fbc02d">★★</sup> | `Collection<?> c` (required)       | `boolean`       | Checks if all elements are present            | O(n×m)      | 1.2          | `list.containsAll(collection);`|
| [`equals`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#equals(java.lang.Object))<sup style="color:#fbc02d">★★</sup> | `Object o` (required)              | `boolean`       | Compares equality                             | O(n)        | 1.2          | `list.equals(otherList);`    |
| [`get`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#get(int))<sup style="color:#d32f2f">★★★</sup> | `int index` (required)             | `E`             | Returns element at position                   | O(1)        | 1.2          | `E element = list.get(1);`   |
| [`indexOf`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#indexOf(java.lang.Object))<sup style="color:#d32f2f">★★★</sup> | `Object o` (required)              | `int`           | Returns index of first occurrence             | O(n)        | 1.2          | `int i = list.indexOf("item");`|
| [`isEmpty`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#isEmpty())<sup style="color:#d32f2f">★★★</sup> |                                    | `boolean`       | Checks if list is empty                       | O(1)        | 1.2          | `list.isEmpty();`            |
| [`iterator`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#iterator())<sup style="color:#fbc02d">★★</sup> |                                    | `Iterator<E>`   | Returns iterator                              | O(1)        | 1.2          | `Iterator<E> it = list.iterator();`|
| [`lastIndexOf`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#lastIndexOf(java.lang.Object))<sup style="color:#fbc02d">★★</sup> | `Object o` (required)              | `int`           | Returns index of last occurrence              | O(n)        | 1.2          | `int i = list.lastIndexOf("item");`|
| [`listIterator`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#listIterator())<sup style="color:#fbc02d">★★</sup> |                                    | `ListIterator<E>`| Returns list iterator                         | O(1)        | 1.2          | `ListIterator<E> it = list.listIterator();`|
| [`listIterator`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#listIterator(int))<sup style="color:#fbc02d">★★</sup> | `int index` (required)             | `ListIterator<E>`| Returns list iterator starting at index       | O(1)        | 1.2          | `ListIterator<E> it = list.listIterator(1);`|
| [`remove`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#remove(int))<sup style="color:#d32f2f">★★★</sup> | `int index` (required)             | `E`             | Removes element at index                      | O(n)        | 1.2          | `E removed = list.remove(1);`|
| [`remove`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#remove(java.lang.Object))<sup style="color:#d32f2f">★★★</sup> | `Object o` (required)              | `boolean`       | Removes first occurrence of element           | O(n)        | 1.2          | `list.remove("item");`       |
| [`removeAll`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#removeAll(java.util.Collection))<sup style="color:#fbc02d">★★</sup> | `Collection<?> c` (required)       | `boolean`       | Removes all matching elements                 | O(n×m)      | 1.2          | `list.removeAll(collection);`|
| [`retainAll`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#retainAll(java.util.Collection))<sup style="color:#fbc02d">★★</sup> | `Collection<?> c` (required)       | `boolean`       | Retains only elements present in collection   | O(n×m)      | 1.2          | `list.retainAll(collection);`|
| [`set`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#set(int,E))<sup style="color:#d32f2f">★★★</sup> | `int index, E element` (required)  | `E`             | Replaces element at index                     | O(1)        | 1.2          | `list.set(1, "newItem");`    |
| [`size`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#size())<sup style="color:#d32f2f">★★★</sup> |                                    | `int`           | Returns size of list                          | O(1)        | 1.2          | `int size = list.size();`    |
| [`subList`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#subList(int,int))<sup style="color:#fbc02d">★★</sup> | `int fromIndex, int toIndex` (required)| `List<E>`   | Returns sublist view                          | O(1)¹       | 1.2          | `List<E> sub = list.subList(1, 3);`|
| [`toArray`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#toArray())<sup style="color:#d32f2f">★★★</sup> |                                    | `Object[]`      | Returns array of elements                     | O(n)        | 1.2          | `Object[] arr = list.toArray();`|
| [`toArray`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#toArray(T[]))<sup style="color:#d32f2f">★★★</sup> | `T[] a` (required)                 | `<T[]>`         | Returns array in provided array type          | O(n)        | 1.2          | `String[] arr = list.toArray(new String[0]);`|


---

### 🏗️ Static Methods in `List` Interface

| Method Name                                                                 | Arguments                          | Return Type | Description                         | Avg. Time ⏱ | Java Version | Example                |
|-----------------------------------------------------------------------------|------------------------------------|-------------|-------------------------------------|-------------|--------------|------------------------|
| [`of`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#of(E...))<sup style="color:#d32f2f">★★★</sup> | `E... elements` (required)         | `List<E>`   | Immutable list of elements          | O(n)        | 9+           | `List.of("a", "b")`    |
| [`copyOf`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/List.html#copyOf(java.util.Collection))<sup style="color:#fbc02d">★★</sup> | `Collection<? extends E> c` (required)| `List<E>` | Immutable copy of collection        | O(n)        | 9+           | `List.copyOf(myList)`  |


---

### 🛠️ Utility Methods from `Collections` and `Arrays`

| Method Name                                                                 | Arguments                          | Return Type | Description                            | Avg. Time ⏱ | Java Version | Example                                    |
|-----------------------------------------------------------------------------|------------------------------------|-------------|----------------------------------------|-------------|--------------|--------------------------------------------|
| [`Collections.unmodifiableList`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collections.html#unmodifiableList(java.util.List))<sup style="color:#fbc02d">★★</sup> | `List<? extends T> list` (required) | `List<T>`   | Read-only wrapper over original list   | O(1)        | 1.2          | `Collections.unmodifiableList(myList)`    |
| [`Collections.singletonList`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collections.html#singletonList(T))<sup style="color:#fbc02d">★★</sup> | `T item` (required)                | `List<T>`   | Immutable list with a single element   | O(1)        | 1.2          | `Collections.singletonList("a")`          |
| [`Arrays.asList`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Arrays.html#asList(T...))<sup style="color:#d32f2f">★★★</sup> | `T... a` (required)                | `List<T>`   | Fixed-size list backed by an array     | O(1)        | 1.2          | `Arrays.asList("x", "y")`                  |


---

<!-- ### Legend:
#### Priority Markers (Usage Frequency):
<sup style="color:#d32f2f">★★★</sup> Very Important (Used daily)  
<sup style="color:#fbc02d">★★</sup> Important (Used weekly)  
<sup style="color:#388e3c">★</sup> Less Important (Used monthly)   -->

<!-- #### Time Complexity:
- **O(1)** - Constant time (fastest)
- **O(1) amort.** - Amortized constant time
- **O(n)** - Linear time
- **O(n×m)** - Quadratic time (slowest) -->


### `Queue<E>` Interface – Full Cheatsheet

| Method Name                                                                 | Arguments                          | Return Type     | Description                                  | Avg. Time ⏱ | Java Version | Example                      |
|-----------------------------------------------------------------------------|------------------------------------|-----------------|----------------------------------------------|-------------|--------------|------------------------------|
| [`add`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#add(E))<sup style="color:#d32f2f">★★★</sup> | `E e` (required)                   | `boolean`       | Inserts element or throws exception          | O(1)        | 1.5          | `queue.add("item");`         |
| [`offer`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#offer(E))<sup style="color:#d32f2f">★★★</sup> | `E e` (required)                   | `boolean`       | Inserts element or returns false if full     | O(1)        | 1.5          | `queue.offer("item");`       |
| [`poll`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#poll())<sup style="color:#d32f2f">★★★</sup> |                                    | `E`             | Retrieves and removes head, or null if empty | O(1)        | 1.5          | `E e = queue.poll();`        |
| [`remove`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#remove())<sup style="color:#fbc02d">★★</sup> |                                    | `E`             | Retrieves and removes head, throws if empty | O(1)        | 1.5          | `E e = queue.remove();`      |
| [`peek`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#peek())<sup style="color:#d32f2f">★★★</sup> |                                    | `E`             | Retrieves head or null if empty               | O(1)        | 1.5          | `E e = queue.peek();`        |
| [`element`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#element())<sup style="color:#fbc02d">★★</sup> |                                    | `E`             | Retrieves head or throws if empty             | O(1)        | 1.5          | `E e = queue.element();`     |

---

### 🏗️ Static Methods in `Collections` (Queue Utilities)

| Method Name                                                                 | Arguments                          | Return Type     | Description                                  | Avg. Time ⏱ | Java Version | Example                      |
|-----------------------------------------------------------------------------|------------------------------------|-----------------|----------------------------------------------|-------------|--------------|------------------------------|
| [`Collections.asLifoQueue`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collections.html#asLifoQueue(java.util.Deque))<sup style="color:#388e3c">★</sup> | `Deque<T> deque` (required)         | `Queue<T>`      | Returns a LIFO view of a deque               | O(1)        | 1.6          | `Queue<T> lifo = Collections.asLifoQueue(deque);` |
| [`Collections.unmodifiableQueue`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Collections.html#unmodifiableQueue(java.util.Queue))<sup style="color:#388e3c">★</sup> | `Queue<? extends T> queue` (required) | `Queue<T>`   | Returns an unmodifiable view of a queue      | O(1)        | 1.5          | `Queue<T> unmod = Collections.unmodifiableQueue(queue);` |

---

### 🛠️ Static Factory Methods (Java 9+)

| Method Name                                                                 | Arguments                          | Return Type     | Description                                  | Avg. Time ⏱ | Java Version | Example                      |
|-----------------------------------------------------------------------------|------------------------------------|-----------------|----------------------------------------------|-------------|--------------|------------------------------|
| [`Queue.of`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#of(E...))<sup style="color:#d32f2f">★★★</sup> | `E... elements` (required)         | `Queue<E>`      | Creates an unmodifiable queue with elements   | O(n)        | 9+           | `Queue<String> q = Queue.of("A", "B");` |
| [`Queue.copyOf`](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Queue.html#copyOf(java.util.Collection))<sup style="color:#fbc02d">★★</sup> | `Collection<? extends E> coll` (required) | `Queue<E>` | Creates an unmodifiable queue from collection | O(n)        | 9+           | `Queue<String> q = Queue.copyOf(list);` |

---

### Deque<E> Interface (extends Queue<E>)

| Method Name           | Arguments                                                  | Return Type       | Description                                  | Example                        |
|-----------------------|------------------------------------------------------------|-------------------|----------------------------------------------|--------------------------------|
| `addFirst`            | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                 | `void`            | Inserts at front                              | `deque.addFirst("item");`       |
| `addLast`             | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                 | `void`            | Inserts at end                                | `deque.addLast("item");`        |
| `offerFirst`          | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                 | `boolean`         | Inserts at front or false if full             | `deque.offerFirst("item");`     |
| `offerLast`           | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                 | `boolean`         | Inserts at end or false if full               | `deque.offerLast("item");`      |
| `pollFirst`           |                                                            | `E`               | Retrieves and removes first or null if empty | `E e = deque.pollFirst();`      |
| `pollLast`            |                                                            | `E`               | Retrieves and removes last or null if empty  | `E e = deque.pollLast();`       |
| `peekFirst`           |                                                            | `E`               | Retrieves first or null if empty               | `E e = deque.peekFirst();`      |
| `peekLast`            |                                                            | `E`               | Retrieves last or null if empty                | `E e = deque.peekLast();`       |
| `removeFirst`         |                                                            | `E`               | Retrieves and removes first, throws if empty | `E e = deque.removeFirst();`    |
| `removeLast`          |                                                            | `E`               | Retrieves and removes last, throws if empty  | `E e = deque.removeLast();`     |
| `getFirst`            |                                                            | `E`               | Retrieves first, throws if empty               | `E e = deque.getFirst();`       |
| `getLast`             |                                                            | `E`               | Retrieves last, throws if empty                | `E e = deque.getLast();`        |
| `removeFirstOccurrence`| `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>           | `boolean`         | Removes first occurrence of object            | `deque.removeFirstOccurrence(obj);` |
| `removeLastOccurrence` | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>           | `boolean`         | Removes last occurrence of object             | `deque.removeLastOccurrence(obj);` |

---

### Map<K,V> Interface

| Method Name         | Arguments                                                    | Return Type            | Description                                  | Example                                        |
|---------------------|--------------------------------------------------------------|------------------------|----------------------------------------------|------------------------------------------------|
| `clear`             |                                                              | `void`                 | Removes all mappings                          | `map.clear();`                                 |
| `compute`           | `_K key_`, `_BiFunction<? super K, ? super V, ? extends V> remappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | Computes new value                            | `map.compute("key", (k,v) -> v == null ? 1 : v + 1);` |
| `computeIfAbsent`   | `_K key_`, `_Function<? super K, ? extends V> mappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | Computes value if absent                      | `map.computeIfAbsent("key", k -> 1);`          |
| `computeIfPresent`  | `_K key_`, `_BiFunction<? super K, ? super V, ? extends V> remappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | Computes new value if present                 | `map.computeIfPresent("key", (k,v) -> v + 1);` |
| `containsKey`       | `_Object key_` <span style="color:silver; font-style: italic;">(required)</span>         | `boolean`              | Checks if map contains key                    | `map.containsKey("key");`                      |
| `containsValue`     | `_Object value_` <span style="color:silver; font-style: italic;">(required)</span>       | `boolean`              | Checks if map contains value                  | `map.containsValue("value");`                  |
| `entrySet`          |                                                              | `Set<Map.Entry<K,V>>`  | Returns a set view of mappings                | `Set<Map.Entry<K,V>> entries = map.entrySet();`|
| `equals`            | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>          | `boolean`              | Checks equality                               | `map.equals(otherMap);`                        |
| `forEach`           | `_BiConsumer<? super K, ? super V> action_` <span style="color:silver; font-style: italic;">(required)</span> | `void`           | Performs action for each mapping              | `map.forEach((k,v) -> System.out.println(k + v));` |
| `get`               | `_Object key_` <span style="color:silver; font-style: italic;">(required)</span>         | `V`                    | Returns value for key                          | `V val = map.get("key");`                       |
| `getOrDefault`      | `_Object key_`, `_V defaultValue_` <span style="color:silver; font-style: italic;">(required)</span> | `V`           | Returns value or default if absent            | `V val = map.getOrDefault("key", defaultVal);`|
| `isEmpty`           |                                                              | `boolean`              | Checks if map is empty                         | `map.isEmpty();`                               |
| `keySet`            |                                                              | `Set<K>`               | Returns set of keys                            | `Set<K> keys = map.keySet();`                   |
| `merge`             | `_K key_`, `_V value_`, `_BiFunction<? super V, ? super V, ? extends V> remappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V` | Merges value                                | `map.merge("key", "value", (v1, v2) -> v1 + v2);` |
| `put`               | `_K key_`, `_V value_` <span style="color:silver; font-style: italic;">(required)</span>   | `V`                    | Adds or replaces mapping                       | `map.put("key", "value");`                      |
| `putAll`            | `_Map<? extends K, ? extends V> m_` <span style="color:silver; font-style: italic;">(required)</span> | `void`        | Copies all mappings                           | `map.putAll(otherMap);`                         |
| `remove`            | `_Object key_` <span style="color:silver; font-style: italic;">(required)</span>         | `V`                    | Removes mapping                               | `map.remove("key");`                            |
| `replace`           | `_K key_`, `_V value_` <span style="color:silver; font-style: italic;">(required)</span>  | `V`                    | Replaces value for key                        | `map.replace("key", "newValue");`               |
| `replaceAll`        | `_BiFunction<? super K, ? super V, ? extends V> function_` <span style="color:silver; font-style: italic;">(required)</span> | `void` | Replaces all values using function            | `map.replaceAll((k, v) -> v.toUpperCase());`    |
| `size`              |                                                              | `int`                  | Returns number of mappings                     | `int size = map.size();`                         |
| `values`            |                                                              | `Collection<V>`        | Returns collection of values                   | `Collection<V> values = map.values();`           |

---

### SortedMap<K,V> Interface (extends Map<K,V>)

| Method Name   | Arguments                                                      | Return Type          | Description                            | Example                                      |
|---------------|----------------------------------------------------------------|----------------------|----------------------------------------|----------------------------------------------|
| `comparator`  |                                                                | `Comparator<? super K>`| Returns comparator or null if natural | `Comparator<K> c = sortedMap.comparator();`  |
| `subMap`      | `_K fromKey_`, `_K toKey_` <span style="color:silver; font-style: italic;">(required)</span>       | `SortedMap<K,V>`      | Returns view between keys               | `SortedMap<K,V> sm = sortedMap.subMap(fromKey, toKey);` |
| `headMap`     | `_K toKey_` <span style="color:silver; font-style: italic;">(required)</span>                      | `SortedMap<K,V>`      | Returns view of keys less than toKey   | `SortedMap<K,V> hm = sortedMap.headMap(toKey);`         |
| `tailMap`     | `_K fromKey_` <span style="color:silver; font-style: italic;">(required)</span>                    | `SortedMap<K,V>`      | Returns view of keys greater or equal  | `SortedMap<K,V> tm = sortedMap.tailMap(fromKey);`       |
| `firstKey`    |                                                                | `K`                  | Returns first (lowest) key              | `K first = sortedMap.firstKey();`               |
| `lastKey`     |                                                                | `K`                  | Returns last (highest) key              | `K last = sortedMap.lastKey();`                 |

---

### NavigableMap<K,V> Interface (extends SortedMap<K,V>)

| Method Name       | Arguments                                                    | Return Type          | Description                                | Example                                       |
|-------------------|--------------------------------------------------------------|----------------------|--------------------------------------------|-----------------------------------------------|
| `ceilingEntry`    | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `Map.Entry<K,V>`      | Least entry with key ≥ given key           | `Map.Entry<K,V> e = navMap.ceilingEntry(key);` |
| `ceilingKey`      | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `K`                  | Least key ≥ given key                       | `K k = navMap.ceilingKey(key);`                 |
| `descendingKeySet`|                                                              | `NavigableSet<K>`    | Returns reverse order key set               | `NavigableSet<K> ks = navMap.descendingKeySet();` |
| `descendingMap`   |                                                              | `NavigableMap<K,V>`  | Returns reverse order map                   | `NavigableMap<K,V> dm = navMap.descendingMap();` |
| `floorEntry`      | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `Map.Entry<K,V>`      | Greatest entry with key ≤ given key         | `Map.Entry<K,V> e = navMap.floorEntry(key);`    |
| `floorKey`        | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `K`                  | Greatest key ≤ given key                     | `K k = navMap.floorKey(key);`                    |
| `higherEntry`     | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `Map.Entry<K,V>`      | Least entry with key > given key             | `Map.Entry<K,V> e = navMap.higherEntry(key);`   |
| `higherKey`       | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `K`                  | Least key > given key                         | `K k = navMap.higherKey(key);`                   |
| `headMap`         | `_K toKey_`, `_boolean inclusive_` <span style="color:silver; font-style: italic;">(required)</span> | `NavigableMap<K,V>`| Returns view of keys less than (inclusive) | `NavigableMap<K,V> hm = navMap.headMap(toKey, true);` |
| `lastEntry`       |                                                              | `Map.Entry<K,V>`      | Returns last entry                           | `Map.Entry<K,V> e = navMap.lastEntry();`         |
| `lowerEntry`      | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `Map.Entry<K,V>`      | Greatest entry with key < given key          | `Map.Entry<K,V> e = navMap.lowerEntry(key);`    |
| `lowerKey`        | `_K key_` <span style="color:silver; font-style: italic;">(required)</span>                | `K`                  | Greatest key < given key                      | `K k = navMap.lowerKey(key);`                    |
| `pollFirstEntry`  |                                                              | `Map.Entry<K,V>`      | Removes and returns first entry              | `Map.Entry<K,V> e = navMap.pollFirstEntry();`   |
| `pollLastEntry`   |                                                              | `Map.Entry<K,V>`      | Removes and returns last entry               | `Map.Entry<K,V> e = navMap.pollLastEntry();`    |
| `subMap`          | `_K fromKey_`, `_boolean fromInclusive_`, `_K toKey_`, `_boolean toInclusive_` <span style="color:silver; font-style: italic;">(required)</span> | `NavigableMap<K,V>` | Returns view between keys                     | `NavigableMap<K,V> sm = navMap.subMap(fromKey, true, toKey, false);` |
| `tailMap`         | `_K fromKey_`, `_boolean inclusive_` <span style="color:silver; font-style: italic;">(required)</span> | `NavigableMap<K,V>` | Returns view of keys ≥ given key             | `NavigableMap<K,V> tm = navMap.tailMap(fromKey, true);` |

---

### SortedSet<E> Interface

| Method Name       | Arguments                                                   | Return Type      | Description                                               | Example                                               |
|-------------------|-------------------------------------------------------------|------------------|-----------------------------------------------------------|-------------------------------------------------------|
| `comparator`      |                                                             | `Comparator<? super E>` | Returns the comparator used for sorting, or `null` if natural order | `Comparator c = sortedSet.comparator();`              |
| `first`           |                                                             | `E`              | Returns the **first (lowest)** element                    | `E first = sortedSet.first();`                        |
| `last`            |                                                             | `E`              | Returns the **last (highest)** element                    | `E last = sortedSet.last();`                          |
| `headSet`         | `_E toElement_` <span style="color:silver; font-style: italic;">(required)</span> | `SortedSet<E>`   | Elements **strictly less than** `toElement`              | `SortedSet<E> head = sortedSet.headSet(e);`           |
| `tailSet`         | `_E fromElement_` <span style="color:silver; font-style: italic;">(required)</span> | `SortedSet<E>`   | Elements **greater than or equal to** `fromElement`      | `SortedSet<E> tail = sortedSet.tailSet(e);`           |
| `subSet`          | `_E fromElement_`, `_E toElement_` <span style="color:silver; font-style: italic;">(required)</span> | `SortedSet<E>`   | Elements in range **from (inclusive)** to **to (exclusive)** | `SortedSet<E> sub = sortedSet.subSet(from, to);`      |

---

### NavigableSet<E> Interface

| Method Name         | Arguments                                                                 | Return Type        | Description                                                   | Example                                               |
|---------------------|---------------------------------------------------------------------------|--------------------|---------------------------------------------------------------|-------------------------------------------------------|
| `ceiling`           | `_E e_` <span style="color:silver; font-style: italic;">(required)</span> | `E`                | Returns the **least element ≥ e**, or `null` if none          | `E c = navSet.ceiling(e);`                           |
| `floor`             | `_E e_` <span style="color:silver; font-style: italic;">(required)</span> | `E`                | Returns the **greatest element ≤ e**, or `null` if none       | `E f = navSet.floor(e);`                             |
| `higher`            | `_E e_` <span style="color:silver; font-style: italic;">(required)</span> | `E`                | Returns the **least element > e**, or `null` if none          | `E h = navSet.higher(e);`                            |
| `lower`             | `_E e_` <span style="color:silver; font-style: italic;">(required)</span> | `E`                | Returns the **greatest element < e**, or `null` if none       | `E l = navSet.lower(e);`                             |
| `pollFirst`         |                                                                           | `E`                | Retrieves and removes the **first (lowest)** element, or `null` | `E first = navSet.pollFirst();`                      |
| `pollLast`          |                                                                           | `E`                | Retrieves and removes the **last (highest)** element, or `null` | `E last = navSet.pollLast();`                        |
| `descendingSet`     |                                                                           | `NavigableSet<E>`  | Returns a **reverse-order view** of the set                  | `NavigableSet<E> rev = navSet.descendingSet();`       |
| `descendingIterator`|                                                                           | `Iterator<E>`      | Returns an **iterator over elements in reverse order**        | `Iterator<E> it = navSet.descendingIterator();`       |
| `headSet`           | `_E toElement_`, `_boolean inclusive_` <span style="color:silver; font-style: italic;">(required)</span> | `NavigableSet<E>` | View of elements **less than (or equal)** to `toElement`     | `NavigableSet<E> hs = navSet.headSet(e, true);`       |
| `tailSet`           | `_E fromElement_`, `_boolean inclusive_` <span style="color:silver; font-style: italic;">(required)</span> | `NavigableSet<E>` | View of elements **greater than (or equal)** to `fromElement` | `NavigableSet<E> ts = navSet.tailSet(e, true);`       |
| `subSet`            | `_E fromElement_`, `_boolean fromInclusive_`, `_E toElement_`, `_boolean toInclusive_` <span style="color:silver; font-style: italic;">(required)</span> | `NavigableSet<E>` | View of elements **between** `fromElement` and `toElement`    | `NavigableSet<E> ss = navSet.subSet(f, true, t, false);` |

---

### ConcurrentMap<K,V> Interface

| Method Name            | Arguments                                                                                         | Return Type          | Description                                                                                             | Example                                                     |
|------------------------|-------------------------------------------------------------------------------------------------|----------------------|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|
| `putIfAbsent`          | `_K key_`, `_V value_` <span style="color:silver; font-style: italic;">(required)</span>         | `V`                  | If key not present, associates value with key atomically; returns previous value or `null` if none     | `V oldVal = cmap.putIfAbsent(key, value);`                  |
| `remove`               | `_Object key_`, `_Object value_` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`            | Removes entry only if key is mapped to given value                                                     | `boolean removed = cmap.remove(key, value);`                |
| `replace`              | `_K key_`, `_V oldValue_`, `_V newValue_` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`            | Replaces entry for key only if currently mapped to oldValue                                            | `boolean replaced = cmap.replace(key, oldVal, newVal);`     |
| `replace`              | `_K key_`, `_V value_` <span style="color:silver; font-style: italic;">(required)</span>          | `V`                  | Replaces entry for key only if present; returns previous value or `null` if none                        | `V oldVal = cmap.replace(key, value);`                      |
| `computeIfAbsent`      | `_K key_`, `_Function<? super K,? extends V> mappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | If key absent, computes value using mappingFunction and inserts it atomically                          | `V val = cmap.computeIfAbsent(key, k -> newVal);`            |
| `computeIfPresent`     | `_K key_`, `_BiFunction<? super K,? super V,? extends V> remappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | If key present, computes new value using remappingFunction; replaces entry atomically                  | `V val = cmap.computeIfPresent(key, (k,v) -> newVal);`       |
| `compute`              | `_K key_`, `_BiFunction<? super K,? super V,? extends V> remappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | Computes new mapping for key atomically                                                                | `V val = cmap.compute(key, (k,v) -> newVal);`                |
| `merge`                | `_K key_`, `_V value_`, `_BiFunction<? super V,? super V,? extends V> remappingFunction_` <span style="color:silver; font-style: italic;">(required)</span> | `V`                  | Merges existing value with given value using remappingFunction atomically                              | `V val = cmap.merge(key, value, (v1,v2) -> mergedVal);`      |

---

### BlockingQueue<E> Interface

| Method Name         | Arguments                                                                                           | Return Type | Description                                                                                          | Example                                                         |
|---------------------|-----------------------------------------------------------------------------------------------------|-------------|------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| `put`               | `E e` <span style="color:silver; font-style: italic;">(required)</span>                             | `void`      | Inserts the element, waiting if necessary for space to become available                             | `queue.put(e);`                                                |
| `take`              | _none_                                                                                              | `E`         | Retrieves and removes the head, waiting if necessary until an element becomes available             | `E e = queue.take();`                                          |
| `offer`             | `E e`, `long timeout`, `TimeUnit unit` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`   | Inserts the element, waiting up to the timeout if necessary for space                               | `boolean success = queue.offer(e, 1, TimeUnit.SECONDS);`       |
| `poll`              | `long timeout`, `TimeUnit unit` <span style="color:silver; font-style: italic;">(required)</span>   | `E`         | Retrieves and removes the head, waiting up to the timeout if necessary                              | `E e = queue.poll(1, TimeUnit.SECONDS);`                       |
| `remainingCapacity` | _none_                                                                                              | `int`       | Returns the number of additional elements the queue can ideally accept                              | `int cap = queue.remainingCapacity();`                         |
| `drainTo`           | `Collection<? super E> c` <span style="color:silver; font-style: italic;">(required)</span>         | `int`       | Removes all available elements and adds them to the given collection                                | `int drained = queue.drainTo(list);`                           |
| `drainTo`           | `Collection<? super E> c`, `int maxElements` <span style="color:silver; font-style: italic;">(required)</span> | `int`       | Removes up to maxElements and adds them to the given collection                                     | `int drained = queue.drainTo(list, 10);`                       |

---

### TransferQueue<E> Interface

| Method Name       | Arguments                                                                                         | Return Type | Description                                                                                      | Example                                                              |
|-------------------|---------------------------------------------------------------------------------------------------|-------------|--------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| `transfer`        | `E e` <span style="color:silver; font-style: italic;">(required)</span>                           | `void`      | Inserts the element and waits until it is received by a consumer                                | `queue.transfer(e);`                                                |
| `tryTransfer`     | `E e` <span style="color:silver; font-style: italic;">(required)</span>                           | `boolean`   | Attempts to transfer the element immediately, returns `false` if no consumer is waiting         | `boolean success = queue.tryTransfer(e);`                          |
| `tryTransfer`     | `E e`, `long timeout`, `TimeUnit unit` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`   | Waits up to timeout for a consumer to receive the element; returns `false` if timed out         | `boolean success = queue.tryTransfer(e, 1, TimeUnit.SECONDS);`     |
| `hasWaitingConsumer` | _none_                                                                                        | `boolean`   | Returns `true` if any consumers are waiting to receive elements                                 | `boolean waiting = queue.hasWaitingConsumer();`                    |
| `getWaitingConsumerCount` | _none_                                                                                   | `int`       | Returns an estimate of the number of consumers waiting to receive elements                      | `int count = queue.getWaitingConsumerCount();`                     |

---

### ConcurrentNavigableMap<K,V> Interface

| Method Name         | Arguments                                                                 | Return Type                        | Description                                                                                      | Example                                                                |
|---------------------|---------------------------------------------------------------------------|------------------------------------|--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| `subMap`            | `K fromKey`, `boolean fromInclusive`, `K toKey`, `boolean toInclusive`    | `ConcurrentNavigableMap<K,V>`      | Returns a view of the portion of this map whose keys range from `fromKey` to `toKey`            | `ConcurrentNavigableMap<K,V> view = map.subMap(k1, true, k2, false);` |
| `headMap`           | `K toKey`, `boolean inclusive`                                            | `ConcurrentNavigableMap<K,V>`      | Returns a view of the portion of this map whose keys are less than (or equal if inclusive)      | `ConcurrentNavigableMap<K,V> head = map.headMap(k, true);`            |
| `tailMap`           | `K fromKey`, `boolean inclusive`                                          | `ConcurrentNavigableMap<K,V>`      | Returns a view of the portion of this map whose keys are greater than (or equal if inclusive)   | `ConcurrentNavigableMap<K,V> tail = map.tailMap(k, false);`           |
| `descendingMap`     | _none_                                                                    | `ConcurrentNavigableMap<K,V>`      | Returns a reverse-order view of the map                                                         | `ConcurrentNavigableMap<K,V> rev = map.descendingMap();`              |

---

### Argument Types Description

➡️ `_E e_`:  
  <i>Represents a single element of generic type `E`. Used in methods that add, remove, or process one element.</i>

➡️ `_Collection<? extends E> c_`:  
  <i>A collection containing elements of type `E` or its subtypes. Used when adding or manipulating multiple elements at once.</i>

➡️ `_Collection<?> c_`:  
  <i>A collection with unknown element type, commonly used for removal or retention operations.</i>

➡️ `_Object o_`:  
  <i>A general object parameter, used in equality checks or removal of a specific element.</i>

➡️ `_Predicate<? super E> filter_`:  
  <i>A functional interface that tests elements for a condition, used to filter or remove elements matching the predicate.</i>

➡️ `_Consumer<? super E> action_`:  
  <i>A functional interface representing an action to perform on each element (e.g., printing, modifying).</i>

➡️ `_T[] a_`:  
  <i>A generic array provided to `toArray` to specify the output array's runtime type.</i>

➡️ `_int index_`:  
  <i>A zero-based integer index specifying position in the list for insertion, retrieval, or removal.</i>

➡️ `_int fromIndex_`:  
  <i>A starting index, inclusive, for sublist or subrange operations.</i>

➡️ `_int toIndex_`:  
  <i>An ending index, exclusive, for sublist or subrange operations.</i>

➡️ `_K key_`:  
  <i>The key object used in map operations such as lookup, insertion, or deletion.</i>

➡️ `_V value_`:  
  <i>The value associated with a key in map operations, used for insertion or replacement.</i>

➡️ `_Map<? extends K, ? extends V> m_`:  
  <i>A map of key-value pairs, used to bulk insert into another map.</i>

➡️ `_boolean inclusive_`:  
  <i>A boolean flag indicating whether boundary keys should be included (true) or excluded (false) in range operations.</i>

➡️ `_boolean fromInclusive_`, `_boolean toInclusive_`:  
  <i>Boolean flags specifying inclusiveness of the start and end keys in subrange views or operations.</i>

➡️ `_Comparator<? super E> comparator_`:  
  <i>A comparator defining the order of elements in sorted collections or maps.</i>

➡️ `_Iterable<? extends E> iterable_`:  
  <i>An iterable collection of elements used as input for bulk operations.</i>

➡️ `_Spliterator<E> spliterator_`:  
  <i>An object supporting parallel traversal over elements.</i>

➡️ No arguments:  
  <i>Methods with no parameters typically perform queries, clear, or return iterators over the whole collection.</i>

---

## Marker & Utility Interfaces

### Marker & Utility Interfaces in Java – In-Depth Comparison

| Interface        | Package         | Type               | Purpose                                                                                   | Declared Methods     | Common Implementations           | Key Notes                                                                                                 |
|------------------|------------------|--------------------|-------------------------------------------------------------------------------------------|-----------------------|----------------------------------|-----------------------------------------------------------------------------------------------------------|
| `RandomAccess`   | `java.util`       | Marker Interface   | Indicates that a `List` implementation supports fast random access (e.g., O(1) get/index) | ❌ None               | `ArrayList`, `Vector`            | Used by algorithms to decide if index-based traversal is efficient; not used by `LinkedList`             |
| `Cloneable`      | `java.lang`       | Marker Interface   | Signals that `.clone()` method can be called safely; enables field-by-field memory copy   | ❌ None               | `ArrayList`, `HashMap`, `Date`   | Must override `clone()` manually from `Object`; deep vs shallow copy must be handled explicitly           |
| `Serializable`   | `java.io`         | Marker Interface   | Marks a class as eligible for Java Serialization – converting object state to a byte stream | ❌ None               | `ArrayList`, `HashMap`, `String` | Used in I/O, RMI, caching; fields not marked `transient` will be persisted                               |
| `Externalizable` | `java.io`         | Functional Interface | Like `Serializable`, but gives full control over what/how to serialize/deserialize        | ✅ `writeExternal`, `readExternal` | Rarely used directly             | Must define a public no-arg constructor; improves performance & control                                   |
| `Comparable<T>`  | `java.lang`       | Generic Interface  | Enables natural ordering of objects (e.g., alphabetic or numeric sorting) via `compareTo()` | ✅ `compareTo(T o)`   | `String`, `Integer`, `Date`      | Needed for `TreeSet`, `TreeMap`; should be consistent with `equals()`                                     |
| `Comparator<T>`  | `java.util`       | Generic Interface  | Enables external/custom ordering logic without modifying the class                         | ✅ `compare(T o1, T o2)` | Used with `Collections.sort()`   | Can create multiple sort orders; supports chaining with `thenComparing()` in Java 8+                      |

---

### Summary by Behavior

| Interface        | Is Marker? | Serialization | Cloning | Sorting | Access Optimization | Control Level | Usage Context                     |
|------------------|------------|---------------|---------|---------|----------------------|----------------|----------------------------------|
| `RandomAccess`   | ✅         | ❌            | ❌      | ❌      | ✅ (O(1) access hint) | 🚫 No control   | Algorithm optimization hints     |
| `Cloneable`      | ✅         | ❌            | ✅      | ❌      | ❌                   | ⚠️ Partial control | Manual clone implementation needed |
| `Serializable`   | ✅         | ✅            | ❌      | ❌      | ❌                   | 🚫 No control   | Auto save/load over stream       |
| `Externalizable` | ❌         | ✅ (manual)   | ❌      | ❌      | ❌                   | ✅ Full control | Advanced I/O customization        |
| `Comparable`     | ❌         | ❌            | ❌      | ✅      | ❌                   | ✅ Full control | Natural sorting within class     |
| `Comparator`     | ❌         | ❌            | ❌      | ✅      | ❌                   | ✅ Full control | External or lambda-based sorting |

---
