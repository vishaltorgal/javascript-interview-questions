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
10. [Hoisting](#10-hoisting)
11. [this keyword](#11-this-keyword)
12. [Event Loop](#12-event-loop)
13. [Call Stack](#13-call-stack)
14. [Synchronous vs Asynchronous](#14-synchronous-vs-asynchronous)
15. [Arrow functions vs normal functions](#15-arrow-functions-vs-normal-functions)
16. [Pure vs impure functions](#16-pure-vs-impure-functions)
17. [Higher order functions](#17-higher-order-functions)
18. [Currying](#18-currying)
19. [Debouncing vs Throttling](#19-debouncing-vs-throttling)
20. [Shallow copy vs Deep copy](#20-shallow-copy-vs-deep-copy)
21. [Spread operator](#21-spread-operator)


Spread operator
Rest operator
LocalStorage vs SessionStorage vs Cookies
Event bubbling
Memory leaks
Garbage collection
How does JS handle concurrency



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
```

## 6. **What is reduce?**

```jsx
const numbers = [1, 2, 3, 4, 5];

const total = numbers.reduce((accumulator, current) => {
  return accumulator + current;
}, 0); // 0 is the starting value

console.log(total); // 👉 15
```
### ***🔍 How it works step-by-step:***

| Step | Accumulator | Current | Total |
| ---- | ----------- | ------- | ----- |
| 1    | 0           | 1       | 1     |
| 2    | 1           | 2       | 3     |
| 3    | 3           | 3       | 6     |
| 4    | 6           | 4       | 10    |
| 5    | 10          | 5       | 15    |




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

## 10. **Hoisting**

Hoisting in JavaScript is a behavior where variable and function declarations are moved to the top of their scope during compilation.
Only the declaration is hoisted, not the initialization.

***var*** declarations are hoisted and initialized with undefined
```jsx
console.log(a); // undefined
var a = 10;
console.log(a); // 10

```
***What JS sees internally:***
```jsx
var a;
console.log(a);
a = 10;

```
***let and const***
They are hoisted too, but not initialized.
They stay in the `Temporal Dead Zone (TDZ)` until declared.


***Function Hoisting***
Fully hoisted. You can call them before defining.
```jsx
sayHello();

function sayHello() {
  console.log("Hello");
}

```
Not fully hoisted. ***Reason:*** only var sayHi is hoisted, not the function
```jsx
sayHi(); // TypeError

var sayHi = function () {
  console.log("Hi");
};

```

***Arrow Functions***
```jsx
greet(); // ReferenceError or TypeError

const greet = () => {
  console.log("Hey");
};
```

## 11. **this keyword**

The this keyword in JavaScript refers to the object that is executing the current function. Its value is decided at runtime.

```jsx
const user = {
  name: "Vishal",
  greet() {
    console.log(name);
// ReferenceError: name is not defined
// name is not a local variable
// JS looks for name in function scope
console.log(this.name); // Vishal
  }
};

user.greet();

```
## 12. **Event Loop**

The Event Loop allows JavaScript to perform non-blocking asynchronous operations even though JS is single-threaded.

***Example***
```jsx
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");

```
***Output***
```jsx
Start
End
Promise
Timeout

```
The Event Loop continuously checks the call stack and executes synchronous code first, then microtasks, and finally macrotasks, enabling asynchronous behavior in JavaScript.

***What happens step by step***
- "Start" → Call Stack → executed
- setTimeout → Web API → Macrotask Queue
- Promise.then → Microtask Queue
- "End" → Call Stack → executed
- Call Stack empty
- Event Loop runs all Microtasks
- Then runs one Macrotask

## 13. **Call Stack**

 The Call Stack is a data structure that keeps track of which function is currently running and what should run next.
JavaScript uses it to manage function execution.

👉 It works on LIFO principle
Last In, First Out

***Example***
```jsx
function greet() {
  sayHi();
  console.log("Back in greet");
}

function sayHi() {
  console.log("Hi!");
}

greet();

```
***Output***
```jsx
Hi!
Back in greet
```

## 14. **Synchronous vs Asynchronous**

| Feature           | Synchronous              | Asynchronous                    |
| ----------------- | ------------------------ | ------------------------------- |
| Execution         | Runs one after another   | Runs in background              |
| Waiting           | Waits for task to finish | Does not wait                   |
| Blocking          | Blocks next task         | Non-blocking                    |
| Speed             | Slower for long tasks    | Faster and efficient            |
| User Experience   | Can freeze UI            | Keeps UI responsive             |
| Examples          | `console.log`, loops     | `setTimeout`, `fetch`, Promises |
| Real-life example | Standing in a queue      | Ordering food and waiting       |

## 15. **Arrow functions vs normal functions**

| Feature             | Normal Function       | Arrow Function         |
| ------------------- | --------------------- | ---------------------- |
| Syntax              | `function fn() {}`    | `const fn = () => {}`  |
| `this`              | Own `this`            | Inherits from parent   |
| `arguments`         | Available             | Not available          |
| Hoisting            | Yes                   | No                     |
| Constructor (`new`) | Yes                   | No                     |
| Prototype           | Yes                   | No                     |
| Best use case       | Methods, constructors | Callbacks, short logic |

## 16. **Pure vs impure functions**

***Pure Function***

A function is pure if:
- Same input → same output
- No side effects

```jsx
function add(a, b) {
  return a + b;
}
```
- Input add(2, 3) → always 5
- Does not change anything outside

  ***Impure Function***

A function is impure if:
- Output depends on external state, OR
- It changes something outside the functio

```jsx
let tax = 10;

function calculate(price) {
  return price + tax;
}

```
- Output changes if tax changes

| Feature             | Pure Function       | Impure Function |
| ------------------- | ------------------- | --------------- |
| Output              | Same for same input | Can vary        |
| Side effects        | ❌ None              | ✅ Yes           |
| Uses external state | ❌ No                | ✅ Yes           |
| Testable            | Easy                | Hard            |
| Predictable         | Yes                 | No              |

## 17. **Higher order functions**

A Higher Order Function (HOF) is a function that does at least one of these:
- Takes another function as an argument
- Returns a function

***Example 1: Function passed as argument***
  ```jsx
function sayHello() {
  console.log("Hello");
}

function run(fn) {
  fn();
}

run(sayHello);
```
👉 run is a Higher Order Function
👉 sayHello is passed as a function

***Example 2: Function returning another function***
```jsx
function greet() {
  return function () {
    console.log("Hi!");
  };
}

const hello = greet();
hello();

```
👉 greet is a Higher Order Function

***Example 3: map***
```jsx
const numbers = [1, 2, 3];

const double = numbers.map(n => n * 2);

console.log(double); // [2, 4, 6]

```
👉 map is a Higher Order Function
👉 Arrow function is passed to it

## 18. **Currying**

Currying means
👉 breaking a function with multiple arguments into a chain of functions, each taking one argument.

***Normal function (not curried)***
```jsx
function add(a, b) {
  return a + b;
}

add(2, 3); // 5

```

***Curried function***
```jsx
function add(a) {
  return function (b) {
    return a + b;
  };
}

add(2)(3); // 5
```
- First call takes a
- Second call takes b

***Easy real-life analogy***

Ordering food 🍔
- First choose restaurant
- Then choose item
- Instead of ordering everything at once.

## 19. **Currying**

Both Debouncing and Throttling are techniques used to improve browser performance by limiting how many times a function executes over time.

***Debouncing***
- `Debouncing` delays the execution of a function until after a certain time has passed since the last event.
- `Real-world analogy:` An elevator. The doors won't close until people stop walking in. If someone walks in while the doors are closing, the timer resets, and the doors stay open.
- `Example:` Search input, resize

***Throttling***
- `Throttling` ensures a function is called at most once in a specified interval, no matter how many times the event is triggered. Used when you want regular updates but not too frequently.
- `Real-world analogy:` A water faucet with a slow drip. No matter how hard you turn the handle, it only lets out one drop every 2 seconds.
- `Example:` Scroll, mouse move, API calls

## 20. **Shallow copy vs Deep copy**
Shallow copy copies only the top-level properties, while deep copy clones everything, including nested objects

```jsx
const original = {
  name: "Alice",
  address: { city: "New York" }
};

// --- SHALLOW COPY ---
const shallow = { ...original };
shallow.address.city = "Los Angeles"; 

console.log(original.address.city); // "Los Angeles" (Wait, what?! It changed!)

// --- DEEP COPY ---
const deep = JSON.parse(JSON.stringify(original))
deep.address.city = "Miami";

console.log(original.address.city); // "Los Angeles" (Original stays safe)
```

| Feature           | Shallow Copy                  | Deep Copy                                       |
| ----------------- | ----------------------------- | ----------------------------------------------- |
| Levels copied     | First level only              | All levels                                      |
| Nested objects    | Referenced                    | Fully cloned                                    |
| Original affected | Yes, if nested changes        | No                                              |
| Methods to create | Spread `...`, `Object.assign` | `JSON.parse(JSON.stringify)`, `structuredClone` |
| Use case          | Simple objects/arrays         | Nested objects/complex structures               |

## 21. **Spread operator**
