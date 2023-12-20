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

### 9. Default Parameters:

ES6 allows you to assign default values to function parameters, simplifying the handling of missing or undefined values.

```
const greet = (name = 'Guest') => `Hello, ${name}!`;
```

### 10. Symbol and Iterators:

Symbols provide a way to create unique identifiers, and iterators allow you to define custom iteration behavior for objects.

```
const mySymbol = Symbol('mySymbol');
const iterableObject = {
  [mySymbol]: 'Hello',
  [Symbol.iterator]() {
    // Custom iterator logic
  }
};
```

These features, among others introduced in ES6, contribute to improving the overall readability, maintainability, and expressiveness of JavaScript code. As a result, developers can write more efficient and structured code, making it easier to build and maintain large-scale applications.

---

## 3Q: Why do we write `console.log`?
A: `console.log` is a function in JavaScript that is commonly used for debugging and logging information to the console. It allows developers to print messages, variables, or other data to the console, which can be viewed in the browser's developer tools or other JavaScript environments.

Here are some common use cases for console.log:

### Debugging:
Developers use console.log statements to print the values of variables or objects during development. This helps in understanding the flow of the program and identifying potential issues.

```
let x = 10;
console.log('The value of x is:', x);
```

### Checking Code Execution:
Developers use console.log to check if a particular part of the code is executed or to trace the sequence of function calls.
```
function myFunction() {
  console.log('myFunction is called');
  // Other code logic
}
```

### Inspecting Objects:
console.log is frequently used to inspect the properties and values of objects.
```
const person = { name: 'John', age: 30 };
console.log('Person:', person);
```

### Logging Error Messages:
When an error occurs, developers often use console.log to print relevant information about the error, helping in the debugging process.

```
try {
  // Some code that may throw an error
} catch (error) {
  console.log('Error:', error.message);
}
```

### Logging Messages for Users:
In some cases, developers use console.log to provide informative messages to users, especially during development.

```
console.log('Welcome to the application!');
```

It's important to note that console.log is a debugging tool and should not be left in the production code, as it can impact performance and may expose sensitive information. In production, developers often use more sophisticated logging libraries or disable logging statements.

Other console methods, such as console.warn, console.error, and console.info, provide additional functionality for different types of messages and can be useful in different debugging scenarios.

---

## 4Q: If we have several `console.log` in our application and want to enable or disable it whenever we want. How do we achieve it?
A: 

### 1. Environment Variable

```
if (process.env.NODE_ENV === 'development') {
    console.log("This will only be logged in development mode");
}
```

In a production environment, the NODE_ENV is usually set to 'production', so these logs won't appear.

### 2. Configuration

To enable or disable console.log statements selectively in your application, you can use a conditional check or wrap your logging statements within a function that you can control based on a configuration or environment variable. This way, you can easily toggle logging on or off as needed. 
Here's an example using a configuration flag:
```
// Configuration flag to control logging
const enableLogging = true;

// Function to conditionally log messages
const customLog = (message) => {
  if (enableLogging) {
    console.log(message);
  }
};

// Example usage
customLog('This message will be logged.');

// To disable logging, set enableLogging to false
// const enableLogging = false;
// customLog('This message will not be logged.');
```

In this example:

The enableLogging variable is used as a configuration flag. Setting it to true enables logging, while setting it to false disables logging.

The customLog function checks the value of enableLogging before calling console.log. If enableLogging is false, the log statement is skipped.

When you want to disable logging, you can set enableLogging to false.

This approach allows you to have fine-grained control over logging in your application. You can also use environment variables or other configuration mechanisms to control logging behavior based on different environments (e.g., development, production).

Alternatively, you can consider using a dedicated logging library that provides more advanced features, such as different log levels (info, warn, error) and centralized logging. Libraries like winston or log4js provide configurable logging options and can be more suitable for larger applications.

---

## 5Q: What is `Doctype` in HTML and Does it make any difference when we don't mention it?
A: DOCTYPE (Document Type Declaration) is an instruction or preamble specified in HTML and XML documents to tell browsers which version of the HTML or XML standard the document is following. It is not an HTML tag but rather a declaration placed at the very beginning of an HTML document.

The DOCTYPE declaration is used to define the document type and version, and it helps browsers render the document correctly. It also influences the browser's rendering mode, determining whether the browser should render the document in standards mode, quirks mode, or almost standards mode.

Here is an example of a typical DOCTYPE declaration for HTML5:

```
<!DOCTYPE html>
```

In HTML5, this declaration is quite simple and is usually sufficient for most modern web development. For older versions of HTML, the DOCTYPE declaration can be more complex.

### Importance of DOCTYPE:

