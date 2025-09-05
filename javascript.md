
---

# JavaScript 

### 1. Core Language Fundamentals

* Variables and Constants (`var`, `let`, `const`)
* Data Types (Primitive: string, number, boolean, null, undefined, symbol, bigint)
* Type Conversion & Type Coercion
* Operators (arithmetic, comparison, logical, assignment, ternary)
* Expressions vs Statements

---

### 2. Control Flow & Logic

* Conditional Statements (`if`, `else if`, `switch`)
* Loops (`for`, `while`, `do…while`, `for…of`, `for…in`)
* Loop Control (`break`, `continue`)

---

### 3. Functions & Execution

* Function Declarations vs Function Expressions
* Arrow Functions
* Default & Rest Parameters
* Return Values
* Scope (block, function, global)
* Closures
* Higher-Order Functions (functions as arguments/return values)
* Recursion
* The `this` keyword
* Call, Apply, Bind

---

### 4. Objects & Arrays

* Object Literals, Properties & Methods
* Accessing Properties (dot notation, bracket notation)
* Object Methods (`Object.keys`, `Object.values`, `Object.entries`, `Object.assign`)
* Arrays (creation, indexing, iteration)
* Array Methods (`map`, `filter`, `reduce`, `forEach`, `find`, `some`, `every`, `sort`)
* Destructuring (objects & arrays)
* Spread & Rest Operators

---

### 5. DOM & Browser Interaction

* Document Object Model (DOM) Overview
* Selecting Elements (`getElementById`, `querySelector`, etc.)
* Modifying Content & Attributes (`innerHTML`, `textContent`, `setAttribute`)
* Styling via JS (`style`, class manipulation)
* Creating & Removing Elements (`createElement`, `append`, `remove`)
* Events & Event Listeners
* Event Bubbling & Delegation
* Forms & Input Handling
* Browser APIs (LocalStorage, SessionStorage, Geolocation, Clipboard, Notifications, Canvas, Audio/Video)

---

### 6. Error Handling & Debugging

* `try…catch…finally`
* Throwing Errors (`throw new Error`)
* Custom Error Objects
* Debugging Tools (console methods, breakpoints, debugger)

---

### 7. Asynchronous JavaScript

* Event Loop & Call Stack
* `setTimeout`, `setInterval`
* Callbacks
* Promises (creation, chaining, error handling)
* `async / await`
* Fetch API (AJAX requests)
* JSON Handling
* Web APIs (XHR, WebSockets, APIs integration)

---

### 8. Object-Oriented Programming (OOP) in JS

* Constructor Functions
* Prototypes & Prototype Chain
* Classes (`class`, `constructor`, methods)
* Inheritance (`extends`, `super`)
* Encapsulation & Private Fields (`#field`)
* Static Methods
* Object.create & Factory Functions

---

### 9. Functional Programming in JS

* Pure Functions
* Immutability
* Composition
* Currying & Partial Application
* Higher-Order Array Methods revisited

---

### 10. Advanced JavaScript Concepts

* Execution Context & Call Stack
* Hoisting (variables & functions)
* Temporal Dead Zone
* Closures in Depth
* The `this` Binding Rules
* Prototype Chain & Inheritance Mechanisms
* ES6+ Modules (`import`, `export`)
* Garbage Collection & Memory Management

---

### 1. Core Language Fundamentals

* Variables and Constants (`var`, `let`, `const`)

---

# 🔑 JavaScript Variables and Constants

---

## 1. `var`
* The **old way** of declaring variables (before ES6).
* **Function-scoped**, not block-scoped.
* Can be **redeclared** and **reassigned**.
* Hoisted to the top with `undefined`.
### Example:
```js
var name = "Alice";
var name = "Bob"; // redeclaration allowed
console.log(name); // "Bob"
```
```js
if (true) {
  var x = 10; 
}
console.log(x); // ✅ 10 (escapes block)
```
* **Today:** Rarely used, only for **legacy codebases**.
* **Problem:** Not block-scoped → causes bugs.
* **Alternative:** Prefer `let` or `const`.
---

## 2. `let`
* Introduced in **ES6 (2015)**.
* **Block-scoped** (only accessible inside `{}`).
* Can be reassigned, but **cannot be redeclared** in the same scope.
### Example:
```js
let age = 20;
age = 21; // ✅ can reassign
// let age = 25; ❌ Error (no redeclaration in same block)

if (true) {
  let y = 50;
  console.log(y); // ✅ 50
}
// console.log(y); ❌ Error (block-scoped)
```
* Safer than `var` → doesn’t “leak” out of blocks.
* Use `let` if the value **will change** later.
* Compared to `const`: choose `let` when you **need reassignment**.
---

