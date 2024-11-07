---
title: "Introduction to React: Learn the Basics of This Essential Frontend Tool"
datePublished: Thu Nov 07 2024 14:25:08 GMT+0000 (Coordinated Universal Time)
cuid: cm37egl5p000009jv8wqm2u8g
slug: introduction-to-react-learn-the-basics-of-this-essential-frontend-tool
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/UYsBCu9RP3Y/upload/2d5f5d442277a7d3f3933b746dc34048.jpeg
tags: reactjs

---

React is a <mark>javascript library</mark> for building user interfaces, a library can be defined as a <mark>set of functions and classes</mark> that are grouped in a package

The main idea behind libraries is to create a reusable code that anyone in the development community can utilize and contribute to.

React js is an opensource Javascript library that is used for building user interfaces

### why should we choose to learn React.js?

* Easy to learn.
    
* Highly maintainable.
    
* Super-fast in rendering views.
    
* Component-based, with the ability to split the code as much as we want
    
* Simple in the debugging process.
    

# Features of React

* **JSX**: React uses the JSX syntax in writing components, which makes them more independent.
    
* **Component**: React adopts the component-based application approach which allows us to use the same component repeatedly.
    
* **One way data flow**: React only allows us to pass data from parent to child, which is very helpful in tracing data when debugging.
    
* **Virtual DOM**: React uses the Virtual DOM which makes rendering UI super fast.
    
* **Simplicity**: React is very simple to learn and work with, especially for newcomers.
    

Creating your react app

1. Let’s create a folder for the React projects. You can choose any empty folder.
    
2. Access it using the Command line/ Terminal.
    
3. Run the following command to create the React project:  
    **npx create-react-app** `<project-name>`  
    ***Note***\*: Replace the\* `<project-name>` with your project name
    

React maintains two virtual DOMs at once one contains the <mark>updated virtual DOM </mark> and one which is just <mark>the pre-updated version</mark>

<mark>Diffing </mark> once react finds out what has been changed it only updates the affected objects on Real DOM

ReactDOM - This is <mark>a package that provides DOM specific</mark> methods, it can be used at the top level of a web app to enable efficient way of managing DOM elements.

The syntax is:

`ReactDOM.render(element,container,callback)`

### JSX

Jsx- This is a syntax extension to Javascript used with React to describe what the UI should look like javascript+ Html = React Js

Thanks to React ,<mark>JSX is transformed into HTML</mark> and then it gets <mark>injected into an HTML</mark> element (root).

This injection is actually happening in the index.js file thanks to ReactDOM

some rules to keep in mind when using JSX elements

Apostrophes (‘) or quotes on strings (“)

Commas (,) instead of semicolon (;)

Two curly brackets {{}}instead of quotes (““)

### **HTML**

```javascript
<h1 style= "color:red; font-size:60px">
...
</h1>
```

---

### \---&gt; **JSX**

```javascript
<h1 style={{ color: "red", fontSize: 60 }}>...</h1>
```

### Camel Case

Its the practice of writing phrases in a single word with no spaces we use it to write variables in Javascript

The concept is very basic. There are 2 simple rules to follow:

1. No spaces, no underscores ( \_ ) and no dashes (-)
    
2. If the variable is composed of multiple words, all words begin with a **capital letter** except **the first word**.
    

# Examples

Let’s see more styling examples.  
We will frequently find that the HTML version is ordered right before the JSX version.

---

### HTML

```javascript
<div style='text-align:center'/>
```

### JSX

```javascript
<div style={{textAlign:'center'}}/>
```

### HTML

```javascript
<div style="transform:translateX(25px)"/>
```

### JSX

```javascript
<div style={{transform:'translateX(25px)'}}/>
```

### HTML

```javascript
<div style="box-shadow:0 5px 8px #000"/>
```

### JSX

```javascript
<div style={{boxShadow:"0 5px 8px #000"}}/>
```

# ClassName

Another way to style HTML elements is using the CSS classes. In JSX, to use the CSS class we need to change the attribute **class** into **className**, since the keyword class is reserved in JavaScript.

### HTML

```javascript
 <div class=”colorful”>...</div>
```

### JSX

