# 📘 Chapter 3: Functions Deep Dive

This chapter focuses on how functions truly work in JavaScript — beyond declarations and calls. You'll understand functions as first-class citizens, master higher-order functions, explore callbacks, and unlock the power of closures.

---

## 21. Callback Functions

* What is a callback function?
* Why use callbacks?
* Synchronous vs Asynchronous callbacks

**Example:**

```js
function greetUser(name, callback) {
  console.log("Hello " + name);
  callback();
}

greetUser("Shubham", function() {
  console.log("Welcome to the dashboard.");
});
```

---

## 22. Higher-Order Functions

* Functions that take or return other functions
* Array method examples using HOF: `map`, `filter`, `reduce`

**Example:**

```js
function multiplyBy(factor) {
  return function (number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
console.log(double(5)); // 10
```

---

## 23. Closures

* Lexical scope recap
* What is a closure?
* Why closures are useful (encapsulation, factories, private data)

**Example:**

```js
function outer() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

const counter = outer();
console.log(counter()); // 1
console.log(counter()); // 2
```

---

## 24. Immediately Invoked Function Expressions (IIFE)

* Definition and syntax
* Use cases: isolation, one-time logic, avoiding global scope

**Example:**

```js
(function () {
  console.log("This runs immediately!");
})();
```

---

## 25. Function Execution Context

* Memory and code phase
* Scope chain
* Visualizing the call stack

**Example:**

```js
function one() {
  two();
  console.log("one");
}
function two() {
  console.log("two");
}
one();
```

> Output: two → one

---

## ✅ Exercises

1. Write a function that accepts another function and calls it.
2. Use a higher-order function to triple every number in an array.
3. Create a closure-based counter with reset and increment methods.
4. Write an IIFE that logs a secret value.
5. Trace the order of calls in nested functions and explain the stack.