## 3. `const`
* Also introduced in **ES6**.
* **Block-scoped**.
* Must be **initialized immediately**.
* Cannot be reassigned.
* Objects/arrays can still be modified (the reference is constant, not the content).
### Example:
```js
const PI = 3.14159;
// PI = 3.14; ❌ Error

const numbers = [1, 2, 3];
numbers.push(4); // ✅ allowed (modifying contents)
console.log(numbers); // [1, 2, 3, 4]
```
* Prevents accidental reassignment.
* Makes code **more predictable**.
* Best default choice: use `const` unless you know you’ll reassign.
---
## 🔥 Summary:
* **Use `const` by default** → for safety.
* **Use `let` when reassignment is needed**.
* **Avoid `var`** → only for legacy compatibility.
---

---

# 🔑 JavaScript Data Types
* **Primitive Types** (simple, immutable values)
* **Reference Types** (objects, arrays, functions, etc.)
 **primitives**
 
## 1. **String**
### What it is:
* A sequence of characters (text).
* Written inside quotes (`' '`, `" "`, or `` ` ` ``).
### Example:
```js
let name = "Alice";    // double quotes
let city = 'Nairobi';  // single quotes
let message = `Hello, ${name}`; // template literal (with variables)
```
* Strings are for **text values**.
* Template literals (`` ` ``) are preferred when embedding variables or writing multi-line text.
* Alternatives: numbers (for math), booleans (for true/false).
---

## 2. **Number**
* Represents **both integers and decimals** (no separate int/float types).
* Can also represent special values like `Infinity`, `-Infinity`, `NaN` (Not-a-Number).
### Example:
```js
let age = 25;
let price = 19.99;
console.log(10 / 0); // Infinity
console.log("abc" * 2); // NaN
```
* Numbers are for math & calculations.
* Alternative: `BigInt` (for very large integers).
---

## 3. **Boolean**
* Represents **true/false values**.
* Often used in conditions and logic.
### Example:
```js
let isOnline = true;
let isLoggedIn = false;

if (isOnline) {
  console.log("User is online");
}
```
* Used in **control flow (if/else, loops, comparisons)**.
* Alternative: `0/1` or `"yes/no"` but booleans are clearer.
---

## 4. **Null**
* Represents **intentional absence of value**.
* You set it yourself when you want to say “nothing here.”
### Example:
```js
let user = null; // no user yet
```
* Use `null` when you **know** a value should be empty.
* Alternative: `undefined` (but that usually means “not assigned yet”).
---

## 5. **Undefined**
* Means a variable was declared but **not assigned a value**.
* Default value for uninitialized variables.
### Example:
```js
let name;
console.log(name); // undefined
```
* Used by JavaScript itself to mean “missing value.”
* Alternative: `null` (intentional absence).
---

## 6. **Symbol** (ES6)
* A **unique, immutable identifier**.
* Often used as keys in objects to avoid naming conflicts.
### Example:
```js
const id1 = Symbol("id");
const id2 = Symbol("id");

console.log(id1 === id2); // false (always unique)
```
* Safer than strings when creating object keys.
* Alternative: strings (but they can clash).
---

## 7. **BigInt** (ES2020)
* Represents **integers larger than `Number.MAX_SAFE_INTEGER` (2^53 - 1)**.
* Created by adding `n` at the end of a number.
### Example:

```js
const big = 123456789012345678901234567890n;
console.log(big + 1n); // works fine
```
* Use BigInt when dealing with **huge numbers** (cryptography, financial apps).
* Alternative: `Number`, but it loses precision after 2^53.
---

## ⚡ Summary 

| Type      | Example                 | Use Case                     |
| --------- | ----------------------- | ---------------------------- |
| String    | `"Hello"`, `'Hi'`       | Text, messages               |
| Number    | `42`, `3.14`            | Math, calculations           |
| Boolean   | `true`, `false`         | Logic, conditions            |
| Null      | `null`                  | Intentional empty value      |
| Undefined | `let x;`                | Missing/unset variable       |
| Symbol    | `Symbol("id")`          | Unique keys, avoid conflicts |
| BigInt    | `12345678901234567890n` | Very large integers          |

---
