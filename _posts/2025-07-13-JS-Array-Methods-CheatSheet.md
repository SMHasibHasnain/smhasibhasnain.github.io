---
title: "📚 JavaScript Array Methods Cheat Sheet"
date: 2025-07-13
categories: [JavaScript, Cheat Sheet]
tags: [Array, JavaScript, Methods, Reference, JS]
pin: true
toc: true
comments: true
hidden: false
---

A complete guide to **41 built-in array methods** in JavaScript — grouped, explained, and summarized by purpose, return type, and argument structure.

Learning JavaScript arrays can be tricky at first because there are so many methods, each with subtle differences. Here’s a cheat sheet that helped me untangle them, with easy explanations so you can find what you need quickly.

---

## 1. Mutator Methods (Modify Original Array)

These methods **change the original array** directly. When you want to add, remove, or reorder elements and keep those changes, use these. 

**Be careful:** they affect the array in place, which can sometimes cause bugs if you’re not expecting it.

| Method       | Arguments                     | Description           | Returns       |
|--------------|------------------------------|-----------------------|---------------|
| push()       | ...items                     | Add to end            | New length    |
| pop()        | none                         | Remove last           | Removed item  |
| shift()      | none                         | Remove first          | Removed item  |
| unshift()    | ...items                     | Add to start          | New length    |
| splice()     | start, deleteCount?, ...items? | Add/remove at index   | Removed items |
| sort()       | compareFn?(a, b)             | Sort elements         | Sorted array  |
| reverse()    | none                         | Reverse array         | Reversed array|
| fill()       | value, start?, end?          | Fill with value       | Modified array|
| copyWithin() | target, start?, end?         | Copy section          | Modified array|

---

## 2. Non-Mutating Methods (Return New Arrays)

If you want to **keep your original array unchanged**, these methods return a **new array** with your desired changes or selections. This is great for safer, more predictable code.

| Method       | Arguments                                | Description             | Returns    |
|--------------|-----------------------------------------|-------------------------|------------|
| toSorted()   | compareFn?(a, b)                        | Sorted copy             | New array  |
| toReversed() | none                                   | Reversed copy           | New array  |
| toSpliced()  | start, deleteCount?, ...items?          | Splice copy             | New array  |
| slice()      | start?, end?                           | Portion of array        | New array  |
| concat()     | ...arrays/items                        | Merge arrays            | New array  |
| map()        | callback(element, index?, array?), thisArg? | Transform items     | New array  |
| filter()     | callback(element, index?, array?), thisArg? | Filter items        | New array  |
| flat()       | depth?                                | Flatten nested arrays    | New array  |
| flatMap()    | callback(element, index?, array?), thisArg? | Map + flatten       | New array  |
| from()       | arrayLike, mapFn?(element, index?), thisArg? | From iterable       | New array  |
| of()         | ...items                              | From arguments           | New array  |

---

## 3. Iteration / Evaluation Methods

These methods **loop through the array**, performing actions or checks. Some return new arrays, some return values, and some don’t return anything. They’re essential for processing arrays efficiently.

| Method       | Arguments                                | Description             | Returns     |
|--------------|-----------------------------------------|-------------------------|-------------|
| forEach()    | callback(element, index?, array?), thisArg? | Loop over items   | undefined   |
| map()        | callback(element, index?, array?), thisArg? | Transform          | New array   |
| filter()     | callback(element, index?, array?), thisArg? | Filter             | New array   |
| reduce()     | callback(acc, cur, index?, array?), initialValue? | Left-to-right reduce | Single value|
| reduceRight()| Same as reduce()                        | Right-to-left reduce   | Single value|
| some()       | callback(element, index?, array?), thisArg? | If any match        | Boolean     |
| every()      | callback(element, index?, array?), thisArg? | If all match        | Boolean     |

---

## 4. Search & Index Methods

Use these when you need to **find elements or check their existence**. They return indexes, booleans, or the element found, making it easy to locate data in arrays.

| Method          | Arguments                              | Description           | Returns           |
|-----------------|--------------------------------------|-----------------------|-------------------|
| indexOf()       | searchElement, fromIndex?             | First match index     | Index or -1       |
| lastIndexOf()   | searchElement, fromIndex?             | Last match index      | Index or -1       |
| includes()      | searchElement, fromIndex?             | Check presence        | Boolean           |
| find()          | callback(element, index?, array?), thisArg? | First match element | Value or undefined|
| findIndex()     | callback(element, index?, array?), thisArg? | Index of first match | Index or -1       |
| findLast()      | callback(element, index?, array?), thisArg? | Last match element  | Value or undefined|
| findLastIndex() | callback(element, index?, array?), thisArg? | Index of last match | Index or -1       |

