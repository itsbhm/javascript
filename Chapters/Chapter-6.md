# 📘 Chapter 6: DOM & Events

JavaScript allows us to interact with the structure and content of HTML documents via the **DOM (Document Object Model)** and respond to user interactions using **events**. This chapter gives you a strong working knowledge of DOM APIs and event handling.

---

## 36. What is the DOM?

* The DOM is the browser’s representation of an HTML document.
* It is a tree of nodes created from your HTML.
* JavaScript can use the DOM to read, change, create, or delete HTML elements.

**Example:**

```html
<body>
  <h1 id="main">Title</h1>
</body>
```

```js
const heading = document.getElementById("main");
heading.innerText = "Updated Title";
```

---

## 37. Selecting Elements

* `getElementById`, `getElementsByClassName`
* `querySelector`, `querySelectorAll`

**Example:**

```js
const btn = document.querySelector("button");
const links = document.querySelectorAll("a");
```

---

## 38. Modifying Content and Attributes

* `innerText`, `textContent`, `innerHTML`
* `setAttribute`, `getAttribute`, `removeAttribute`

**Example:**

```js
const img = document.querySelector("img");
img.setAttribute("src", "logo.png");
```

---

## 39. Event Listeners and Event Objects

* `.addEventListener()`
* Event types: `click`, `submit`, `keydown`, etc.
* Accessing `event.target`, `event.type`

**Example:**

```js
btn.addEventListener("click", function (e) {
  console.log("Button clicked:", e.target);
});
```

---

## 40. Handling Forms and Inputs with JS

* Prevent default form behavior
* Read values from inputs

**Example:**

```js
const form = document.querySelector("form");
form.addEventListener("submit", function (e) {
  e.preventDefault();
  const username = document.querySelector("#username").value;
  console.log("Submitted username:", username);
});
```

---

## 41. Event Delegation

* Attach a single listener to a parent instead of multiple children
* Use `event.target` to determine the source

**Example:**

```js
const ul = document.querySelector("ul");
ul.addEventListener("click", function (e) {
  if (e.target.tagName === "LI") {
    e.target.classList.toggle("active");
  }
});
```

---

## 42. DOM Performance Tips

* Minimize reflows and repaints
* Batch DOM reads and writes
* Use `documentFragment` for large inserts

**Example:**

```js
const frag = document.createDocumentFragment();
for (let i = 0; i < 100; i++) {
  const li = document.createElement("li");
  li.textContent = `Item ${i}`;
  frag.appendChild(li);
}
document.querySelector("ul").appendChild(frag);
```

---

## 43. MutationObserver (Intro Only)

* Allows observing changes to the DOM tree
* Useful for reacting to UI updates, async insertions

**Example:**

```js
const observer = new MutationObserver(mutations => {
  console.log("DOM changed!", mutations);
});

observer.observe(document.body, { childList: true, subtree: true });
```

---

## ✅ Exercises

1. Select all links and highlight them on hover.
2. Create a dynamic form validation that prevents empty submission.
3. Use event delegation to handle clicks on a list of items.
4. Use `setAttribute` to change the background image on a div.
5. Observe changes to an element using `MutationObserver`.
