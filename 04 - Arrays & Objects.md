## Arrays & Objects

In JavaScript, **Arrays** and **Objects** are the two most important data structures. They let you store collections of data.

  * An **Array** is an **ordered list** of items. Think of a shopping list or a numbered list of lockers. The *order* matters.
  * An **Object** is an **unordered collection** of properties, stored as **key-value pairs**. Think of a dictionary or a student ID card. You look up a "key" (like "Name") to find its "value" (like "Alice").

-----

## 📦 Arrays

An array is a special variable that can hold more than one value at a time, in a specific order.

### Creating Arrays

The most common way is using the **array literal** syntax, which is just a set of square brackets `[]`.

```javascript
// Creates an empty array
const emptyArray = [];

// Creates an array of strings
const fruits = ["Apple", "Orange", "Banana"];

// Creates an array of numbers
const numbers = [10, 50, 200];

// An array can hold different data types (though it's often cleaner to keep them the same)
const mixed = ["hello", 100, true, null];
```

#### Accessing Array Items (0-Based Indexing)

This is the most important concept for beginners: **Arrays are 0-indexed**. This means the *first* item is at index `0`, the second at index `1`, and so on.

You access items using square brackets `[index]`.

```javascript
const fruits = ["Apple", "Orange", "Banana"];

console.log(fruits[0]); // Output: "Apple"
console.log(fruits[1]); // Output: "Orange"
console.log(fruits[2]); // Output: "Banana"
console.log(fruits[3]); // Output: undefined (this index doesn't exist)
```

#### Finding the Length

The `.length` property tells you how many items are in the array.

```javascript
const fruits = ["Apple", "Orange", "Banana"];
console.log(fruits.length); // Output: 3
```

> **Key Tip:** To get the **last** item in any array, you use `array[array.length - 1]`.
>
>   * `fruits.length` is 3.
>   * The last index is 2.
>   * So, `fruits[3 - 1]` (which is `fruits[2]`) gets you "Banana".

-----

### Basic Array Methods

"Methods" are built-in functions that you can run *on* an array using a dot (`.`).

> **Important:** Pay attention to whether a method **mutates** (changes the original array) or returns a new one.

#### Mutating Methods (They change the original array)

  * **`push()`**: Adds one or more items to the **end** of the array.
    ```javascript
    const colors = ["Red", "Green"];
    colors.push("Blue");
    // colors is now ["Red", "Green", "Blue"]
    ```
  * **`pop()`**: Removes the **last** item from the array.
    ```javascript
    const colors = ["Red", "Green", "Blue"];
    colors.pop();
    // colors is now ["Red", "Green"]
    ```
  * **`unshift()`**: Adds one or more items to the **beginning** of the array.
    ```javascript
    const colors = ["Red", "Green"];
    colors.unshift("Yellow");
    // colors is now ["Yellow", "Red", "Green"]
    ```
  * **`shift()`**: Removes the **first** item from the array.
    ```javascript
    const colors = ["Yellow", "Red", "Green"];
    colors.shift();
    // colors is now ["Red", "Green"]
    ```

#### Non-Mutating Methods (They return a new array)

  * **`slice()`**: Returns a *new* array, copying a "slice" of the old one. It takes `(startIndex, endIndex)`.
      * `startIndex`: The index to start copying from (inclusive).
      * `endIndex`: The index to stop copying *before* (exclusive).
    <!-- end list -->
    ```javascript
    const animals = ["Ant", "Bison", "Camel", "Duck", "Elephant"];

    // Get items from index 2 ("Camel") up to (but not including) index 4 ("Elephant")
    const middleAnimals = animals.slice(2, 4);

    // console.log(middleAnimals); // Output: ["Camel", "Duck"]
    // console.log(animals);     // Output: ["Ant", "Bison", "Camel", "Duck", "Elephant"] (original is unchanged!)
    ```

#### Other Useful Methods

  * **`indexOf()`**: Returns the *first* index where a given element is found (or `-1` if not found).
    ```javascript
    const names = ["Alice", "Bob", "Charlie", "Bob"];
    console.log(names.indexOf("Bob")); // Output: 1
    console.log(names.indexOf("David")); // Output: -1
    ```

-----

### Nesting, Concat & Spread Operator

#### Nesting (Arrays inside Arrays)

You can put arrays inside other arrays. This is great for creating grids, game boards, or matrices.

```javascript
// A 3x3 tic-tac-toe board
const board = [
  ['X', 'O', 'X'], // Row 0
  ['O', 'X', 'O'], // Row 1
  ['X', 'O', 'O']  // Row 2
];

// How to get the middle 'X'?
// 1. Get the row at index 1: board[1]  (which is ['O', 'X', 'O'])
// 2. Get the item at index 1 from that row: board[1][1]

console.log(board[1][1]); // Output: 'X'
```

#### `concat()` (The "Old Way" to Combine)

