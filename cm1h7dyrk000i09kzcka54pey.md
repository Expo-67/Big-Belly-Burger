---
title: "Express Js"
datePublished: Wed Sep 25 2024 01:45:26 GMT+0000 (Coordinated Universal Time)
cuid: cm1h7dyrk000i09kzcka54pey
slug: express-js
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/2JIvboGLeho/upload/52bd149fd0531d5c22ca86b6dcd1bf70.jpeg
tags: express, expressjs-cilb5apda0066e053g7td7q24

---

A minimal and flexible <mark>web framework for Node j</mark>s, used for building server side web applications and APIS.

Express provides <mark>basic tools that facilitate the creation of Node.js application</mark> without obscuring Node.js features that you know and love

When it comes to frameworks they can be either opinionated or Unopiniated(extremely flexible and you can use which library to use and no strict rules)

### How does Express work?

Express js ussually has an entry point where we can perform the following steps:

* Include third party dependecies
    
* Configure Express.js app settings such as the template engine and its files’ extensions.
    
* Define middlewaress such as error handlers, static files folder, cookies and other parsers.
    
* Define routes.
    
* Connect to databases such as MongoDB, Redis or MySQL.
    
* Start the app.
    

To install express run the command :`npm install express -- save`, before that be sure to install the package.json file(`npm init -y`) .

