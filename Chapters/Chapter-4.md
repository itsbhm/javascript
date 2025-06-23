# 📘 Chapter 4: Intermediate JavaScript Features

This chapter explores advanced syntax and powerful capabilities of JavaScript that help you write cleaner, more efficient, and more maintainable code.

---

## 26. Short-Circuiting and Logical Operators

* `&&` returns first falsy, `||` returns first truthy
* Using logical operators for defaults

**Example:**

```js
const user = null;
const defaultUser = user || "Guest"; // "Guest"
const isLoggedIn = true && "Dashboard"; // "Dashboard"
```

---

## 27. Optional Chaining (`?.`) and Nullish Coalescing (`??`)

* Safely accessing nested object properties
* Handling `null` and `undefined` vs falsy values

**Example:**

```js
const user = {
  profile: {
    name: "Shubham"
  }
};
console.log(user.profile?.name); // "Shubham"
console.log(user.settings?.theme); // undefined

let theme = user.settings?.theme ?? "light";
console.log(theme); // "light"
```

---

## 28. Default Parameters

* Assigning defaults to function parameters

**Example:**

```js
function greet(name = "Guest") {
  console.log("Hello, " + name);
}
greet(); // "Hello, Guest"
```

---

## 29. Chaining Methods and Immutability Concepts

* Using multiple array methods
* Returning new arrays instead of mutating originals

**Example:**

```js
const nums = [1, 2, 3, 4, 5];
const result = nums.filter(n => n > 2).map(n => n * 2);
console.log(result); // [6, 8, 10]
```

---

## 30. Value vs Reference

* Primitive vs Non-Primitive assignment behavior

**Example:**

```js
let a = 5;
let b = a;
a = 10;
console.log(b); // 5 (copied by value)

const obj1 = { val: 1 };
const obj2 = obj1;
obj1.val = 5;
console.log(obj2.val); // 5 (referenced)
```

---

## 31. Garbage Collection in JS

* Automatic memory management
* Reachability and memory leaks

**Concepts:**

* Objects are cleaned when no references exist
* Be cautious with event listeners, global variables, closures holding memory

**Example:**

```js
let user = {
  name: "Shubham"
};
user = null; // Eligible for garbage collection
```

---

## ✅ Exercises

1. Use `||` and `&&` to build a conditional greeting system.
2. Use optional chaining to access deep object data safely.
3. Write a function that has two parameters, one with a default.
4. Chain `filter`, `map`, and `reduce` to transform an array.
5. Show how primitive values differ from objects in memory.