```javascript
<div className='colorful'>...</div>
```

# Attributes: src

The `src` attribute is also available in JSX but it's slightly different from HTML. There are multiple ways to assign a value to the src attribute.

## Hard-coded string (not a variable)

### HTML

```xml
<img src=“/profile.png”></img>
```

### JSX

```javascript
<img src={"/profile.png"} alt="profile" />

 {/*  or we can also do */}

<img src="/profile.png" alt="profile" />
```

## Variable (can be a number, object, array, etc...)

### JSX

```javascript
<img src={myProfileImageUrl}></img>
```

Attributes in JSX are very similar to HTML. We just need to replace the quotes ("") with **curly brackets {}**.

### Adding an image

# 📁 The "public" directory

If you add the image in the 📁**public** directory, you need to reference it in the **src** attribute with an absolute URL(as a string).

**Tips**

* Make sure you add the forward slash “/”, it’s called the root.
    
* If your image is inside a **subfolder** called 📁images inside the 📁public folder, you need to specify it
    
    * `<img src=”/subfolder/myImage.png”/>`
        
        ### JSX📁The "src" directory
        
        If you add the image in the 📁**src** directory, you need to **import it** (using a relative path to src) then **set it** in the **src** attribute of the tag.
        
        ***Tips***
        
        * *Add the dot “.” and forward slash “/”, when importing an image inside src.*
            
        
        JSX
        
        ```xml
        import myWonderfulImage from "./myImage.png"
        
           function App(){
        
           return <img src={myWonderfulImage} alt ='myImage' />
        
           }
        ```
        

```xml
<img src="/myImage.png" alt="myimage"
```

When using JSX be sure to import the react library because JSX tags are compiles to React.createElement()

In React v17 version the library started supporting new JSX changes therefore we can inject JSX syntax into Javascript without importing React library

One of the common mistakes made in JSX, is u<mark>sing multiple root elements</mark> (when returning or creating JSX tags). This is a limitation in JSX. To fix this, we should use a `<div>`, empty tag (`<></>`) or `<React.Fragment>`.

*The wrong way*

```xml
 return  (

   <img src="/profile.png" className="my-profile" />

   <p>{firstName} {lastName}</p>

   )
```

*The right way:*

```xml
 return (

   <div>

     <img src="/profile.png" className="my-profile" alt="myprofile" />

     <p>

       {firstName} {lastName}

     </p>

   </div>

 );

 // or this way

 return (

   <>

     <img src="/profile.png" className="my-profile" alt="my profile" />

     <p>

       {firstName} {lastName}

     </p>

   </>

 );

// this is another way

 return (

   <React.Fragment>

     <img src="/profile.png" className="my-profile" alt="my profile" />

     <p>

       {firstName} {lastName}

     </p>

   </React.Fragment>

 );
```

### Introduction to component

A component is a piece of code that can be reused and made to cooperate with other components to create a UI

# Advantages of using components

Working with components makes web development much easier. The reasons are:

* ### Reusability:
    

Every implemented component can, if not must, be reused while building our web application.  
Let’s take the example of a sidebar on a dashboard, it will be used whichever page we display.

* ### Maintainability:
    

Every component is implemented separately from the others so it can be maintained without affecting other UI compositions.

* ### Platform independence:
    

In reality, the web components are built using HTML, CSS and JavaScript which make it a cross-platform.

* ### Privacy:
    

Since every component is built to operate alone, that ensures that its content is more private than shared code.

Components are the building blocks of any React app, you will notice that a typical React app will have plenty of them.

Simply put a component is a Javascript class or function that optionally accepts input and returns React elements

# Types of components

As we have said earlier, there are two types of React components, this division happened before the appearance of React version 16.8.  
But for the purpose of learning, it’s best if we know them.

The two types of React components are:

* **Class components:** referring to JavaScript classes.
    
* **Functional components:** referring to JavaScript function.
    

# Class Components

If you read articles on the Internet about React components, you will find the following names that refer to **class components**:

**Smart Component**  
Before React 16.8, the logic was only implemented in this type of component, because of the advantage that classes give over functions

**Stateful Component**  
Before february 2019, only class could hold and manage JavaScript State.

