# 📘 Chapter 2: Working with Data

This chapter dives into JavaScript's ability to **store**, **manipulate**, and **work with data** using strings, numbers, booleans, arrays, objects, and other powerful data structures.

---

## 11. Strings and String Methods

* Concatenation, Template Literals
* Common String Methods: `slice`, `substring`, `replace`, `includes`, `indexOf`, `split`

**Example:**

```js
const name = "Shubham";
console.log("Hello " + name); // Concatenation
console.log(`Hello ${name}`); // Template literal
console.log(name.slice(0, 3)); // "Shu"
```

---

## 12. Numbers and Math

* Dealing with floats and integers
* `Math` object: `floor`, `ceil`, `round`, `abs`, `random`

**Example:**

```js
let score = 9.4;
console.log(Math.round(score)); // 9
console.log(Math.random()); // 0.0 - 1.0
```

---

## 13. Booleans, Comparisons, and Equality

* Truthy and Falsy
* Comparison Operators: `==`, `===`, `!=`, `!==`

**Example:**

```js
const isAdult = age >= 18;
console.log(Boolean("hello")); // true
console.log(Boolean("")); // false
console.log(5 == "5"); // true
console.log(5 === "5"); // false
```

---

## 14. Arrays

* Creating Arrays
* Accessing Elements
* Modifying Arrays: `push`, `pop`, `shift`, `unshift`, `splice`, `slice`

**Example:**

```js
let fruits = ["apple", "banana", "orange"];
fruits.push("mango");
console.log(fruits[0]); // apple
```

---

## 15. Array Advanced Methods

* Iterating with `for`, `for...of`, `forEach`
* `map`, `filter`, `reduce`, `find`, `some`, `every`
* `sort`, `reverse`, `flat`, `fill`, `join`

**Example:**

```js
let nums = [1, 2, 3, 4];
let doubled = nums.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8]
```

---

## 16. Objects

* Creating and Accessing Properties
* Dot vs Bracket Notation
* Looping with `for...in`, `Object.keys()`, `Object.values()`

**Example:**

```js
const person = {
  name: "Shubham",
  age: 25
};
console.log(person.name);
```

---

## 17. Destructuring

* Array Destructuring
* Object Destructuring with Defaults

**Example:**

```js
const [a, b] = [1, 2];
const { name, age } = person;
```

---

## 18. Spread and Rest Operators

* Spread: Arrays, Objects, Function Calls
* Rest: Function Parameters

**Example:**

```js
const numbers = [1, 2, 3];
const allNumbers = [...numbers, 4];

function sum(...args) {
  return args.reduce((a, b) => a + b);
}
```

---

## 19. Dates and Times

* `Date` object basics
* Getting & setting time values

**Example:**

```js
const now = new Date();
console.log(now.getFullYear());
console.log(now.toLocaleDateString());
```

---

## 20. The `this` Keyword

* Global context vs Function context
* Arrow Functions and `this`

**Example:**

```js
const user = {
  name: "Shubham",
  greet() {
    console.log(`Hi, I’m ${this.name}`);
  }
};
user.greet();
```

---

## ✅ Exercises

1. Create a string variable and manipulate it using at least 3 string methods.
2. Use `Math.random()` to simulate a dice roll.
3. Write a function that accepts an array of numbers and returns only the even ones.
4. Create an object and use both dot and bracket notation to access its properties.
5. Use destructuring to extract values from an array and object.
6. Write a function using rest parameters to return the product of all arguments.
7. Print today’s date in local format.
8. Show the difference of `this` in a regular vs arrow function.
