# 📘 Chapter 11: Mini Projects & Practice

This chapter puts your JavaScript skills to work by helping you build **real-world mini projects**. These hands-on exercises will reinforce everything you've learned—DOM, events, async, modularity, architecture, and more.

---

## 75. Tip Calculator

Build a calculator that takes a bill amount and tip percentage and displays the tip amount and total.

**HTML:**

```html
<input id="bill" placeholder="Bill Amount" />
<input id="tip" placeholder="Tip %" />
<button id="calc">Calculate</button>
<p id="result"></p>
```

**JavaScript:**

```js
const bill = document.getElementById("bill");
const tip = document.getElementById("tip");
const result = document.getElementById("result");

calc.addEventListener("click", () => {
  const billVal = parseFloat(bill.value);
  const tipVal = parseFloat(tip.value);
  if (!billVal || !tipVal) return;
  const tipAmt = (billVal * tipVal) / 100;
  const total = billVal + tipAmt;
  result.textContent = `Tip: ₹${tipAmt.toFixed(2)} | Total: ₹${total.toFixed(2)}`;
});
```

---

## 76. Form Validator

Build a form that validates inputs live (e.g., email, password).

**HTML:**

```html
<form>
  <input id="email" placeholder="Email" />
  <input id="pass" placeholder="Password" />
  <p id="msg"></p>
</form>
```

**JavaScript:**

```js
const email = document.getElementById("email");
const pass = document.getElementById("pass");
const msg = document.getElementById("msg");

email.addEventListener("blur", () => {
  if (!email.value.includes("@")) {
    msg.textContent = "Invalid email format";
  } else {
    msg.textContent = "";
  }
});

pass.addEventListener("input", () => {
  msg.textContent = pass.value.length < 6 ? "Password too short" : "";
});
```

---

## 77. Simple Todo List (localStorage)

Create a basic to-do app with persistence.

**HTML:**

```html
<input id="task" />
<button id="add">Add</button>
<ul id="list"></ul>
```

**JavaScript:**

```js
const taskInput = document.getElementById("task");
const list = document.getElementById("list");
const add = document.getElementById("add");

let tasks = JSON.parse(localStorage.getItem("todos")) || [];

function render() {
  list.innerHTML = "";
  tasks.forEach((task, i) => {
    const li = document.createElement("li");
    li.textContent = task;
    li.onclick = () => {
      tasks.splice(i, 1);
      save();
    };
    list.appendChild(li);
  });
}

function save() {
  localStorage.setItem("todos", JSON.stringify(tasks));
  render();
}

add.addEventListener("click", () => {
  if (taskInput.value) {
    tasks.push(taskInput.value);
    taskInput.value = "";
    save();
  }
});

render();
```

---

## 78. Weather App using Fetch API

Use the OpenWeatherMap API (or mock) to show temperature.

**HTML:**

```html
<input id="city" placeholder="City" />
<button id="fetch">Get Weather</button>
<p id="weather"></p>
```

**JavaScript:**

```js
const city = document.getElementById("city");
const weather = document.getElementById("weather");

fetch.addEventListener("click", async () => {
  try {
    const res = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city.value}&appid=YOUR_KEY&units=metric`);
    const data = await res.json();
    weather.textContent = `${data.name}: ${data.main.temp}°C`;
  } catch {
    weather.textContent = "City not found";
  }
});
```

---

## 79. Quiz Game (DOM + Events)

Cycle through questions and calculate score.

**HTML/JS (Concept):**

```js
const quiz = [
  { q: "2+2", a: ["3", "4"], correct: 1 },
  { q: "Capital of India?", a: ["Mumbai", "Delhi"], correct: 1 }
];

let index = 0, score = 0;
function showQuestion() {
  const q = quiz[index];
  const ui = `${q.q}<br>${q.a.map((ans, i) => `<button onclick='check(${i})'>${ans}</button>`).join('')}`;
  document.body.innerHTML = ui;
}
function check(i) {
  if (i === quiz[index].correct) score++;
  index++;
  if (index < quiz.length) showQuestion();
  else document.body.innerHTML = `Score: ${score}`;
}
showQuestion();
```

---

## 80. Loading Spinner Implementation

**HTML:**

```html
<div id="spinner">Loading...</div>
<div id="data"></div>
```

**JavaScript:**

```js
document.getElementById("spinner").style.display = "block";
setTimeout(() => {
  document.getElementById("spinner").style.display = "none";
  document.getElementById("data").textContent = "Data loaded!";
}, 2000);
```

---

## 81. REST Client with Fetch API

User enters a URL and fetches JSON.

**HTML:**

```html
<input id="url" placeholder="Enter API URL" />
<button id="call">Call API</button>
<pre id="output"></pre>
```

**JavaScript:**

```js
call.addEventListener("click", async () => {
  try {
    const res = await fetch(url.value);
    const data = await res.json();
    output.textContent = JSON.stringify(data, null, 2);
  } catch {
    output.textContent = "Invalid URL or error occurred.";
  }
});
```

---

## 82. Text-to-Image Frontend UI (Mock)

**Concept:** Input + button → simulate image creation

**HTML:**

```html
<input id="prompt" placeholder="Describe image" />
<button id="gen">Generate</button>
<img id="img" />
```

**JavaScript:**

```js
gen.addEventListener("click", () => {
  img.src = `https://placehold.co/300?text=${encodeURIComponent(prompt.value)}`;
});
```

---

## 83. Image Generation Server Basics (Mock API)

Return mock image data from a fake backend:

```js
function getImage(prompt) {
  return new Promise((res) => {
    setTimeout(() => res(`https://placehold.co/200?text=${prompt}`), 1000);
  });
}
```

---

## 84. Error Handling in Frontend (Toast/UI)

**HTML:**

```html
<div id="toast"></div>
```

**JavaScript:**

```js
function showToast(msg) {
  const t = document.getElementById("toast");
  t.textContent = msg;
  t.style.display = "block";
  setTimeout(() => t.style.display = "none", 3000);
}

try {
  throw new Error("Oops!");
} catch (e) {
  showToast(e.message);
}
```

---

## 85. Bonus: JavaScript for the Haters (Critical Thinking Module)

Explore why JS behaves strangely:

* `typeof null === "object"`
* `NaN !== NaN`
* `[] + {}` vs `{}` + \[]
* Hoisting oddities

**Example:**

```js
console.log(typeof null); // "object"
console.log(NaN === NaN); // false
```

---

## ✅ Exercises

1. Add input validation to quiz and weather apps
2. Refactor any project into modular JS structure
3. Show toast messages using dynamic DOM code
4. Use async/await with error handling in at least two apps
5. Use `localStorage` to persist state in two projects
