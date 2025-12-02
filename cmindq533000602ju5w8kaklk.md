---
title: "React Interview questions"
datePublished: Mon Dec 01 2025 16:44:28 GMT+0000 (Coordinated Universal Time)
cuid: cmindq533000602ju5w8kaklk
slug: react-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/xkBaqlcqeb4/upload/b99bcdc38994cdb594e32c9b6f15d6db.jpeg

---

1. <mark>What is React and why is it popular?</mark>
    

React is a JavaScript library for building user interfaces,

Its key based on building reusable component based architecture (allowing developers to create reusable UI components)

React Virtual DOM is able to create a copy of the real DOM

2. <mark>What is an SPA (Single Page Application )</mark>
    

A web app that only loads once (single index.html file) after loading the entire page it updates the contents dynamically using JavaScript

SPA leads to faster load times, Better responsiveness, Smoother user interactions

3. <mark>What is JSX and how does it differ from html?</mark>
    

JSX or JavaScript XML a syntax extension for JavaScript that allows devs to write HTML like code directly into JavaScript files

4. <mark>Explain the difference between functional and class components?</mark>
    

Class components were used before hooks while functional components came after hooks

1\. Functional Components

* Simple JavaScript functions
    
* Use **Hooks** (useState, useEffect, etc.)
    
* Easier to write, faster, recommended in modern React
    
* No `this` keyword
    

2\. Class Components

* ES6 classes extending `React.Component`
    
* Use **state** and **lifecycle methods** (componentDidMount, etc.)
    
* More verbose
    
* Use `this` to access state and props
    
* Mostly legacy—functional components replaced them
    
    Example
    

Functional Component

```javascript
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={() => setCount(count + 1)}>Add</button>
    </div>
  );
}

export default Counter;
```

### **Class Component**

```javascript
import React, { Component } from "react";

class Counter extends Component {
  constructor() {
    super();
    this.state = { count: 0 };
  }

  render() {
    return (
      <div>
        <h2>Count: {this.state.count}</h2>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Add
        </button>
      </div>
    );
  }
}

export default Counter;
```

**Functional Component(** Uses **hooks** for state and logic.)

\*\*Class Component (\*\*a react component written as a **class** that uses **this**, **state**, and **lifecycle methods**.)

5. What is the difference between a stateless and a stateful component in React?
    

Stateless components do not manage or store there data they simply <mark>receive data via prompts and display it</mark>. Best used if you want to display any logic on your user interface

Stateful components on the other hand <mark>can manage their own state </mark> and can <mark>update their existing state based on user interaction</mark> or other events

with the introduction of functional components you can keep components to be stateful or stateless

6. What are props in React and how are they used?
    

Props or what we call properties is how we pass down data from <mark>a parent component to a child component.</mark>

Note that Props and state are used to control and manipulate how components behave and render

7. What is the difference between state and props in React?
    
    State- this is a mutable object that stores dynamic data (<mark>data that changes over time</mark>)
    
    state is private and is fully controlled by the component it belongs to
    
    Props- this is an Immutable Object meaning <mark>data cannot be modified</mark>
    
    props is only controlled by the parent component and cannot be changed by the children
    
8. What are controlled and uncontrolled components
    

Controlled components are used when <mark>control is required </mark> over the <mark>data being entered i</mark>nto a form such as in form validation where you need to fetch example the username and password to check authenticity. Controlled components are accessed through the state atributes which makes it easier to change.

Uncontrolled components are used when there is <mark>no need to Dynamically inspect</mark> the user inputs. Uncontrolled are managed through a ref

9. What is the purpose of the key attribute in React Lists?
    

### Help React identify each list item uniquely

* Keys tell React <mark>which item changed, was added, or removed</mark>.
    
* This makes updates `faster and more efficient.`
    

### Why it matters:

* Without keys, React may **re-render incorrectly** or mix up items.
    
* Keys ensure React updates **only the specific items** that need changes.
    

### Example:

```javascript
<ul>
  {items.map(item => (
    <li key={item.id}>{item.name}</li>
  ))}
</ul>
```

Keys help React keep track of list items so it updates the UI correctly and efficiently.

10. What are fragments in React and how are they useful
    

Fragments- a way to <mark>group multiple elements together </mark> without adding extra node to the DOM.

fragments are used when you want to avoid unnecessary

### Module 2

11. What is the virtual DOM and how does React use it to improve performance?
    

A virtual DOM is a <mark>lightweight copy in memory representation </mark> of the actual DOM ( when running a React component they are two doms one is the real dom and another the virtual dom)

Virtual DOM works by checking through the code you are writing and only the changes that are made in the code are made to reflect in the original DOM

12. What are React lifecycle methods and when are they used?
    

React lifecycle methods are **special functions in class components** that let developers run code at specific moments in a component’s life.

They help you control what happens when a component:

1. **Initializes** (gets created)
    
2. **Mounts** (first appears on the screen)
    
3. **Updates** (when props or state change)
    
4. **Unmounts** (gets removed from the screen)
    
    ✅ **Main Lifecycle Stages**
    

### **1\. Initialization**

* Component sets up state and props.
    
* Happens in the **constructor()**.
    

### **2\. Mounting (component appears)**

* `componentDidMount()`  
    Used for: API calls, fetching data, setting timers.
    

### **3\. Updating (state/props change)**

* `componentDidUpdate()`  
    Used for: responding to changes, re-fetching data.
    

### **4\. Unmounting (component removed)**

* `componentWillUnmount()`  
    Used for: cleanup, removing event listeners, clearing intervals.
    
    ## ✅ **Simple Summary**
    

**Lifecycle methods let you run code at specific points from creation → update → removal of a component.** Only used in **class components**. Functional components use **hooks** instead (like `useEffect`).

13. Explain the UseState and useEffect hooks with examples
    

Usestate- it is used to store the fetched data and the loading state ( a container think of doing a count and every time the value increases it is stored in the container )

UseEffect - it is used to perform side effects example when making an API call what happens in the background that is all controlled by use effects