Adding these in package.json file:"scripts": {

```json
"scripts": {
    "start": "node server",
    "dev": "node --watch server"
```

Lets create our first app using express:

`const express = require (‘express’);` - include this library to import express

`const app = express();`\- create an application

`const port = 4000;` - the application is a web server running localy in port 4000

```javascript
app.get('*', function(req, res){  res.end('Hello World');  });
```

This code sets up a route in an Express app that matches any URL. When a request is made to any URL, the server will respond with the text "Hello World" and then end the response.

Express.js request handle is similar to the one we pass as a callback

```javascript
app.listen(port, function() {
  console.log('The server is running, ' +
      ' please, open your browser at http://localhost:%s', 
      port);
});
```

This code is using the `app.listen` method to start a server on the specified `port`. When the server starts running, it will log a message to the console using `console.log`. The message will indicate that the server is running and provide the URL for accessing it, using the `port` variable to specify the port number.

When we run the file server in the terminal it can automatically generate output without running the command, `node server.js` but run the command `npm run dev`;

```javascript
app.get("/about", (req, res) => {
  res.send("About");
});
```

In this instance when we run the `local host:8000/about` it displays the details of About

res has a method called send file // setup static folder

```javascript
// setup static folder
app.use(express.static(path.join(__dirname, "public")));
```

This code sets up a static folder for serving static files such as images, CSS, and JavaScript files. It uses the `express.static` middleware in Express to serve files <mark>from the "public" directory located</mark> in the current working directory of the application. This means that any files placed in the "public" directory can be accessed by clients making requests to the server.

```javascript
app.get("/api/posts", (req, res) => {
  res.json(posts);
});
```

This code creates a route for the GET request to the "/api/posts" endpoint. When a GET request is made to this endpoint, the server responds by sending a JSON representation of the variable "posts" back to the client.

Make sure that you have installed postman on your vs code

Create an env(enviroment varables)file and inside it put the PORT=’8080’ in this scenario.In server.js be sure to import the port const `port = process.env.PORT||8000`"scripts": {

```json
"scripts": {
    "start": "node server",
    "dev": "node --watch --env-file=.env server"
  },
```

be sure to modify your package.json on the dev by adding the env file.

```javascript
app.get("/api/posts/:id", (req, res) => {
  const id = parseInt(req.params.id);
  res.json(posts.filter((post) => post.id === id));
});
```

This code sets up a route in the app to handle GET requests to the "/api/posts/:id" endpoint. When a request is made to this endpoint, the code retrieves the "id" parameter from the request and converts it to an integer using the parseInt function. Then, it filters the "posts" array to find the post with the matching id and sends the filtered post as a JSON response.

Open postman and put GET : [http://localhost:8000/api/posts/2](http://localhost:8000/api/posts/2) press send in this example it brings details from the database with an id of 2

### dealing wih query strings

[http://localhost:8000/api/posts/?limit=2](http://localhost:8000/api/posts/?limit=2) when you press send you only get 2 fields of data also after setting:

```javascript
 if (!isNaN(limit) && limit > 0) {
    res.json(posts.slice(0, limit));
  } else {
    res.json(posts);
  }
});
```

This code is a conditional statement that checks if the variable "limit" is a number and greater than 0. If both conditions are true, it returns a JSON response with a subset of the "posts" array, containing the first "limit" number of elements. If either condition is false, it returns a JSON response with the entire "posts" array.

Setting status code: They are used to communicate the result of a clients request:

* Successful (e.g., 200 OK)
    
* Redirected (e.g., 301 Moved Permanently)
    
* Failed due to a client-side error (e.g., 400 Bad Request)
    
* Failed due to a server-side error (e.g., 500 Internal Server Error)
    

```javascript
app.get("/api/posts/:id", (req, res) => {
  const id = parseInt(req.params.id);
  const post = posts.find((post) => post.id === id);

  if (!post) {
    res.status(404).json({ msg: 'A post with the id of ${id} was not found'});
  } else {
    res.status(200).json(post);
  }
});
```

This code sets up a route for the GET request to "/api/posts/:id". When a request is made to this endpoint, the code retrieves the id parameter from the request and converts it to an integer using parseInt. It then searches for a post with the matching id in the posts array using the find method.

If a post with the specified id is found, it sends a response with a status code of 200 and the JSON data of the found post. If no post is found, it sends a response with a status code of 404 and a JSON object containing a message indicating that a post with the specified id was not found.

[http://localhost:8000/api/posts/1](http://localhost:8000/api/posts/1) when we put this in postman it will display only 1 post as specifified.

### Routes

This refers to how an application responds to a client request at a particular endpoint which is URI path and a specific HTTP request method (GET, POST ..)

The route structure:

```javascript
app.METHOD(PATH, HANDLER)
```

app is an instance of express

METHOD is a HTTP request method in lowercase

PATH is a path on the server

HANDLER is the function executed when the route is matched

In the example below the route path will match requests to (/about)

```javascript
app.get('/about', function (req, res) {
  res.send('about');
})
```

```javascript
app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...');
  next(); // pass control to the next handler
})
```

This code defines a route for the "/secret" URL path in an Express app. When a request is made to this path, the function provided as the second argument is called. Inside this function, it logs a message to the console saying "Accessing the secret section ...". It then calls <mark>the </mark> `next()` <mark>function, which passes control to the next handler in the middleware chain.</mark> This allows for additional processing to be done before sending a response back to the client.

Create a folder called routes create a file called posts.js

```javascript
const express = require("express");// import express 
const router = express.Router();// import routes

let posts = [
  { id: 1, title: "Post One" },
  { id: 2, title: "Post two" },
  { id: 3, title: "Post three" },
];

// Get all posts
router.get("/", (req, res) => {
  const limit = parseInt(req.query.limit);

  if (!isNaN(limit) && limit > 0) {
    res.status(200).json(posts.slice(0, limit));
  }
  res.status(200).json(posts);
});

//Get single post
router.get("/:id", (req, res) => { // be sure that it reads router
  const id = parseInt(req.params.id);
  const post = posts.find((post) => post.id === id);

  if (!post) {
    res.status(404).json({ msg: "A post with the id of ${id} was not found" });
  }
  res.status(200).json(post);
});

module.exports = router;
```

Next make sure you bring the routes file in server.js

```javascript
const express = require("express");
const path = require("path");
const posts = require("./routes/posts"); // imported the path to routes folder
const port = process.env.PORT || 8000;

const app = express();
// // setup static folder
// app.use(express.static(path.join(__dirname, "public")));

//Routes
app.use("/api/posts", posts);

app.listen(port, () => console.log("Server is running on port ${port}"));
```

### Getting data from the request body

Open a new postman [http://localhost:8000/api/posts](http://localhost:8000/api/posts) make sure it is a post request and pick the www-form

```javascript
//Body parser middleware
app.use(express.json());// takes care of submitting raw json
app.use(express.urlencoded({ extended: false }));// allow us to send form data
```

add this code in server.js

### creating a new post

```javascript
// create new post
router.post("/", (req, res) => {
  const newPost = {
    id: posts.length + 1,
    title: req.body.title,
  };

  if (!newPost.title) {
    return res.status(400).json({ msg: "Please include a title" });
  }
  posts.push(newPost);
  res.status(201).json(posts); //201 meaning that its successful
});
```

in the postman request view output. key put title and value add Brads posts it will be visible at the body.

### PUT Request

```javascript
router.put("/:id", (req, res) => {
  const id = parseInt(req.params.id);
  const post = posts.find((post) => post.id === id);

  if (!post) {
    return res
      .status(404)
      .json({ msg: "A post with the id of ${id} was not found" });
  }

  post.title = req.body.title;
  res.status(200).json(posts);
});
```

If we run this in post man: [http://localhost:8000/api/posts/2](http://localhost:8000/api/posts/2) this says that for id 2 when we send PUT and also dont forget to put x-www-form-urlencoded and set Key: title , Value: Updated post. The output will be as follows

CRUD- Create Read update and delete.

```json
[
    {
        "id": 1,
        "title": "Post One"
    },
    {
        "id": 2,
        "title": "Updated Post"
    },
    {
        "id": 3,
        "title": "Post three"
    }
]
```

### Delete request

```javascript
router.delete("/:id", (req, res) => {
  const id = parseInt(req.params.id);
  const post = posts.find((post) => post.id === id);

  if (!post) {
    return res
      .status(404)
      .json({ msg: "A post with the id of ${id} was not found" });
  }
  posts = posts.filter((post) => post.id !== id);
  res.status(200).json(posts);
});
```

If we run this in post man: [http://localhost:8000/api/posts/](http://localhost:8000/api/posts/2)1 this says that for id 1 when we send Delete one post will be deleted

### Middleware

This are functions that have access to the request and response object

A **function** that sits between the <mark>request from the user</mark> and the <mark>response from the server</mark>. It helps process the request before sending back a response.

`app.use((req, res, next) => { console.log('Request received'); next(); // Pass control to the next middleware });`

In this example, every time a request is received, it logs "Request received" and then moves on to the next step

Middleware can

* Modify the request or response.
    
* End the request-response cycle.
    
* Pass control to the next middleware function in the stack.
    

Make a seperate folder for middleware and have files in (logger.js(insert middleware code here))

In your main file index.js import the path of middleware and also dont forget to add this.

```javascript
ace
Save

Middleware

5/7

Express (Routing)

Middleware Introduction
Middleware functions are functions that have access to the request object (req), the response object (res), and the next function in the application’s request-response cycle.

The next function is a function in the Express router that, when invoked, executes the middleware succeeding the current middleware.
Middleware functions can perform the following tasks:

Execute any code.
Make changes to the request and the response objects.
End the request-response cycle.
Call the next middleware in the stack.
If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

Writing middleware (1/2)
Here is a simple example of a middleware function

//Simple request time logger
const myLogger = function (req, res, next) {
  console.log("A new request received at " + Date.now());
   next();
}
To load the middleware function, call app.use(), specifying which middleware function. For example, the following code loads the myLogger middleware function before the route to the root path (/).

const express = require('express');
const app = express();


//Simple request time logger
const myLogger = function (req, res, next) {
  console.log("A new request received at " + Date.now());
   next();
}

app.use(myLogger);

app.get('/', function (req, res) {
  res.send('Hello World!')
})

app.listen(3000);
```

The given code is an example of how to use middleware in an Express application. Middleware functions are functions that have access to the **request object**, the **response object**, and the **next function** in the application’s request-response cycle. They can perform tasks such as <mark>executing code, making changes to the request and response objects, ending the request-response cycle, and calling the next middleware in the stack.</mark>

In this specific example, a simple middleware function called myLogger is defined to log the time of a new request. This function takes three parameters: req (request), res (response), and next. Inside the function, it logs the time of the new request using console.log and then calls the next function to pass control to the next middleware function.

To load the middleware function, the app.use() method is used to specify which middleware function to use. In this example, the myLogger middleware function is loaded before the route to the root path (/) using app.use(myLogger).

Finally, the Express app listens on port 3000 and responds with "Hello World!" when a request is made to the root path.

Overall, this code demonstrates how to define and use a simple middleware function in an Express application to log request times. The output will be

```javascript
A new request received at 1584954785016
```

```javascript
const express = require('express');
const app = express();

//Middleware function to log request protocol
app.use('/things', function(req, res, next){
   console.log("A request for things received at " + Date.now());
   next();
});


// Route handler that sends the response
app.get('/things', function(req, res){
   res.send('Things');
});

app.listen(3000);
```

This code is using the Express framework for Node.js to create a simple web server. It first imports the express module and creates an instance of the express application.

Then, it defines a **middleware function using** `app.use()`. This function logs a message to the console when a request for the '/things' route is received, and then calls the `next()` function to pass control to the next middleware in the stack.

Next, it defines a route handler using `app.get()` for the '/things' route. This handler sends the response 'Things' when a GET request is made to the '/things' endpoint.

Finally, it starts the server and listens on port 3000 for incoming requests.

### Error handling middleware

Error hanling has four arguments

```javascript
app.use(function (err, req, res, next) //This are the arguments
{
  console.error(err.stack)
  res.status(500).send('Something broke!')
})
```

In order to call the error-handling middleware we need to pass the error to the next()

```javascript
app.get('/', (req, res, next) => {
  next(new Error('I am passing you an error!'));
});
```

### Third party Middlewares

body parser- we need to parse incoming requests bodies in a middleware, we need to install it first

```javascript
npm install --save body-parser
```

include the following in your index.js

```javascript
const bodyParser = require('body-parser');


//To parse URL encoded data
app.use(bodyParser.urlencoded({ extended: false }))


//To parse json data
app.use(bodyParser.json())
```

The first line of code is importing the 'body-parser' module, which is a middleware for parsing incoming request bodies in a middleware before your handlers, available under the req.body property.

The second line of code is using the **bodyParser middleware to parse incoming URL encoded data.** The extended option allows to choose between parsing the URL-encoded data with the querystring library (when false) or the qs library (when true).

The third line of code is using the bodyParser middleware to parse incoming JSON data. This allows the server to parse and access JSON data sent in the request body.

**cookie -parser**\- It passes cookie header and populates a req.cookies with objects that have cookie names as keys

Install cookie parser first - **npm install --save cookie-parser**

To mount include the following lines of code

```javascript
var cookieParser = require('cookie-parser');
app.use(cookieParser())
```

When a request is recieved by Express each middleware that matches the request is run in the order it is initialized ,so if an error occurs, all middlewares that are assigned to handle errors will be called in order until one of them does not call the next() function call.

### Template engines

A template engine facilitates the use of **static template files**.At runtime it replaces variables in a **template file with actual values and transforms the template into an HTML file**  
The popular template engines that work with Express are Pug, Mustache and EJS

To render templates you have to set the following setting properties:

* Views - specifies a directory where the template files are located example(app.set(‘views’, ‘./views’)
    
    * view engine - specifies the template engine that you use For example, to use the Pug template engine: app.set('view engine', 'pug')
        

### **Template Engine**

Pug template engine- pug uses white spaces and indentation.

we can create our own template engine.

Start by installing Pug template engine:

```javascript
install pug --save
```

Once pug has been installed set as the default template engine for your app

```javascript
app.set('view engine', 'pug');
app.set('views','./views');
```

create a new directory called views inside it create a file called first \_ view plug and enter:

```javascript
doctype html
html
   head
      title = "Hello Pug"
   body
      p.greetings#people Hello World!
```

add the following in the app route

```javascript
app.get('/first_template', function(req, res){
   res.render('first_view');
});  // Output will be Hello world
```

**Pug features**

1. Simple tags
    
    Tags are nested according to their indentation. Like in the example before, `<title>` was indented within the `<head>` tag, so it was inside it. But, the `<body>` tag was on the same indentation and that means it is a sibling of the `<head>` tag.
    
    We don’t need to close tags. As soon as Pug encounters the next tag on the same or outer indentation level, it closes the tag automatically.  
    We have 3 methods for putting text inside a tag:
    
    * Space separated
        
        ```javascript
        h1 Welcome to Pug
        ```
        
        * Piped text
            
            ```javascript
             | To insert multiple lines of text, 
             | You can use the pipe operator
            ```
            
            * Block of text
                
                ```javascript
                div.
                   But that gets tedious if you have a lot of text.
                   You can use "." at the end of a tag to denote a block of text.
                   To put tags inside this block, simply enter tag in a new line and 
                   indent it accordingly.
                ```
                

Comments

Pug uses the same method of commenting as Javascript

```javascript
//This is a Pug comment
<!--This is a Pug comment-->
```

**Attributes**

To define attributes we need to define a list of attributes that are separated using commas and put them inside parenthesis

```xml
div.container.column.main#division(width = "100", height = "100")
```

This line of cde from above is converted into this :

```xml
<div class = "container column main" id = "division" width = "100" height = "100"></div>
```

**Passing values to Templates**

Create a new route handler:

```javascript
const express = require('express');
const app = express();

app.get('/dynamic_view', function(req, res){
   res.render('dynamic', {
      name: “Gomycode", 
      url:"http://www.tutorialspoint.com"
   });
});

app.listen(3000);
```

create a new view file called dynamic\_pug with the following code:

```xml
html
   head
      title=name
   body
      h1=name
      a(href = url) URL
```

We can also insert passed variables within text to insert passed variable within text we use#{variable name}

```xml
html
   head
      title = name
   body
      h1 Greetings from #{name}
      a(href = url) URL
```

This is a simple HTML code **written in Pug, a template engine for Node.js**. It creates a webpage with a title in the head section and a greeting message and a hyperlink in the body section. The title of the webpage is set to the value of the variable "name". The h1 tag displays a greeting message using the value of the "name" variable, and the hyperlink uses the value of the "url" variable as its URL.

**Conditionals**

If a user is logged into an account it should display Hi, user and if not then Login, Sign up we can define a simple template like:

```xml
html
   head
      title Simple template
   body
      if(user)
         h1 Hi, #{user.name}
      else
         a(href = "/sign_up") Sign Up
```

When we render using our routes we can pass an object as:

```javascript
res.render('/dynamic',{
   user: {name: "Ayush", age: "20"}
});
```

### include and Components

Pug provides a very intuitive way to create components for a web page. For example, if you see a news website, the header with logo and categories is always fixed. Instead of copying that to every view we create, we can use the include feature. Following example shows how we can use this feature.  
Create 3 views with the following code

### HEADER.PUG

```javascript
div.header.
   I'm the header for this website.
```

### CONTENT.PUG

```javascript
html
   head
      title Simple template
   body
      include ./header.pug
      h3 I'm the main content
      include ./footer.pug
```

### FOOTER.PUG

```javascript
div.footer.
   I'm the footer for this website.
```

Create a route as follows:

```javascript
var express = require('express');
var app = express();

app.get('/components', function(req, res){
    res.render('content');
});

app.listen(3000);
```

The code is using the Node.js framework Express to create a web server. It first imports the express module and then creates an instance of the express application.

The `app.get` method is used to define a route for the server. In this case, when a GET request is made to the '/components' endpoint, the server will render the 'content' view.

Finally, the `app.listen` method is used to start the server and make it listen for incoming requests on port 3000.