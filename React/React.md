# React Interview Question and Answers

## 1Q: How to create a `React Projects`?
A: `Create React App (CRA)` is a package, more precisely, it's a command-line tool that sets up a new React project with a sensible default configuration.
  - We need to have both `Node.js` and `npm (Node Package Manager)` installed on our machine. CRA relies on these tools for project setup and management `Node > 14 version`.
  - This package give us bundlers, set up of jest, react-testing libraries. It's a ready to work on project instead of installing all these.
  - Create React App doesn’t handle backend logic or databases; it just creates a frontend build pipeline, so we can use it with any backend we want.
  - It uses `Babel` and `webpack`, but we don’t need to know anything about them.
  - When we’re ready to deploy to production, create a minified bundle with `npm run build`.
  - We don’t need to install or configure tools like `webpack` or `Babel`. They are preconfigured and hidden so that we can focus on the code.

```
npx create-react-app demo-app
cd demo-app
npm start //starts development server
```

---

## 2Q: What is `Packaging content`?
A: `Packaging the content` generally refers to bundling and preparing the application's source code, assets, and dependencies for deployment.
- This process ensures that the application is optimized for performance, reducing file sizes and organizing the code in a way that can be efficiently served to users.
- Like Minification, Bundling (mostly used is Webpack), Transpilation, Tree Shaking, Code Splitting.
- Webpack, together with other tools like Babel, ESLint, and various plugins, Webpack facilitates an efficient and optimized build process.
- By packaging the content in this way, developers can ensure that their React applications are performant, load quickly, and provide a good user experience.
- Additionally, the resulting optimized bundles are more suitable for deployment to production environments.

---

## 3Q: What is `build`?
A: `Create-react-app` package has a `webpack bundler` which compiles our project and runs it on localhost(server).

---

## 4Q: What is in the `public` folder?
A: `index.html` - The main HTML file for our React application. This file typically contains a root element (e.g., a <div> with an id like `root`) where our React app is mounted. It also includes `links to external stylesheets`, `scripts`, and other `meta` tags.

`Favicon and Other Static Assets` - Images, icons, or other files that should be served directly by the server. For example, a favicon.ico file for the website's icon.

`manifest.json` - This is a JSON file that provides metadata about the web application. It includes information such as the application's name, icons for different devices, background color, display mode, and other settings. The manifest is used by the browser when a user decides to add the web app to their home screen.

`robots.txt` - A file used by web crawlers to understand how they should navigate and index your site. It specifies rules about which parts of your site can or cannot be crawled.

The public folder is useful for assets that don't need to go through the build process and can be referenced directly from the HTML file. When we build our React application, the contents of the public folder are typically copied to the build output directory (e.g., build) as it is.

```
index.html

<head>
  <meta charset="utf-8" />
  <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="theme-color" content="#000000" />
  <meta name="description" content="Web site created using create-react-app" />
  <title>Netflix GPT</title>
</head>
<body>
  <noscript>You need to enable JavaScript to run this app.</noscript>
  <div id="root"></div>
</body>
```

---

## 5Q: What is `Progressive Web App (PWA) configurations`?
A: `Progressive Web App (PWA)` configurations refer to the settings and metadata that define how a web application behaves when installed on a user's device as a Progressive Web App. PWAs are web applications that provide a native app-like experience while being accessed through a web browser. They aim to combine the best features of both web and native apps, offering offline capabilities, push notifications, and more.

---

## 6Q: What is the purpose of `robots.txt`?
A: `robots.txt` is a standard used by websites to communicate with web crawlers and other automated agents, specifying which areas of the site they are allowed to crawl and index. It is a simple text file placed at the root of a website's domain. The primary purpose of robots.txt is to provide guidance to web crawlers and prevent them from accessing certain parts of the website. This helps in SEO(Search Engine Optimization) and makes our application crawlable for search engines.

```
User-agent: *
Disallow: /private/
Disallow: /restricted-page.html
```

`User-agent: *`: Applies rules to all web crawlers (the wildcard * means "all user-agents").
`Disallow: /private/`: Instructs web crawlers not to crawl any content under the /private/ directory.
`Disallow: /restricted-page.html`: Specifically disallows crawling of the page located at /restricted-page.html.

