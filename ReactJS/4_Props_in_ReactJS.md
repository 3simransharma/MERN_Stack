# Props in ReactJS

## What are Props?

**Props** is short for **Properties**.

Props are used to **pass data from a parent component to a child
component** in React.

They allow different components to communicate with each other by
sharing information. Props are similar to **function arguments** because
they pass values to a component.

> **Definition:** Props are read-only values passed from a parent
> component to a child component.

## Why Do We Need Props?

Suppose we create a **Student** component.

Without Props, every student would display the same information.

Example:

``` text
Name: Student
Age: 20
```

But what if we want to display different students?

``` text
Name: Khushi
Age: 32

Name: Aryan
Age: 25

Name: Riya
Age: 22
```

Instead of creating three separate components, we create **one reusable
component** and pass different data using Props.

## How Props Work

A **Parent Component** sends data, and a **Child Component** receives
and displays that data.

``` text
Parent Component
      │
 Sends Props
      │
      ▼
Child Component
```

**Data Flow:** Parent → Child

This is called **One-Way Data Flow**.

## Syntax of Props

### Parent Component (App.jsx)

``` jsx
import Student from "./Student";

function App() {
    return (
        <Student
            name="Khushi"
            age={32}
        />
    );
}

export default App;
```

**Explanation**

-   `Student` is the child component.
-   `name` and `age` are Props.
-   `"Khushi"` is a string.
-   `{32}` is a number.

### Child Component (Student.jsx)

``` jsx
function Student(props) {
    return (
        <>
            <h2>Name: {props.name}</h2>
            <p>Age: {props.age}</p>
        </>
    );
}

export default Student;
```

**Output**

``` text
Name: Khushi
Age: 32
```

## How Props are Passed

Parent:

``` jsx
<Student
    name="Khushi"
    age={32}
/>
```

React internally creates:

``` javascript
props = {
    name: "Khushi",
    age: 32
}
```

The child receives the object:

``` jsx
function Student(props) {
    ...
}
```

Access values using:

``` jsx
props.name
props.age
```

## Passing Multiple Props

``` jsx
<Student
    name="Khushi"
    age={32}
    city="Bhuj"
    course="M.Sc. CA & IT"
/>
```

``` jsx
function Student(props) {
    return (
        <>
            <h2>{props.name}</h2>
            <p>Age: {props.age}</p>
            <p>City: {props.city}</p>
            <p>Course: {props.course}</p>
        </>
    );
}
```

## Props Destructuring

Instead of writing:

``` jsx
props.name
props.age
props.city
```

Use:

``` jsx
function Student({ name, age, city }) {
    return (
        <>
            <h2>{name}</h2>
            <p>Age: {age}</p>
            <p>City: {city}</p>
        </>
    );
}
```

### Why Use Destructuring?

-   Shorter code
-   Easier to read
-   Avoids repeated `props.`
-   Recommended approach in React

## Why are Props Read-Only?

Props belong to the **Parent Component**.

The child component can use the data but **cannot modify it**.

Incorrect example:

``` jsx
function Student(props) {
    props.name = "Riya";   // ❌ Incorrect
    return <h2>{props.name}</h2>;
}
```

React does not allow this because Props are **read-only**.

## One-Way Data Flow

``` text
Parent Component
      │
      │ Props
      ▼
Child Component
```

Data always flows from **Parent → Child**.

## Advantages of Props

-   Pass data from a parent component to a child component.
-   Make components reusable.
-   Reduce code duplication.
-   Keep code modular and organized.
-   Support one-way data flow.
-   Easy to understand and maintain.

## Limitations of Props

-   Props are read-only.
-   Child components cannot modify Props.
-   Data flows only from Parent to Child.
-   Props cannot store changing data by themselves.

## Props vs Function Arguments

  Function Arguments            React Props
  ----------------------------- ------------------------------------
  Passed to a function          Passed to a component
  Used inside the function      Used inside the component
  Can be of any data type       Can be of any data type
  Passed during function call   Passed while rendering a component

### Function Example

``` javascript
function greet(name) {
    return "Hello " + name;
}

greet("Khushi");
```

### React Example

``` jsx
<Student name="Khushi" />
```

## Key Points

-   Props stands for **Properties**.
-   Props pass data from a Parent Component to a Child Component.
-   Props are read-only.
-   Components can receive one or multiple Props.
-   Props can be strings, numbers, booleans, arrays, objects, or
    functions.
-   Props are accessed using `props.propertyName` or destructuring.
-   React follows **One-Way Data Flow**.

## Summary

Props are one of the fundamental concepts of React. They allow data to
be passed from a parent component to a child component, making
components reusable and flexible. Since Props are read-only, they help
maintain a clear one-way flow of data, making React applications easier
to understand, maintain, and debug.