### 1. Rendering Mode:

The presence of a DOCTYPE declaration affects the rendering mode of the browser. It helps the browser determine whether to render the document in standards mode or quirks mode. Standards mode is preferable for consistent rendering across browsers.

### 2. Layout and Box Model:

Different rendering modes may affect how elements are sized and spaced (the box model) in the document. Standards-compliant browsers adhere to a consistent box model, while quirks mode may use a different box model.

### 3. Compatibility:

Including a DOCTYPE declaration is considered good practice for ensuring cross-browser compatibility. It helps avoid inconsistencies in rendering across different browsers.

### Impact of Omitting DOCTYPE:
### Quirks Mode:

If you omit the DOCTYPE declaration, or if it is incorrect, browsers may default to quirks mode. In quirks mode, the browser may use an older, less strict rendering mode, potentially causing layout and styling inconsistencies.

### Compatibility Issues:

Omitting the DOCTYPE may lead to compatibility issues, especially when using newer HTML or CSS features. Different browsers may interpret the document differently, resulting in unpredictable behavior.

### Validation:

A valid DOCTYPE declaration is part of the HTML standard, and adhering to standards helps ensure that your HTML code is valid. Some tools and validators may flag documents without a proper DOCTYPE as potentially problematic.
While modern web development often uses HTML5 and includes a simple DOCTYPE declaration, omitting it may not necessarily break your website. However, it's considered a best practice to include a DOCTYPE to ensure consistent rendering across browsers and to adhere to web standards. Always strive to write well-formed and standards-compliant HTML.

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
A: The spread operator is a syntax in JavaScript that allows for the expansion of elements, such as arrays or objects, into places where multiple elements or key-value pairs are expected. It is represented by three dots (...). The spread operator can be used in various contexts, and its behavior depends on where it's applied.

### 1. Array Spread:
```
const array1 = [1, 2, 3];
const array2 = [...array1, 4, 5];
// Result: array2 is [1, 2, 3, 4, 5]
```
In this example, the spread operator is used to create a new array (array2) by expanding the elements of array1 and adding additional elements.

### 2. Function Arguments:
```
function exampleFunction(arg1, arg2, arg3) {
  console.log(arg1, arg2, arg3);
}

const args = [1, 2, 3];
exampleFunction(...args);
// Result: logs "1 2 3"
```
The spread operator can be used to pass elements of an array as individual arguments to a function.

### 3. Object Spread (introduced in ECMAScript 2018):
```
const obj1 = { key1: 'value1', key2: 'value2' };
const obj2 = { ...obj1, key3: 'value3' };
// Result: obj2 is { key1: 'value1', key2: 'value2', key3: 'value3' }
```

Similar to array spread, the spread operator can be used to create a new object by expanding the properties of an existing object.

The spread operator is a concise and powerful feature in JavaScript, commonly used for tasks like array manipulation, function parameter handling, and object composition.

---

## 11Q: What is `Arrow Function`?
A: An arrow function in JavaScript is a concise way to write function expressions. It was introduced in ECMAScript 6 (ES6) and provides a more compact syntax compared to traditional function expressions. Arrow functions are especially useful for short, one-line functions.

Here's the basic syntax of an arrow function:

```
// Traditional function expression
const add = function (a, b) {
  return a + b;
};

// Arrow function
const addArrow = (a, b) => a + b;
```

### Key features of arrow functions:

### Concise Syntax:
Arrow functions allow you to omit the function keyword, curly braces {}, and return keyword for single expressions. If the function body consists of a single statement, you can write it on one line without the need for explicit return.

### Lexical this:
Arrow functions do not have their own this context. Instead, they inherit the this value from the enclosing scope. This behavior can be beneficial in certain situations, especially when dealing with callbacks and event handlers.

```
function Example() {
  this.value = 42;

  // Traditional function expression
  this.method1 = function () {
    console.log(this.value);
  };

  // Arrow function - retains the 'this' value from the surrounding context
  this.method2 = () => {
    console.log(this.value);
  };
}
```

### 3. No arguments Object:
Arrow functions do not have their own arguments object. If you need to access function arguments, you should use the rest parameters syntax (...args).

```
const exampleFunction = (...args) => {
  console.log(args);
};
```

Arrow functions are commonly used in modern JavaScript development, especially for short, simple functions or when the lexical scoping of this is advantageous. However, it's important to be aware of their differences from traditional functions, particularly regarding the handling of this and the absence of the arguments object.

---

## 12Q: What is `setTimeOut` and `setInterval`?
A: `setTimeout` and `setInterval` are two functions in JavaScript that are used to execute code after a specified delay. They are part of the browser's Web APIs and are commonly used for asynchronous operations.

