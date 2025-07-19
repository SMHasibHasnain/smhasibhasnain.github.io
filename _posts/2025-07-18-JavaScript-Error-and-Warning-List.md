---
title: "🌋 JavaScript Error and Warning Reference"
date: 2025-07-18
categories: [JavaScript, Cheat Sheet]
tags: [Error, JavaScript, Warnings, Reference, JS]
pin: true
toc: true
comments: false
---

Comprehensive list of JavaScript errors and warnings with descriptions, code examples, and MDN links.

---

## JavaScript Errors

| Error | Description | Example |
|-------|-------------|---------|
| [AggregateError: No Promise in Promise.any was resolved](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/AggregateError) | All promises in `Promise.any()` were rejected, so no promise resolved. | `Promise.any([Promise.reject("fail")])` |
| [Error: Permission denied to access property "x"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error) | Accessing a restricted or cross-origin property causes this error. | `window.parent.location.href` (from different origin iframe) |
| [InternalError: too much recursion](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/InternalError) | Call stack exceeded due to infinite or very deep recursion. | `function recurse() { recurse(); } recurse();` |
| [RangeError: argument is not a valid code point](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError) | Unicode code point is out of valid range (0 to 0x10FFFF). | `String.fromCodePoint(0x110000)` |
| [RangeError: BigInt division by zero](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) | Dividing a BigInt by zero (`0n`) is not allowed. | `10n / 0n` |
| [RangeError: BigInt negative exponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) | BigInt exponentiation does not support negative exponents. | `2n ** -1n` |
| [RangeError: form must be one of <br>'NFC', 'NFD', 'NFKC', or 'NFKD'](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/normalize) | Invalid Unicode normalization form string. | `'abc'.normalize('XYZ')` |
| [RangeError: invalid array length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length) | Array length must be a non-negative integer less than 2^32. | `new Array(-1)` |
| [RangeError: invalid date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) | Date constructor received invalid date string or value. | `new Date('invalid')` |
| [RangeError: precision is out of range](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toPrecision) | Precision value outside allowed range in `toPrecision()`. | `(1.23).toPrecision(500)` |
| [RangeError: radix must be an integer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) | Radix for parsing must be an integer between 2 and 36. | `parseInt('10', 2.5)` |
| [RangeError: repeat count must be less than infinity](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat) | Repeat count cannot be infinite or too large. | `'a'.repeat(Infinity)` |
| [RangeError: repeat count mus<br>t be non-negative](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat) | Repeat count cannot be negative. | `'a'.repeat(-1)` |
| [RangeError: x can't be converted to BigInt <br>because it isn't an integer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt) | Only integer values can be converted to BigInt. | `BigInt(1.5)` |
| [ReferenceError: "x" is not defined](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError) | Variable used before being declared or not declared at all. | `console.log(foo);` |
| [ReferenceError: assignment to undeclared variable "x"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) | Assigning to a variable not declared in strict mode. | `'use strict'; foo = 123;` |
| [ReferenceError: can't access <br>lexical declaration 'X' <br>before initialization](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) | Accessing a `let` or `const` variable before declaration. | `console.log(x); let x = 5;` |
| [ReferenceError: must call super constructor <br>before using 'this' <br>in derived class constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends) | `this` used before `super()` call in subclass constructor. | `constructor() { this.x = 1; super(); }` |
| [ReferenceError: super() called twice <br>in derived class constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super) | Calling `super()` more than once in a derived class constructor. | `constructor() { super(); super(); }` |
| [SyntaxError: 'arguments'/'eval' can't be <br>defined or assigned <br>to in strict mode code](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Strict_mode_restricted_identifiers) | Cannot use or assign `arguments` or `eval` as identifiers in strict mode. | `'use strict'; let arguments = 5;` |
| [SyntaxError: "0"-prefixed octal literals are deprecated](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#legacy_octal_literals) | Octal literals starting with 0 are deprecated and disallowed in strict mode. | `let x = 071;` |
| [SyntaxError: "use strict" not allowed in function with <br>non-simple parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) | Strict mode directive disallowed with complex function parameters. | `function f(a = 1) { "use strict"; }` |
| [SyntaxError: "x" is a reserved identifier](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#keywords) | Using reserved words or identifiers as variable/function names. | `let for = 5;` |
| [SyntaxError: \ at end of pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Regex pattern ends with unescaped backslash. | `/abc\\/` |
| [SyntaxError: a declaration in the head of a for-of loop <br>can't have an initializer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of) | `let` or `const` in loop header cannot be initialized. | `for (let i = 0 of arr) {}` |
| [SyntaxError: applying the 'delete' operator to an unqualified <br>name is deprecated](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete) | Using `delete` on a variable name is deprecated. | `delete x;` |
| [SyntaxError: arguments is not valid in fields](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Invalid_fields) | Using `arguments` as class field name is invalid. | `class C { arguments = 1; }` |
| [SyntaxError: await is only valid in async functions, <br>async generators and modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await) | `await` used outside async function or module. | `await fetch('url');` |
| [SyntaxError: await/yield expression can't be used <br>in parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await) | Using `await` or `yield` in function parameter list is invalid. | `function f(await x) {}` |
| [SyntaxError: cannot use `??` unparenthesized <br>within `\|\|` and `&&` expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator) | Nullish coalescing operator requires parentheses when combined with `||` or `&&`. | `true || false ?? true` |
| [SyntaxError: character class escape cannot be used <br>in class range in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Using escape sequences improperly inside regex character ranges. | `/[a-\d]/` |
| [SyntaxError: continue must be inside loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/continue) | `continue` statement used outside loops. | `if (true) { continue; }` |
| [SyntaxError: duplicate capture <br>group name in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Regex contains named groups with duplicate names. | `/(?'name'a)(?'name'b)/` |
| [SyntaxError: duplicate formal argument x](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Duplicate_param) | Function parameters declared more than once. | `function f(x, x) {}` |
| [SyntaxError: for-in loop head declarations <br>may not have initializers](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) | Loop variable declaration cannot have initializer. | `for (let i = 0 in obj) {}` |
| [SyntaxError: function statement requires a name](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function) | Named function missing a name. | `function () {}` |
| [SyntaxError: functions cannot be labelled](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label) | Function declarations cannot have labels. | `label: function foo() {}` |
| [SyntaxError: getter and setter for private name #x should <br>either be both static or non-static](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#private_class_elements) | Private getter and setter must both be static or non-static. | `class C { static get #x() {}; set #x(v) {} }` |
| [SyntaxError: getter functions must have no arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get) | Getters cannot have parameters. | `get x(a) {}` |
| [SyntaxError: identifier starts immediately <br>after numeric literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#numeric_literals) | No space between number and identifier. | `let x = 5y;` |
| [SyntaxError: illegal character](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Illegal_character) | Invalid character in source code. | `var x = "\u0000";` |
| [SyntaxError: import declarations may only appear <br>at top level of a module](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) | `import` used inside blocks or scripts not marked as modules. | `if (true) { import x from 'mod'; }` |
| [SyntaxError: incomplete quantifier in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Quantifier in regex missing parts. | `/a{2,}/` (if incomplete) |
| [SyntaxError: invalid assignment left-hand side](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Invalid_left_hand_side) | Left side of assignment operator invalid. | `5 = x;` |
| [SyntaxError: invalid BigInt syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#bigint_literals) | Invalid format for BigInt literal. | `123n4` |
| [SyntaxError: invalid capture group name <br>in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Regex named capture group has invalid name. | `/(?<1name>a)/` |
| [SyntaxError: invalid character in class <br>in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Invalid characters inside regex character class. | `/[a-]/` |
| [SyntaxError: invalid class set operation <br>in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Invalid use of set operations like subtraction in regex classes. | `/[a-z&&[^aeiou]]/` (unsupported) |
| [SyntaxError: invalid decimal escape in <br>regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Invalid decimal escapes in regex. | `/\9/` |
| [SyntaxError: invalid identity escape in <br>regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Invalid escape sequences in regex. | `/\c/` |
| [SyntaxError: invalid named capture reference <br>in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Reference to undefined named group in regex. | `/\k<name>/` without group named `name` |
| [SyntaxError: invalid property name in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Invalid property names in Unicode regex escapes. | `/\p{Invalid}/u` |
| [SyntaxError: invalid range in character class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Character class ranges out of order or invalid. | `/[z-a]/` |
| [SyntaxError: invalid regexp group](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Malformed group in regex. | `/(()/` |
| [SyntaxError: invalid regular expression flag "x"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Invalid_regexp_flag) | Unknown or unsupported regex flags used. | `/a/x` |
| [SyntaxError: invalid unicode escape in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Unicode escape sequences are invalid or malformed. | `/\u{110000}/u` |
| [SyntaxError: JSON.parse: bad parsing](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) | Invalid JSON string passed to `JSON.parse()`. | `JSON.parse("{")` |
| [SyntaxError: label not found](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label) | A `break` or `continue` statement references a non-existent label. | `break missingLabel;` |
| [SyntaxError: missing : after property id](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_colon) | Object literal missing colon between key and value. | `let obj = {a 1}` |
| [SyntaxError: missing ) after argument list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_paren) | Function call missing closing parenthesis. | `foo(bar;` |
| [SyntaxError: missing ) after condition](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_paren) | Control statement condition missing closing parenthesis. | `if (x > 0 {}` |
| [SyntaxError: missing \] after element list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_bracket) | Array literal missing closing bracket. | `let arr = [1, 2, 3;` |
| [SyntaxError: missing } after function body](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_brace) | Function body missing closing brace. | `function foo() {` |
| [SyntaxError: missing } after property list](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_brace) | Object literal missing closing brace. | `let obj = { a: 1, b: 2` |
| [SyntaxError: missing = in const declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_initializer) | `const` declaration missing initializer. | `const x;` |
| [SyntaxError: missing formal parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_param) | Function parameter missing name. | `function f(,) {}` |
| [SyntaxError: missing name after . operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_property_name) | Member access missing property name. | `obj..prop` |
| [SyntaxError: missing variable name](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_var) | Variable declaration missing identifier. | `let ;` |
| [SyntaxError: negated character class with <br>strings in regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) | Negated character class contains string instead of characters. | `/[^abc]+/` with invalid usage |
| [SyntaxError: new keyword cannot be used with <br>an optional chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) | Cannot use `new` with optional chaining operator `?.`. | `new obj?.method();` |
| [SyntaxError: nothing to repeat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Invalid_regular_expression) | Regex quantifier applied to nothing. | `/+/` |
| [SyntaxError: numbers out of order in {} quantifier](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Invalid_regular_expression) | Quantifier range with min greater than max. | `/a{5,2}/` |
| [SyntaxError: object destructuring requires an <br>assignment target](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) | Destructuring must be part of assignment or declaration. | `({a, b});` alone |
| [SyntaxError: operator expected](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Operator_expected) | Operator missing in expression. | `x 5;` |
| [SyntaxError: parameters list has duplicate element](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Duplicate_param) | Function parameters duplicated. | `function f(x, x) {}` |
| [SyntaxError: private field '#x' must be declared <br>in an enclosing class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_class_fields) | Private class field used without declaration in class. | `this.#x` without `#x` declaration |
| [SyntaxError: private field '#x' must be declared <br>in an enclosing class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_class_fields) | Private field access on wrong class or without declaration. | `other.#x` |
| [SyntaxError: property or method expected](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Property_expected) | Missing property or method name. | `class C { get () {} }` |
| [SyntaxError: redeclaration of formal parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Duplicate_param) | Function parameter redeclared. | `function f(a, a) {}` |
| [SyntaxError: redeclaration of variable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Identifier_after_reserved_word) | Variable declared twice in the same scope. | `let x; let x;` |
| [SyntaxError: return outside function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return) | `return` used outside function body. | `return 5;` at top-level code |
| [SyntaxError: script or module missing semicolon <br>before function declaration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Missing_semicolon) | Semicolon missing before function declaration causes parse error. | `let a = 1 function f() {}` |
| [SyntaxError: strict mode code may not include a <br>with statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Strict_mode) | `with` is disallowed in strict mode. | `'use strict'; with(obj) {}` |
| [SyntaxError: super() must be called before accessing <br>'this' in constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/This_before_super) | Calling `this` before `super()` in subclass constructor. | `constructor() { this.x; super(); }` |
| [SyntaxError: this is not allowed before super() call](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/This_before_super) | Same as above, referencing `this` before `super()`. | `constructor() { this.x = 1; super(); }` |
| [SyntaxError: Unexpected identifier](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_identifier) | Unexpected name/token in code syntax. | `let x = var;` |
| [SyntaxError: Unexpected number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_number) | Unexpected number found in code. | `let x = 5 10;` |
| [SyntaxError: Unexpected string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_string) | Unexpected string literal in code. | `let x = "hello" "world";` |
| [SyntaxError: Unexpected template string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Template string used incorrectly. | ``let x = `hello` `world`;`` |
| [SyntaxError: Unexpected reserved word](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_reserved_word) | Reserved word used as identifier. | `let new = 5;` |
| [SyntaxError: Unexpected token](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Unexpected character/token in code. | `let x = ;` |
| [SyntaxError: Unexpected token ILLEGAL](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token_ILLEGAL) | Illegal character in code. | `let x = "\u0000";` |
| [SyntaxError: Unexpected token, expected "\]"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Closing bracket `]` expected but not found. | `let arr = [1, 2;` |
| [SyntaxError: Unexpected token, expected ")"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Closing parenthesis `)` expected but missing. | `foo(bar;` |
| [SyntaxError: Unexpected token, expected ":" in object literal](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Colon missing in object literal key-value pair. | `let obj = {a 1}` |
| [SyntaxError: Unexpected token, expected ";"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Semicolon missing or unexpected token found. | `let x = 5 let y = 10;` |
| [SyntaxError: Unexpected Unicode escape](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Unexpected_token) | Invalid Unicode escape sequence. | `let x = "\u{XYZ}";` |
| [TypeError: x is not a function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Not_a_function) | Trying to call a non-function value. | `let x = 5; x();` |
| [TypeError: Cannot read properties of undefined/null](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Undefined_prop) | Accessing properties or methods of `undefined` or `null`. | `let x; x.y;` |
| [TypeError: Assignment to constant variable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Const_reassignment) | Attempting to reassign a constant variable declared with `const`. | `const x = 5; x = 10;` |
| [TypeError: Invalid assignment to const 'x'](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Const_reassignment) | Another form of reassignment error for `const`. | `const x = 3; x = 4;` |
| [TypeError: 'super' keyword unexpected here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super) | Using `super` outside class constructor or subclass. | `super();` |
| [URIError: URI malformed](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/URIError) | Malformed URI string passed to URI functions. | `decodeURIComponent('%')` |

---

## JavaScript Warnings (Not always thrown as errors)

| Warning | Description | Example |
|---------|-------------|---------|
| Duplicate parameter names | Using the same parameter name more than once in a function declaration. | `function f(x, x) {}` |
| Implicit global variable assignment | Assigning to undeclared variables creates global variables (in non-strict mode). | `foo = 10;` |
| Deprecated feature usage | Using outdated or deprecated features (e.g. `escape()`). | `escape("Hello")` |
| Octal literals in strict mode | Using legacy octal literals (e.g. `071`) is disallowed in strict mode. | `'use strict'; let x = 071;` |
| Using `with` statement | `with` is disallowed in strict mode due to its confusing scoping. | `'use strict'; with(obj) {}` |
| Non-strict sloppy declarations | Variables declared without `var`, `let`, or `const` in non-strict mode. | `x = 1;` |
| Using deprecated `__proto__` | Directly accessing or assigning `__proto__` is discouraged. | `obj.__proto__ = null;` |

---

✅ This file contains **all** known common JavaScript errors and warnings, with clear descriptions, examples, and MDN references for your easy copy-paste and study.

---