---

## 7Q: Who are `web crawlers`?
A: Web crawlers, also known as spiders, bots, or web robots, are automated programs or scripts designed to browse and index content on the internet. They play a crucial role in the operation of search engines and other services that rely on collecting information from web pages.

---

## 8Q: What is `nodemodules`?
A: The `node_modules` directory is a standard directory in a Node.js project that contains the dependencies (third-party packages or libraries) used by the project. When you install packages using Node Package Manager (npm) or Yarn, these packages are downloaded and stored in the node_modules directory.

```
## dependenies management
"dependencies": {
  "express": "^4.17.1",
  "axios": "^0.21.1"
}
```

- node_modules directory is not included in version control systems (like Git). Instead, the `package.json` and `package-lock.json` files are used to describe the project's dependencies.
  
- Developers can then `run npm install` to fetch the dependencies based on the version information in these files.

- The node_modules directory can contain a large number of files, especially for projects with many dependencies. These files include the actual code of the dependencies, as well as various configuration files and documentation. Since these files are managed by package managers, developers typically don't need to interact directly with the contents of the node_modules directory.

---

## 9Q: What is `Functional Components`?
A: `Functional components` are a type of component that are primarily defined as normal JavaScript functions.
- They are also sometimes referred to as stateless components because, initially, they can't manage state or lifecycle methods. However, with the introduction of React Hooks in React 16.8, functional components gained the ability to use state and lifecycle features through hooks.
```
import React from 'react';

const FunctionalComponent = () => {
  return (
    <div>
      <h1>Hello, I'm a functional component!</h1>
    </div>
  );
};

export default FunctionalComponent;
```
- const FunctionalComponent declares a functional component.
- () => {...} is an arrow function that defines the component's body.
- The component returns JSX, describing the structure and content to be rendered.

---

## 10Q: What is `JSX`?
A: `JSX stands for JavaScript XML`. It's a syntax extension for JavaScript recommended by React for describing what the UI should look like. 
- JSX is used to create React DOM elements.
- JSX is not HTML inside the JavaScript. JSX is an HTML-like syntax.
- JSX is not part of React.
- We can write React without JSX. It provides a more concise and readable syntax for defining UI components. JSX makes developers' lives easy.

```
const element = <h1>Hello, JSX!</h1>;
```
- The JSX is transformed into a series of React.createElement calls during the build process.

- We can embed JavaScript expressions within curly braces {}. This allows us to include dynamic content and JavaScript logic within our JSX.
```
const name = "John";
const element = <p>Hello, {name}!</p>;
```

--- 
## 11Q: What is `state` and `props`?
A: `state` and `props` are used to manage and pass data in a React application. 

### State:
- state is a built-in object in React components that represents the current condition or data of the component.
- It allows a component to manage its own data and to be aware of changes to that data. When the state of a component changes, React automatically re-renders the component to reflect the updated state.

### In functional components, state can be managed using the `useState` hook.
```
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={incrementCount}>Increment</button>
    </div>
  );
};
```

### In class components, state is initialized in the constructor using this.state and updated using this.setState().
```
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  incrementCount = () => {
    this.setState({ count: this.state.count + 1 });
  };

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={this.incrementCount}>Increment</button>
      </div>
    );
  }
}
```
### Props:
- props (short for properties) are inputs to a React component. They are values passed from a parent component to a child component.
- Props allow us to customize and configure a component based on the data received from its parent. They make it easy to reuse components and create a hierarchy of components.
- Props are passed as attributes in JSX when a component is used.

In function components,
```
// Parent Component
import React from 'react';
import ChildComponent from './ChildComponent';

const ParentComponent = () => {
  const data = 'Hello from parent!';
  
  return <ChildComponent message={data} />;
};

// Child Component
const ChildComponent = (props) => {
  return <p>{props.message}</p>;
};
```

### let's see how destructuring can be applied to make the code more concise
```
// With destructuring
import React from 'react';

const ChildComponent = ({ message }) => {
  return (
    <div>
      <p>{message}</p>
    </div>
  );
};

export default ChildComponent;
```
- The ParentComponent passes the message prop to the ChildComponent, which then uses that prop to display the message.

