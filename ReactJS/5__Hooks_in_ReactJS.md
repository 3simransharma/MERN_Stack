# Hooks in ReactJS

# Introduction

While developing React applications, components often need additional
features such as:

-   Storing data
-   Updating data
-   Performing tasks automatically
-   Sharing data between components
-   Improving application performance

React provides these features through **Hooks**.

<br>

# What are Hooks?

A **Hook** is a special function provided by React that allows
**Functional Components** to use React features.

Before Hooks were introduced, these features were available only in
**Class Components**.

> **Definition:** Hooks are special functions in React that allow
> Functional Components to use features such as State, Effects, Context,
> and References.

------------------------------------------------------------------------

# Why Do We Need Hooks?

Consider the following component.

``` jsx
function App() {
    return (
        <h2>Hello Students</h2>
    );
}
```

This component only displays the user interface.

Suppose we want to:

-   Store a counter value
-   Display a welcome message automatically
-   Load student information from a server
-   Access an input box directly
-   Share login information with other components

A normal Functional Component cannot perform these tasks by itself.

React provides **Hooks** to add these capabilities.

------------------------------------------------------------------------

# Why are they Called Hooks?

The word **Hook** means **to attach or connect**.

Just as a hook allows us to hang different objects on a wall, React
Hooks allow us to attach additional features to a Functional Component.

``` text
Functional Component
        │
        ▼
      Hook
        │
        ▼
Additional React Feature
```

Each Hook provides a different feature.

------------------------------------------------------------------------

# Commonly Used React Hooks

  ## Commonly Used React Hooks

| Hook | Purpose | Common Applications / Examples |
|------|---------|--------------------------------|
| **useState()** | Stores and updates component data (State). | Counter, Like Button, Form Data |
| **useEffect()** | Performs tasks after a component is rendered. | API Call, Page Title, Timer |
| **useContext()** | Shares data between multiple components without passing Props repeatedly. | User Login, Theme Switching |
| **useRef()** | Accesses DOM elements or stores mutable values without causing a re-render. | Focus Input Box, Access Input Elements |
| **useMemo()** | Stores calculated values to improve application performance. | Large Calculations, Expensive Computations |
| **useCallback()** | Stores functions to avoid unnecessary recreation and improve performance. | Optimizing Event Handlers |
| **useReducer()** | Manages complex state using a reducer function. | Shopping Cart, Todo Application |
| **useLayoutEffect()** | Executes code before the browser paints the screen. | DOM Measurements, Layout Calculations |
| **useId()** | Generates unique IDs for HTML elements. | Form Labels, Accessibility |
| **useTransition()** | Marks slow updates as non-urgent to keep the UI responsive. | Search Filtering, Large List Updates |
| **useDeferredValue()** | Delays updating a value to improve performance. | Live Search, Search Suggestions |

<br>

# How Hooks Work

Hooks add additional functionality to Functional Components.

``` text
Functional Component

↓

Needs Additional Feature

↓

Use Hook

↓

Feature Added
```

Examples:

``` text
useState()   → Store Data
useEffect()  → Perform Tasks Automatically
useContext() → Share Data
useRef()     → Access DOM Elements
```

------------------------------------------------------------------------

# Basic Rules of Hooks

### Rule 1

Use Hooks **only inside Functional Components** or **Custom Hooks**.

### Rule 2

Always call Hooks **at the top level** of the component.

✔ Correct

``` jsx
const [count, setCount] = useState(0);
```

❌ Incorrect

``` jsx
if (isLogin) {
    useState(0);
}
```

### Rule 3

Do not call Hooks inside:

-   Loops
-   if statements
-   Nested functions

This ensures React executes Hooks in the same order every time the
component renders.

------------------------------------------------------------------------

# Advantages of Hooks

-   Makes Functional Components more powerful.
-   Eliminates the need for Class Components in most cases.
-   Makes code cleaner and easier to read.
-   Encourages code reuse.
-   Simplifies React development.
-   Improves maintainability.

------------------------------------------------------------------------


# Understanding Order of React Hooks

| Order | Hook |
|:----:|:-------------|
| **1** | `useState()` 
| **2** | `useEffect()` 
| **3** | `useContext()` 
| **4** | `useRef()` 
| **5** | `useMemo()` 
| **6** | `useCallback()` 
| **7** | `useReducer()`

# Key Points

-   Hooks are special functions provided by React.
-   Hooks allow Functional Components to use React features.
-   Different Hooks provide different functionalities.
-   The most commonly used Hooks are **useState()** and **useEffect()**.
-   Hooks should always be called at the top level of a Functional
    Component.

------------------------------------------------------------------------