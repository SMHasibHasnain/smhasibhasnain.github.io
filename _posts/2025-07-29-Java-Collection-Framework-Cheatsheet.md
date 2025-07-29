---
title: "🍵 Java Collection Framework"
date: 2025-07-29
categories: [Java, Cheat Sheet]
tags: [JavaScript, Collection Framework, Reference]
pin: true
toc: true
comments: false
---

## Java Collection Framework – Overview Table

![Alt Text](/assets/img/collection.png)


| <abbr title="The main Collection interface category such as List, Set, Queue, or Map">Interface</abbr> | <abbr title="The concrete Java class implementing the interface">Implementation</abbr> | <abbr title="Other Java interfaces this class also implements, showing class hierarchy and additional capabilities">Also Implements</abbr> | <abbr title="Order in which elements are stored or retrieved, e.g., insertion order, sorted order, or none">Ordering</abbr> | <abbr title="Indicates if duplicate elements (or keys for Map) are allowed">Duplicates</abbr> | <abbr title="Specifies if null elements or null keys/values are permitted">Null Allowed</abbr> | <abbr title="Whether this implementation is safe for use by multiple threads concurrently">Thread Safe</abbr> | <abbr title="If true, iterators throw ConcurrentModificationException if collection is structurally modified during iteration">Fail-Fast Iterator</abbr> | <abbr title="Average time complexity of common operations like add, get, and remove (Big-O notation)">Performance (avg)</abbr> | <abbr title="Indicates whether the implementation is considered legacy (older) or modern (recommended)">Legacy / Modern</abbr> | <abbr title="Typical use cases or scenarios where this implementation is best suited">Typical Use Case</abbr> |
|---------------|--------------------|----------------------|--------------|----------------|------------------|------------------|-------------------------|------------------------|----------------------|------------------------|
| `List`        | `ArrayList`        | `RandomAccess`, `Cloneable`, `Serializable` | Insertion | ✅ Allows duplicates         | ✅ Allows null (one or more)  | ❌ Not thread safe           | ✅ Yes               | `O(1)` get, `O(n)` remove | Modern               | Fast random access, dynamic array |
|               | `LinkedList`       | `Deque`, `Queue`, `Cloneable`, `Serializable` | Insertion | ✅ Allows duplicates         | ✅ Allows null           | ❌ Not thread safe           | ✅ Yes               | `O(1)` add/remove at ends | Modern               | Frequent insertions/deletions |
|               | `Vector`           | `RandomAccess`, `Cloneable`, `Serializable` | Insertion | ✅ Allows duplicates         | ✅ Allows null           | ✅ Thread safe               | ✅ Yes               | `O(1)` get, synchronized | Legacy               | Legacy synchronized list |
|               | `Stack`            | `Vector`, `Cloneable`, `Serializable` | LIFO       | ✅ Allows duplicates         | ✅ Allows null           | ✅ Thread safe               | ✅ Yes               | `O(1)` push/pop        | Legacy               | Stack operations (push/pop) |
| `Set`         | `HashSet`          | `Set`, `Cloneable`, `Serializable` | Unordered  | ❌ No duplicates allowed      | ✅ Allows null (one)      | ❌ Not thread safe           | ✅ Yes               | `O(1)` add/remove       | Modern               | Unique items, fast access |
|               | `LinkedHashSet`    | `HashSet`, `Set`, `Cloneable`, `Serializable` | Insertion | ❌ No duplicates allowed      | ✅ Allows null           | ❌ Not thread safe           | ✅ Yes               | `O(1)` add/remove       | Modern               | Ordered set preserving insertion order |
|               | `TreeSet`          | `NavigableSet`, `SortedSet`, `Cloneable`, `Serializable` | Sorted     | ❌ No duplicates allowed      | ❌ Does NOT allow null    | ❌ Not thread safe           | ✅ Yes               | `O(log n)` operations   | Modern               | Sorted unique items |
| `Queue`       | `PriorityQueue`    | `Serializable`, `Iterable`, `Queue` | Natural or Comparator based | ✅ Allows duplicates         | ✅ Allows null           | ❌ Not thread safe           | ✅ Yes               | `O(log n)` insertion    | Modern               | Priority-based access |
|               | `ArrayDeque`       | `Deque`, `Cloneable`, `Serializable` | Insertion | ✅ Allows duplicates         | ❌ Does NOT allow null    | ❌ Not thread safe           | ✅ Yes               | `O(1)` insertion/removal at ends | Modern               | Double-ended queue (FIFO/LIFO) |
|               | `LinkedList`       | `Deque`, `Queue`, `Cloneable`, `Serializable` | Insertion | ✅ Allows duplicates         | ✅ Allows null           | ❌ Not thread safe           | ✅ Yes               | `O(1)` insertion/removal at ends | Modern               | FIFO queue and double-ended queue |
| `Map`         | `HashMap`          | `Map`, `Cloneable`, `Serializable` | Unordered  | ❌ No duplicate keys, values can duplicate | ✅ Allows one null key <br>and multiple null values | ❌ Not thread safe           | ✅ Yes               | `O(1)` put/get/remove   | Modern               | General-purpose key-value mapping |
|               | `LinkedHashMap`    | `HashMap`, `Map`, `Cloneable`, `Serializable` | Insertion | ❌ No duplicate keys, values can duplicate | ✅ Allows one null key <br>and multiple null values | ❌ Not thread safe           | ✅ Yes               | `O(1)` put/get/remove   | Modern               | Maintains insertion order for keys |
|               | `TreeMap`          | `NavigableMap`, `SortedMap`, `Cloneable`, `Serializable` | Sorted     | ❌ No duplicate keys, values can duplicate | ❌ Does NOT allow null keys | ❌ Not thread safe           | ✅ Yes               | `O(log n)` operations   | Modern               | Sorted key-value mapping |
|               | `Hashtable`        | `Map`, `Cloneable`, `Serializable` | Unordered  | ❌ No duplicate keys, values can duplicate | ❌ Does NOT allow null keys or values | ✅ Thread safe               | ✅ Yes               | `O(1)` synchronized get/put | Legacy               | Legacy synchronized map |
|               | `ConcurrentHashMap`| `ConcurrentMap`, `Map`, `Serializable` | Unordered  | ❌ No duplicate keys, values can duplicate | ❌ Does NOT allow null keys or values | ✅ Thread safe               | ❌ No<br>(uses other <br>concurrency control) | `O(1)` concurrent access | Modern               | High-performance concurrent map |



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

