## 🚀 Welcome to JavaScript Functions, Scope & Execution Context

This guide will walk you through the most fundamental concepts in JavaScript, from the basics of writing a function to the deep theory of how JavaScript runs your code.

-----

## 1\. Function Basics

A **function** is a reusable block of code designed to perform a specific task. Think of it as a recipe: you "define" it once, and then you can "call" (or "invoke") it anytime you want to "cook" that dish.

### Defining a Function

This is the "recipe" itself. You use the `function` keyword, give it a name, list its "parameters" (ingredients) in parentheses `()`, and write the "instructions" (body) inside curly braces `{}`.

```javascript
// This is a function "declaration"
function greet(name) {
  // This is the "body" of the function
  console.log("Hello, " + name + "!");
}
```

### Calling a Function

This is the act of "running" the recipe. You use the function's name followed by parentheses `()`.

```javascript
// "Calling" or "invoking" the function
greet("Alice"); // Output: Hello, Alice!
greet("Bob");   // Output: Hello, Bob!
```

### The `return` Keyword

Functions can also send a value *back* to the code that called them. This is done using the `return` keyword. When `return` is hit, the function stops executing and sends back the value.

If you don't use `return`, the function automatically returns a special value: `undefined`.

```javascript
// This function adds two numbers and returns the result
function add(num1, num2) {
  let sum = num1 + num2;
  return sum;
  
  // Any code after the 'return' statement is NOT executed
  console.log("This will never run.");
}

// We can store the returned value in a variable
let result = add(5, 3);
console.log(result); // Output: 8
```

-----

## 2\. More on Params & Arguments

These terms are often confused, but the difference is simple:

  * **Parameters:** The variables listed in the function's definition. They are *placeholders* (like `num1` and `num2`).
  * **Arguments:** The *actual values* you pass into the function when you call it (like `5` and `3`).

### Default Parameters (ES6)

You can provide a default value for a parameter in case an argument isn't provided.

```javascript
// 'Bot' is the default value for 'user'
function registerUser(user = 'Bot') {
  return user + ' is registered';
}

console.log(registerUser('Alice')); // Output: Alice is registered
console.log(registerUser());        // Output: Bot is registered (default value is used)
```

### Rest Parameters (`...`)

The rest parameter syntax (`...`) **gathers an indefinite number of arguments into a single array**.

```javascript
// '...numbers' will gather all passed-in arguments into an array called 'numbers'
function sum(...numbers) {
  let total = 0;
  for (const num of numbers) {
    total += num;
  }
  return total;
}

console.log(sum(1, 2, 3));                 // Output: 6
console.log(sum(1, 2, 3, 4, 5, 100)); // Output: 115
```

### Objects and Arrays as Parameters

You can pass any data type into functions, including objects and arrays. This works via "pass by reference," meaning the function gets a "pointer" to the original object or array in memory.

```javascript
// --- Objects as params ---
function loginUser(userObj) {
  return `The user ${userObj.name} with id ${userObj.id} is logged in`;
}

const user = {
  id: 1,
  name: 'John',
};
console.log(loginUser(user)); // Output: The user John with id 1 is logged in

// --- Arrays as params ---
function getRandom(arr) {
  const randomIndex = Math.floor(Math.random() * arr.length);
  return arr[randomIndex];
}

console.log(getRandom([1, 2, 3, 4, 5])); // Output: (a random number from the array)
```

-----

## 3\. Global & Function Scope

**Scope** defines *where* your variables and functions are accessible in your code.

### Global Scope

A variable declared *outside* of any function is in the **Global Scope**. It can be accessed from *anywhere* in your script.

> **Caution:** Relying on global variables is generally bad practice. It can lead to bugs because any function can change them at any time ("polluting the global scope").

```javascript
let globalVar = "I am everywhere!";

function showGlobal() {
  console.log(globalVar); // Accessible inside the function
}
showGlobal(); // Output: I am everywhere!
```

### Function Scope (Local Scope)

A variable declared *inside* a function is in that function's **Local Scope**. It can *only* be accessed from within that function.

