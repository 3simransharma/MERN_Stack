# ReactJS Notes

# JSX (JavaScript XML)

## What is JSX?

JSX stands for **JavaScript XML**.

It is a syntax used in React that allows us to write **HTML-like code
inside JavaScript**. JSX makes it easier to design the user interface
because it looks similar to HTML.

Example:

``` jsx
function App() {
  return (
    <h1>Hello, React!</h1>
  );
}
```

Although it looks like HTML, JSX is **not HTML**. Before the browser can
understand it, React converts JSX into normal JavaScript.

## Why is JSX Used?

-   Makes UI code easy to read and write.
-   Allows HTML-like syntax inside JavaScript.
-   Makes components easier to build.
-   Reduces the amount of code compared to creating HTML elements
    manually.
-   Helps organize the user interface into reusable components.

## Features of JSX

-   HTML-like syntax
-   Can use JavaScript expressions inside `{ }`
-   Supports reusable components
-   Easier to maintain than plain JavaScript DOM code

Example:

``` jsx
const name = "Kriti";

function App() {
  return <h1>Welcome, {name}!</h1>;
}
```

# How Does a React Application Load?

When we start a React application using:

``` bash
npm run dev
```

the following steps take place.

## Step 1: Vite Starts the Development Server

The command:

``` bash
npm run dev
```

starts a local development server.

Example:

``` text
VITE v8.1.5 ready

➜ Local: http://localhost:5173/
```

The application is now available at the Local URL.

## Step 2: The Browser Requests the Application

When you open the Local URL, the browser sends a request to the Vite
development server.

``` text
Browser
   │
   │ Request
   ▼
Vite Development Server
```

## Step 3: Vite Sends `index.html`

The Vite server sends the `index.html` file to the browser.

Inside `index.html`, there is a script tag like this:

``` html
<script type="module" src="/src/main.jsx"></script>
```

This tells the browser to load the `main.jsx` file.

## Step 4: `main.jsx` Executes

`main.jsx` is the entry point of the React application.

It imports:

-   React
-   ReactDOM
-   App.jsx
-   index.css

Example:

``` jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import "./index.css";
```

Then it renders the App component:

``` jsx
ReactDOM.createRoot(document.getElementById("root")).render(
  <App />
);
```

## Step 5: `App.jsx` Loads

React executes the `App.jsx` component.

This component contains the main user interface of the application.

Example:

``` jsx
function App() {
  return <h1>Hello React!</h1>;
}

export default App;
```

## Step 6: Other Components Load

If `App.jsx` contains other components, React loads them one by one.

Example:

``` jsx
function App() {
  return (
    <>
      <Navbar />
      <Home />
      <Footer />
    </>
  );
}
```

Loading order:

``` text
App
 ├── Navbar
 ├── Home
 └── Footer
```

## Step 7: React Creates the User Interface

React converts the JSX into JavaScript and then updates the browser's
DOM. Finally, the browser displays the webpage.

# Complete Loading Flow

``` text
User
   │
   │ Opens http://localhost:5173
   ▼
Vite Development Server
   │
   │ Sends index.html
   ▼
index.html
   │
   │ Loads
   ▼
main.jsx
   │
   │ Renders
   ▼
App.jsx
   │
   │ Loads
   ▼
Other Components
   │
   ▼
React Converts JSX
   │
   ▼
Browser DOM
   │
   ▼
Web Page Displayed
```

# Summary

-   JSX stands for JavaScript XML.
-   JSX allows us to write HTML-like code inside JavaScript.
-   `main.jsx` is the entry point of every React application.
-   `App.jsx` is the main component.
-   Vite starts the development server.
-   `index.html` loads `main.jsx`.
-   `main.jsx` renders `App.jsx`.
-   React converts JSX into JavaScript and updates the DOM.
-   Finally, the browser displays the webpage.