The `concat()` method joins two or more arrays and returns a *new* array.

```javascript
const arr1 = ["a", "b", "c"];
const arr2 = ["d", "e", "f"];
const arr3 = arr1.concat(arr2);

// console.log(arr3); // Output: ["a", "b", "c", "d", "e", "f"]
// arr1 and arr2 are unchanged.
```

#### Spread Operator (`...`) (The "New Way")

The spread operator `...` is a modern, powerful, and clean way to "spread" the elements of one array into a new one.

  * **Use 1: Copying an array**

    ```javascript
    const original = ["a", "b", "c"];
    const copy = [...original]; // This is a new array, not a reference!
    ```

  * **Use 2: Combining arrays (the new `concat`)**

    ```javascript
    const arr1 = ["a", "b"];
    const arr2 = ["c", "d"];
    const newArr = [...arr1, ...arr2, "e", "f"];

    // console.log(newArr); // Output: ["a", "b", "c", "d", "e", "f"]
    ```

-----

### ✍️ Array Challenge

**Task:** Manage a simple "To-Do" list.

1.  Create an array `todos` with two tasks: "Learn JavaScript" and "Do laundry".
2.  Add "Buy groceries" to the *end* of the list.
3.  Remove "Learn JavaScript" from the *start* of the list.
4.  Log the final `todos` array.

**Solution:**

```javascript
// 1. Create array
const todos = ["Learn JavaScript", "Do laundry"];

// 2. Add to end
todos.push("Buy groceries");

// 3. Remove from start
todos.shift();

// 4. Log the result
console.log(todos); // Output: ["Do laundry", "Buy groceries"]
```

-----

## 🧑‍💻 Objects

An object is a collection of related data and/or functionality, stored as **key-value pairs**.

### Object Literals

This is the most common way to create an object, using curly braces `{}`.

```javascript
// An object representing a car
const car = {
  // key: value
  make: "Toyota",
  model: "Camry",
  year: 2022,
  isElectric: false,
  // A value can also be an array
  features: ["Bluetooth", "Backup Camera", "Sunroof"],
  // A value can even be another object
  owner: {
    name: "John Doe",
    age: 30
  }
};
```

#### Accessing Object Properties

You have two ways to get data out of an object.

  * **1. Dot Notation (The common way)**
    You use this when you know the exact name of the key.

    ```javascript
    console.log(car.model); // Output: "Camry"
    console.log(car.features[0]); // Output: "Bluetooth" (Accessing array inside object)
    console.log(car.owner.name); // Output: "John Doe" (Accessing nested object)
    ```

  * **2. Bracket Notation (The flexible way)**
    You *must* use this when the key is a variable or contains spaces/special characters.

    ```javascript
    // Using a key with a space (not possible with dot notation)
    const person = {
      "first name": "Jane"
    };
    console.log(person["first name"]); // Output: "Jane"

    // Using a variable to access a key
    const myKey = "make";
    console.log(car[myKey]); // Output: "Toyota" (Same as car.make)
    ```

#### Adding and Modifying Properties

You can add new key-value pairs or update existing ones at any time.

```javascript
const person = {
  name: "Alice"
};

// 1. Update an existing property
person.name = "Alice Smith";

// 2. Add a new property
person.age = 25;
person.email = "alice@example.com";

// person is now { name: "Alice Smith", age: 25, email: "alice@example.com" }

// You can also remove a property
delete person.email;
// person is now { name: "Alice Smith", age: 25 }
```

-----

### Object Spread Operator & Methods

#### Spread Operator (`...`) (for Objects)

Just like with arrays, you can use `...` to copy or merge objects.

  * **Use 1: Copying an object**

    ```javascript
    const car1 = { make: "Honda", model: "Civic" };
    const car1Copy = { ...car1 };
    ```

  * **Use 2: Merging objects**

    ```javascript
    const baseDetails = {
      name: "Laptop",
      brand: "Dell"
    };

    const specs = {
      ram: 16,
      storage: 512
    };

    const product = { ...baseDetails, ...specs };
    // product is { name: "Laptop", brand: "Dell", ram: 16, storage: 512 }
    ```

    > **Key Tip:** If keys conflict, the *last* object "wins".

    > ```javascript
    > const defaults = { theme: "light", version: 1 };
    > const userPrefs = { theme: "dark", name: "Alex" };
    > ```

    > const settings = { ...defaults, ...userPrefs };
    > // settings is { theme: "dark", version: 1, name: "Alex" }
    > // "theme" from userPrefs overwrote the one from defaults.

    > ```
    > ```

#### Object Methods

These are methods that live on the main `Object` constructor. You pass your object *into* them.

  * **`Object.keys(obj)`**: Returns an **array** of the object's keys.
  * **`Object.values(obj)`**: Returns an **array** of the object's values.
  * **`Object.entries(obj)`**: Returns an **array of arrays**, where each inner array is `[key, value]`.