### List<E> Interface

| Method Name       | Arguments                                                    | Return Type     | Description                                  | Example                      |
|-------------------|--------------------------------------------------------------|-----------------|----------------------------------------------|------------------------------|
| `add`             | `_int index_`, `_E element_` <span style="color:silver; font-style: italic;">(required)</span> | `void`          | Inserts element at specified position         | `list.add(1, "item");`       |
| `add`             | `_E element_` <span style="color:silver; font-style: italic;">(required)</span>               | `boolean`       | Adds element to end of list                    | `list.add("item");`          |
| `addAll`          | `_int index_`, `_Collection<? extends E> c_` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`       | Inserts all elements at specified position    | `list.addAll(1, collection);`|
| `addAll`          | `_Collection<? extends E> c_` <span style="color:silver; font-style: italic;">(required)</span> | `boolean`       | Adds all elements to end of list               | `list.addAll(collection);`   |
| `clear`           |                                                              | `void`          | Removes all elements                           | `list.clear();`              |
| `contains`        | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>                  | `boolean`       | Checks if element is present                   | `list.contains("item");`     |
| `containsAll`     | `_Collection<?> c_` <span style="color:silver; font-style: italic;">(required)</span>           | `boolean`       | Checks if all elements are present             | `list.containsAll(collection);`|
| `equals`          | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>                  | `boolean`       | Compares equality                              | `list.equals(otherList);`    |
| `get`             | `_int index_` <span style="color:silver; font-style: italic;">(required)</span>                  | `E`             | Returns element at position                     | `E element = list.get(1);`   |
| `indexOf`         | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>                  | `int`           | Returns index of first occurrence              | `int i = list.indexOf("item");`|
| `isEmpty`         |                                                              | `boolean`       | Checks if list is empty                         | `list.isEmpty();`            |
| `iterator`        |                                                              | `Iterator<E>`   | Returns iterator                               | `Iterator<E> it = list.iterator();`|
| `lastIndexOf`     | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>                  | `int`           | Returns index of last occurrence               | `int i = list.lastIndexOf("item");`|
| `listIterator`    |                                                              | `ListIterator<E>`| Returns list iterator                           | `ListIterator<E> it = list.listIterator();`|
| `listIterator`    | `_int index_` <span style="color:silver; font-style: italic;">(required)</span>                  | `ListIterator<E>`| Returns list iterator starting at index        | `ListIterator<E> it = list.listIterator(1);`|
| `remove`          | `_int index_` <span style="color:silver; font-style: italic;">(required)</span>                  | `E`             | Removes element at index                        | `E removed = list.remove(1);`|
| `remove`          | `_Object o_` <span style="color:silver; font-style: italic;">(required)</span>                  | `boolean`       | Removes first occurrence of element            | `list.remove("item");`       |
| `removeAll`       | `_Collection<?> c_` <span style="color:silver; font-style: italic;">(required)</span>           | `boolean`       | Removes all matching elements                   | `list.removeAll(collection);`|
| `retainAll`       | `_Collection<?> c_` <span style="color:silver; font-style: italic;">(required)</span>           | `boolean`       | Retains only elements present in collection    | `list.retainAll(collection);`|
| `set`             | `_int index_`, `_E element_` <span style="color:silver; font-style: italic;">(required)</span> | `E`             | Replaces element at index                       | `list.set(1, "newItem");`    |
| `size`            |                                                              | `int`           | Returns size of list                            | `int size = list.size();`    |
| `subList`         | `_int fromIndex_`, `_int toIndex_` <span style="color:silver; font-style: italic;">(required)</span> | `List<E>`       | Returns sublist view                            | `List<E> sub = list.subList(1, 3);` |
| `toArray`         |                                                              | `Object[]`      | Returns array of elements                       | `Object[] arr = list.toArray();` |
| `toArray`         | `_T[] a_` <span style="color:silver; font-style: italic;">(required)</span>                     | `<T[]>`         | Returns array in provided array type            | `String[] arr = list.toArray(new String[0]);` |

---

### Queue<E> Interface

| Method Name       | Arguments                                                    | Return Type       | Description                                  | Example                       |
|-------------------|--------------------------------------------------------------|-------------------|----------------------------------------------|-------------------------------|
| `add`             | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                   | `boolean`         | Inserts element or throws exception          | `queue.add("item");`           |
| `offer`           | `_E e_` <span style="color:silver; font-style: italic;">(required)</span>                   | `boolean`         | Inserts element or returns false if full     | `queue.offer("item");`         |
| `poll`            |                                                              | `E`               | Retrieves and removes head, or null if empty| `E e = queue.poll();`           |
| `remove`          |                                                              | `E`               | Retrieves and removes head, throws if empty | `E e = queue.remove();`         |
| `peek`            |                                                              | `E`               | Retrieves head or null if empty               | `E e = queue.peek();`           |
| `element`         |                                                              | `E`               | Retrieves head or throws if empty             | `E e = queue.element();`        |

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
