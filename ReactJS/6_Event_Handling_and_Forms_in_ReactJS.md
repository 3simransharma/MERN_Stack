# Event Handling & Forms in ReactJS

## Objectives


-   To Understand events in React.
-   Handle user interactions using React events.
-   Use `onClick`, `onChange`, `onMouseOver`, and `onSubmit`.
-   Understand the Event Object and `event.target.value`.
-   Create forms in React.
-   Store form values using `useState()`.
-   Understand Controlled Components.
-   Handle form submission using `onSubmit`.
-   Understand `preventDefault()`.

------------------------------------------------------------------------

# 1. Event Handling in React

Users interact with websites by clicking buttons, typing text,
submitting forms, moving the mouse, and pressing keyboard keys. These
actions are called **Events**.

> **Definition:** Event Handling is the process of performing an action
> when a user interacts with an element on a webpage.

``` text
User Interaction
      ↓
Event Occurs
      ↓
Function Executes
      ↓
Task is Performed
```

## Common Events in React

  ## Common Events in ReactJS

| Event | When It Occurs | Common Use / Example |
|---|---|---|
| `onClick` | When the user clicks an element. | Button click, Like button, Counter |
| `onChange` | When the value of an input changes. | Text input, Form fields |
| `onSubmit` | When a form is submitted. | Login Form, Registration Form |
| `onMouseOver` | When the mouse pointer moves over an element. | Hover message, Preview |
| `onMouseOut` | When the mouse pointer leaves an element. | Remove hover effect |
| `onDoubleClick` | When the user double-clicks an element. | Open or edit an item |
| `onKeyDown` | When a keyboard key is pressed down. | Search box, Keyboard controls |
| `onKeyUp` | When a pressed keyboard key is released. | Keyboard input handling |
| `onFocus` | When an input or element receives focus. | Highlight an input field |
| `onBlur` | When an input or element loses focus. | Form validation |

React event names use **camelCase**, such as `onClick`, `onChange`, and
`onSubmit`.

------------------------------------------------------------------------

# 2. `onClick` Event

The `onClick` event occurs when the user clicks an element.

``` jsx
function App() {
    function showMessage() {
        alert("Welcome to React!");
    }

    return (
        <button onClick={showMessage}>
            Click Me
        </button>
    );
}

export default App;
```

``` text
Click Button
     ↓
onClick
     ↓
showMessage()
     ↓
Alert Appears
```

We normally write:

``` jsx
onClick={showMessage}
```

This tells React to execute the function **when the button is clicked**.

We should not normally write:

``` jsx
onClick={showMessage()}
```

because this calls the function immediately during rendering.

## Using an Arrow Function

``` jsx
function App() {
    return (
        <button onClick={() => alert("Hello Students")}>
            Click Me
        </button>
    );
}

export default App;
```

------------------------------------------------------------------------

# 3. Event Handling with `useState()`

Events and State often work together.

``` jsx
import { useState } from "react";

function App() {
    const [count, setCount] = useState(0);

    return (
        <>
            <h2>Count: {count}</h2>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>
        </>
    );
}

export default App;
```

``` text
User Clicks Increase
        ↓
onClick Occurs
        ↓
setCount() Executes
        ↓
State Changes
        ↓
Component Re-renders
        ↓
Updated Count Appears
```

------------------------------------------------------------------------

# 4. `onMouseOver` Event

The `onMouseOver` event occurs when the mouse pointer moves over an
element.

``` jsx
function App() {
    function showMessage() {
        alert("Mouse is over the button!");
    }

    return (
        <button onMouseOver={showMessage}>
            Move Mouse Here
        </button>
    );
}

export default App;
```

------------------------------------------------------------------------

# 5. Event Object

When an event occurs, React provides information about that event
through an **Event Object**.

``` jsx
function App() {
    function showValue(event) {
        console.log(event.target.value);
    }

    return (
        <input
            type="text"
            onChange={showValue}
        />
    );
}

export default App;
```

Here, `event` contains information about the event.

## Understanding `event.target.value`

| Part | Meaning |
|------|---------|
| `event` | Contains information about the event that occurred |
| `target` | Refers to the element where the event occurred |
| `value` | Gives the current value of that element |

If a user types `Khushi` into an input box:

``` jsx
event.target.value
```

contains:

``` text
Khushi
```