```javascript
function sayHi() {
  let localVar = "I am only inside sayHi";
  console.log(localVar);
}

sayHi(); // Output: I am only inside sayHi

// This will cause an error!
// console.log(localVar); // Uncaught ReferenceError: localVar is not defined
```

-----

## 4\. Block Scope

This was introduced in ES6 (2015) with the `let` and `const` keywords.
A "block" is any code surrounded by curly braces `{...}` (like in an `if` statement or `for` loop).

  * `let` and `const` variables are **Block Scoped**. They only exist within the block they are defined in.
  * `var` variables are **Function Scoped**. They *ignore* blocks.

This is a key reason `let` and `const` are preferred over `var`.

```javascript
// Using var (Function Scoped)
for (var i = 0; i < 3; i++) {
  console.log(i); // 0, 1, 2
}
console.log("After the loop, i is: " + i); // Output: After the loop, i is: 3 (i "leaked" out)

// Using let (Block Scoped)
for (let j = 0; j < 3; j++) {
  console.log(j); // 0, 1, 2
}
// This will cause an error!
// console.log("After the loop, j is: " + j); // Uncaught ReferenceError: j is not defined
// 'j' only existed inside the { } of the loop.
```

-----

## 5\. Nested Scope

You can define functions *inside* other functions. This creates **nested scopes**.

**The Rule:** An inner function can access variables from its *own* scope, its *parent's* scope, and the *global* scope. This is called the **Scope Chain**.

This is also called **Lexical Scope**, meaning scope is determined by *where you wrote the code*.

```javascript
let globalName = "Global";

function outer() {
  let outerName = "Outer";

  function inner() {
    let innerName = "Inner";
    // 'inner' can see all three scopes
    console.log("From Inner: " + innerName);
    console.log("From Outer: " + outerName);
    console.log("From Global: " + globalName);
  }

  inner();

  // This will error! 'outer' cannot see 'innerName'
  // console.log(innerName); 
}

outer();
```

-----

## 6\. Declaration vs. Expression

There are two main ways to create a function, and they have one *major* difference.

### Function Declaration

This is what we've seen so far. It's "declared" with the `function` keyword at the start of the statement.

```javascript
function add(a, b) {
  return a + b;
}
```

  * **Key Feature: Hoisting.** Function declarations are "hoisted" (lifted) to the top of their scope. This means you can *call* the function *before* you've defined it in the code.

<!-- end list -->

```javascript
// This works!
let sum = add(10, 2);
console.log(sum); // Output: 12

function add(a, b) {
  return a + b;
}
```

### Function Expression

This is when you create a function and *assign it to a variable*.

```javascript
// 'subtract' is a variable that holds a function
let subtract = function(a, b) {
  return a - b;
};
```

  * **Key Feature: Not Hoisted.** The `let` or `const` variable is hoisted but is in the "Temporal Dead Zone," meaning you cannot access it before its definition.

<!-- end list -->

```javascript
// This will NOT work!
// let diff = subtract(10, 2); // ReferenceError: Cannot access 'subtract' before initialization

let subtract = function(a, b) {
  return a - b;
};

// You must call it *after* the expression is defined
let diff = subtract(10, 2);
console.log(diff); // Output: 8
```

-----

## 7\. Arrow Functions (ES6)

Arrow functions are a shorter, modern way to write function expressions.

```javascript
// Regular Function Expression
let add = function(a, b) {
  return a + b;
};

// Arrow Function
let addArrow = (a, b) => {
  return a + b;
};

// --- Special Syntax Rules ---

// 1. If it just returns a value, you can drop { } and 'return'
let addShort = (a, b) => a + b;

// 2. If it has only *one* parameter, you can drop ( )
let double = num => num * 2;

console.log(addShort(3, 4)); // Output: 7
console.log(double(5));      // Output: 10
```

**Most Important Difference:** Arrow functions do not have their own `this` keyword. They *inherit* `this` from their surrounding (lexical) scope.

-----

## 8\. Immediately Invoked Function Expressions (IIFE)

An IIFE (pronounced "iffy") is a function that you define and execute *immediately*.

