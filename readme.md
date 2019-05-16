# React Training workshop notes

## **intro**

### Why React

1.) Declarative

2.) Composable

```js
// react library is the blueprint, i.e. the instructions for the app
import React from "react";

// ReactDom is used to render the blueprint
import ReactDom from "react-dom";
```

### **React Training Team Definitions**

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

**component**:

## To Look at

- Modules
  - `react-icons/fa`

```js
import { faPlus } from "react-icons/fa";
```
