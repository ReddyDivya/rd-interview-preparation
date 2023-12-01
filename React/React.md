# React Interview Question and Answers
---

- How to create a `React Projects`?
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

- What is `Packaging content`?
A: `Packaging the content` generally refers to bundling and preparing the application's source code, assets, and dependencies for deployment.
- This process ensures that the application is optimized for performance, reducing file sizes and organizing the code in a way that can be efficiently served to users.
- Like Minification, Bundling (mostly used is Webpack), Transpilation, Tree Shaking, Code Splitting.
- Webpack, together with other tools like Babel, ESLint, and various plugins, Webpack facilitates an efficient and optimized build process.
- By packaging the content in this way, developers can ensure that their React applications are performant, load quickly, and provide a good user experience.
- Additionally, the resulting optimized bundles are more suitable for deployment to production environments.

---

- What is `build`?
A: `Create-react-app` package has a `webpack bundler` which compiles our project and runs it on localhost(server).

- What is `Functional Components`?
- What is `class components`?
- What is `JSX`?
- How to `create components` i.e `Functional`, `Class`?
- What are `props`?
- What are `states`?
- What is `context`?
- How do you `conditionally Render the component`?

https://github.com/DopplerHQ/awesome-interview-questions#reactjs

https://arc.dev/developer-blog/reactjs-interview-questions/