In class components, props are accessed through the `this.props` object. When a component is created, React automatically assigns the props passed to it as attributes of this.props. Here's an example demonstrating how props are used in a class component:

- Remember that props in class components are read-only.

```
import React from 'react';

class Greeting extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, {this.props.name}!</h1>
        <p>{this.props.message}</p>
      </div>
    );
  }
}

// Example usage of the Greeting component
const App = () => {
  return (
    <Greeting name="John" message="Welcome to React!" />
  );
}
```
---
## 12Q: What is `useState`?
A: `useState` is a React hook that was introduced in React 16.8 to functional components. It provides a way for functional components to have local state. 
- Before the introduction of hooks, only class components could manage state. Now, with useState, functional components can manage state as well, making them more powerful and expressive.

```
import React, { useState } from 'react';

const Counter = () => {
/*
  The useState hook returns an array with two elements:
  - 1. The current state value.
  - 2. A function that allows you to update the state.
*/
  const [count, setCount] = useState(0); //initial value is 0

  const increment = () => {
    // setCount is used to update the state
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```
- When the state is updated, React re-renders the component, and the new state value is displayed.
- We can use multiple useState calls in a single functional component to manage multiple pieces of state independently.

---

## 13Q: What is the difference between the `useState variables` and `normal variables`?
A: The primary difference between useState variables and normal variables lies in how they interact with the React component lifecycle and the rendering process. 

### useState Variables
- It enables functional components to have a local state.
- When a useState variable is updated using its corresponding update function (e.g., setCount), React automatically triggers a re-render of the component.
- React efficiently updates only the parts of the DOM affected by the state change, optimizing performance.
```
// Using useState
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};
```

### Normal variables
- If we use normal variables to store data in a React component, changing the value of those variables does not automatically trigger a re-render.
- Normal variables are commonly used in class components and functional components without hooks.
- Normal variables can be used for various purposes, including storing data that doesn't affect the component's rendering or doesn't need to trigger a re-render.
```
import React from 'react';

class ExampleComponent extends React.Component {
  render() {
    const msg = "This is a normal variable";

    return (
      <div>
        <p>{msg}</p>
      </div>
    );
  }
}

export default ExampleComponent;
```

---
## 14Q: Why are we using the `[] in useState` initialization?
A: In the useState hook in React, the square brackets [] are used as array destructuring to capture the current state value and the function that updates that state. 
- The [] around state and setState are part of the array destructuring syntax in JavaScript. They are used to unpack the values returned by useState into separate variables.

```
const [state, setState] = useState(initialState);
```
Here's a breakdown of how it works:

### Initialization:

useState(initialState) initializes the state with an initial value, and it returns an array where:
The first element is the current state value (state in the example).
The second element is the function to update the state (setState in the example).

### Array Destructuring
The const [state, setState] syntax is array destructuring. It takes the two elements from the array returned by useState and assigns them to the variables state and setState.

```
import React, { useState } from 'react';

const Counter = () => {
  // useState returns an array: [count, setCount]
  const [count, setCount] = useState(0);

  const increment = () => {
    // setCount is used to update the count state
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```
- Using array destructuring makes the code concise and readable, and it's a common pattern when working with the useState hook.

In this example, useState(0) initializes the count state with an initial value of 0. The array destructuring const [count, setCount] is used to capture the current state value (count) and the function to update the state (setCount). The increment function uses setCount to update the state, triggering a re-render with the updated value.

---
## 15Q: What's `named export` and `export default` in React?
A: There are two main ways to export elements from a module: `named exports (normal exports)` and `default exports`.

### Named Exports (Normal Exports):
In named exports, we have to export multiple elements from a module using the export keyword, and we have to import them using the same name in the import statement. Each exported element is identified by a name.

```
// File: MyComponent.js

export const FunctionComponent = () => {
  // ... component logic
};

export const AnotherComponent = () => {
  // ... component logic
};
```

To import these components in another file, you use their names:
```
import { FunctionComponent, AnotherComponent } from './MyComponent';
```