`setTimeout`:
The setTimeout function is used to execute a specified function or code snippet once, after a specified delay (in milliseconds). The basic syntax is as follows:

```
setTimeout(function, delay);
```

Example:
```
console.log("Start");

setTimeout(function() {
  console.log("Delayed log after 2000 milliseconds");
}, 2000);

console.log("End");
```

In this example, the messages "Start" and "End" will be logged immediately, while the message inside setTimeout will be logged after a delay of 2000 milliseconds (2 seconds).

### 2. setInterval:
The setInterval function is used to repeatedly execute a specified function or code snippet at a fixed time interval. The basic syntax is as follows:

```
setInterval(function, interval);
```

Example:
```
console.log("Start");

setInterval(function() {
  console.log("Repeated log every 1000 milliseconds");
}, 1000);
```

In this example, the message "Start" will be logged immediately, and the message inside setInterval will be logged every 1000 milliseconds (1 second) in an ongoing manner until the program is stopped.

It's important to note that both setTimeout and setInterval use asynchronous execution. They add the specified function or code snippet to the JavaScript event queue, and the execution takes place when the main thread is not busy.

Care should be taken when using setInterval to avoid potential overlapping of executions if the code inside the interval takes longer to execute than the specified interval duration. Additionally, both functions return an identifier that can be used to cancel the scheduled execution using clearTimeout or clearInterval, respectively.

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

## 15Q: Can you explain the concept of closures in JavaScript?
A:  A Closures occur when a function is defined inside another function and has access to the outer function's variables. This happens because the inner function "closes over" the outer function's scope, creating a persistent reference to its variables even after the outer function has finished execution. This is a powerful mechanism for data encapsulation and maintaining state in asynchronous operations.

```
Closure => function + lexical scope
```


### Example 1

```
function outerFunction() {
  let outerVariable = "I am from the outer function";

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

// Create a closure by invoking outerFunction and assigning the result to a variable
let closureFunction = outerFunction();

// Invoke the closureFunction, which has access to outerVariable from its lexical scope
closureFunction(); // Outputs: "I am from the outer function"
```

### Explanation
- When outerFunction is invoked, it returns innerFunction, creating a closure
- The closure closureFunction retains access to outerVariable even after outerFunction has finished executing. When closureFunction is invoked later, it still has access to the outerVariable and logs its value. This encapsulation of variables is a fundamental aspect of closures in JavaScript.


### Example 2: Counter Using Closure

```
function createCounter() {
  let count = 0;

  return function() {
    return ++count;
  };
}

let counter = createCounter();
console.log(counter()); // Outputs: 1
console.log(counter()); // Outputs: 2
console.log(counter()); // Outputs: 3
```

### Exaplanation
In this example, createCounter returns a function that, when invoked, increments and returns the count variable. The closure keeps track of the state (the value of count) even though createCounter has finished executing.



### Example 3: Data Encapsulation

```
function person(name) {
  // Private variable
  let age = 0;

  // Public method with closure
  return {
    getName: function() {
      return name;
    },
    getAge: function() {
      return age;
    },
    setAge: function(newAge) {
      age = newAge;
    }
  };
}

let john = person("John");
console.log(john.getName()); // Outputs: "John"
console.log(john.getAge()); // Outputs: 0
john.setAge(30);
console.log(john.getAge()); // Outputs: 30
```

### Explanation
Here, the `person` function returns an object with methods to interact with private variables (name and age). The closure maintains access to the name and age variables even after person has completed execution.



### Example 4: Callbacks and Asynchronous Operations
```
function fetchData(url, callback) {
  fetch(url)
    .then(response => response.json())
    .then(data => callback(data))
    .catch(error => console.error("Error:", error));
}

function processData(data) {
  console.log("Data received:", data);
}

fetchData("https://api.example.com/data", processData);
```

### Explanation

In this example, `fetchData` is a function that fetches data from a URL and calls the provided `callback (processData)` with the retrieved data. The callback has access to the data variable due to the closure, allowing it to work with the fetched data even though it's called asynchronously.


### Example 5: Timer Using Closure
```
function createTimer(delay) {
  let seconds = 0;
  let intervalId;

  function updateTimer() {
    console.log(`${seconds} seconds have passed.`);
    seconds++;
  }

  return {
    start: function() {
      intervalId = setInterval(updateTimer, delay * 1000);
    },
    stop: function() {
      clearInterval(intervalId);
    }
  };
}

let timer = createTimer(1); // Timer updates every 1 second
timer.start();

// After 5 seconds, stop the timer
setTimeout(() => {
  timer.stop();
}, 5000);

```

