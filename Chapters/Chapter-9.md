# 📘 Chapter 9: Object-Oriented JavaScript (OOP)

Object-Oriented Programming (OOP) in JavaScript enables code reuse, abstraction, and structure through **objects**, **classes**, and **prototypes**. This chapter focuses on using OOP features effectively in JavaScript.

---

## 59. Objects & Prototypes

* Everything in JS is based on objects
* Each object has an internal `[[Prototype]]` (accessed via `__proto__` or `Object.getPrototypeOf()`)
* Inheritance is prototype-based in JavaScript

**Example:**

```js
const animal = {
  speak() {
    console.log("Animal speaks");
  }
};

const dog = Object.create(animal);
dog.speak(); // Animal speaks
```

---

## 60. Constructor Functions

* The traditional way to create objects before ES6 classes
* Use `new` keyword to create instances

**Example:**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log(`Hi, I’m ${this.name}`);
};

const user = new Person("Shubham", 25);
user.greet();
```

---

## 61. ES6 Classes and `extends`

* Introduced in ES6
* Syntactic sugar over prototype-based inheritance

**Example:**

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const tommy = new Dog("Tommy");
tommy.speak(); // Tommy barks.
```

---

## 62. Encapsulation, Inheritance, and Polymorphism

* **Encapsulation**: Hide internal state and expose only necessary parts
* **Inheritance**: Reuse code from a parent class
* **Polymorphism**: Redefine method behavior in child class

**Example – Polymorphism:**

```js
class Shape {
  area() {
    return 0;
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }
  area() {
    return Math.PI * this.radius ** 2;
  }
}
```

---

## 63. Static Methods & Properties

* Belong to the class itself, not instances
* Used for utility methods

**Example:**

```js
class MathHelper {
  static square(n) {
    return n * n;
  }
}

console.log(MathHelper.square(5)); // 25
```

---

## 64. Private Fields and Methods

* Introduced in ES2022
* Use `#` prefix to declare private members

**Example:**

```js
class Counter {
  #count = 0;
  increment() {
    this.#count++;
    return this.#count;
  }
}

const c = new Counter();
console.log(c.increment()); // 1
// console.log(c.#count); // Error
```

---

## ✅ Exercises

1. Create a `Book` class with `title`, `author`, and a `describe()` method.
2. Create a base `Shape` class and override `area()` in subclasses.
3. Use a static method to compare two values.
4. Use a constructor function to make multiple user objects.
5. Implement a counter with a private field.
