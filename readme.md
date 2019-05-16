# React Training workshop notes

## **intro**

**React Elements**:

```js
const reactElement = react.createElement(
  "button",
  { className: "custom-class", onClick: () => alert("Hey") },
  "+ Add"
);
```

can be written in JSX like this:

```jsx
<button onClick={() => alert("Hey")} className="custom-class">
  + Add
</button>
```

**components**:
Composition is when you can reuse the code in a nicely packaged way, components are just functions that return code

```jsx
function CTAbutton(props) {
  return (
    <button>
      {props.icon} {props.text}
    </button>
  );
}
```

### Why React

#### 1.) **Declarative**:

React want you to exactly declare how your components work under the hood

```jsx
function CTAbutton(props) {
  return (
    <button>
      {props.icon} {props.text}
    </button>
  );
}
```

Simply adding an onClick to the Custom Component wont do anything

```jsx
<CTAbutton onClick={() => alert("clicked")} icon={icon} text={text} />
```

We need to change the `CTAbutton` component to call onClick under the hood on the actual jsx/html (`button`) element in order to be able to run an `onClick`

```jsx
function CTAbutton(props) {
  return (
    <button onClick={props.onClick}>
      {props.icon} {props.text}
    </button>
  );
}
```

#### 2.) **Composable**:

we can write code in one place and export it and reuse it anywhere in our app

```js
// react library is the blueprint, i.e. the instructions for the app
import React from "react";

// ReactDom is used to render the blueprint
import ReactDom from "react-dom";
```

### **React Training Team Definitions**

## To Look at

- Modules
  - `react-icons/fa`

```js
import { faPlus } from "react-icons/fa";
```