Developers often use `e` instead of `event`:

``` jsx
function showValue(e) {
    console.log(e.target.value);
}
```

Both are the same.

------------------------------------------------------------------------

# 6. `onChange` Event

The `onChange` event occurs whenever the value of an input changes.

``` jsx
function App() {
    function showValue(e) {
        console.log(e.target.value);
    }

    return (
        <input
            type="text"
            onChange={showValue}
        />
    );
}

export default App;
```

As the user types, the latest input value is printed in the console.

------------------------------------------------------------------------

# 7. Forms in React

A **Form** is used to collect information from users.

Examples include:

-   Login Form
-   Registration Form
-   Contact Form
-   Feedback Form
-   Admission Form
-   Search Form

> **Definition:** A Form is a collection of input elements used to
> collect information from the user.

``` jsx
function App() {
    return (
        <form>
            <input
                type="text"
                placeholder="Enter Name"
            />

            <button type="submit">
                Submit
            </button>
        </form>
    );
}

export default App;
```

------------------------------------------------------------------------

# 8. Forms with `useState()`

In React, `useState()` is commonly used to store information entered by
the user.

``` jsx
const [name, setName] = useState("");
```

When the user enters a name, `setName()` updates the State.

## Example: Display Name While Typing

``` jsx
import { useState } from "react";

function App() {
    const [name, setName] = useState("");

    return (
        <>
            <input
                type="text"
                placeholder="Enter Name"
                value={name}
                onChange={(e) => setName(e.target.value)}
            />

            <h2>Hello {name}</h2>
        </>
    );
}

export default App;
```

``` text
User Types
    ↓
onChange
    ↓
e.target.value
    ↓
setName()
    ↓
State Changes
    ↓
Component Re-renders
    ↓
Updated Name Appears
```

------------------------------------------------------------------------

# 9. Controlled Components

Consider:

``` jsx
<input
    type="text"
    value={name}
    onChange={(e) => setName(e.target.value)}
/>
```

The input value is connected to React State using `value={name}`, and
`onChange` updates that State.

> **Definition:** A Controlled Component is a form element whose value
> is controlled by React State.

``` text
User Types
    ↓
onChange
    ↓
setName()
    ↓
State
    ↓
Input Value
```

------------------------------------------------------------------------

# 10. Multiple Form Inputs

``` jsx
import { useState } from "react";

function App() {
    const [name, setName] = useState("");
    const [age, setAge] = useState("");

    return (
        <>
            <input
                type="text"
                placeholder="Enter Name"
                value={name}
                onChange={(e) => setName(e.target.value)}
            />

            <input
                type="number"
                placeholder="Enter Age"
                value={age}
                onChange={(e) => setAge(e.target.value)}
            />

            <h2>Student Details</h2>

            <p>Name: {name}</p>
            <p>Age: {age}</p>
        </>
    );
}

export default App;
```

Each input can have its own State variable.

------------------------------------------------------------------------

# 11. `onSubmit` Event

The `onSubmit` event occurs when a form is submitted.

``` jsx
<form onSubmit={handleSubmit}>
```

When the user clicks a submit button, `handleSubmit()` executes.

## Example: Form Submission

``` jsx
import { useState } from "react";

function App() {
    const [name, setName] = useState("");

    function handleSubmit(e) {
        e.preventDefault();
        alert(`Welcome ${name}`);
    }

    return (
        <form onSubmit={handleSubmit}>
            <input
                type="text"
                placeholder="Enter Name"
                value={name}
                onChange={(e) => setName(e.target.value)}
            />

            <button type="submit">
                Submit
            </button>
        </form>
    );
}

export default App;
```

------------------------------------------------------------------------

# 12. `preventDefault()`

When a form is submitted, the browser has its own default
form-submission behavior.

In React, we often want JavaScript to handle the form.

``` jsx
e.preventDefault();
```

> **Definition:** `preventDefault()` prevents the browser from
> performing the default action associated with an event.

------------------------------------------------------------------------

# 13. Example: Student Login Form