<!-- end list -->

```javascript
const user = {
  id: 123,
  username: "admin",
  email: "admin@test.com"
};

const keys = Object.keys(user);
// keys is ["id", "username", "email"]

const values = Object.values(user);
// values is [123, "admin", "admin@test.com"]

const entries = Object.entries(user);
// entries is [ ["id", 123], ["username", "admin"], ["email", "admin@test.com"] ]
```

-----

### Destructuring & Naming

**Destructuring** is a powerful shortcut for pulling values *out* of an object or array and into their own variables.

#### Object Destructuring

Instead of writing `const name = person.name;`, you can do this:

```javascript
const person = {
  firstName: "Jane",
  lastName: "Doe",
  age: 28,
  city: "New York"
};

// The old way
// const fName = person.firstName;
// const lName = person.lastName;

// The new, destructuring way
// This line creates two new variables: firstName and lastName
const { firstName, lastName } = person;

console.log(firstName); // Output: "Jane"
console.log(lastName); // Output: "Doe"
```

  * **Renaming (Naming)**
    What if you want the variable to have a different name? Use a colon (`:`).
    ```javascript
    const { firstName: fName, age } = person;

    console.log(fName); // Output: "Jane" (not firstName)
    console.log(age);   // Output: 28
    ```

#### Array Destructuring

This works for arrays too, but it uses the *order* of the elements, not their names.

```javascript
const colors = ["Red", "Green", "Blue"];

// The old way
// const firstColor = colors[0];
// const secondColor = colors[1];

// The new, destructuring way
const [firstColor, secondColor] = colors;

console.log(firstColor);  // Output: "Red"
console.log(secondColor); // Output: "Green"
```

-----

### JSON Intro

**JSON** stands for **J**ava**S**cript **O**bject **N**otation.

  * It is a **text format** used to send data between a server and a web page.
  * It *looks* almost identical to a JavaScript object, but it's a **string**.

**Key Rules for JSON (This is crucial\!):**

1.  All **keys** *must* be strings in **double quotes** (`"`).
2.  All **string values** *must* be in **double quotes** (`"`). (No single quotes `'` allowed).
3.  It cannot contain functions or `undefined`.

**Example JSON String:**

```json
{
  "id": 1234,
  "productName": "Coffee Mug",
  "inStock": true,
  "colors": ["White", "Black"]
}
```

#### Converting To/From JSON

You will *never* write JSON by hand like this. You'll use two built-in methods:

  * **`JSON.stringify(object)`**: Takes a JS object and turns it into a JSON **string** (to *send* data).
  * **`JSON.parse(string)`**: Takes a JSON **string** and turns it back into a usable JS **object** (to *receive* data).

<!-- end list -->

```javascript
// 1. You have a JavaScript object
const post = {
  title: "My First Blog Post",
  author: "Alex",
  views: 100,
  isPublished: true
};

// 2. You need to "stringify" it to send to a server
const jsonString = JSON.stringify(post);

console.log(jsonString);
// Output: '{"title":"My First Blog Post","author":"Alex","views":100,"isPublished":true}'
// Notice it's now a single string, and all keys have double quotes!

// 3. You receive a JSON string from a server (simulated here)
const dataFromServer = '{"id": 1, "username": "jane_doe"}';

// 4. You must "parse" it to use it as an object
const userObject = JSON.parse(dataFromServer);

console.log(userObject.username); // Output: "jane_doe"
```

-----

### ✍️ Object Challenge

**Task:** Create and manage a `book` object.

1.  Create an object `book` with properties:
      * `title`: "The Hitchhiker's Guide to the Galaxy"
      * `author`: "Douglas Adams"
      * `genres`: an array with "Sci-Fi" and "Comedy"
2.  Add a new property `pageCount` with the value `224`.
3.  Use **destructuring** to pull the `title` and `author` into their own variables.
4.  Use `Object.keys()` to log an array of all the property names in the `book` object.
5.  Convert the entire `book` object into a JSON string and log it.

**Solution:**

```javascript
// 1. Create the object
const book = {
  title: "The Hitchhiker's Guide to the Galaxy",
  author: "Douglas Adams",
  genres: ["Sci-Fi", "Comedy"]
};

// 2. Add a new property
book.pageCount = 224;

// 3. Destructure title and author
const { title, author } = book;

console.log(`Title: ${title}, Author: ${author}`);
// Output: Title: The Hitchhiker's Guide to the Galaxy, Author: Douglas Adams

// 4. Log all keys
const bookKeys = Object.keys(book);
console.log(bookKeys);
// Output: ["title", "author", "genres", "pageCount"]

// 5. Convert to JSON string
const bookJSON = JSON.stringify(book);
console.log(bookJSON);
// Output: '{"title":"The Hitchhiker\'s Guide to the Galaxy","author":"Douglas Adams","genres":["Sci-Fi","Comedy"],"pageCount":224}'
```
