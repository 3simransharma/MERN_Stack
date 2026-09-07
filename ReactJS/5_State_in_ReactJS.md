# State in ReactJS

# What is State?

A **State** is a built-in object in React that stores data **inside a
component**.

Unlike Props, the value of a State **can change** during the execution
of a program.

Whenever the State changes, React automatically updates the User
Interface (UI).

> **Definition:** State is a built-in object that stores data inside a
> component, and its value can change over time.

<br>

# Why Do We Need State?

Initially:

``` text
Count : 0
```

After clicking **Increase**:

``` text
Count : 1
```

Changing values are stored using **State**.

<br>

# Real-Life Examples

-   Instagram Likes
-   Shopping Cart
-   Counter
-   Theme Switcher
-   Logged-in User
-   Form Inputs
-   Game Score

<br>

# Importing useState

``` jsx
import { useState } from "react";
```

<br>

# Syntax

``` jsx
const [count, setCount] = useState(0);
```

-   `count` → Current state value
-   `setCount()` → Updates the state
-   `0` → Initial value

<br>

# Example 1: Simple Counter

``` jsx
import { useState } from "react";

function Counter() {

    const [count, setCount] = useState(0);

    return (
        <>
            <h2>Count : {count}</h2>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>
        </>
    );
}

export default Counter;
```

<br>

# Example 2: Increase & Decrease Counter

``` jsx
import { useState } from "react";

function Counter() {

    const [count, setCount] = useState(0);

    return (
        <>
            <h2>{count}</h2>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>

            <button onClick={() => setCount(count - 1)}>
                Decrease
            </button>
        </>
    );
}

export default Counter;
```

<br>

# Example 3: Age Counter

``` jsx
import { useState } from "react";

function AgeButton() {

    const [count, setCount] = useState(0);

    function decreaseCount() {
        if (count > 0) {
            setCount(count - 1);
        }
    }

    return (
        <>
            <button onClick={decreaseCount}>-</button>

            <h2>{count}</h2>

            <button onClick={() => setCount(count + 1)}>+</button>
        </>
    );
}

export default AgeButton;
```

## Explanation

-   '+' increases the value.
-   '-' decreases the value.
-   The value never becomes negative because of:

``` jsx
if (count > 0) {
    setCount(count - 1);
}
```

<br>

# Why Don't We Use Normal Variables?

``` jsx
let count = 0;

count++;
```

React does not update the UI when normal variables change.

State solves this problem.

<br>

# Why Do We Use `const` Instead of `let`?

``` jsx
const [count, setCount] = useState(0);
```

We never write:

``` jsx
count++;
```

or

``` jsx
count = count + 1;
```

Instead, we write:

``` jsx
setCount(count + 1);
```

`setCount()` tells React to update the State and re-render the
component.

## Why `const`?

-   Prevents accidental reassignment.
-   Forces us to use the setter function.
-   Makes the code safer and predictable.

> **Remember:** `count` is read, but `setCount()` changes it.

<br>

# Rules of State

-   Import `useState`.
-   Create State using `useState()`.
-   Never modify State directly.
-   Always use the setter function.
-   Updating State re-renders the component.

<br>

# Props vs State

  Props                  State
  ---------------------- -------------------------
  Passed from Parent     Stored inside Component
  Read-only              Can change
  Passes data            Stores changing data
  Controlled by Parent   Controlled by Component

<br>

# Therefore,

State stores changing data inside a React component. The `useState` Hook
creates State and provides a setter function to update it. Whenever the
State changes, React automatically updates the User Interface.
