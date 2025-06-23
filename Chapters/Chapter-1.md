# 📘 Chapter 1: JavaScript Fundamentals

Welcome to your first step into modern JavaScript! This chapter lays the groundwork you need to understand how JavaScript runs, how it interacts with web pages, and how to write and structure your first bits of real code.

---

## 1. What is JavaScript?

* History, Usage, Integration with HTML/CSS
* Adding JS to HTML (`<script>` tag, inline, external)

**Example:**

```html
<button onclick="alert('Hello!')">Click Me</button>
```

```html
<script>
  console.log("Hello from inline script");
</script>
```

```html
<script src="script.js"></script>
```

---

## 2. Code Execution and Environment

* Interpreters, Engines, Browsers vs Node.js
* Execution Context, Call Stack, Memory Heap

**Example:**

```js
console.log("Executed!");
```

---

## 3. Variables and Data Types

* `var`, `let`, `const`
* Primitive Types: String, Number, Boolean, Undefined, Null, Symbol

**Example:**

```js
let name = "Shubham";
const age = 25;
var score = 90;
```

---

## 4. Type Conversion and Coercion

* `parseInt`, `parseFloat`, `Number()`, `String()`, `Boolean()`
* Implicit coercion

**Example:**

```js
Number("5"); // 5
"5" + 1; // "51"
"5" - 1; // 4
```

---

## 5. Operators and Expressions

* Arithmetic, Assignment, Comparison
* Logical operators (`&&`, `||`, `!`)
* Ternary Operator

**Example:**

```js
const age = 18;
const status = age >= 18 ? "Adult" : "Minor";
```

---

## 6. Control Flow

* `if`, `else`, `else if`
* `switch` statement
* Truthy and Falsy values

**Example:**

```js
if (true) {
  console.log("It runs!");
} else {
  console.log("It doesn't run.");
}
```

---

## 7. Loops and Iteration

* `for`, `while`, `do-while`
* `break`, `continue`
* Looping over arrays and strings

**Example:**

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

---

## 8. Functions

* Function Declaration vs Expression
* Arrow Functions
* Parameters, Arguments, Return

**Example:**

```js
function greet(name) {
  return "Hello, " + name;
}
```

---

## 9. Scope and Hoisting

* Global, Function, Block Scope
* Variable Hoisting Rules

**Example:**

```js
function showScope() {
  let inside = "block";
  console.log(inside);
}
showScope();
```

---

## 10. Strict Mode

* `'use strict'` explanation and importance

**Example:**

```js
"use strict";
undeclaredVar = 5; // ReferenceError
```

---

## ✅ Exercises

1. Write a function to return whether a number is even or odd using ternary.
2. Create a loop that prints all even numbers from 1 to 20.
3. Demonstrate both `let` and `var` in a block to show scope difference.
4. Write a switch statement that logs day names from day numbers (0–6).
5. Try converting a string to number using both implicit and explicit methods.
