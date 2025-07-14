---
title: "JavaScript Array Methods Cheat Sheet"
date: 2025-07-13 
categories: [JavaScript, Cheat Sheet]
tags: [Array, JavaScript, Methods, Reference, JS]
pin: true
toc: true
comments: true
hidden: false
---

A complete guide to **41 built-in array methods** in JavaScript — grouped, explained, and summarized by purpose, return type, and argument structure.

---

## 🔁 1. Mutator Methods (Modify Original Array)

| Method | Arguments | Description | Returns |
|--------|-----------|-------------|---------|
| `push()` | `...items` | Add to end | New length |
| `pop()` | *none* | Remove last | Removed item |
| `shift()` | *none* | Remove first | Removed item |
| `unshift()` | `...items` | Add to start | New length |
| `splice()` | `start`, `deleteCount?`, `...items?` | Add/remove at index | Removed items |
| `sort()` | `compareFn?(a, b)` | Sort elements | Sorted array |
| `reverse()` | *none* | Reverse array | Reversed array |
| `fill()` | `value`, `start?`, `end?` | Fill with value | Modified array |
| `copyWithin()` | `target`, `start?`, `end?` | Copy section | Modified array |

---

## 🧪 2. Non-Mutating Methods (Return New Arrays)

| Method | Arguments | Description | Returns |
|--------|-----------|-------------|---------|
| `toSorted()` | `compareFn?(a, b)` | Sorted copy | New array |
| `toReversed()` | *none* | Reversed copy | New array |
| `toSpliced()` | `start`, `deleteCount?`, `...items?` | Splice copy | New array |
| `slice()` | `start?`, `end?` | Portion of array | New array |
| `concat()` | `...arrays/items` | Merge arrays | New array |
| `map()` | `callback(element, index?, array?)`, `thisArg?` | Transform items | New array |
| `filter()` | `callback(element, index?, array?)`, `thisArg?` | Filter items | New array |
| `flat()` | `depth?` | Flatten nested arrays | New array |
| `flatMap()` | `callback(element, index?, array?)`, `thisArg?` | Map + flatten | New array |
| `from()` | `arrayLike`, `mapFn?(element, index?)`, `thisArg?` | From iterable | New array |
| `of()` | `...items` | From arguments | New array |

---

## 🔄 3. Iteration / Evaluation Methods

| Method | Arguments | Description | Returns |
|--------|-----------|-------------|---------|
| `forEach()` | `callback(element, index?, array?)`, `thisArg?` | Loop over items | `undefined` |
| `map()` | `callback(element, index?, array?)`, `thisArg?` | Transform | New array |
| `filter()` | `callback(element, index?, array?)`, `thisArg?` | Filter | New array |
| `reduce()` | `callback(acc, cur, index?, array?)`, `initialValue?` | Left-to-right reduce | Single value |
| `reduceRight()` | Same as `reduce()` | Right-to-left reduce | Single value |
| `some()` | `callback(element, index?, array?)`, `thisArg?` | If any match | Boolean |
| `every()` | `callback(element, index?, array?)`, `thisArg?` | If all match | Boolean |

---

## 🔍 4. Search & Index Methods

| Method | Arguments | Description | Returns |
|--------|-----------|-------------|---------|
| `indexOf()` | `searchElement`, `fromIndex?` | First match index | Index or -1 |
| `lastIndexOf()` | `searchElement`, `fromIndex?` | Last match index | Index or -1 |
| `includes()` | `searchElement`, `fromIndex?` | Check presence | Boolean |
| `find()` | `callback(element, index?, array?)`, `thisArg?` | First match element | Value or `undefined` |
| `findIndex()` | `callback(element, index?, array?)`, `thisArg?` | Index of first match | Index or -1 |
| `findLast()` | `callback(element, index?, array?)`, `thisArg?` | Last match element | Value or `undefined` |
| `findLastIndex()` | `callback(element, index?, array?)`, `thisArg?` | Index of last match | Index or -1 |

