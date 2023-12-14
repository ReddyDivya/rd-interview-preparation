# JavaScript Interview Questions and Answers

## 1Q: What is `Hoisting`?
A: `Hoisting` is a JavaScript behavior in which variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can use variables and functions in your code before they are formally declared. However, it's important to note that while declarations are hoisted, initializations are not.

Here are two key aspects of hoisting:

### Variable Hoisting:

- Variable declarations using var are hoisted to the top of their scope.
- Only the declaration is hoisted, not the initialization.
- If a variable is used before it is declared, it will have the value undefined.

```
console.log(x); // undefined
var x = 5;
```

In this example, the var x declaration is hoisted to the top, but the assignment (x = 5) remains in place. The console.log statement prints undefined because the assignment has not occurred yet.

### Function Hoisting:

- Function declarations are hoisted in their entirety.
- This includes both the function name and its implementation.
- You can call a function before its declaration in the code.

```
foo(); // "Hello, hoisting!"
function foo() {
  console.log("Hello, hoisting!");
}
```

Here, the function foo is hoisted, so calling it before the declaration is valid.

It's important to distinguish between var, let, and const when it comes to hoisting:

- With var, both the declaration and initialization are hoisted.
- With let and const, hoisting occurs, but the variable is not initialized until the actual declaration is encountered in the code. Attempting to access a let or const variable before its declaration results in a ReferenceError.

```
console.log(a); // ReferenceError: a is not defined
let a = 10;
```

In modern JavaScript, it's a good practice to use let and const for variable declarations to avoid some of the unexpected behaviors associated with var hoisting. Functions, on the other hand, are typically hoisted in a predictable manner regardless of the type of declaration.

---

## 2Q: What is the use of `ES6`?
A: ECMAScript 2015 (ES6) is a significant update to the JavaScript language specification, bringing many new features and enhancements to the language. The primary goals of ES6 are to make JavaScript more expressive, readable, and scalable for large and complex applications. Here are some key features and use cases of ES6:

### 1. let and const Declarations:

ES6 introduced the let and const keywords for declaring variables. let allows block-scoped variables, and const is used for declaring constants.
```
let x = 10;
const PI = 3.14159;
```

### 2. Arrow Functions:

Arrow functions provide a more concise syntax for writing functions. They automatically bind to the surrounding this value and have implicit return for one-liner functions.

```
const add = (a, b) => a + b;
```

### 3. Template Literals:

Template literals allow the interpolation of variables and expressions within strings using backticks (`).

```
const name = 'World';
const greeting = `Hello, ${name}!`;
```

### 4. Destructuring Assignment:

Destructuring assignment allows you to extract values from arrays or objects and assign them to variables in a concise way.

```
const person = { name: 'John', age: 30 };
const { name, age } = person;
```

### 5. Spread and Rest Operators:

The spread (...) operator is used for array and object spreading, while the rest operator is used for collecting the remaining elements into a single variable.

```
const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4, 5];
```

### 6. Classes:

ES6 introduced a class syntax for defining constructor functions and creating objects, providing a more familiar and structured way to work with prototypes.

```
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}
```

### 7. Promises:

Promises provide a cleaner and more readable way to work with asynchronous code, making it easier to reason about and handle errors.

```
const fetchData = () => {
  return new Promise((resolve, reject) => {
    // Asynchronous operation
    if (success) {
      resolve(data);
    } else {
      reject(error);
    }
  });
};
```

### 8. Modules:

ES6 introduced a modular system for organizing and managing code. Modules allow developers to encapsulate code in separate files and import/export functionality.

```
// module.js
export const add = (a, b) => a + b;

// main.js
import { add } from './module';
```

### 9. 





---

## 3Q: Why do we write `console.log`?
A: 
---

## 4Q: If we have several `console.log` in our application and want to enable or disable it whenever we want. How do we achieve it?
A: `Environment Variable`

```
if (process.env.NODE_ENV === 'development') {
    console.log("This will only be logged in development mode");
}
```

In a production environment, the NODE_ENV is usually set to 'production', so these logs won't appear.

---

## 5Q: What is `Doctype` in HTML and Does it make any difference when we don't mention it?
A: 

---

## 6Q: What is the difference between `CSS` and `CSS3`?
A:

---

## 7Q: What is `ECMAScript`?
A:

---

## 8Q: What is the difference between `var`, `let`, and `const`?
A:

---

## 9Q: If I have variables that are not going to be modified throughout the application, where can I use `var` or `const` to employ them wherever they're required? How will it affect speed and performance? 
A: 
### Readability and Intent:
const explicitly communicates that the variable won't be reassigned. This can make your code more readable and help other developers understand your intentions.
Using var for variables that won't be modified can be confusing because it implies the variable could be reassigned later in the code.

### Scope:
const has block scope, which means it is limited to the block in which it is declared. This can help prevent unintended variable hoisting or scope-related issues.
var has function scope, and it is hoisted to the top of the function or global scope, which can sometimes lead to unexpected behavior.

### Maintainability:
const helps prevent accidental reassignment, reducing the chances of introducing bugs when maintaining or updating your code.

Regarding performance, the use of var or const for variables that won't be modified is unlikely to have a significant impact on the overall performance of your application. Modern JavaScript engines are highly optimized and can handle both declarations efficiently.

However, it's worth noting that the use of const may lead to better optimizations in some cases. Since const indicates that a variable won't be reassigned, the engine may be able to make certain optimizations during compilation.

In summary, for variables that won't be modified, it's a good practice to use const for its clarity, readability, and the additional benefits it provides in terms of preventing accidental reassignment and potential optimizations.

---

## 10Q: What is a `Spread Operator`?
A: 

---

## 11Q: What is `Arrow Function`?
A:

---

## 12Q: What is `setTimeOut` and `setInterval`?
A:

---

## 13Q: How do you `stop setInterval after some intervals`, How do you achieve it?
A: To stop a setInterval after a certain number of intervals or after a specific duration, you can use the clearInterval function. The setInterval function returns an interval ID, which you can pass to clearInterval to stop the interval. 
Here's an example:
```
// Set up a setInterval and store the interval ID
const intervalId = setInterval(function() {
    // Code to be executed at each interval

    // Check a condition to determine when to stop the interval
    if (someCondition) {
        // Stop the interval when the condition is met
        clearInterval(intervalId);
    }
}, intervalDuration);
```

---

## 14Q: Write a program to find the highest number of occurrences in an array and the number of times it occurred in the array `[1, 1, 2, 3, 1, 4]`?
A: 
```
const findHighestOccur = (arr) => {
    const count = {};

    for (const element of arr) {
        if (count[element]) {
            count[element] += 1;
        } else {
            count[element] = 1;
        }
    }

    let maxElement;
    let maxOccurrence = 0;

    for (const element in count) {
        if (count[element] > maxOccurrence) {
            maxElement = element;
            maxOccurrence = count[element];
        }
    }

    return { maxElement, maxOccurrence };
};

console.log(findHighestOccur([1, 1, 2, 3, 1, 4])); //{maxElement: "1", maxOccurrence: 3}
console.log(findHighestOccur([2, 3, 1, 4, 2, 2, 3, 3, 2]));//{maxElement: "2", maxOccurrence: 4}
```

- I added the logic to find the element with the highest occurrence.
- I used a for...in loop to iterate over the properties of the count object.
- The function now returns an object with maxElement and maxOccurrence.
- The console.log statement will log the result of the function.

---