### Explanation

In this example, the `createTimer` function returns an object with `start` and `stop` methods. The start method uses setInterval to invoke the `updateTimer` function at regular intervals, and stop uses `clearInterval` to stop the timer. The closure maintains access to the seconds variable, allowing it to persist across multiple invocations of updateTimer. This demonstrates how closures can be used to encapsulate state and functionality in scenarios like timers.

---
## 16Q: Guess the output of the JS code snippet
  ```
  let a = a+1;
  console.log(a)
  ```
A:   
```
VM115:1 Uncaught ReferenceError: a is not defined
    at <anonymous>:1:9
```

## 17Q: Why is `JSONP` used?
A: JSONP (JSON with Padding) is used as a technique for making cross-origin requests in web development. It is primarily used when a web page hosted on one domain wants to make a request for data to a server on a different domain. JSONP is an alternative to the XMLHttpRequest object or the Fetch API, which are subject to the same-origin policy, meaning they cannot make requests to a different domain than the one that served the web page.

Here are a few key reasons why JSONP is used:

### Cross-Origin Requests:
The same-origin policy in web browsers restricts web pages from making requests to a different domain than the one that served the web page. JSONP is a workaround for this limitation, as it allows cross-origin requests by dynamically adding script tags to the DOM, which are not subject to the same-origin policy.

### Support for Old Browsers:
JSONP is an older technique and has been used historically when support for modern alternatives like Cross-Origin Resource Sharing (CORS) wasn't widespread. JSONP is compatible with older browsers that may not fully support CORS.

---

## 17Q: Guess the output of the JS code snippet
```
console.log(typeof typeof 42)
```
A: string

### Here's the breakdown:

`typeof 42` returns 'number' because 42 is a number.
Then, typeof 'number' returns 'string' because the typeof operator returns a string indicating the type of the operand.
So, the overall expression is equivalent to typeof 'number', which results in the output 'string'.

---

## 18Q: Guess the output of the JS code snippet
```
var arr = [1, 2, 3, 4]
var vArr = arr.concat([5]);
alert(arr.length)
alert(vArr.length)
```
A: 
### Output
```
4
5
```
---

## 19Q: To refresh a webpage using JavaScript
A: We can use the `location.reload()` method. This method reloads the current URL, effectively refreshing the page. 

Here's an example:

```
// Refresh the page after 2000 milliseconds (2 seconds)
setTimeout(function() {
  location.reload();
}, 2000);
```

- In this example, `setTimeout` is used to delay the page refresh by 2000 milliseconds (2 seconds). 
- If we want an immediate refresh, we can call `location.reload()` without using setTimeout:

```
// Refresh the page immediately
location.reload();
```

Remember that automatically refreshing a page can be disruptive to the user experience, so it's essential to use this feature judiciously and considerate of the user's expectations.

---

## 20Q: Guess the output of the JS code snippet
```
function varTest()
{
  var x = 31;
  if(true)
  {
    var x = 71;
    console.log(x);
  }
  console.log(x);
}//varTest
```
A: 
### Output
```
71
31
```
---

## 21Q: Sort an object array in an ascending order `[{name: 'Rahul'}, {name: 'Sameer'}, {name: 'Pinky'}, {name: 'Sonu'}]`
A: 
```
const data = [
  { name: 'Rahul' },
  { name: 'Sameer' },
  { name: 'Pinky' },
  { name: 'Sonu' },
];

// Sorting the array in ascending order based on the 'name' property
const sortedArray = data.sort((a, b) => {
  const nameA = a.name.toLowerCase();
  const nameB = b.name.toLowerCase();

  if (nameA < nameB) {
    return -1;
  }
  if (nameA > nameB) {
    return 1;
  }
  return 0;
});

console.log(sortedArray);
```
In this example, the sort function is used with a custom comparison function. The comparison function takes two objects (a and b) and compares their "name" properties in a case-insensitive manner. The result of the comparison determines the order of the sorted array.

After running this code, sortedArray will contain the objects sorted in ascending order based on the "name" property.

### Method 2: 
```
const data = [
  { name: 'Rahul' },
  { name: 'Sameer' },
  { name: 'Pinky' },
  { name: 'Sonu' },
];

const sortedArray = data.sort((a, b) => a.name.localeCompare(b.name));

console.log(sortedArray);
```

---

## 21Q: Guess the output of the code
```
const arr = [3, 5, 7];
arr.foo = 'hello';
for(let i in arr)
{
  console.log(i);
}

for(let i in arr)
{
  console.log(i);
}
```

### Output

```
0
1
2
foo
0
1
2
foo
```