``` jsx
import { useState } from "react";

function App() {
    const [email, setEmail] = useState("");
    const [password, setPassword] = useState("");

    function handleSubmit(e) {
        e.preventDefault();

        console.log("Email:", email);
        console.log("Password:", password);

        alert("Login Form Submitted");
    }

    return (
        <form onSubmit={handleSubmit}>
            <h2>Student Login</h2>

            <input
                type="email"
                placeholder="Enter Email"
                value={email}
                onChange={(e) => setEmail(e.target.value)}
            />

            <br /><br />

            <input
                type="password"
                placeholder="Enter Password"
                value={password}
                onChange={(e) => setPassword(e.target.value)}
            />

            <br /><br />

            <button type="submit">
                Login
            </button>
        </form>
    );
}

export default App;
```

This example combines:

``` text
Form
  +
useState()
  +
onChange
  +
Event Object
  +
onSubmit
  +
preventDefault()
```

------------------------------------------------------------------------

# 14. Example: Feedback Form

``` jsx
import { useState } from "react";

function App() {
    const [name, setName] = useState("");
    const [feedback, setFeedback] = useState("");

    function handleSubmit(e) {
        e.preventDefault();

        console.log("Name:", name);
        console.log("Feedback:", feedback);

        alert("Thank you for your feedback!");
    }

    return (
        <form onSubmit={handleSubmit}>
            <h2>Feedback Form</h2>

            <input
                type="text"
                placeholder="Enter Name"
                value={name}
                onChange={(e) => setName(e.target.value)}
            />

            <br /><br />

            <textarea
                placeholder="Enter Feedback"
                value={feedback}
                onChange={(e) => setFeedback(e.target.value)}
            />

            <br /><br />

            <button type="submit">
                Submit Feedback
            </button>
        </form>
    );
}

export default App;
```

------------------------------------------------------------------------

# 15. Event Handling vs Forms

  -----------------------------------------------------------------------
  Event Handling                      Forms
  ----------------------------------- -----------------------------------
  Handles user actions                Collects user information

  Uses events such as `onClick`       Uses input elements

  Can work without State              Commonly combined with State

  Example: Button Click               Example: Login Form

  Common events: `onClick`,           Common events: `onChange`,
  `onMouseOver`                       `onSubmit`
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 16. How State, Events, and Forms Work Together

``` text
FORM
 ↓
User enters information
 ↓
onChange occurs
 ↓
useState() stores information
 ↓
User clicks Submit
 ↓
onSubmit occurs
 ↓
Form Data is Processed
```

Example:

``` text
Student enters "Khushi"
        ↓
onChange
        ↓
setName("Khushi")
        ↓
name = "Khushi"
        ↓
Student clicks Submit
        ↓
onSubmit
        ↓
handleSubmit()
        ↓
Form Submitted
```

------------------------------------------------------------------------

# 17. Common Mistakes

## Mistake 1: Calling the Function Directly

❌ Incorrect:

``` jsx
<button onClick={showMessage()}>
    Click
</button>
```

✅ Correct:

``` jsx
<button onClick={showMessage}>
    Click
</button>
```

## Mistake 2: Forgetting `onChange`

When using a controlled input:

``` jsx
value={name}
```

also provide an `onChange` handler:

``` jsx
<input
    value={name}
    onChange={(e) => setName(e.target.value)}
/>
```

## Mistake 3: Forgetting `preventDefault()`

When React handles form submission:

``` jsx
function handleSubmit(e) {
    e.preventDefault();
}
```

prevents the browser's default form-submission behavior.

------------------------------------------------------------------------

# 18. Important Concepts to Remember

| Concept | Purpose |
|---|---|
| `onClick` | Handles clicks |
| `onChange` | Handles input changes |
| `onSubmit` | Handles form submission |
| `event` / `e` | Contains information about the event |
| `e.target` | Element that triggered the event |
| `e.target.value` | Current value of the input |
| `useState()` | Stores form data |
| `value={state}` | Connects an input value with State |
| `preventDefault()` | Prevents default browser behavior |

<br/>

# Therefore,

**Event Handling** allows a React application to respond to user actions
such as clicking buttons, typing text, and submitting forms.

**Forms** are used to collect information from users. React commonly
combines Forms with `useState()`, `onChange`, and `onSubmit`.

### Event Handling Flow

``` text
User Interaction
       ↓
     Event
       ↓
Event Handler
       ↓
State Changes
       ↓
UI Updates
```

### Form Flow

``` text
User Types
    ↓
onChange
    ↓
e.target.value
    ↓
useState()
    ↓
User Submits
    ↓
onSubmit
    ↓
Form Data Processed
```
