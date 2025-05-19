## 1. **Is JavaScript Object-Oriented?**

JavaScript is a multi-paradigm language, meaning it supports various programming styles, including 
 - Object-Oriented Programming (OOP), 
 - Functional Programming (FP), 
 - and Procedural Programming.

<br>

## 2. **What are closures**

It is an inner function that has access to the outer or enclosing function’s variables, functions and other data even after the outer function has finished its execution. 


Own scope where variables defined between its curly brackets
Outer function's variables
Global variables

### Key Points
The closure has three scope chains.
- Own scope where variables defined between its curly brackets
- Outer function's variables
- Global variables


### ***Closures Example***
```jsx
function Welcome(name) {
  var greetingInfo = function (message) {
    console.log(message + " " + name);
  };
  return greetingInfo;
}
var myFunction = Welcome("John");
myFunction("Welcome "); //Output: Welcome John
myFunction("Hello Mr."); //output: Hello Mr. John

```

<br>

## 3. **What is a service worker**
A Service worker is basically a script (JavaScript file) that runs in the background, separate from a web page and provides features that don't need a web page or user interaction. Some of the major features of service workers are Rich offline experiences(offline first web application development), periodic background syncs, push notifications, intercept and handle network requests and programmatically managing a cache of responses.

### ***Service worker Example***
```jsx
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fetch API Example</title>
</head>
<body>
  <h1>Random User</h1>
  <div id="user"></div>

  <script>
    // URL of the public API
    const apiURL = 'https://randomuser.me/api/';

    // Function to fetch user data
    async function fetchUserData() {
      try {
        const response = await fetch(apiURL); // Make HTTP request
        const data = await response.json();   // Parse JSON data
        const user = data.results[0];         // Access user data

        `;
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }

    // Call the function to fetch and display user data
    fetchUserData();
  </script>
</body>
</html>

```

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
<br>

## 5. **slice() vs splice()**

| Feature               | `slice()`                       | `splice()`                          |
| --------------------- | ------------------------------- | ----------------------------------- |
| **Purpose**           | Extracts a portion of an array  | Adds, removes, or replaces elements |
| **Mutates original?** | ❌ No (does NOT change original) | ✅ Yes (CHANGES original)            |
| **Return Value**      | A **new array**                 | An array of **removed items**       |
| **Use Cases**         | Copy part of array              | Remove or insert items in-place     |

<br>

## 5. **What is reduce()**

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
<br>