**Container Components**  
It’s called so, because usually it holds/contains other numeros (mostly functional) components.

```javascript
class Greeting extends React.Component {

 render(){

   return <h1>Hi, I’m a smart component!</h1>;

 }
}
```

# Functional Components:

These components are purely presentational and are simply represented by a function. This function optionally takes props and returns a React element to be rendered to the page.

Generally, it is preferred to use functional components whenever possible because of their predictability and conciseness. Since, they are purely presentational, their output is always the same if we give them the same props.

You may find functional components referred to as stateless, dumb or presentational in other reading material. All these names are derived from the simple nature that functional components take on.

* Functional because they are basically functions
    
* Stateless because they do not hold and/or manage state
    
* Presentational because all they do is output UI elements
    

But always remember, this is all before developing with React 16.8.  
For now, all functional component can do the same things as class based component.

Ways to export a component are:

# Default export

Similar to JavaScript file, we can export our component, as the example below shows, using the keyword `export default`.

```javascript
const MyFirstComponent = () => {

 return (

   <>

     <h2>Hello from my first component !!</h2>

   </>

 );

};

export default MyFirstComponent;
```

By doing that we’ve made the file **MyComponent.js** export automatically the component MyFirstComponent.

# Named exports

The other way to export a component is by the named export. Let’s take a look at the example.

This is how we can export more than one component from a single file.

```javascript
import React from "react";

export const MyFirstComponent = () => {

 return (

   <>

     <h2>Hello from my first component !!</h2>

   </>

 );

};

export const MySecondComponent = () => {

 return (

   <>

     <h2>Hello from my second component!! </h2>

   </>

 );

};
```

### HOC

The high order function in Javascript, a function that accepts another function as a parameter

Well, React clones and imitates that functionality with a component, so it gives us the possibility to create a <mark>Higher-Order Componen</mark>t which is a component that accepts a component as a parameter.

# Why HOC?

In software development, there is one important principle that is commonly used by the name of « DRY » (which stands for "Don’t Repeat Yourself").

Creating a simple utility function, that is used across several parts of the codebase is something you may have done repeatedly. You are essentially following the DRY principle by doing so. You are reusing the same utility function, without repeating the code.

In React, one of the ways to follow “DRY” across components, is to use the Higher-Order Component (HOC) concept. W<mark>e can share common functionalities without repeating code.</mark>

# Example of HOC

In this example, we will add a waiting message on the wrapped component. Don’t get too overwhelmed by this strange code. We’ll break it down later.

```javascript
import React from "react";

const higherOrderComponent = WrappedComponent => {

 class HOC extends React.Component {

   state = {

     isLoading: false

   };
   render() {

     return this.state.isLoading ? (

       <h1>Wait a moment...</h1>

     ) : (

       <WrappedComponent />

     );

   }
 }
 return HOC;
};
```

# Returning multiple nodes:

Since the component is only but a JavaScript function, and we know that JavaScript functions can only return a single object, value or item, therefore, the component can only return one JSX element.  
Granted, it all seems a bit overcomplicated. Here is the right way to do it.  
We wrap all the selected elements inside a single element div or section or any other wrapper of our choice. Take a look at the example below.

```javascript
const MyComponent = () => {

   // return multiple root node

   // WRONG!

   return (

    <Comp1 />

    <Comp2 />

   )

   }

   // this code will trigger an error

   // Parse Error: Adjacent JSX elements must be wrapped in an enclosing tag
```

### The correct way to do it:

```javascript
return (

 <div>

   <Comp1 />

   <Comp2 />

 </div>
);
```

# React fragment

Naturally, the `div` or `section` or any other HTML container inherently have default CSS properties that could affect our design.  
To sidestep these default properties, React gives us the **React.Fragment** which is a wrapper that has no effect on the CSS. A React fragment cannot be styled.

Take a look at its syntax in the provided example:

```javascript
return (
 <React.Fragment>
   <div />
   <div />
 </React.Fragment>
);
//this also is valid
return (
 <>
   <div />
   <div />
 </>
);
```

# Using absolute paths

Using an absolute path can be a little bit tricky and it can lead to a lot of problems when trying to reuse the component.