## 22Q: for...in loop in JavaScript
A: The for...in loop in JavaScript is used to iterate over the enumerable properties of an object, including array indices. However, it's important to note that this loop is not recommended for iterating over arrays, as it may also iterate over non-numeric properties.

Here are a couple of examples with the for...in loop along with their expected outputs:

### 1. Iterating over Object Properties

```
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

for (let key in person) {
  console.log(key + ':', person[key]);
}
```

### Output

```
name: John
age: 30
city: New York
```

In this example, the for...in loop iterates over the properties of the person object, and it logs both the property names (key) and their corresponding values to the console.

### Example 2: Iterating over Array Indices
```
const numbers = [1, 2, 3, 4];

for (let index in numbers) {
  console.log('Index:', index, 'Value:', numbers[index]);
}
```

### Output

```
Index: 0 Value: 1
Index: 1 Value: 2
Index: 2 Value: 3
Index: 3 Value: 4
```
In this example, the for...in loop is used to iterate over the indices of the numbers array. It logs both the index and the corresponding value to the console.

### Example 3: Caution with Non-Numeric Properties in Arrays
```
const colors = ['red', 'green', 'blue'];
colors.foo = 'bar';

for (let key in colors) {
  console.log(key + ':', colors[key]);
}
```

### Output
```
0: red
1: green
2: blue
foo: bar
```

In this example, a non-numeric property foo is added to the colors array. The for...in loop iterates over both array indices and additional properties, logging them to the console.

---

## 23Q: Guess the output of the code
```
let i;
for(i=0; i<3; i++)
{
  const log = () => {
    console.log(i);
  }
  setTimeout(log, 100)
}

```

### Output
```
3
3
3
```

However, due to the `asynchronous nature of setTimeout`, the value of `i` at the time the `log` function is executed will be the final value after the loop has completed its iterations. This is a common issue when using setTimeout inside a loop.

### Here's what happens step by step:

- The for loop is executed three times, incrementing i from 0 to 2.
- The setTimeout function is scheduled three times, each with a delay of 100 milliseconds.
- After the loop completes, the value of i is 3.
When the setTimeout callbacks execute after the delay, they all log the final value of i, which is 3.

If we want to capture the value of `i` at each iteration, we can use a `block-scoped` variable (e.g., by using let in the loop header) or by creating a closure for each iteration. 

### Here's an example using a closure:

```
for (let i = 0; i < 3; i++) {
  const log = (value) => {
    console.log(value);
  };
  setTimeout(() => log(i), 100 * i);
}
```
In this example, the value of i is captured in the closure for each iteration, ensuring that the correct value is logged after the corresponding delay. The setTimeout delay is adjusted to 100 * i to stagger the logging.

--- 

## 24Q: Guess the output of the code snippet
```
const promise = new Promise(res => res(2))
promise.then(v => {
  console.log(v);
  return v*2;
})
.then(v => {
  console.log(v);
  return v*2;
})
.then(v => {
  console.log(v);
})
```
A: 
### Output
```
const promise = new Promise(res => res(2));

promise
  .then(v => {
    console.log(v);   // Output: 2
    return v * 2;
  })
  .then(v => {
    console.log(v);   // Output: 4
    return v * 2;
  })
  .then(v => {
    console.log(v);   // Output: 8
  });
```

### Explanation:

- The Promise is created with an immediately resolved value of 2.
- The first then handler is called when the promise is resolved. It logs the value 2 to the console and returns 2 * 2.
- The second then handler is called with the value 4 (result of the previous then). It logs 4 to the console and `returns 4 * 2`.
- The third then handler is called with the value 8 (result of the previous then). It logs 8 to the console.

### Final Output
```
2
4
8
```
Each then handler in the chain receives the result of the previous one and can perform additional operations on it. This chaining is a key feature of promises, allowing you to write asynchronous code in a more readable and sequential manner.

---

## 25Q: Find minimum value from an array `[10, 2, 4, 9, 20, 40]`
A: 

### Method 1
```
const numbers = [10, 2, 4, 9, 20, 40];
const minValue = Math.min(...numbers);

console.log("Minimum value:", minValue);
```

### Method 2
```
const numbers = [10, 2, 4, 9, 20, 40];
const minValue = Math.min.apply(null, numbers);

console.log("Minimum value:", minValue);
```

---

## 26Q: What is `JavaScript`?
A: 

---

## 27Q: What is `map`, `filter`, `find`?
A:

---

## 28Q: What is the difference between `map` and `forEach`
A:

---

## 29Q: Guess the output of the code snippet
```
let c = {greeting : 'hey'};
let d;

d = c;
c.greeting = 'hello!';

console.log(d.greeting);
```
A: 
### Explanation

