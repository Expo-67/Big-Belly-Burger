---
title: "Asynchronous Programming in Javascript"
datePublished: Thu Mar 13 2025 10:49:42 GMT+0000 (Coordinated Universal Time)
cuid: cm8788v9h000309jpataf6dwp
slug: asynchronous-programming-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/RYyr-k3Ysqg/upload/edda36572527ea487522b27a5eb282cf.jpeg
tags: javascript

---

Asynchronous programming in Javascript is a paradigm that allows you to perform non-blocking operations, enabling your code to continue executing while waiting for time -consuming tasks to complete

### Promise

A `Promise` is an object that represents a value that may be available now, or in the future, or never. It has three states: `pending`, `fulfilled`, or `rejected`. Promises help handle asynchronous operations in a more readable way compared to callbacks.

Consuming Promises

Axios is an abstraction on top of the XML HTTP request, it is promise based

.then - then is a function on a promise not axios

part of the definition of a promise is that it handles the eventual

Axios returns much data from the API it also includes the HTTP

### Handling errors with Promises

When using Promises, you can handle errors using `.catch()`, `.then()`'s second argument, or `.finally()` for cleanup tasks. Let's dive into the different ways to manage errors:

1. catch () - handles errors that occur during execution of a promise
    
2. then () - The `.then()` method can take a second argument, which is an error-handling function. This approach allows you to handle errors immediately after a successful result.
    
3. finally()- used to execute code after the Promise is settled, regardless of whether it was resolved or rejected. It
    

### Creating a promise

To create a promise in JavaScript, you use the `Promise` constructor, which takes a function known as the executor. This executor function has two parameters: `resolve` and `reject`. You call `resolve()` when the operation completes successfully, and `reject()` when there is an error.

Make sure when creating a promise it

`const myPromise = new Promise((resolve, reject) => {` (executer function)

`let isSuccess = true; // Simulating a condition if (isSuccess) { resolve("The operation was successful!"); } else {`

`reject("The operation failed."); } });`

### Promise States

JavaScript `Promise` represents an operation that may complete in the future, and it can be in one of three states:

### 1\. **Pending**

* **Description**: The initial state of a promise, which means that the operation has not completed yet.
    
* **Behavior**: It remains pending until it is either resolved or rejected.
    
* **Example**: When you create a new `Promise`, it is in the pending state until `resolve()` or `reject()` is called
    

### 2\. **Fulfilled**

* **Description**: The promise has been completed successfully, and it has a resulting value.
    
* **Behavior**: Once fulfilled, the value of the promise can be accessed using `.then()`.
    
* **Example**: If the operation succeeds, you call `resolve(value)`, which moves the promise from the pending state to the fulfilled state.
    

### **3.Rejected**

* **Description**: The promise has failed, and it has a reason why it failed (usually an error).
    
* **Behavior**: Once rejected, the error is caught using `.catch()`.
    
* **Example**: If the operation fails, you call `reject(error)`, which moves the promise from the pending state to the rejected state.
    
    A **pending** promise can transition to either **fulfilled** (resolved) or **rejected**.
    
    Once a promise is **fulfilled** or **rejected**, it becomes **settled**. A settled promise cannot change states again.
    

In practice:

* You use `.then()` to handle the **fulfilled** state.
    
* You use `.catch()` to handle the **rejected** state.
    
* `.finally()` can be used for actions that should happen regardless of whether the promise is fulfilled or rejected.
    

# Iterating with Async / Await

Using `async`/`await` to iterate over asynchronous operations allows you to handle each promise one at a time in a sequential manner, instead of all at once. This is particularly useful when you need to execute each operation in order, rather than in parallel.

1. **Event Loop Mechanism:** Asynchronous programming in JavaScript relies on the event loop, a mechanism that allows non-blocking execution of code. The event loop continuously checks the message queue for events or tasks and executes them in a sequential manner.
    
2. **Callbacks:** Callback functions are a fundamental concept in asynchronous JavaScript. They are functions passed as arguments to other functions, to be executed later when a specific event occurs. Callbacks enable the execution of code after asynchronous operations, such as file I/O or network requests, are completed.
    
3. **Promises:** Promises are a more structured way to handle asynchronous operations compared to callbacks. They represent a value that might be available now, or in the future, or never. Promises have states (pending, fulfilled, or rejected) and provide methods like `.then()` and `.catch()` for handling the result or error of an asynchronous operation.
    
4. **Async/Await:** Introduced in ECMAScript 2017, the `async` and `await` keywords simplify asynchronous code and make it look more synchronous. An `async` function returns a promise, and within it, the `await` keyword is used to pause execution until a promise is resolved or rejected. This syntax enhances code readability and maintainability.
    
5. **Error Handling:** Asynchronous programming in JavaScript requires careful error handling due to the nature of non-blocking operations. Callbacks often involve error-first patterns (callback takes an error as its first parameter), while Promises use `.catch()` for error handling. Async/Await simplifies error handling by allowing the use of try/catch blocks within asynchronous code.