---

## 📍 5. Element Access & Iterators

| Method | Arguments | Description | Returns |
|--------|-----------|-------------|---------|
| `at()` | `index` | Get item at index (can be negative) | Element or `undefined` |
| `keys()` | *none* | Iterator of indexes | Iterator |
| `values()` | *none* | Iterator of values | Iterator |
| `entries()` | *none* | Iterator of `[index, value]` pairs | Iterator |

---

## 🧱 6. Structure & Conversion Utilities

| Method | Arguments | Description | Returns |
|--------|-----------|-------------|---------|
| `isArray()` | `value` | Check if value is array | Boolean |
| `toString()` | *none* | Convert to comma-separated string | String |
| `join()` | `separator?` | Join into custom string | String |
| `valueOf()` | *none* | Primitive value | The array itself |
| `prototype` | *(object)* | Extend array behavior | Object |

---

## ✅ Catagorized by Return Type

| Return Type       | Methods |
|-------------------|---------|
| **New Array**     | `map()`, `filter()`, `slice()`, `concat()`, `flat()`, `flatMap()`, `toSorted()`, `toReversed()`, `toSpliced()`, `from()`, `of()` |
| **Boolean**       | `some()`, `every()`, `includes()`, `isArray()` |
| **Index**         | `indexOf()`, `lastIndexOf()`, `findIndex()`, `findLastIndex()` |
| **Single Value**  | `reduce()`, `reduceRight()`, `find()`, `findLast()`, `at()`, `join()`, `toString()`, `valueOf()` |
| **Iterator**      | `keys()`, `values()`, `entries()` |
| **Undefined**     | `forEach()` |

---

## 🔁 Catagorized by Similar Purpose

| Category              | Methods |
|------------------------|---------|
| **Add/Remove Elements** | `push()`, `pop()`, `shift()`, `unshift()`, `splice()`, `toSpliced()` |
| **Sort/Reverse**       | `sort()`, `toSorted()`, `reverse()`, `toReversed()` |
| **Search**             | `includes()`, `indexOf()`, `lastIndexOf()`, `find()`, `findIndex()`, `findLast()`, `findLastIndex()` |
| **Transform**          | `map()`, `flatMap()`, `from()` |
| **Filter/Evaluate**    | `filter()`, `every()`, `some()` |
| **Reduce**             | `reduce()`, `reduceRight()` |
| **Access/Iterate**     | `at()`, `keys()`, `values()`, `entries()` |
| **Info/Conversion**    | `isArray()`, `toString()`, `join()`, `valueOf()`, `prototype` |

---

## 🧠 Catagorized by Number of Arguments

| # of Arguments | Methods |
|----------------|---------|
| **0** | `pop()`, `shift()`, `reverse()`, `toReversed()`, `keys()`, `values()`, `entries()`, `toString()`, `valueOf()` |
| **1** | `push(item)`, `includes(value)`, `flat(depth)`, `at(index)`, `isArray(value)`, `join(separator)`, `find(callback)`, `map(callback)`, `filter(callback)`, `forEach(callback)`, `every(callback)`, `some(callback)` |
| **2** | `indexOf(value, fromIndex)`, `lastIndexOf(value, fromIndex)`, `fill(value, start)`, `slice(start, end)`, `copyWithin(target, start)`, `reduce(callback, initialValue)`, `reduceRight(callback, initialValue)` |
| **3+** | `splice(start, deleteCount, ...items)`, `copyWithin(target, start, end)`, `from(arrayLike, mapFn, thisArg)`, `flatMap(callback, thisArg)` |

---

## 🧠 Optional Callback Parameters

In most callback-based methods like `map()`, `filter()`, etc.:

- Only the first parameter `element` is **required**.
- `index` and `array` are **optional** but available.

```js
array.map((element) => element * 2); // index, array optional