---

## 5. Element Access & Iterators

These methods help you **access specific elements or iterate over keys and values** without changing the array. Useful for controlled traversal or when working with array-like structures.

| Method     | Arguments    | Description                    | Returns           |
|------------|--------------|--------------------------------|-------------------|
| at()       | index        | Get item at index (can be negative) | Element or undefined |
| keys()     | none         | Iterator of indexes            | Iterator          |
| values()   | none         | Iterator of values             | Iterator          |
| entries()  | none         | Iterator of [index, value] pairs | Iterator       |

---

## 6. Structure & Conversion Utilities

These are handy **utility methods** to check, convert, or extend arrays. They don't change the array but help you understand or transform it into other forms.

| Method      | Arguments    | Description                  | Returns          |
|-------------|--------------|------------------------------|------------------|
| isArray()   | value        | Check if value is array      | Boolean          |
| toString()  | none         | Convert to comma-separated string | String       |
| join()      | separator?   | Join into custom string       | String           |
| valueOf()   | none         | Primitive value              | The array itself  |
| prototype   | (object)     | Extend array behavior         | Object           |

---

## Categorized by Return Type

Understanding what each method returns helps you predict how to chain them and avoid unexpected bugs.

- **New Array**: methods that return a new array rather than modifying the original.  
  Examples: `map`, `filter`, `slice`, `concat`, `flat`, `flatMap`, `toSorted`, `toReversed`, `toSpliced`, `from`, `of`

- **Boolean**: methods that return true or false based on conditions.  
  Examples: `some`, `every`, `includes`, `isArray`

- **Index**: methods that return the position of elements or -1 if not found.  
  Examples: `indexOf`, `lastIndexOf`, `findIndex`, `findLastIndex`

- **Single Value**: methods that return a single value calculated from the array, like a sum or found element.  
  Examples: `reduce`, `reduceRight`, `find`, `findLast`, `at`, `join`, `toString`, `valueOf`

- **Iterator**: methods that return an iterable to traverse keys or values.  
  Examples: `keys`, `values`, `entries`

- **Undefined**: methods that return undefined and are used for side effects.  
  Example: `forEach`

---

## Categorized by Similar Purpose

Grouping methods by what they do helps pick the right one when coding:

- **Add/Remove Elements**: `push`, `pop`, `shift`, `unshift`, `splice`, `toSpliced`

- **Sort/Reverse**: `sort`, `toSorted`, `reverse`, `toReversed`

- **Search**: `includes`, `indexOf`, `lastIndexOf`, `find`, `findIndex`, `findLast`, `findLastIndex`

- **Transform**: `map`, `flatMap`, `from`

- **Filter/Evaluate**: `filter`, `every`, `some`

- **Reduce**: `reduce`, `reduceRight`

- **Access/Iterate**: `at`, `keys`, `values`, `entries`

- **Info/Conversion**: `isArray`, `toString`, `join`, `valueOf`, `prototype`

---

## Categorized by Number of Arguments

Different methods expect different numbers of arguments. Some take none, some take one, and others take multiple.

Knowing this helps you use them correctly without errors.

- **0 arguments**: `pop`, `shift`, `reverse`, `toReversed`, `keys`, `values`, `entries`, `toString`, `valueOf`

- **1 argument**: `push(item)`, `includes(value)`, `flat(depth)`, `at(index)`, `isArray(value)`, `join(separator)`, `find(callback)`, `map(callback)`, `filter(callback)`, `forEach(callback)`, `every(callback)`, `some(callback)`

- **2 arguments**: `indexOf(value, fromIndex)`, `lastIndexOf(value, fromIndex)`, `fill(value, start)`, `slice(start, end)`, `copyWithin(target, start)`, `reduce(callback, initialValue)`, `reduceRight(callback, initialValue)`

- **3+ arguments**: `splice(start, deleteCount, ...items)`, `copyWithin(target, start, end)`, `from(arrayLike, mapFn, thisArg)`, `flatMap(callback, thisArg)`

---

## Remember

Many methods like map, filter, and forEach take a callback function with parameters.

Only the first parameter, typically the current element, is required.

The second and third parameters (index and the whole array) are optional but can be useful if needed.
