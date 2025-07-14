---
title: "📚 JavaScript Array Methods Cheat Sheet"
date: 2025-07-13
categories: [JavaScript, Cheat Sheet]
tags: [Array, JavaScript, Methods, Reference, JS]
pin: true
toc: true
comments: false
hidden: false
---

A complete guide to **41 built-in array methods** in JavaScript — grouped, explained, and summarized by purpose, return type, and argument structure.

Learning JavaScript arrays can be tricky at first because there are so many methods, each with subtle differences. Here’s a cheat sheet that helped me untangle them, with easy explanations so you can find what you need quickly.

---

## 1. Mutator Methods (Modify Original Array)

These methods **change the original array** directly. When you want to add, remove, or reorder elements and keep those changes, use these. 

**Be careful:** they affect the array in place, which can sometimes cause bugs if you’re not expecting it.

| Method       | Arguments                                    | Description           | Returns        |
|--------------|----------------------------------------------|-----------------------|----------------|
| [`push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)       | `...items`                                     | Add to end            | New length     |
| [`pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)         | none                                         | Remove last           | Removed item   |
| [`shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)     | none                                         | Remove first          | Removed item   |
| [`unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) | `...items`                                     | Add to start          | New length     |
| [`splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)   | `start`, <span style="color:#888">deleteCount</span>, <span style="color:#888">...items</span> | Add/remove at index   | Removed items  |
| [`sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)       | <span style="color:#888">compareFn(a, b)</span> | Sort elements         | Sorted array   |
| [`reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) | none                                         | Reverse array         | Reversed array |
| [`fill()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)       | `value`, <span style="color:#888">start</span>, <span style="color:#888">end</span> | Fill with value       | Modified array |
| [`copyWithin()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) | `target`, <span style="color:#888">start</span>, <span style="color:#888">end</span> | Copy section          | Modified array |

---

## 2. Non-Mutating Methods (Return New Arrays)

If you want to **keep your original array unchanged**, these methods return a **new array** with your desired changes or selections. This is great for safer, more predictable code.

| Method       | Arguments                                                   | Description           | Returns    |
|--------------|-------------------------------------------------------------|-----------------------|------------|
| [`toSorted()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toSorted)   | <span style="color:#888">compareFn(a, b)</span>                 | Sorted copy           | New array  |
| [`toReversed()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toReversed) | none                                                      | Reversed copy         | New array  |
| [`toSpliced()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toSpliced)  | `start`, <span style="color:#888">deleteCount</span>, <span style="color:#888">...items</span> | Splice copy           | New array  |
| [`slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)      | <span style="color:#888">start</span>, <span style="color:#888">end</span>               | Portion of array      | New array  |
| [`concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)     | `...arrays/items`                                         | Merge arrays          | New array  |
| [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)        | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span>          | Transform items       | New array  |
| [`filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)     | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span>          | Filter items          | New array  |
| [`flat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)       | <span style="color:#888">depth</span>                                | Flatten nested arrays | New array  |
| [`flatMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)    | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span>          | Map + flatten         | New array  |
| [`from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)       | `arrayLike`, <span style="color:#888">mapFn(element, index)</span>, <span style="color:#888">thisArg</span>   | From iterable         | New array  |
| [`of()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of)         | `...items`                                                 | From arguments        | New array  |

---

## 3. Iteration / Evaluation Methods

These methods **loop through the array**, performing actions or checks. Some return new arrays, some return values, and some don’t return anything. They’re essential for processing arrays efficiently.

| Method        | Arguments                                                   | Description            | Returns      |
|---------------|-------------------------------------------------------------|------------------------|--------------|
| [`forEach()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)    | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | Loop over items        | undefined    |
| [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)            | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | Transform             | New array    |
| [`filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)      | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | Filter                | New array    |
| [`reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)      | `callback(acc, cur, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">initialValue</span> | Left-to-right reduce  | Single value |
| [`reduceRight()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) | Same as `reduce()`                                      | Right-to-left reduce   | Single value |
| [`some()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)          | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | If any match          | Boolean      |
| [`every()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)        | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | If all match          | Boolean      |

