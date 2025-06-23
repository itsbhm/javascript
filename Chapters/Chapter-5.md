# 📘 Chapter 5: Error Handling & Debugging

Errors are a natural part of coding. What separates great developers is how well they understand and handle them. In this chapter, we’ll cover **JavaScript’s error model**, **debugging techniques**, and **writing code that fails gracefully.**

---

## 32. `try...catch...finally`

* Catching runtime errors
* Code inside `finally` runs no matter what

**Example:**

```js
try {
  let result = someUndefinedVar + 1;
} catch (error) {
  console.error("Something went wrong:", error.message);
} finally {
  console.log("Execution finished");
}
```

> 💡 `try/catch` only works with **runtime errors**, not syntax errors.

---

## 33. Custom Errors

* Throw your own errors for validation or control

**Example:**

```js
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}

try {
  divide(10, 0);
} catch (e) {
  console.error(e.message);
}
```

---

## 34. The `Error` Object

* Built-in object to handle stack traces and messages
* Types: `Error`, `ReferenceError`, `SyntaxError`, etc.

**Example:**

```js
try {
  JSON.parse("invalid JSON");
} catch (e) {
  console.log(e.name); // SyntaxError
  console.log(e.message);
  console.log(e.stack);
}
```

---

## 35. Debugger Statements

* Halts execution and opens debugger if available

**Example:**

```js
function inspect(value) {
  debugger; // Triggers DevTools pause
  return value * 2;
}
inspect(5);
```

---

## 36. Using DevTools to Debug JS Code

* Open DevTools (F12 or Right Click > Inspect)
* Use **Console**, **Sources**, and **Network** tabs
* Set **breakpoints**, watch variables, and step through code

### Common Tips:

* Use `console.log()` to inspect values
* Use `typeof` and `Array.isArray()` to check types
* Filter logs with `%c` styling:

```js
console.log("%cStyled log", "color: red; font-weight: bold");
```

---

## ✅ Exercises

1. Use `try...catch` to wrap a function that might fail.
2. Throw a custom error if a password is less than 6 characters.
3. Log the name and stack of an error thrown inside `JSON.parse()`.
4. Add `debugger` inside a loop and trace variable value in DevTools.
5. Inspect a page using Chrome DevTools and locate a script error.
