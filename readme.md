# React Training workshop notes

## **intro**

## Morning (day 1)

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

### React State

#### 1.) Setting state

`setState` merges the object passed in with the current state object

state is only declared once in the constructor of class components

```jsx
this.state = {
  count: 10,
  error: null
};
this.setState({
  count: val,
  error: null
});
```

you call useState for any new state values you need

`useState` will overide the current state with whatever is passed into the second child that get destructured from `useState`

can call `set[StateValue]` for as many values as you need updated

```jsx
const [count, setCount] = useState(10);
const [error, setError] = useState(null);
function updateApp() {
  setCount(20);
  setError("some error");
}
```

#### 2.) what happens on render and state change

```jsx
// element created on first render
const element = Counter();

// after some event
const newElement = Counter();
diff(element, newElement);
```

React will store the last element it rendered in memory and compare it to the element when it is rendered again with new values

React will only update the parts that have changed, which makes it extremely fast

### Hooks and useState

```js
const states = [[4, fn], [10, fn]];
const callCount = -1;

function useState(defaultValue) {
  const id = ++callCount;
  if(states[id]) {
      return states[id]
  }
  const setValue = newValue => {
    // change state
    states[id][0] = newValue;

    // rerender
    renderHook();
  };
  const arr = [defaultValue, setValue];
  states.push(arr);
  return arr;
}

import React from 'react'
import CrappyRender from 'crappy-render-dom'
CrappyRender(){
    callCount = -1;
    ReactDom.render(<MyCompWithUseState />, document.getElementById('id'))
}
```

## Afternoon (day 1)

### **useEffect**

We should think in terms of state and not events
let state change drive your application

you can use useEffect as many times as you need for your component

```js
function myComponent({ someVal }) {
  const [count, setCount] = useState(0);

  useEffect(() => {
    doSomeSideEffect();
  }, [someVal]);

  useEffect(() => {
    doDifferentSideEffect();
  }, [count]);

  return <div>{count}</div>;
}
```

#### custom hook with effect

custom title hook

```js
function useTitle(customTitle) {
  const title = customTitle.substr(0, 20);
  useEffect(() => {
    document.title = title;
  }, [title]);
}
```

#### Hook Cleanup

any async action that runs in a useEffect before a component is unmounted

```js
import { useState, useEffect } from "react";
import axios from "axios";

export default function(url) {
  const [data, setData] = useState([]);

  useEffect(() => {
    let current = true;
    axios.get(url).then(response => {
      if (current) {
        setData(response.data);
      }
      return () => {
        current = false;
      };
    });
  }, [url]);
  return { data, setData };
}
```

## To Look at

- Modules
  - `react-icons/fa`
  - `reach`

```js
import { faPlus } from "react-icons/fa";
import { Tabs, TabList, Tab, TabPanels, TabPanel } from "@reach/tabs";
```