⇒ So, we advise you to use the relative paths instead.

```javascript
//relative path
import MyFirstComponent from "./MyFirstComponent";
//absolute path
import MyFirstComponent from '/src/component/MyFirstComponent'
```

One way data flow

This approach means that the data can only travel, in a <mark>unidirectional fashion, from a parent to a child component (top to bottom) </mark> and not the other way around. Unlike other libraries and the frameworks, React makes sure that this feature remains in its architecture.

The reason behind React keeping this perk in its ecosystem is because the one-way data flow makes it easier to trace the data and it’s changes over the component tree, it sounds a little bit confusing but let’s view an illustration to further clarify the concept.

### What are props?

To make this unidirectional data flow possible, React uses **props**.  
Props or **properties** are the tools that React uses to pass data from parent to child elements.Let’s think of it as a parameter in a JavaScript function.  
We can change the value of this parameter but the sets of instructions to be executed remain the same.Take your facebook page for example. You will find your name on the right, next to your picture.From a coding perspective, facebook developers can't create a customized navbarfor every profile.  
This is only possible and achievable using React props.  
The structure of these elements will be fixed and the content (name, image url...) will be received as a props.  
JS example

Here is another example to consolidate what we were just talking about.

```javascript
function Greeting(name) {
return "hello " + name;
}
console.log(Greeting('Jon Snow'))// it will display "hello Jon Snow"
console.log(Greeting('Ramsay Bolton')) // it will display "hello Ramzay Bolton"
console.log(Greeting('I am nobody')) // it will display "hello I am nobody"
```

The Greeting function receives a name as an argument. However, with whichever name we set, it will still display a concatenated `hello` alongside the name.

# React example

Now let’s try the same idea with a React component.

```javascript
function Greeter(props) {
 return <h1>hello {props.name}</h1>;
}
// And invoking the <Greeter/> component…
const App = () => {
 return (
   <div>
     <Greeter name="world" /> {/* 💥 "world" is the prop value*/}
     <Greeter name="I am the King" /> {/* 💥 "I am the King" is the prop value*/}
   </div>
 );
};
export default App;
```

# Let's recap!

React Props are like function arguments in JavaScript and attributes in HTML. To send props into a component, use the same syntax as HTML attributes:  
`<Greeter name="world" />`

```javascript
function Greeter(props) {

 return <h1>hello {props.name}</h1>;

}
```

As we can see, the component Greeter receives the name as a props and displays it in an h1 tag. Another thing to keep in mind is that props are an object and whatever we pass as attributes in the component is called in the parent.  
Notice : Props are immutable which mean that the child can only read the content of a props. It cannot change it.

Please consider that the names we give to props are personalized.  
Even though we can call the props whatever we want, there are some best practices to follow:  
The name should be significant and meaningful so others can understand the props' value.  
Use lower camel case (e.g. isActive).  
keep the name short ( &lt; 50 characters ).

Props should be descriptive. Props describe what a component does and not why it does it. A common mistake is naming props after the current user or the current environment. For example :  
hasSubmitPermission describes the permission of the user and the reason for variation but not the component itself. A better name could be hasSubmitButton. i.e.`<MyForm hasSubmitButton={user.canSubmit} />`

# Using props

It’s time to use our first props after creating it!  
First thing to do when using props is to pass it as a parameter to the component's function.

```javascript
// we always use the keyword props in the function parameter
const Welcome = props =>{
 return (
   <h1>
     `Hello`
   </h1>
 )
}
```

# The props object

---

### At he props object

In the previous slide, we saw that props always arrive as an object to child components.  
In order to use it, we need to treat it as an object. We can access the desired value by using the **dot property accessor.**

```javascript
const Welcome = props =>{P

console.log(`props:`,props)

 return (

   <h1> welcome {props.name}</h1>

 )

}pp.js
```

```javascript
const App = () => (
 <div>
   <Welcome name="Sara" />
 </div>
);
```

### Welcome.js

```javascript
const Welcome = props =>{
console.log(`props:`,props)
 return (
   <h1> welcome </h1>
 )
}
```

* Props are arguments that are passed into React components.
    
* Props are used to ensure communication inside the component tree.
    