### Export Default
In export default, we export a single element as the default export from a module. There can only be one default export per module. When importing a default export, we can use any name for the imported element.

```
// File: MyComponent.js

const MyComponent = () => {
  // ... component logic
};

export default MyComponent;
```

To import the default export in another file, you can use any name:
```
import CustomName from './MyComponent';
```

---

## 16Q: Is it a good way to add inline CSS style to elements?
A: Not a good way to add inline CSS style to the elements. One good approach is writing in an App.css(external CSS file). Another approach is a CSS Framework like Tailwind CSS.

---

## 17Q: What is `Tailwind CSS`?
A: `Tailwind CSS` is a CSS Framework, it is a tool that helps us style our website or large web application. It gives us pre-built classes, Tailwind provides small building blocks (called utility classes) that we can combine to create our own unique designs.

### Install `Tailwind CSS`
A: ### Install
```
npm install -D tailwindcss
npx tailwindcss init
```

It creates tailwind.config.js file.

### Configure your template paths (tailwind.config.js)
```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### Add the Tailwind directives to your CSS (src/App.css)
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```
---
## 18Q: Why do we add tailwind directives to index.css?
A: Tailwind CSS is typically added to the index.css file (or any other main CSS file) using directives to import the Tailwind styles and utilities. 

The directives are specific comments that instruct tools like PostCSS to process and include the Tailwind styles into the final CSS file. These directives are necessary for integrating Tailwind into our project.

### To center an image using Tailwind CSS
![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/a373e306-6b08-45e5-ada4-87dced45bc52)

---

## 19Q: Can you build a `carousal` in React?
A: ![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/fd149223-7520-432b-ac0b-db1669e9d390)

### Optimizing the above code
![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/88b70faa-04b9-41d5-a110-a84f36530eab)


