# JavaScript Interview Questions and Answers

## 1Q: What is `Hoisting`?
A: `Hoisting` is a JavaScript behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can use variables and functions before they are declared in our code.

It's important to note that while the declarations are hoisted, the initializations (assignment of values) are not. This means that if you try to use a variable before it's assigned a value, you'll get undefined. For functions, the entire function declaration is hoisted, allowing you to call the function before its actual declaration in the code.

Here's a basic example to illustrate hoisting:

```
// Example 1: Variable Hoisting
console.log(x); // Outputs: undefined
var x = 5;

// Example 2: Function Hoisting
foo(); // Outputs: "Hello, hoisting!"
function foo() {
  console.log("Hello, hoisting!");
}

// Example 3: Hoisting with Let and Const
console.log(y); // ReferenceError: y is not defined
let y = 10;
```

---

## 2Q: What is the use of `ES6`?
A:

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
