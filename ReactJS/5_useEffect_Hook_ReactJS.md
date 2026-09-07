# useEffect Hook in ReactJSddd

## What is useEffect?

React provides many Hooks.

You have already learned:

```jsx
useState()
```

It is used to **store and update data**.

Now let's learn another Hook:

```jsx
useEffect()
```

It is used to **perform a task automatically**.

> **Definition:** `useEffect` is a React Hook that executes a function
> after a component is rendered (displayed on the screen).

---

## Why do We Need useEffect?

Suppose your website opens.

Immediately after opening the website you want to:

- Show a welcome message.
- Load student data.
- Change the browser tab title.
- Start a timer.

These tasks should happen automatically.

Instead of waiting for the user to click a button, React performs these
tasks using **useEffect**.

---

## What is Rendering?

Before learning `useEffect`, understand **Rendering**.

**Rendering** means displaying a component on the screen.

Example:

```jsx
function App() {
    return <h2>Hello Students</h2>;
}
```

### Rendering Flow

```text
React calls App()

↓

Component is rendered

↓

Hello Students appears
```

---

## Where does useEffect Execute?

```text
React calls Component

↓

Component is rendered

↓

UI appears

↓

useEffect executes
```

React first displays the UI and then executes the code inside
`useEffect`.

---

## Real-Life Analogy

```text
Students enter classroom

↓

Teacher says

"Good Morning!"
```

The teacher greets students **after** they enter.

Similarly,

```text
Component Loads

↓

Component Appears

↓

useEffect Runs
```

---

## Importing useEffect

```jsx
import { useEffect } from "react";
```

---

## Syntax

```jsx
useEffect(() => {

    // Code

}, []);
```

---

## Understanding the Syntax

```jsx
useEffect(() => {

    console.log("Welcome");

}, []);
```

| Part | Meaning |
|---|---|
| `useEffect` | React Hook |
| `()` | Arrow Function |
| `{}` | Code to execute |
| `[]` | Dependency Array |

---

## Example 1: Welcome Message

```jsx
import { useEffect } from "react";

function App() {

    useEffect(() => {
        alert("Welcome Students!");
    }, []);

    return (
        <h2>ReactJS</h2>
    );
}

export default App;
```

### Output

```text
Open Website

↓

ReactJS appears

↓

Alert appears

Welcome Students!
```

### Explanation

React first renders the component and then executes the code inside
`useEffect`.

---

## Example 2: Console Message

```jsx
import { useEffect } from "react";

function App() {

    useEffect(() => {
        console.log("Component Loaded");
    }, []);

    return (
        <h2>Hello Students</h2>
    );
}

export default App;
```

### Console Output

```text
Component Loaded
```

This message appears **only once** because of the empty dependency
array.

---

## Dependency Array

The **Dependency Array** tells React **when** the `useEffect` function
should execute.

## Case 1: Empty Dependency Array

```jsx
useEffect(() => {

    console.log("Runs Once");

}, []);
```

**Output:** Runs only once when the component loads.

```text
Open Website

↓

Runs Once
```

---

## Case 2: No Dependency Array

```jsx
useEffect(() => {

    console.log("Runs Every Time");

});
```

Runs after **every render**.

```text
Open Page

↓

Runs

↓

Click Button

↓

Runs Again

↓

Click Button

↓

Runs Again
```

---

## Case 3: With Dependency

```jsx
useEffect(() => {

    console.log("Count Changed");

}, [count]);
```

Runs **only when `count` changes**.

If `count` does not change, `useEffect` does not execute.

---

## Example 3: Browser Title

```jsx
import { useState, useEffect } from "react";

function App() {

    const [count, setCount] = useState(0);

    useEffect(() => {
        document.title = `Count : ${count}`;
    }, [count]);

    return (
        <>
            <h2>{count}</h2>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>
        </>
    );
}

export default App;
```

Every time `count` changes, the browser title is updated automatically.

---

## Example 4: Student Login

```jsx
import { useEffect } from "react";

function Dashboard() {

    useEffect(() => {
        alert("Welcome Khushi");
    }, []);

    return (
        <h2>Student Dashboard</h2>
    );
}

export default Dashboard;
```

The alert appears only once when the dashboard opens.

---

## Flow of useEffect

```text
Component Loads

↓

React Displays UI

↓

useEffect Executes

↓

Task is Performed
```

---

## Difference between useState and useEffect

| `useState` | `useEffect` |
|---|---|
| Stores data | Performs a task |
| Returns state value | Executes code |
| Updates UI through state | Runs after rendering |
| Example: Counter | Example: Alert, Page Title |

---

## Common Uses of useEffect

- Show a welcome message
- Fetch data from an API
- Change the browser title
- Start a timer
- Save data to Local Storage
- Add event listeners

---

## Advantages

- Executes tasks automatically.
- Keeps UI and logic separate.
- Useful for loading data.
- Executes only when needed.

---

## Key Points

- `useEffect` is a React Hook.
- It executes code after a component is rendered.
- It is mainly used for automatic tasks.
- The Dependency Array controls when it executes.
- `[]` → Runs once.
- No Dependency Array → Runs after every render.
- `[count]` → Runs only when `count` changes.

---

## In-short we can say that....

`useEffect` is a React Hook used to perform tasks automatically after a
component is rendered. It is commonly used to display welcome messages,
fetch data from APIs, update the browser title, start timers, and
perform other automatic tasks. The Dependency Array controls when the
effect should run.
