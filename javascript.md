
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

Perfect 👌 That’s a clear format.
So for each concept, I’ll do this flow:

1. **What it is**
2. **Code examples**
3. **Why it’s used (vs alternatives)**

Let’s re-do **Variables and Constants (`var`, `let`, `const`)** in that exact structure.

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