In the provided code snippet, c and d are both references to the same object. When you assign d = c;, you are not creating a new object; instead, both c and d point to the same object in memory. Therefore, modifying the object through one reference affects both references. Here's a step-by-step explanation:

### Output
```
hello!
```

---

## 30Q: Which one is true?
```
const bird = {
  size : 'small'
}

const mouse = {
  name:'Mickey',
  small: true
}
```
A: Both objects (bird and mouse) are considered truthy in JavaScript because they are non-empty objects.

---

## 31Q: What is the output?
```
const person = {name : 'Lydia'};
Object.defineProperty(person, 'age', {value : 21});

console.log(person);
console.log(Object.keys(person));
```
### Output

```
{ name: 'Lydia', age: 21 }
[ 'name', 'age' ]
```

### Explanation

- The person object is defined with the property `name set to Lydia`.

- `Object.defineProperty` is used to add a new property age to the person object with the value 21.

- The first console.log(person) outputs the entire modified person object, which now includes the age property.

- The second console.log(Object.keys(person)) outputs an array of the enumerable property names of the person object, which are 'name' and 'age'.

---

## 32Q: Guess the output
```
const myPromise = () => Promise.resolve('I have resolved');

function firstFun() {
  // Using the then method to handle the resolved value
  myPromise().then(res => console.log(res));
  console.log('second');
}

async function secondFun() {
  // Using async/await to handle the resolved value
  console.log(await myPromise());
  console.log('second');
}

// Calling the first function
firstFun();

// Calling the second function
secondFun();

```

### Output
```
second
I have resolved
second
I have resolved
```

### Explanation

firstFun Function:

1. `Calls myPromise()` and uses the then method to handle the resolved value asynchronously.
Logs 'second' to the console immediately after initiating the promise.
secondFun Function:

2. `Uses the async/await` syntax to handle the resolved value of the promise.
Logs 'second' to the console immediately after initiating the promise.

3. `Calling the Functions`:
When firstFun is called, 'second' is logged before the resolved value of the promise.
When secondFun is called, the resolved value is logged first due to the await keyword, and then 'second' is logged.

In both cases, 'second' is logged to the console before or after the resolution of the promise, depending on whether the promise is handled using then or async/await. The order of execution is affected by the asynchronous nature of promises and the event loop in JavaScript.

---

## 33Q: Guess the output

### Using 'var'
```
for(var i=0; i<3; i++)
{
  setTimeout(() => console.log(i), 1);
}
```

### Output
```
3
3
3
```

### Explanation:

With `var`, there is only one variable i that is shared across the entire function scope. Due to the asynchronous nature of setTimeout, when the callbacks are executed, they all reference the same i after the loop has completed, resulting in the same value being logged three times:

### Using 'let'
```
for(let i=0; i<3; i++)
{
  setTimeout(() => console.log(i), 1);
}
```

### Explanation:

With let, a new variable i is created for each iteration of the loop, creating a closure for each setTimeout callback. This captures the value of i at the time the callback is created, resulting in the expected output:

### Output
```
0
1
2
```

---

## 34Q: Guess the output
```
const foo = () => console.log('First');
const bar = () => setTimeout(() => console.log('First'));
const baz = () => console.log('Third');

bar();
foo();
baz();
```

### Explanation

- `bar()` schedules a setTimeout callback, but it doesn't immediately log anything. The callback logs 'Second' after a delay specified in setTimeout.

- `foo()` logs 'First' immediately.

- `baz()` logs 'Third' immediately.

### Output

```
First
Third
Second
```
The order is determined by the synchronous execution of foo() and baz() and the asynchronous nature of setTimeout in `bar()`. The setTimeout callback in `bar()` is pushed to the callback queue and executed after the current synchronous code has completed.

---

## 35Q: Guess the output
A: 
```
String.prototype.giveLeelaPizza = () =>
{
  return 'Just give Leela a Pizza'
}

const name = 'Leela';
name.giveLeelaPizza();
```

### Explanation

String.prototype.giveLeelaPizza adds a new method to the prototype of all string objects. This method simply returns the string 'Just give Leela a Pizza'.

`const name = 'Leela';` creates a string variable named name with the value 'Leela'.

`name.giveLeelaPizza();` calls the custom method on the string variable. When you call a method on a primitive value like a string, JavaScript temporarily converts the primitive value to an object (a string object in this case) to access the method. After the method call, it reverts to the primitive value.

The result is logged to the console, which will be the string returned by the giveLeelaPizza method: `Just give Leela a Pizza`.

### Output
```
Just give Leela a Pizza
```

---

