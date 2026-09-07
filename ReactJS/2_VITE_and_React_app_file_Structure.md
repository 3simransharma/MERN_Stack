# ReactJS Notes

## What is Vite?

**Vite** (pronounced **"veet"**/**vit**/**vITe**) is a modern build tool used to create
and develop web applications. It helps developers create React projects
quickly and provides a faster development experience.

In simple words, **Vite prepares everything required for a React
project**, so we can start writing code without doing manual setup.

## Why is Vite Used?

Vite is used because it makes React development faster and easier.

-   Creates a React project automatically.
-   Starts the development server very quickly.
-   Reloads changes instantly without refreshing the entire page.
-   Builds optimized files for deployment.
-   Supports modern JavaScript features.
-   Easy to use and lightweight.

## Advantages of Vite

-   Faster than older React tools.
-   Easy project setup.
-   Instant updates while coding (Hot Module Replacement - HMR).
-   Better performance during development.
-   Recommended for new React projects.

## Vite vs Create React App (CRA)

  Create React App (CRA)     Vite
  -------------------------- ----------------------
  Slower startup             Very fast startup
  Slower page reload         Instant updates
  Larger project setup       Lightweight setup
  Older tooling              Modern tooling
  Takes more time to build   Faster build process

# What Happens When We Create a React Project?

When we run the following command:

``` bash
npm create vite@latest my-react-app -- --template react
```

Vite automatically:

1.  Creates the project folder.
2.  Installs the required packages.
3.  Generates the project structure.
4.  Creates all necessary React files.
5.  Starts the development server.

After that, we can immediately begin writing React code.

# React Project Structure

## 1. node_modules

-   Stores all installed packages and libraries.
-   Created automatically after running `npm install`.
-   Do not edit files inside this folder manually.

## 2. public

-   Stores static files.
-   Files inside this folder are served directly to the browser.
-   Examples: Images, icons, PDF files, favicon.

## 3. src (Source Folder)

-   The main folder of a React project.
-   Contains all the application source code.
-   Most development work is done inside this folder.

## 4. assets

-   Stores project resources such as images, logos, fonts, and icons.

## 5. App.jsx

-   The main React component.
-   Used to design the application's user interface.
-   Usually contains other React components.

## 6. App.css

-   Contains styles for the **App** component only.

## 7. index.css

-   Contains global styles for the entire application.

## 8. main.jsx

-   The entry point of the React application.
-   Loads the **App** component into the browser.
-   Runs first when the application starts.

## 9. index.html

-   The main HTML page of the project.
-   React renders the application inside this page.

## 10. package.json

-   Stores project information.
-   Contains project name, version, dependencies, and scripts.

## 11. package-lock.json

-   Stores the exact versions of installed packages.
-   Ensures the project behaves the same on every computer.

## 12. vite.config.js

-   Configuration file for Vite.
-   Used to customize project settings.

## 13. README.md

-   Documentation file for the project.

## 14. .gitignore

-   Lists files and folders that Git should ignore.

# React Application Flow

``` text
main.jsx
    │
    ▼
App.jsx
    │
    ▼
Other Components
    │
    ▼
Browser (User Interface)
```

## Flow

1.  `main.jsx` is executed first.
2.  It loads the `App.jsx` component.
3.  `App.jsx` displays the main user interface.
4.  Other components are rendered inside `App.jsx`.
5.  The browser displays the final web page.

# Summary

-   Vite is a fast build tool for React.
-   It creates the project structure automatically.
-   `src` is the main coding folder.
-   `main.jsx` is the entry point.
-   `App.jsx` is the main component.
-   `package.json` manages dependencies and scripts.
-   `node_modules` stores installed packages.
-   `public` and `assets` store project resources.