```javascript
(function() {
  let privateVar = "I am safe in here";
  console.log("This function ran immediately!");
  console.log(privateVar);
})();

// This will fail!
// console.log(privateVar); // ReferenceError: privateVar is not defined
```

**Why use this?** Its main purpose was to **create private scope**. Before `let` and `const`, `var` variables would leak to the global scope. Wrapping code in an IIFE kept variables private.

-----

## 9\. Function Challenges

Let's test your knowledge.

### Challenge 1: The Scoping Puzzle

What will be logged to the console?

```javascript
let animal = "dog";

function outer() {
  let animal = "cat"; // <-- This "shadows" the global 'animal'

  function inner() {
    let animal = "tiger";
    console.log(animal); // What logs here?
  }

  inner();
  console.log(animal); // What logs here?
}

outer();
console.log(animal); // What logs here?
```

\<details\>
\<summary\>\<b\>Click for Solution 1\</b\>\</summary\>
\<p\>\<b\>Output:\</b\>\</p\>
\<pre\>
tiger
cat
dog
\</pre\>
\<p\>\<b\>Why:\</b\> \<code\>console.log\</code\> always looks for the variable in the *closest* scope first and works its way out.
\<ol\>
\<li\>\<code\>inner()\</code\> finds \<code\>animal = "tiger"\</code\> in its own scope.\</li\>
\<li\>\<code\>outer()\</code\> finds \<code\>animal = "cat"\</code\> in its own scope.\</li\>
\<li\>The final log is in the global scope, so it finds \<code\>animal = "dog"\</code\>.\</li\>
\</ol\>
\</p\>
\</details\>

-----

## 10\. Execution Context

This is the "theory" part, but it's *essential* for understanding *how* JavaScript works.

The **Execution Context** is the "environment" or "container" that JavaScript creates to manage and execute your code.

This container has two main parts:

1.  **Memory (Variable Environment):** A place in memory for all your variables, functions, and arguments.
2.  **Execution (Thread of Execution):** The part that runs your code one line at a time.

There are two types of Execution Context:

1.  **Global Execution Context (GEC):** The default context, created when your script first loads.
2.  **Function Execution Context (FEC):** Created *every time* a function is *called*.

-----

## 11\. Execution Context In Action

This is the most important part. Every time an Execution Context is created, it happens in two phases:

### Phase 1: Creation Phase (Memory Allocation)

Before *any* code runs, JavaScript *scans* the code to set up memory.

1.  It finds all **Function Declarations** (`function myFunc...`) and stores the *entire function* in memory. **This is Hoisting.**
2.  It finds all variables (`let`, `const`, `var`) and allocates memory for them.
      * `var` variables are initialized as `undefined`.
      * `let` and `const` variables are stored but *not* initialized (they are in the "Temporal Dead Zone" or TDZ).

### Phase 2: Execution Phase

*Now* your code is executed line by line. Assignments happen, and functions are called.

-----

### Example Walkthrough (Using Your Code)

Let's trace this example code:

```javascript
// 1.
const x = 100;
// 2.
const y = 50;
// 3.
function getSum(n1, n2) {
// 4.
  const sum = n1 + n2;
// 5.
  return sum;
// 6.
}
// 7.
const sum1 = getSum(x, y);
// 8.
const sum2 = getSum(10, 5);
// 9.
console.log(sum1, sum2);
```

#### 1\. Global Execution Context (GEC) - Creation Phase

JavaScript scans the file:

  * **Line 1:** Finds `const x`. Allocates memory for `x` as "uninitialized".
  * **Line 2:** Finds `const y`. Allocates memory for `y` as "uninitialized".
  * **Line 3:** Finds `function getSum`. Stores the *entire function* in memory.
  * **Line 7:** Finds `const sum1`. Allocates memory for `sum1` as "uninitialized".
  * **Line 8:** Finds `const sum2`. Allocates memory for `sum2` as "uninitialized".

#### 2\. GEC - Execution Phase

