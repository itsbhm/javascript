# 📘 Chapter 8: JavaScript Architecture

Modern JavaScript projects demand scalable, modular, and maintainable code. In this chapter, you’ll learn how to structure your code and use ES Modules, loading strategies, environment-based builds, and the basics of bundlers.

---

## 53. Script Loading – `defer` vs `async`

* `defer`: loads in parallel, executes after HTML parsing
* `async`: loads in parallel, executes immediately when ready

**Example:**

```html
<script src="script.js" defer></script>
<script src="script.js" async></script>
```

> ⚠️ Use `defer` when script depends on DOM; avoid `async` unless safe

---

## 54. ES Modules (import/export)

* Use `export` to expose variables/functions
* Use `import` to include from other files
* Requires `type="module"` in script tag

**Example:**

```js
// math.js
export const add = (a, b) => a + b;

// main.js
import { add } from './math.js';
console.log(add(2, 3));
```

```html
<script type="module" src="main.js"></script>
```

---

## 55. Project File Organization

Split responsibilities into folders:

```
src/
├── components/
├── utils/
├── services/
├── pages/
├── styles/
└── index.js
```

* Separate concerns for logic, UI, and assets

---

## 56. Writing Modular JavaScript Code

* Each module does **one thing**
* Avoid large files and global scope
* Use named exports + organized folder structure

**Example:**

```js
// utils/math.js
export function square(n) {
  return n * n;
}

// app.js
import { square } from './utils/math.js';
```

---

## 57. Bundlers (Vite/Webpack) and Environment Variables

* Bundlers package all JS/CSS/assets into production files
* Popular tools: **Vite**, **Webpack**, **Parcel**
* Use `.env` for app configuration

**Example – .env:**

```
VITE_API_URL=https://api.example.com
```

**Access in JS:**

```js
console.log(import.meta.env.VITE_API_URL);
```

---

## 58. Code Splitting and Lazy Loading Basics

* Reduce load time by loading parts only when needed
* Split by route, component, or logic

**Conceptual Example:**

```js
const loadModule = async () => {
  const { someUtil } = await import('./utils/heavy.js');
  someUtil();
};
```

---

## ✅ Exercises

1. Add `type="module"` in a script and import from another file.
2. Design a folder structure for a shopping cart app.
3. Set up a simple `.env` and use it with Vite.
4. Use dynamic `import()` to load a file on a button click.
5. Compare `async`, `defer`, and normal script execution.