---
## 20Q: Why to use the `key` in the map?
A: `Map` is a data structure that allows us to store `key-value pairs` where each key and value can be of any data type.
When working with React, using keys in a Map (or more commonly, in React components' lists) is important for several reasons:

### Uniqueness: 
Keys must be unique within a map or a list of React elements. This uniqueness helps React identify which items have changed, been added, or been removed. This is crucial for React's efficient rendering algorithm, which aims to update only the parts of the DOM that have changed.

### Performance:
Using keys allows React to efficiently update the DOM by reordering, adding, or removing only the necessary elements. This improves the performance of our React application, especially when dealing with large lists.

### Stability: 
React uses keys to determine the identity of elements. If the order of elements changes without keys, React might mistakenly think that elements have been added or removed, leading to unnecessary re-rendering and potential bugs. Keys provide stability to the identity of elements, helping React correctly identify changes.

```
function MyComponent({ items }) {
  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```
In this example, each <li> element has a key attribute with a unique identifier (item.id). This helps React efficiently update the list when the items array changes.

---

## 21Q: Build an `Image Slider`, which automatically slides after every 5 seconds?
A: We can do it using `setTimeOut` for that we require `useEffect` hook. React has a Render cycle after that useEffect is called. 

### setIimeOut
The setTimeout function is commonly used to schedule the execution of a function after a specified delay.

![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/79657126-562d-46ba-8db2-9171f2dafc11)

---
## 22Q: What is `useEffect`?
A: The `useEffect` hook is used to perform side effects in functional components. The useEffect hook takes two arguments: a function that contains the code for the side effect, and an optional dependency array. The dependency array is a crucial part of useEffect, and it serves several purposes.

---

## 23Q: Why dependency array is required in `useEffect`?
A: It's important to include the variable in the dependency array. This ensures that the effect is re-run whenever those values change. If we omit the dependency array, the effect might capture stale values and not react to changes.

```
import React, { useEffect, useState } from 'react';

function MyComponent({ data }) {
  const [processedData, setProcessedData] = useState([]);

  useEffect(() => {
    // Perform some side effect with the data
    const processed = processData(data);

    // Update the state
    setProcessedData(processed);

    // Cleanup function (executed on unmount)
    return () => {
      // Cleanup code here
    };
  }, [data]); // Dependency array with 'data'

  return (
    <div>
      {/* Render component using processedData */}
    </div>
  );
}
```

---
## 24Q: Why do we need to clear time out?
A: Whenever a component is unmounting, we need to clear the set timeout. It's a good practice otherwise it leads to several issues. 

The clearTimeout function is used to cancel a timeout that has been previously set with setTimeout. Here are some reasons why clearing timeouts is important:

![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/e16c3100-426b-42b5-9d01-8b8988a3a79d)

---

## 25Q: Is cleanup mandatory or optional?
A: It is mandatory.

## 26Q: What is Lifecycle?
A: A lifecycle refers to the various stages that a component or application goes through from mount, update, and unmount.

### React Component Lifecycle in a class component

```
constructor()
render()
componentDidMount()
componentDidUpdate()
componentWillUnmount()
```

### 1. Mount Phase
constructor()
render(dummy data)
  -> HTML render(with dummy data)
  -> API Calls
  -> `this.setState` -> state variable is updated

### 2. Update Phase
  -> render(API data)
  -> HTML render(new API data)
  -> componentDidUpdate() -> `this.setState` -> state variable is updated
  
---

## 27Q: Is it a good way to keep data in components like image info?
A: No, it's not a good practice to keep in a component directly. We should keep all in a constant file.

---
## 28Q: What is `Context API`?
A:

---

## 29Q: What is the difference between `Controlled components` and `UnControlled components`?
A:

---

## 30Q: What are the advantages of using `React Hooks`?
A:

---

## 31Q: What is the use of `key in React JS`?
A: 

---

## 32Q: What is `HOC with an example`?
A:

---

## 33Q: What is the difference between `Real DOM` and `Virtual DOM`?
A:

---

## 34Q: What is `useMemo`?
A:

---

## 35Q: What is `useContext`?
A:

---

## 36Q: When to use `useContext` and `Redux`?
A:

---

## 37Q: What is `Hoisting`?
A:

---

## 38Q: What is the output of the below code snippets?
![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/df06ac96-f77a-4c36-8410-e3e81010d9bc)

![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/3dcc5d6f-dc12-491b-bd80-58515652de3b)
 
![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/76bcf30c-5e8c-4a95-9342-73ba753da470)

![image](https://github.com/ReddyDivya/rd-interview-preparation/assets/34181144/eba640c0-32ce-4bf3-9784-9d979086a255)

---

## 39Q: What are the `features of React`?
A: 

---

## 40Q: Is `React faster than the Angular`?
A:

---

## 41Q: Why React is a `One-way data binding`?
A:

---

## 42Q: What is `Babel`?
A:

---

## 43Q: Is React a framework or library?
A:

---

## 44Q: What is the use of `ES6`?
A:

---

## 45Q: What are the different parts of components?
A: Function, class components

---

## 46Q: Which one is better `Function Components` and `Class Components`?
A:

---

## 47Q: What is `Node JS`?
A:

---

## 48Q: What is `Prop drilling`?
A:

---

## 49Q: Can we create `Custom Hooks`. Did you use it anytime??
A: 

---

## 50Q: What is `React strict Mode`?
A:

---

## 51Q: How to pass data between components and which one is better?
A: props, context API, Redux, callback functions

---

## 52Q: How does `Routing` work?
A:

---

## 53Q: How to `add Redux to our React project`? 
A:

---

## 54Q: Explain hooks other than useState and useEffect?
A: useRef, useReducer


---

## 55Q: Why do we write `console.log`?
A: `Environment Variable`
```
if (process.env.NODE_ENV === 'development') {
    console.log("This will only be logged in development mode");
}
```
In a production environment, the NODE_ENV is usually set to 'production', so these logs won't appear.

---

## 56Q: If we have several `console.log` in our application and want to enable or disable it whenever we want. How do we achieve it?
A: Common function



## 46Q: 






---

## 28Q: What is `class components`?
- How to `create components` i.e `Functional`, `Class`?
- What are `props`?
- What are `states`?
- What is `context`?
- How do you `conditionally Render the component`?

https://github.com/DopplerHQ/awesome-interview-questions#reactjs

https://arc.dev/developer-blog/reactjs-interview-questions/