* Props are immutable as their value cannot be changed by the child component.
    
* Props are only passed from parent to child.
    

### Children Prop

Let's do a quick reminder of HTML. An HTML element is the combination of an opening tag, a content and closing tag.  
That approach is still valid using React. <mark>We can create a component and pass or insert content between the opening and closing tags. </mark> That is what we call React children.

```javascript
const App = () => {
 return (
   <div>
     <Welcome>Sarrah </Welcome>
   </div>
 );
};
```

# Children prop usage

That is amazing, isn't it? The value passed between the two tags can be used by the child component. Only the syntax has changed.  
To access this value, we use `props.children`. Here is a much more detailed example below

```javascript
const App = () => {

 return (
   <div>
     <Welcome>Arya Stark</Welcome>
   </div>
 );
};
```

```javascript
const Welcome = props => {

 // whatever is passed between the tags of the component call can be accessed via this syntax
 return <h1>Welcome {props.children}</h1>;
};
```

# Rerendering on prop changes

React components will render if the props change. React runs a comparison between the new and previous Props and will automatically render the new ones.  
We have this simple React component that displays the title on screen :

```javascript
import React from "react";
const MyComponent = ({ title }) => <h1>{title}</h1>;
export default MyComponent;
```

We are simply going to pass a title props to MyComponent component :

```javascript

<MyComponent title="I'm learning React" />;

//output on screen: I'm learning React
```

As we have said in the beginning, props are a core idea in React's architecture.  
Let's reflect on something for a moment. If we have used a prop in a component but we forget to send its value from the parent component, that will inherently produce problems in the execution. For that reason, React provides a technique that will enormously help us. That technique is called the **<mark>Default props</mark>**<mark>.</mark>

This code defines a very simple ReactHeader component that renders an `<h1>` element containing a heading for the documentation of a particular React version.

```javascript
// Simple React Component

function ReactHeader(props) {

 return <h1>React {props.version} Documentation</h1>;

}
```

In the ReactHeader component, we are going to set the prop version to 18. Everything else seems to be working properly in the ReactHeader component.

# Solution:

You could fix this by setting the `default props` in the component :

```javascript
// Simple React Component

function ReactHeader(props) {

 return <h1>React {props.version} Documentation</h1>;

}

// Set default props
ReactHeader.defaultProps = {

 version: "16"

};
```

### PropTypes

Props are a very important mechanism for passing read-only attributes to React components. These attributes are usually required to be of a certain type or form for them to be used properly in the component.

If a prop is passed to a component in a type or form that is unfamiliar, the component may not behave as we intend it to. Thus, a great way of improving React components is props validation.

React provides an internal mechanism for adding typechecking to components. React components use a special property named **<mark>propTypes</mark>** <mark>to set up typechecking.</mark>

When props are passed to a ReacReact.PropTypes:

Prior to React 15.5.0, a utility named PropTypes was available, as part of the React package, which provided a lot of validators for configuring type definitions for component props. It could be accessed with **React.PropTypes**.

However, in later versions of React, (now 18), this utility has been moved to a separate package named prop-types, so you need to add it as a dependency for your project in order to get access to the **PropTypes** utility:

```javascript
npm install prop-types --save-dev
```

It can be imported into your project files as follows:

```javascript
import PropTypes from "prop-types";
```

## PropTypes validators:

As stated in the previous section, the `PropTypes` utility exports a lot of validators for configuring type definitions. Here are the validators for the basic data types:

`PropTypes.any // PropTypes.bool // PropTypes.number // PropTypes.string // PropTypes.func // PropTypes.array // PropTypes.object // PropTypes.symbol`

```javascript
Component.propTypes = {

 anyProp: PropTypes.any,

 booleanProp: PropTypes.bool,

 numberProp: PropTypes.number,

 stringProp: PropTypes.string,

 functionProp: PropTypes.func

};
```

# Multiple types:

`PropTypes` also export validators that can allow a limited set of values or multiple sets of data types for a prop. Here they are:

* **PropTypes.oneOf:** The prop is limited to a specified set of values, treating it like an enum.
    
* **PropTypes.oneOfType:** The prop should be one of a specified set of types, behaving like a union of types.