## 36Q: How long `cool_secrets` accessible?
```
sessionStorage.setItem('cool_secrets', 123);
```

### Explanation

The `sessionStorage` in JavaScript is a web storage option that allows data to be stored for the duration of the page session. The data stored in sessionStorage is accessible as long as the page or tab is open. When the page is closed or the tab is closed, the data in sessionStorage is cleared.

The item with the key 'cool_secrets' is set to the value 123 in the sessionStorage. As mentioned, this data will persist as long as the page or tab is open. If you close the page or tab, the data will be cleared, and you would need to set it again when the page is reloaded.

Remember that sessionStorage is specific to the page session, and it won't persist across multiple tabs or windows. Each tab or window will have its own separate sessionStorage.

If you want data to persist even when the page is closed and reopened, you might consider using localStorage instead, which has a longer lifespan and persists across sessions.

---

## 37Q: What is the output?
```
function getAge(...args) //rest parameters
{
  console.log(typeof args);
}

getAge(21);
```
### Output

```
object
```
---

## 38Q: Which of these methods the original array
```
const emojis = ['😀', '👑', '💼'];

console.log(emojis.map(x => x + '😀')); // ['😀😀', '👑😀', '💼😀']
console.log(emojis.filter(x => x !== '👑')); //['😀', '💼']
console.log(emojis.find(x => x !== '👑')); //😀
console.log(emojis.reduce((acc, cur) => acc + '😀')); //😀😀😀
console.log(emojis.slice(1, 2, '😀')); //['👑']
console.log(emojis.splice(1, 2, '😀')); //['👑', '💼']

```

### Output
```
['😀😀', '👑😀', '💼😀'] - This logs a new array where each element is the original emoji followed by '😀'
['😀', '💼'] - This logs a new array with elements that do not equal '👑'
😀 - This logs the first element that does not equal '👑', which is '😀'
😀😀😀 - This logs the result of concatenating '😀' to each element in the array using reduce

//The slice method extracts a section of the array, but it only takes two arguments (start and end indices). The third argument ('😀') is ignored. It logs a new array with the sliced elements:
['👑']

// The splice method changes the contents of an array by removing or replacing existing elements. It logs an array of removed elements, which are ['👑', '💼'], and modifies the original emojis array by replacing them with '😀'
['👑', '💼']
```

---

## 39Q: Find elements from an array over 60.
A:
```
let arr = [111, 43, 56, 78, 65, 123];
console.log(arr.filter(elem => elem > 60));
```

### Output
```
[111, 78, 65, 123]
```

---

## 39Q: Multiply elements from an array with 20.
A:
```
let arr = [2, 11, 4, 6, 7, 5, 12];
console.log(arr.map((index, elem) => elem*2));
```

### Output
```
[4, 22, 8, 12, 14, 10, 24]
```

---

## 40Q: Guess the output of the code snippet?
```
console.log('Hello');

setTimeout(() => {
  console.log('How are you?')
}, 0);

console.log('Bye');
```

### Output
```
Hello
Bye
How are you?
```

### Explanation:

- The first console.log('Hello') is executed, and "Hello" is printed to the console.
- The setTimeout function is encountered. It schedules the anonymous arrow function to be executed after a delay of 0 milliseconds. However, the execution of this function is deferred to a later point in the event loop.
- The console.log('Bye') is executed, and "Bye" is printed to the console.
- Now, the event loop gets to the point where it executes the function scheduled by setTimeout. "How are you?" is printed to the console.

---

## 43Q: What is the output of the code snippet below?
```
console.log(a);
console.log(b);
var a = 10;
let b = 20;
```
A: This code will result in an error. The reason is that there's a temporal dead zone for variables declared with let and const before their declaration. In your code, you try to log the values of a and b before they are declared.

### Output

```
undefined
Uncaught ReferenceError: b is not defined at <anonymous>:2:13
```
---

## 44Q: What is `splice` and `slice`?
A: `splice` and `slice` are two array methods in JavaScript, and they serve different purposes.

### 1. splice
The splice method is used to change the contents of an array by `removing or replacing existing elements and/or adding new elements in place`. It modifies the original array. 

### The syntax for splice is as follows:
```
array.splice(start, deleteCount, item1, item2, ...);
```

- `start`: The index at which to start changing the array.
- `deleteCount`: The number of elements to remove from the array. If set to 0, no elements are removed.
- `item1, item2, ...`: Elements to add to the array at the specified start index.

### Example
```
let fruits = ['apple', 'banana', 'orange', 'grape'];

// Remove 1 element starting from index 1 and replace it with 'kiwi' and 'melon'
fruits.splice(1, 1, 'kiwi', 'melon');

console.log(fruits); // Output: ['apple', 'kiwi', 'melon', 'orange', 'grape']
```

