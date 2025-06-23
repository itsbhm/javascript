# 📘 Chapter 7: Asynchronous JavaScript

JavaScript is single-threaded, but asynchronous programming allows us to write non-blocking code. This chapter explores the **event loop**, **callbacks**, **promises**, and `async/await` with practical examples.

---

## 44. Synchronous vs Asynchronous Code

* **Synchronous**: Code runs line by line and blocks the next task.
* **Asynchronous**: Code runs in the background and resumes later.

**Example:**

```js
console.log("Start");
setTimeout(() => console.log("Inside timeout"), 1000);
console.log("End");
```

---

## 45. setTimeout and setInterval

* `setTimeout(callback, delay)` runs once after a delay.
* `setInterval(callback, delay)` runs repeatedly every interval.

**Example:**

```js
setTimeout(() => console.log("Hi after 2s"), 2000);
const interval = setInterval(() => console.log("Every second"), 1000);
```

---

## 46. Callbacks and Callback Hell

* A **callback** is a function passed to another function.
* Nesting multiple callbacks causes readability issues → *callback hell*.

**Example:**

```js
function step1(cb) {
  setTimeout(() => {
    console.log("Step 1");
    cb();
  }, 1000);
}
step1(() => {
  console.log("Step 2");
});
```

---

## 47. Promises – `.then`, `.catch`, `.finally`

* Promises provide cleaner syntax for async tasks.

**Example:**

```js
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve("Data received"), 1000);
  });
};

fetchData()
  .then(res => console.log(res))
  .catch(err => console.error(err))
  .finally(() => console.log("Done"));
```

---

## 48. Promise Combinators

* `Promise.all([])` – Wait for all to finish.
* `Promise.race([])` – First settled promise wins.
* `Promise.allSettled([])` – Wait for all, get results + status.

**Example:**

```js
Promise.all([
  fetch("/api/one"),
  fetch("/api/two")
])
.then(responses => console.log("All done"));
```

---

## 49. Async/Await Syntax

* `async` makes a function return a promise.
* `await` pauses until a promise resolves.

**Example:**

```js
async function getUser() {
  const res = await fetch("/user");
  const data = await res.json();
  console.log(data);
}
getUser();
```

---

## 50. Error Handling in Async/Await

**Example:**

```js
async function fetchData() {
  try {
    const res = await fetch("invalid-url");
    const data = await res.json();
  } catch (err) {
    console.error("Error:", err.message);
  }
}
```

---

## 51. Chaining Promises

Chain `.then()` calls to execute promises in sequence.

**Example:**

```js
fetch("/api/step1")
  .then(res => res.json())
  .then(data => fetch("/api/step2?ref=" + data.id))
  .then(res => res.json())
  .then(final => console.log(final));
```

---

## 52. Microtask vs Macrotask Queue (Concept Only)

* **Microtasks**: `Promises`, `queueMicrotask()`
* **Macrotasks**: `setTimeout`, `setInterval`, DOM events

> Microtasks run immediately after the current task, before rendering or macrotasks.

**Example:**

```js
console.log("script start");
setTimeout(() => console.log("setTimeout"), 0);
Promise.resolve().then(() => console.log("promise"));
console.log("script end");
```

> Output: script start → script end → promise → setTimeout

---

## ✅ Exercises

1. Simulate a delay using `setTimeout` and print steps.
2. Create a countdown using `setInterval`.
3. Rewrite a nested callback example with Promises.
4. Fetch fake JSON using `async/await` and handle errors.
5. Demonstrate the order of microtask vs macrotask with logs.
