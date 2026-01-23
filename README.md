# JavaScript Interview Questions (2025–2026)

### Table of Contents
1. [Is JavaScript Object-Oriented?](#1-is-javascript-object-oriented)
2. [What are closures?](#2-what-are-closures)
3. [What is a Service Worker?](#3-what-is-a-service-worker)
4. [Array Methods Comparison](#4-array-methods-comparison)
5. [slice vs splice](#5-slice-vs-splice)
6. [What is reduce?](#6-what-is-reduce)
7. [What is a Promise?](#7-what-is-a-promise)
8. [Destructuring](#8-destructuring)
9. [What is Webpack?](#9-what-is-webpack)




## 1. **Is JavaScript Object-Oriented?**

JavaScript is a multi-paradigm language, meaning it supports various programming styles, including 
 - Object-Oriented Programming (OOP), 
 - Functional Programming (FP), 
 - and Procedural Programming.


## 2. **What are closures?**

It is an inner function that has access to the outer or enclosing function’s variables, functions and other data even after the outer function has finished its execution. 

### ***Closures Example***
```jsx
function outer() {
  let count = 0;

  function inner() {
    count++;
    console.log(count);
  }

  return inner;
}

const counter = outer();
counter(); // 1
counter(); // 2

```
***Key Points***

- A closure is formed automatically in JavaScript.
- It remembers variables from the lexical scope, not the call stack.
- Each closure has its own copy of the outer variables.
- 
## 3. **What is a service worker?**
A service worker is a background JavaScript script that runs separately from the web page and lets you control network requests, caching, and offline behavior of a web app.

***Key Characteristics***

- Runs in the background, not tied to a web page
- No DOM access
- Event driven (install, activate, fetch)
- Works only on HTTPS (except localhost)
- Enables offline support and PWA features

## 4. **Array Methods Comparison**

| Method       | Description                                             | Mutates Original Array? | Return Value               | Use Case                  |
| ------------ | ------------------------------------------------------- | ----------------------- | -------------------------- | ------------------------- |
| `map()`      | Transforms each item and returns a **new array**        | ❌ No                    | New array                  | Transform items           |
| `forEach()`  | Runs a function on each item (no return)                | ❌ No                    | `undefined`                | Side effects like logging |
| `filter()`   | Returns a **new array** with items that match condition | ❌ No                    | New array                  | Filter items              |
| `reduce()`   | Reduces array to a single value                         | ❌ No                    | Any (number, object, etc.) | Summing, combining        |
| `slice()`    | Returns a **portion** of the array                      | ❌ No                    | New array                  | Get a subarray            |
| `splice()`   | Adds/removes items in-place                             | ✅ Yes                   | Removed items              | Modify original array     |
| `find()`     | Returns the **first matching item**                     | ❌ No                    | Single item or `undefined` | Get first match           |
| `includes()` | Checks if array contains a value                        | ❌ No                    | `true` or `false`          | Check existence           |


### ***map() – Transform values***
```jsx
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2); // [2, 4, 6]
```

### ***forEach() – Just loop through***
```jsx
const fruits = ['apple', 'banana'];
fruits.forEach(f => console.log(f)); // apple banana (logs only)
```

### ***filter() – Get items matching a condition***
```jsx
const nums = [1, 2, 3, 4];
const even = nums.filter(n => n % 2 === 0); // [2, 4]
```

### ***reduce() – Collapse into one value***
```jsx
const nums = [1, 2, 3];
const sum = nums.reduce((acc, val) => acc + val, 0); // 6
```

### ***slice() – Copy part of an array***
```jsx
const items = ['a', 'b', 'c', 'd'];
const part = items.slice(1, 3); // ['b', 'c']
```

### ***splice() – Remove or insert items***
```jsx
const items = ['a', 'b', 'c'];
items.splice(1, 1, 'x');  // ['a', 'x', 'c'] (mutated)
```
### ***find() – Get the first match***
```jsx
const nums = [1, 2, 3];
const firstEven = nums.find(n => n % 2 === 0); // 2

```

### ***includes() – Check existence***
```jsx
const items = ['a', 'b', 'c'];
items.includes('b'); // true
items.includes('x'); // false
```


## 5. **slice vs splice**

| Feature               | `slice()`                       | `splice()`                          |
| --------------------- | ------------------------------- | ----------------------------------- |
| **Purpose**           | Extracts a portion of an array  | Adds, removes, or replaces elements |
| **Mutates original?** | ❌ No (does NOT change original) | ✅ Yes (CHANGES original)            |
| **Return Value**      | A **new array**                 | An array of **removed items**       |
| **Use Cases**         | Copy part of array              | Remove or insert items in-place     |

### ***slice() – Copy part of an array***
```jsx
const items = ['a', 'b', 'c', 'd'];
const part = items.slice(1, 3); // ['b', 'c']
```

### ***splice() – Remove or insert items***
```jsx
const items = ['a', 'b', 'c'];
items.splice(1, 1, 'x');  // ['a', 'x', 'c'] (mutated)

## 6. **What is reduce?**

```jsx
const numbers = [1, 2, 3, 4, 5];

const total = numbers.reduce((accumulator, current) => {
  return accumulator + current;
}, 0); // 0 is the starting value

console.log(total); // 👉 15

### ***🔍 How it works step-by-step:***

| Step | Accumulator | Current | Total |
| ---- | ----------- | ------- | ----- |
| 1    | 0           | 1       | 1     |
| 2    | 1           | 2       | 3     |
| 3    | 3           | 3       | 6     |
| 4    | 6           | 4       | 10    |
| 5    | 10          | 5       | 15    |

```


## 7. **What is a Promise?**
A Promise represents a value that may be available now, later, or never.

### ***Class Component Example***
```jsx
const promise = new Promise((resolve, reject) => {
  resolve('Done!');
});

promise.then(result => console.log(result)); // Done!
```
<br>

## 8. **Destructuring**

### ***✅ 1. Array Destructuring***
```jsx
const colors = ['red', 'green', 'blue'];

const [first, second] = colors;

console.log(first);  // 'red'
console.log(second); // 'green'

```
### ***👉 You can skip items***
```jsx
const [ , , third] = colors;
console.log(third); // 'blue'

```
### ***✅ 2. Object Destructuring***
```jsx
const user = { name: 'John', age: 30 };

const { name, age } = user;

console.log(name); // 'John'
console.log(age);  // 30

```
### ***👉 Rename during destructuring:***
```jsx
const { name: userName } = user;
console.log(userName); // 'John'

```

### ***✅ 3. Destructuring in Function Parameters***
```jsx
function greet({ name, age }) {
  console.log(`Hello, ${name}! You are ${age} years old.`);
}

const person = { name: 'Alice', age: 25 };
greet(person);

```
### ***✅ 4. Default Values***
```jsx
const [x = 10, y = 20] = [5];
console.log(x); // 5
console.log(y); // 20

const { city = 'Unknown' } = { name: 'Tom' };
console.log(city); // 'Unknown'
```

### ***🔁 5. Swap Values Using Destructuring***
```jsx
let a = 5;
let b = 10;

[a, b] = [b, a];

console.log(a); // 10
console.log(b); // 5

```
### ***🔍 How it works:***
- [b, a] creates a new array: [10, 5]
- Then [a, b] = [10, 5] reassigns a = 10, b = 5

<br>

## 9. **What is Webpack?**

Webpack is a powerful module bundler for JavaScript applications.
It takes all your files (JavaScript, CSS, images, etc.) and bundles them into optimized output files (usually one or a few .js files) that the browser can load efficiently.

### ***🔧 Why Webpack is Useful***

- Combines multiple JS files into one (bundling)

- Converts modern JS (ES6+) to older JS (using Babel)

- Supports loaders (e.g., for CSS, images, fonts)

- Optimizes output (minification, tree-shaking)

- Supports plugins (e.g., HTML generation, caching)

- Works with frameworks like React, Vue, Angular