### 2. slice
The slice method, on the other hand, returns a shallow copy of a portion of an array into a new array. It doesn't modify the original array. 

### The syntax for slice is as follows:
```
array.slice(start, end);
```

`start`: The beginning index of the slice. If omitted, it starts from the beginning of the array.
`end`: The ending index (exclusive) of the slice. If omitted, it goes up to the end of the array.

### Example
```
let numbers = [1, 2, 3, 4, 5];

// Create a new array containing elements from index 1 to 3 (exclusive)
let slicedNumbers = numbers.slice(1, 3);

console.log(slicedNumbers); // Output: [2, 3]
console.log(numbers); // Original array is unchanged: [1, 2, 3, 4, 5]
```

In summary, splice is used to modify the original array by adding, removing, or replacing elements, while slice is used to create a new array containing a portion of the original array without modifying the original array.

---
## 45Q: What is `reduce`?
A: The reduce method is an array method in JavaScript used for reducing the elements of an array to a single value. It iterates over each element of the array, applying a callback function that you provide, and accumulates a result.

### The syntax for reduce is as follows:

```
array.reduce(callback(accumulator, currentValue, index, array), initialValue);
```

callback: A function that is called for each element in the array. It takes four arguments:

accumulator: The accumulator accumulates the callback's return values. It is the accumulated result of the previous iterations.
currentValue: The current element being processed in the array.
index: (optional) The index of the current element being processed in the array.
array: (optional) The array reduce was called upon.
initialValue: (optional) A value to use as the first argument to the first call of the callback. If no initial value is supplied, the first element in the array will be used as the initial accumulator value, and the iteration will start from the second element.

### Example
```
let numbers = [1, 2, 3, 4, 5];

let sum = numbers.reduce(function(accumulator, currentValue) {
  return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15
```

In this example, the reduce method starts with an initial accumulator value of 0 and adds each element of the array to it. The final result is the sum of all the elements in the array.

The reduce method is powerful and versatile. You can use it for various tasks, such as calculating averages, finding the maximum or minimum value, flattening arrays, and more. It's a functional programming concept that allows you to express complex operations concisely.

---

## 46Q: Print `Hello, How are you?` as `Hello Divya, How are you?`
A:
### Using Template Literals
```
let name = "Divya";
let greeting = `Hello ${name}, How are you?`;

console.log(greeting);
```

### Using replace
```
let str = "Hello, How are you?";
console.log(str.replace("Hello", "Hello Divya"));
```
---

## 47Q: What could be the difference between `map` and `filter` for elements returned over 5 from an array in JavaScript?
A: 


---

## 48Q: What is `optional chaining`?
A: 

---

## 49Q: What is `API Integration`? Which is better `fetch` and `axios`?
A: 

---

## 50Q: What is `Material-UI`?
A:

---

## 51Q: What are `const with Primitive` and `const with non-primitive`?
A:

---

## 52Q: What is the output of the code snippet and get output `1, 2 without let`?
```
for(var i=1; i<=2; i++)
{
  setTimeout(function(){
    alert(i)
  }, 100)
}
```

---

## 53Q: What is Types of copy(`Shallow copy` and `Deep copy`)?
A:

---

## 54Q: What is `Prototype` and How it works?
A:

---

## 55Q: When do we use `bind` vs `call` and `apply`?
A:

---

## 56Q: Difference between `Spread Operator` and `Rest Operator`?
A:

---

## 57Q: Get the second last element from the array.
```
let arr = ['a', 'b', 'c', 'd', 'e', 'f'];
output: 'e'
```

### Output
```
let arr = ['a', 'b', 'c', 'd', 'e', 'f'];
let secondLastElement = arr[arr.length - 2];

console.log(secondLastElement); // Output: 'e'
```
---

## 58Q: What is the output of the code snippet?
```
console.log(3+"3");
console.log(3-"3");
```
A: 
### Output
```
33
0
```
### Explanation:

### Example 1: console.log(3 + "3");

The first operand is a number (3).
The second operand is a string ("3").
Since one operand is a string, the + operator is used for string concatenation.
The number 3 is converted to a string, and then the strings are concatenated.
The result is the string '33'.
Therefore, console.log(3 + "3"); will output 33.

### Example 2: console.log(3 - "3");

The first operand is a number (3).
The second operand is a string ("3").
When the - operator is used, JavaScript tries to convert the string operand to a number.
The string "3" is converted to the number 3.
The subtraction is performed as 3 - 3.
The result is the number 0.
Therefore, console.log(3 - "3"); will output 0.

---

## 59Q:
