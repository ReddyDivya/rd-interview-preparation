# React Interview Question and Answers

## How to create a `React Projects`?
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

## What is `Packaging content`?
A: `Packaging the content` generally refers to bundling and preparing the application's source code, assets, and dependencies for deployment.
- This process ensures that the application is optimized for performance, reducing file sizes and organizing the code in a way that can be efficiently served to users.
- Like Minification, Bundling (mostly used is Webpack), Transpilation, Tree Shaking, Code Splitting.
- Webpack, together with other tools like Babel, ESLint, and various plugins, Webpack facilitates an efficient and optimized build process.
- By packaging the content in this way, developers can ensure that their React applications are performant, load quickly, and provide a good user experience.
- Additionally, the resulting optimized bundles are more suitable for deployment to production environments.

---

## What is `build`?
A: `Create-react-app` package has a `webpack bundler` which compiles our project and runs it on localhost(server).

## What is in the `public` folder?
A: `index.html` - The main HTML file for our React application. This file typically contains a root element (e.g., a <div> with an id like `root`) where our React app is mounted. It also includes `links to external stylesheets`, `scripts`, and other `meta` tags.

`Favicon and Other Static Assets` - Images, icons, or other files that should be served directly by the server. For example, a favicon.ico file for the website's icon.

`manifest.json` - A JSON file that provides metadata about the web application. It includes information such as the name, description, icons, and other settings. This is often used for `Progressive Web App (PWA) configurations`.

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
