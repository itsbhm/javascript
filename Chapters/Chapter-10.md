# 📘 Chapter 10: Algorithms & Interview Prep

This chapter is designed to build your problem-solving mindset and prepare you for technical interviews. You’ll implement classic algorithms, learn how to measure code performance, and build coding fluency using JavaScript.

---

## 65. Big O Notation

* Describes the time/space complexity of an algorithm
* Common complexities:

  * O(1): Constant
  * O(n): Linear
  * O(log n): Binary Search
  * O(n²): Nested Loops

**Example:**

```js
function sum(arr) {
  let total = 0;
  for (let num of arr) total += num;
  return total; // O(n)
}
```

---

## 66. Recursion Basics

* A function calls itself until a base case is met

**Example – Factorial:**

```js
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}
```

---

## 67. Cumulative Sum Algorithm

* Used in prefix sums and rolling sums

**Example:**

```js
function cumulativeSum(arr) {
  let result = [];
  let sum = 0;
  for (let num of arr) {
    sum += num;
    result.push(sum);
  }
  return result;
}
```

---

## 68. Binary Search (Iterative & Recursive)

**Iterative:**

```js
function binarySearch(arr, target) {
  let left = 0, right = arr.length - 1;
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (arr[mid] === target) return mid;
    if (arr[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1;
}
```

**Recursive:**

```js
function binarySearchRec(arr, target, left = 0, right = arr.length - 1) {
  if (left > right) return -1;
  const mid = Math.floor((left + right) / 2);
  if (arr[mid] === target) return mid;
  if (arr[mid] < target) return binarySearchRec(arr, target, mid + 1, right);
  return binarySearchRec(arr, target, left, mid - 1);
}
```

---

## 69. Least Recently Used (LRU) Cache Design (Intro)

* Remove the least recently accessed item from cache

**Conceptual JS Sketch:**

```js
class LRUCache {
  constructor(limit = 5) {
    this.cache = new Map();
    this.limit = limit;
  }

  get(key) {
    if (!this.cache.has(key)) return null;
    const value = this.cache.get(key);
    this.cache.delete(key);
    this.cache.set(key, value);
    return value;
  }

  put(key, value) {
    if (this.cache.has(key)) this.cache.delete(key);
    else if (this.cache.size >= this.limit) {
      const first = this.cache.keys().next().value;
      this.cache.delete(first);
    }
    this.cache.set(key, value);
  }
}
```

---

## 70. Two Sum / Three Sum Problem Variants

**Two Sum:**

```js
function twoSum(arr, target) {
  const map = {};
  for (let i = 0; i < arr.length; i++) {
    const diff = target - arr[i];
    if (map[diff] !== undefined) return [map[diff], i];
    map[arr[i]] = i;
  }
}
```

**Three Sum – Concept:** Sort → fix `i` → two-pointer approach

---

## 71. Sorting: Bubble, Merge, Quick Overview

**Bubble Sort:**

```js
function bubbleSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length - i - 1; j++) {
      if (arr[j] > arr[j + 1]) [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
    }
  }
  return arr;
}
```

**Merge Sort & Quick Sort:** Theory only in this chapter

---

## 72. Hashmaps/Sets Usage

* Lookup, de-dupe, frequency count

**Example:**

```js
const set = new Set([1, 2, 2, 3]); // {1,2,3}
const map = new Map();
map.set("a", 1);
```

---

## 73. String Manipulation Problems

* Reverse, palindrome check, frequency count, anagram

**Example – Anagram Check:**

```js
function isAnagram(a, b) {
  return a.split('').sort().join('') === b.split('').sort().join('');
}
```

---

## 74. Practice with Test-Driven Development (Vitest Intro)

* Use tests to validate logic

**Example:**

```js
// sum.test.js
import { describe, it, expect } from 'vitest';
import { sum } from './sum';

describe("sum", () => {
  it("adds numbers", () => {
    expect(sum(2, 3)).toBe(5);
  });
});
```

---

## ✅ Exercises

1. Find max number in an array (O(n))
2. Use recursion to reverse a string
3. Implement a working bubble sort
4. Solve Two Sum with hashmap
5. Create a basic test file for a sum function