Now the code runs:

  * **Line 1: `const x = 100;`**
      * Assigns `100` to `x`. (Memory: `x` is now `100`).
  * **Line 2: `const y = 50;`**
      * Assigns `50` to `y`. (Memory: `y` is now `50`).
  * **Line 3-6:** This is a declaration. It's skipped because it's already in memory.
  * **Line 7: `const sum1 = getSum(x, y);`**
      * The GEC *pauses*.
      * The `getSum(100, 50)` function is called.
      * A *new* **Function Execution Context (FEC)** is created.

#### 3\. `getSum(100, 50)` FEC - Creation Phase

JavaScript scans the `getSum` function:

  * **Line 3 (Params):** Allocates memory for `n1` and `n2`.
  * **Line 4:** Allocates memory for `const sum` as "uninitialized".

#### 4\. `getSum(100, 50)` FEC - Execution Phase

  * **Line 3:** The arguments are assigned to the parameters. (`n1 = 100`, `n2 = 50`).
  * **Line 4: `const sum = n1 + n2;`**
      * The calculation is done (`100 + 50 = 150`).
      * `150` is assigned to `sum`. (Memory: `sum` is now `150`).
  * **Line 5: `return sum;`**
      * The function returns the value `150`.
  * **This FEC is now destroyed.**

#### 5\. GEC - Execution Phase (Continued)

  * **Line 7: `const sum1 = ...;`**
      * The GEC receives the returned value `150`.
      * `150` is assigned to `sum1`. (Memory: `sum1` is now `150`).
  * **Line 8: `const sum2 = getSum(10, 5);`**
      * The GEC *pauses* again.
      * A *brand new FEC* is created for `getSum(10, 5)`.
      * The same process repeats (`n1=10`, `n2=5`, `sum=15`).
      * That FEC returns `15` and is destroyed.
      * The GEC receives `15` and assigns it to `sum2`. (Memory: `sum2` is now `15`).
  * **Line 9: `console.log(sum1, sum2);`**
      * Prints `150 15` to the console.
  * The script ends. The GEC is destroyed.

-----

## 12\. The Call Stack

So how does JavaScript keep track of all these Execution Contexts? It uses the **Call Stack**.

The Call Stack manages which function is currently running.

  * It follows the **LIFO (Last In, First Out)** principle. (Like a stack of plates).
  * **Push:** When a function is *called*, its new Execution Context is **pushed** onto the *top* of the stack.
  * **Pop:** When a function *returns* (finishes), its Execution Context is **popped** off the top.

JavaScript *only* executes the function that is **at the very top of the stack**.

### Call Stack Visualization

Let's trace this code:

```javascript
function first() {
  console.log('first...');
  second();
}
function second() {
  console.log('second...');
  third();
}
function third() {
  console.log('third...');
}
first();
```

1.  **Script Starts:**
      * `Global EC` is **pushed** onto the stack.
      * **Stack:** `[Global EC]`
2.  **`first()` is called:**
      * `first()` is **pushed** on top. `first()` runs.
      * **Stack:** `[Global EC, first]`
      * **Console:** `first...`
3.  **`second()` is called (from inside `first()`):**
      * `second()` is **pushed** on top. `first()` pauses. `second()` runs.
      * **Stack:** `[Global EC, first, second]`
      * **Console:** `second...`
4.  **`third()` is called (from inside `second()`):**
      * `third()` is **pushed** on top. `second()` pauses. `third()` runs.
      * **Stack:** `[Global EC, first, second, third]`
      * **Console:** `third...`
5.  **`third()` finishes:**
      * `third()` is **popped** off the stack.
      * **Stack:** `[Global EC, first, second]`
      * `second()` resumes.
6.  **`second()` finishes:**
      * `second()` is **popped** off the stack.
      * **Stack:** `[Global EC, first]`
      * `first()` resumes.
7.  **`first()` finishes:**
      * `first()` is **popped** off the stack.
      * **Stack:** `[Global EC]`
8.  **Script Ends:**
      * `Global EC` is **popped** off the stack.
      * **Stack:** `[]` (Empty)

**Stack Overflow:** If a function calls itself over and over without stopping (bad recursion), the stack will keep growing `[GEC, fn, fn, fn, ...]` until it runs out of memory and crashes. This is a **"Stack Overflow"** error.