---

## 4. Search & Index Methods

Use these when you need to **find elements or check their existence**. They return indexes, booleans, or the element found, making it easy to locate data in arrays.

| Method          | Arguments                                                      | Description           | Returns            |
|-----------------|----------------------------------------------------------------|-----------------------|--------------------|
| [`indexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)       | `searchElement`, <span style="color:#888">fromIndex</span>            | First match index     | Index or -1        |
| [`lastIndexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)   | `searchElement`, <span style="color:#888">fromIndex</span>            | Last match index      | Index or -1        |
| [`includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)      | `searchElement`, <span style="color:#888">fromIndex</span>            | Check presence        | Boolean            |
| [`find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)          | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | First match element   | Value or undefined |
| [`findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)     | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | Index of first match  | Index or -1        |
| [`findLast()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLast)      | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | Last match element    | Value or undefined |
| [`findLastIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findLastIndex) | `callback(element, index`, <span style="color:#888">`?`,</span> `array`<span style="color:#888">`?`</span>), <span style="color:#888">thisArg</span> | Index of last match   | Index or -1        |

---

## 5. Element Access & Iterators

These methods help you **access specific elements or iterate over keys and values** without changing the array. Useful for controlled traversal or when working with array-like structures.

| Method       | Arguments             | Description                        | Returns             |
|--------------|-----------------------|----------------------------------|---------------------|
| [`at()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at)         | `index`                      | Get item at index (can be negative) | Element or undefined |
| [`keys()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/keys)     | none                        | Iterator of indexes             | Iterator            |
| [`values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values) | none                        | Iterator of values              | Iterator            |
| [`entries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries) | none                      | Iterator of [index, value] pairs | Iterator          |

---

## 6. Structure & Conversion Utilities

These are handy **utility methods** to check, convert, or extend arrays. They don't change the array but help you understand or transform it into other forms.

| Method       | Arguments              | Description                       | Returns           |
|--------------|------------------------|---------------------------------|-------------------|
| [`isArray()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)    | `value`                       | Check if value is array       | Boolean           |
| [`toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)  | none                         | Convert to comma-separated string | String        |
| [`join()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)          | <span style="color:#888">separator</span>          | Join into custom string        | String            |
| [`valueOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/valueOf)    | none                         | Primitive value               | The array itself   |
| [`prototype`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype)   | `(object)`                   | Extend array behavior          | Object            |

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

## Categorized by Number of Arguments

Different methods expect different numbers of arguments. Some take none, some take one, and others take multiple.

Knowing this helps you use them correctly without errors.

- **0 arguments**: `pop`, `shift`, `reverse`, `toReversed`, `keys`, `values`, `entries`, `toString`, `valueOf`

- **1 argument**: `push(item)`, `includes(value)`, `flat(depth)`, `at(index)`, `isArray(value)`, `join(separator)`, `find(callback)`, `map(callback)`, `filter(callback)`, `forEach(callback)`, `every(callback)`, `some(callback)`

- **2 arguments**: `indexOf(value, fromIndex)`, `lastIndexOf(value, fromIndex)`, `fill(value, start)`, `slice(start, end)`, `copyWithin(target, start)`, `reduce(callback, initialValue)`, `reduceRight(callback, initialValue)`

- **3+ arguments**: `splice(start, deleteCount, ...items)`, `copyWithin(target, start, end)`, `from(arrayLike, mapFn, thisArg)`, `flatMap(callback, thisArg)`

---

## Ultimate JS Array Method CheatSheet (Categorized by Similar Purpose)

Grouping methods by what they do helps pick the right one when coding:

| Category                     | Methods                                                                                                     |
|------------------------------|-------------------------------------------------------------------------------------------------------------|
| 🛠️ Add / Remove Items          | [`push()`](https://www.w3schools.com/jsref/jsref_push.asp)<sup style="color:#d32f2f">★★★</sup>, [`pop()`](https://www.w3schools.com/jsref/jsref_pop.asp)<sup style="color:#d32f2f">★★★</sup>, [`shift()`](https://www.w3schools.com/jsref/jsref_shift.asp)<sup style="color:#d32f2f">★★★</sup>, [`unshift()`](https://www.w3schools.com/jsref/jsref_unshift.asp)<sup style="color:#d32f2f">★★★</sup>, [`splice()`](https://www.w3schools.com/jsref/jsref_splice.asp)<sup style="color:#d32f2f">★★★</sup>, [`toSpliced()`](https://www.w3schools.com/jsref/jsref_array_tospliced.asp)<sup style="color:#fbc02d">★★</sup> |
| 📥 Copy / Extract              | [`slice()`](https://www.w3schools.com/jsref/jsref_slice_array.asp)<sup style="color:#d32f2f">★★★</sup>, [`concat()`](https://www.w3schools.com/jsref/jsref_concat_array.asp)<sup style="color:#d32f2f">★★★</sup>, [`fill()`](https://www.w3schools.com/jsref/jsref_fill.asp)<sup style="color:#388e3c">★</sup>, [`copyWithin()`](https://www.w3schools.com/jsref/jsref_copywithin.asp)<sup style="color:#388e3c">★</sup>, [`with()`](https://www.w3schools.com/jsref/jsref_array_with.asp)<sup style="color:#388e3c">★</sup> |
| 🔄 Transform Elements          | [`map()`](https://www.w3schools.com/jsref/jsref_map.asp)<sup style="color:#d32f2f">★★★</sup>, [`flatMap()`](https://www.w3schools.com/jsref/jsref_array_flatmap.asp)<sup style="color:#d32f2f">★★★</sup> |
| ✅ Filter by Condition         | [`filter()`](https://www.w3schools.com/jsref/jsref_filter.asp)<sup style="color:#d32f2f">★★★</sup> |
| 🧠 Accumulate to One Value     | [`reduce()`](https://www.w3schools.com/jsref/jsref_reduce.asp)<sup style="color:#d32f2f">★★★</sup>, [`reduceRight()`](https://www.w3schools.com/jsref/jsref_reduceright.asp)<sup style="color:#fbc02d">★★</sup> |
| 🔁 Iterate (Side Effects Only) | [`forEach()`](https://www.w3schools.com/jsref/jsref_foreach.asp)<sup style="color:#d32f2f">★★★</sup> |
| 🔃 Reorder / Sort              | [`sort()`](https://www.w3schools.com/jsref/jsref_sort.asp)<sup style="color:#d32f2f">★★★</sup>, [`reverse()`](https://www.w3schools.com/jsref/jsref_reverse.asp)<sup style="color:#d32f2f">★★★</sup>, [`toSorted()`](https://www.w3schools.com/jsref/jsref_array_tosorted.asp)<sup style="color:#fbc02d">★★</sup>, [`toReversed()`](https://www.w3schools.com/jsref/jsref_array_toreversed.asp)<sup style="color:#fbc02d">★★</sup> |
| 🧱 Flatten Arrays              | [`flat()`](https://www.w3schools.com/jsref/jsref_array_flat.asp)<sup style="color:#d32f2f">★★★</sup>, [`flatMap()`](https://www.w3schools.com/jsref/jsref_array_flatmap.asp)<sup style="color:#d32f2f">★★★</sup> |
| 🔍 Search by Value             | [`indexOf()`](https://www.w3schools.com/jsref/jsref_indexof.asp)<sup style="color:#d32f2f">★★★</sup>, [`lastIndexOf()`](https://www.w3schools.com/jsref/jsref_lastindexof.asp)<sup style="color:#fbc02d">★★</sup>, [`includes()`](https://www.w3schools.com/jsref/jsref_includes.asp)<sup style="color:#d32f2f">★★★</sup> |
| 🔎 Search by Condition         | [`find()`](https://www.w3schools.com/jsref/jsref_find.asp)<sup style="color:#d32f2f">★★★</sup>, [`findIndex()`](https://www.w3schools.com/jsref/jsref_findindex.asp)<sup style="color:#d32f2f">★★★</sup>, [`findLast()`](https://www.w3schools.com/jsref/jsref_array_findlast.asp)<sup style="color:#fbc02d">★★</sup>, [`findLastIndex()`](https://www.w3schools.com/jsref/jsref_array_findlastindex.asp)<sup style="color:#fbc02d">★★</sup> |
| ✅ Test Conditions (Boolean)   | [`some()`](https://www.w3schools.com/jsref/jsref_some.asp)<sup style="color:#d32f2f">★★★</sup>, [`every()`](https://www.w3schools.com/jsref/jsref_every.asp)<sup style="color:#d32f2f">★★★</sup> |
| 📍 Access by Index             | [`at()`](https://www.w3schools.com/jsref/jsref_array_at.asp)<sup style="color:#fbc02d">★★</sup> |
| 🔑 Keys / Values / Entries     | [`keys()`](https://www.w3schools.com/jsref/jsref_keys.asp)<sup style="color:#388e3c">★</sup>, [`values()`](https://www.w3schools.com/jsref/jsref_values.asp)<sup style="color:#388e3c">★</sup>, [`entries()`](https://www.w3schools.com/jsref/jsref_entries.asp)<sup style="color:#388e3c">★</sup> |
| 🧾 Convert to String           | [`join()`](https://www.w3schools.com/jsref/jsref_join.asp)<sup style="color:#fbc02d">★★</sup>, [`toString()`](https://www.w3schools.com/jsref/jsref_tostring_array.asp)<sup style="color:#388e3c">★</sup> |
| 🏗️ Create Arrays (Static)      | [`Array.from()`](https://www.w3schools.com/jsref/jsref_from.asp)<sup style="color:#fbc02d">★★</sup>, [`Array.of()`](https://www.w3schools.com/jsref/jsref_array_of.asp)<sup style="color:#388e3c">★</sup>, [`Array.isArray()`](https://www.w3schools.com/jsref/jsref_from.asp)<sup style="color:#fbc02d">★★</sup> |
| 📉 Others                     | (no methods with 0-star priority here) |

---

## Further Reading & Deep Dive

Explore these trusted resources to **master JavaScript array methods**, from documentation to hands-on practice.

- [**MDN Web Docs – Array**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) : *The most comprehensive and accurate reference for all JavaScript array methods, complete with syntax, examples, and browser compatibility.*
- [**W3Schools – JavaScript Arrays**](https://www.w3schools.com/js/js_arrays.asp) : *Beginner-friendly overview of JavaScript arrays and methods, with interactive code examples.*
- [**JavaScript.info – Array Methods**](https://javascript.info/array-methods) : *Modern, in-depth explanations with visuals and sample problems. Great for serious learners.* 
- [**freeCodeCamp – 30 Useful JavaScript Array Methods**](https://www.freecodecamp.org/news/javascript-array-methods-how-to-manipulate-arrays-in-js/)  
  *Practical guide on when and how to use key methods like `map`, `reduce`, `filter`, and more.*
- [**JavaScript Tutorial – Array Methods**](https://www.javascripttutorial.net/javascript-array/) : *A structured tutorial series that covers everything from basic array creation to advanced operations.*
- [**Exercism – JavaScript Track**](https://exercism.org/tracks/javascript/exercises) : *Solve exercises and get feedback from mentors. Ideal for refining your problem-solving with arrays.*
- [**Codewars – JavaScript Kata (Array)**](https://www.codewars.com/kata/search/javascript?q=array) : *Solve progressively harder challenges that focus specifically on array logic.*
- [**LeetCode – Array Problems**](https://leetcode.com/tag/array/) : *Apply array methods in algorithm challenges commonly asked in interviews.*