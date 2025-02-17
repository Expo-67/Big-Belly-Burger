---
title: "Learning Node.js: A Step-by-Step Guide"
datePublished: Mon Feb 17 2025 03:51:40 GMT+0000 (Coordinated Universal Time)
cuid: cm78iqthn000509k03lyadgb0
slug: learning-nodejs-a-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1726037514817/11b2971f-1fc9-4d54-8257-1f814c901d92.png
tags: nodejs, node-js

---

This is a Javascript runtime + Javascript library ()

Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient

Quite often we use node to build APIs(Application Programming Interfaces)- services that power our client applications

### Local Enviroment setup

You need to have two softwares available :

1. Text editor- this is where you type your code a good example is <mark>VS Code,</mark> the files that you create with your editor are called <mark>source files</mark> and contain <mark>program source code .</mark>
    
    The source files are named with the .js extension
    
2. Node.js binary installables
    
    The Node.js interpreter will be used to interpret and execute your Javascript code
    

`node -v` (find out the version of node that you have)

Node js has the following important modules:

1. Import required modules- we use the require directive to load the HTTP module( `var http = require("http");`)
    
2. Create server- A server which listens to the clients requests: we use the HTTP instance and call `http.createServer()` to create a server instance and then bind it to port 8081 using the listen method assocaiated with the server instance.
    
    We pass it a function with the parameters request and response.
    
    ```javascript
    http.createServer(function (request, response) {
       // Send the HTTP header 
       // HTTP Status: 200 : OK
       // Content Type: text/plain
       response.writeHead(200, {'Content-Type': 'text/plain'});
       
       // Send the response body as "Hello World"
       response.end('Hello World\n');
    }).listen(8081);
    
    // Console will print the message
    console.log('Server running at http://127.0.0.1:8081/');
    ```
    
    1. Read request and return response
        
        The server created will <mark>read a HTTP request</mark> made by the client which can be a browser or a console and then <mark>return the response</mark>
        
        ```javascript
        var http = require("http"); //import of http module
        
        http.createServer(function (request, response) {
           // Sets the HTTP header 
           // HTTP Status: 200 : OK
           // Content Type: text/plain
           response.writeHead(200, {'Content-Type': 'text/plain'});
           
           // Send the response body as "Hello World"
           response.end('Hello World\n');
        }).listen(8081);
        
        // Console will print the message
        console.log('Server running at http://127.0.0.1:8081/');
        ```
        
        This code is creating a simple HTTP server using Node.js. It first imports the 'http' module, then creates a server using the `http.createServer` method. Inside the server creation function, it sets the HTTP header with a status code of 200 and a content type of text/plain. It then sends the response body as "Hello World" and listens on port 8081.
        
        After creating the server, it logs a message to the console indicating that the server is running at [http://127.0.0.1:8081/](http://127.0.0.1:8081/).
        
        ### Take note:
        
        **Local modules** are modules created <mark>locally within your Node.js application</mark>. They are not part of the built-in Node.js modules
        
        To import a node module we use the keyword <mark>require</mark>
        
        HTTP module does not need to be installed but you can just require it
        
        `const http = require('http');`
        
        diffrence between <mark>core modules</mark> and <mark>third party modules</mark>\- the first one is installed with nodejs and the second one is installed separately.
        
        npm init - initializes a node project with package.json file.
        
        ### REPL
        
        Read Eval Print Loop, node comes bundled in this enviroment
        
        * **Read** − Reads user's input, parses the input into JavaScript data-structure, and stores it into memory.
            
        * **Eval** − Takes and evaluates the data structure.
            
        * **Print** − Prints the result.
            
        * **Loop** − Loops the above command until the user presses **ctrl-c** twice.
            

It can be started by running the command `$node`

use VAR- when var keyword is used then the value is stored but not printed.

```javascript
$ node
> x = 10
10
> var y = 10
undefined
> x + y
20
> console.log("Hello World")
Hello World
undefined
```

In the given code, we are using the Node.js environment to execute JavaScript code. We first declare a variable `x` and assign it the value `10`. When we enter `x` in the console, it returns `10`. Then we declare a variable `y` using the `var` keyword and assign it the value `10`. When we enter `x + y`, it returns `20` because `x` has the value `10` and `y` also has the value `10`, so they add up to `20`. Lastly, we use `console.log()` to print the string "Hello World" to the console, and it returns `Hello World` followed by `undefined`.

### Multiline Expression

```javascript
$ node
> var x = 0  // declairing the variable x and initialize to 0
undefined
> do {
   ... x++; //increaments x by 1
   ... console.log("x: " + x); //logs value of x
   ... } 
while ( x < 5 ); // as long as x is less than 5
x: 1
x: 2
x: 3
x: 4
x: 5
undefined
>
```

This code is using a do-while loop in JavaScript. It starts by declaring a variable x and initializing it to 0. Then, it enters a do-while loop that increments x by 1 and logs the value of x to the console as long as x is less than 5. After the loop finishes, it returns "undefined" in the console.

### Underscore Variable

```javascript
$ node
> var x = 10
undefined
> var y = 20
undefined
> x + y
30
> var sum = _
undefined
> console.log(sum)
30
undefined
>
```

This code is using the Node.js environment to perform some basic arithmetic operations. It first declares two variables, x and y, and assigns them the values 10 and 20, respectively. Then it adds the values of x and y together using the + operator, which results in 30.

After that, it declares a new variable sum and a<mark>ssigns it the value of the special underscore variable (_), which in this case holds the value 30.</mark>

Finally, it logs the value of sum using console.log(), which prints 30 to the console.

REPL commands

* **ctrl + c** − terminates the current command.
    
* **ctrl + c twice** − terminates the Node REPL.
    
* **ctrl + d** − terminates the Node REPL.
    
* **Up/Down Keys** − see command history and modify previous commands.
    
* **tab Keys** − list all of the current commands.
    
* **.help** − list all of the commands.
    
* **.break** − exits from multiline expression.
    
* **.clear** − exits from multiline expression.
    
* **.save filename** − saves the current Node REPL session to a file.
    
* **.load filename** − loads file content from current Node REPL session
    

### NPM - Node Package Manager

Online repositories for node.js packages/modules which are searchable

`npm --version`(verifies the version of npm)

`npm install npm -g` (updates an old version of npm)

`npm install<module name>`( syntax to install a node module) example `npm install express`

In your .js file you can use this module: `var express = require('express')`

* By default NPM installs any dependency in the local mode. Locally deployed packages are accessible `via require()` example, when we installed express module, it created node\_modules directory in the current directory where it installed the express module. use `npm ls` to list down all localy installed modules.
    
* Globally installed packages/dependencies are stored in a system directory, such dependencies can be used in CLI function of any Node.js but can not be imported using `require()` example installing express globally use the command `npm install express -g` use the command `npm ls -g` to check all the modules globally
    

### package.json

This is a JSON file that serves as the central configuration point for your Node.js project

The attributes for the package.json file are:

* **name** − the name of the package
    
* **version** − the version of the package
    
* **description** − the description of the package
    
* **homepage** − the homepage of the package
    
* **author** − the author of the package
    
* **contributors** − the name of the contributors to the package
    
* **dependencies** − the list of dependencies. NPM automatically installs all the dependencies mentioned here in the node\_module package folder.
    
* **repository** − the repository type and the URL of the package.
    
* **main** − the package entry point.
    
* **keywords** − keywords.
    

`npm uninstall express` - uninstalling a module

`npm update express` - update a module(in this example we are updating express)

`npm init` - generates the skeleton of the package.json

### callback

A clallback function is called at the completion of a given task, all node apis are written in such a way that they support callbacks

### Blocking code

create a text file named input.txt with random code “Random test just for testing!!!“

create a main.js file with the following code.

```javascript
var fs = require("fs");
// fs is the file system module we will see it later
var data = fs.readFileSync('input.txt');

console.log(data.toString());
console.log("Program Ended");
```

This code is using the 'fs' module in Node.js to read the contents of a file called 'input.txt'. The 'fs' module is used for file operations in Node.js. The method 'readFileSync' is used to read the file synchronously, meaning the program will wait until the file is read before moving on to the next line of code.

The 'data' variable stores the contents of the file as a buffer, which is then converted to a string using the 'toString()' method. This string is then printed to the console using 'console.log()'.

Finally, the program prints "Program Ended" to the console, indicating that it has finished running.

Run the main .js you will get the output “Random test just for testing“

### Non-blocking code

create a text file named input.txt with random code “Random test just for testing!!!“

update main.js with this code:

```javascript
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
//this is the callBack function
   if (err) return console.error(err);
   console.log(data.toString());
});

console.log("Program Ended");
```

This code is using the Node.js 'fs' (file system) module to read the contents of a file named 'input.txt'. The 'fs.readFile' function takes two parameters: the file to read and a callback function to be executed once the file is read.

The callback function takes two parameters: 'err' for any error that may occur during reading the file, and 'data' for the contents of the file. If there is an error, it will be logged to the console. If there is no error, the contents of the file will be logged to the console using 'console.log(data.toString())'.

After calling 'fs.readFile', the code continues to execute and logs "Program Ended" to the console. This happens before the file is read and the callback function is executed, because reading the file is an asynchronous operation.  
Run the main .js you will get the output “Random test just for testing“

From the above two examples of blocking and non-blocking calls: The program <mark>blocks the call until it reads the file and only then it proceeds to end program(</mark>The program blocks the call until it reads the file and only then proceeds to end the program.<mark>)</mark>. The second program shows that the <mark>program does not wait for file reading and proceeds to print ‘Program Ended’ </mark> and at the same time the program, without blocking, continues reading the file.

### Node.js Event loop

Node.js is a **single-threaded** application, but it can support concurrency via the concept of **event** and **callbacks**.This means that while Node.js runs on a <mark>single thread</mark>, it can handle <mark>multiple operations concurrently by using an event-driven, non-blocking I/O model.</mark> This allows Node.js to manage multiple connections simultaneously without the need for multiple threads, making it lightweight and efficient.

Node thread keeps an event loop and whenever a task gets completed it fires the corresponding event signaling the event listener.

in an event-driven application there is generally a main loop that listens for events and then triggers a callback function when one of those events is detected.

Although events look quite similar to callbacks the difference lies in the fact that callback functions are called when an <mark>asynchronous function returns its result</mark>, event handling works on the observer pattern. The function that listens to events act as observers, so whenever an event gets fired its listener function starts executing.

```javascript
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();
```

```javascript
// Import events module
var events = require('events');

// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();

// Create an event handler as follows
var connectHandler = function connected() {
   console.log('connection succesful.');
  
   // Fire the data_received event 
   eventEmitter.emit('data_received');
}

// Bind the connection event with the handler
eventEmitter.on('connection', connectHandler);
 
// Bind the data_received event with the anonymous function
eventEmitter.on('data_received', function() {
   console.log('data received succesfully.');
});

// Fire the connection event 
eventEmitter.emit('connection');

console.log("Program Ended.");
```

First, the `events` module is imported using `require('events')`. Then, an `EventEmitter` object is created using `new events.EventEmitter()`.

A function `connectHandler` is defined to handle the 'connection' event. When the 'connection' event is emitted, this function will log "connection successful" and then emit the 'data\_received' event.

The 'connection' event is bound to the `connectHandler` using `eventEmitter.on('connection', connectHandler)`.

An anonymous function is also bound to the 'data\_received' event using `eventEmitter.on('data_received', function() { console.log('data received successfully.'); })`.

Finally, the 'connection' event is emitted using `eventEmitter.emit('connection')`. This triggers the `connectHandler` function, which in turn emits the 'data\_received' event.

After all the events have been emitted and handled, "Program Ended." is logged to the console.

Once you run the output should be (connection successful, Data recieved successfully, Program ended)

### How do Node App works

In node any asynchronous functions <mark>accepts a callback</mark> as the last parameter and a <mark>callback </mark> accepts an <mark>error as the first parameter</mark>

asynchronous functions=&gt; callback as last parameter

callback =&gt; error as first parameters

create input. txt “Dummy text just for testing”

create a js file called main.js

```javascript
var fs = require("fs");

fs.readFile('input.txt', function (err, data) {
   if (err) {
      console.log(err.stack);
      return;
   }
   console.log(data.toString());
});
console.log("Program Ended");
```

Here fs.readFile() is an async function whose purpose is to read a file. If an error occurs during the read operation, then the **err object** will contain the corresponding error, or else data will contain the contents of the file. **readFile** passes (err) and data to the callback function after the read operation is complete, which finally prints this content:

Program Ended, Dummy Test just for Testing!!

### Event Emitter Class

An fs.read stream emits an event when the file is opened, all objects which emit events are the instances of events. When a new listener is added ‘new listener event’ is fired.

Event Emitter provides multiple properties like on and emit.<mark>on</mark> property used to bind a function with the event and <mark>emit</mark> is used to fire an event

### Methods

1. .addListener(event, listener)- adds a listener at the end of the listeners array for the specified event
    
2. on(event , litsener)- adds a litsener at the <mark>end of the litseners array</mark> for the specified event, no checks are made to see if the listener has been updated.
    
3. once (event, listener) adds a one time litsener to the event, the listener is invoked only next time an event is fired
    
4. removeLitsener(event,listener) <mark>removes a listener </mark> from the listener array for the specified event.
    
5. removeAllLitseners(\[event\]) removes all litseners or those of the specified event
    
6. **listeners(event)** : Returns an array of listeners for the specified event.
    
7. **emit(event, \[arg1\], \[arg2\], \[...\])** : Executes each of the listeners in order with the supplied arguments. Returns true if the event had listeners, false otherwise.
    

Class Methods

listenerCount(emitter,event): -Returns the number of listeners for a given event

Example create a file named litsenerCount.js

```javascript
//import event module
var events = require('events');
// Create an eventEmitter object
var eventEmitter = new events.EventEmitter();
eventEmitter.on('connection',function(){
    console.log("hello connection")
});
// count the number of listener to this event
eventListeners = require('events').EventEmitter.listenerCount(eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");
```

The code first imports the event module and creates an eventEmitter object. Then it adds a listener to the 'connection' event, which logs "hello connection" when the event is emitted.

After that, it uses the `EventEmitter.listenerCount` method to count the number of listeners for the 'connection' event and logs the result. This code is essentially demonstrating how to create and use an event emitter in Node.js, as well as how to check the number of listeners for a specific event.

run the code by running the command: `node litsenerCount.js`

The output will be 1 listener(s ) litsening to connection event.

```javascript
var events = require('events');
var eventEmitter = new events.EventEmitter();

// listener #1
var listner1 = function listner1() {
   console.log('listner1 executed.');
}

// listener #2
var listner2 = function listner2() {
   console.log('listner2 executed.');
}

// Bind the connection event with the listner1 function
eventEmitter.addListener('connection', listner1);

// Bind the connection event with the listner2 function
eventEmitter.on('connection', listner2);

var eventListeners = require('events').EventEmitter.listenerCount
   (eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");

// Fire the connection event 
eventEmitter.emit('connection');

// Remove the binding of listner1 function
eventEmitter.removeListener('connection', listner1);
console.log("Listner1 will not listen now.");

// Fire the connection event 
eventEmitter.emit('connection');

eventListeners = require('events').EventEmitter.listenerCount(eventEmitter,'connection');
console.log(eventListeners + " Listner(s) listening to connection event");

console.log("Program Ended.");
```

This code is an example of using the EventEmitter class in Node.js to handle events.

First, the 'events' module is required and a new instance of EventEmitter is created.

Two listener functions, listner1 and listner2, are defined to log messages when they are executed.

The listener functions are then bound to the 'connection' event using the addListener and on methods of the eventEmitter.

The number of listeners for the 'connection' event is then logged using the listenerCount method.

The 'connection' event is then emitted, causing both listener functions to be executed.

The binding of listner1 is then removed using the removeListener method, and a message is logged to indicate that listner1 will not listen anymore.

The 'connection' event is emitted again, causing only listner2 to be executed this time.

Finally, the number of listeners for the 'connection' event is logged again, and a message indicating that the program has ended is logged.

The output will be:

2 Listner(s) listening to connection event listner1 executed. listner2 executed. Listner1 will not listen now. listner2 executed. 1 Listner(s) listening to connection event Program Ended.

Take Note:

* If an event litsener does not have atleast one litsener registered for the error event and an error event is emitted, the error is dismissed a stack trace is printed and the Node.js process exits.
    
* How many litseners can we watch to an event in Node JS? <mark>unlimited</mark>
    
* By default EventEmitters will print a warning if more than <mark>10</mark> listeners are added for a particular event:
    
* When the EventEmitter object emits an event all of the functions attatched to that specific event are called <mark>synchronously , any values returned they are ignored</mark>
    
* You can make listeners execute <mark>asynchronousl</mark>y by manually wrapping them in setImmediate()
    
* An event listener in Node js is like a <mark>messaging system</mark> inside your code, allowing diffrent parts of your program to communicate. <mark>Emit an event</mark> (it is like saying , hey something happened example you can emit a fileLoaded event. <mark>Litsen for an event</mark>, other parts of your code can listen for these events and react when they happen.
    
    `const EventEmitter = require('events');`
    
    `const eventEmitter = new EventEmitter(); // Listener: What to do when the event happens eventEmitter.on('greet', () => { console.log('Hello, world!'); }); // Emitting the event: Trigger the action`
    
    `eventEmitter.emit('greet'); // Output: Hello, world!`
    
    greet is the event name, the <mark>emit() method </mark> triggers the event. The <mark>on() method</mark> listens and runs the function when the event is triggered
    

## Synchronous vs Asynchronous

The node file system module can be imported using the following syntax: `var fs = require(“fs”)`

### Synchronous

Tasks are executed <mark>one after the other in a sequence</mark>, (step by step

)each task must finish before the next one starts.

If a task takes time like reading a large file , it will block everything else until its done

`const fs = require('fs');`

`// Synchronous file read const data = fs.readFileSync('file.txt', 'utf8'); console.log(data); console.log('This runs after the file is read.');`

In this synchronous example, the file is read **first**. Only after that does the `console.log` run. If the file reading takes time, nothing else happens until it's done.

### Asynchronous

Tasks are started but Node.js can move on to the next task without waiting for the previous one to finish.

This allows Node.js to handle multiple things at once making it faster and non-blocking.

Asynchronous is more common because it allows the server to handle many requests efficiently without blocking.

`const fs = require('fs');`

`// Asynchronous file read fs.readFile('file.txt', 'utf8', (err, data) => { if (err) throw err; console.log(data); }); console.log('This runs immediately, before the file is read.');`

In this asynchronous example, the `fs.readFile` function starts reading the file, but **Node.js doesn't wait**. It moves to the next task (`console.log`). Once the file is read, the callback function is called, and the file data is printed.

The key difference: Synchronous : <mark>waits for a task</mark> to complete before moving on. while Asynchronous: <mark>moves on to the next task without waiting</mark>, when the task finishes it comes back and handles it

syntax for opening a file: `fs.open(path, flags[, mode], callback)`

## Parameters

Here is the description of the parameters used :

* **path** − This is the string that has the file name and the path.
    
* **flags** − Flags indicate the behavior of the file to be opened. All possible values have been mentioned below.
    
* **mode** − It sets the file mode (permission and sticky bits), but only if the file was created. It defaults to 0666, readable and writeable.
    
* **callback** − This is the callback function which gets two arguments (err, fd).
    

## Flags

* **r** : Opens file for reading. An exception occurs if the file does not exist.
    
* **r+** : Opens file for reading and writing. An exception occurs if the file does not exist.
    
* **rs** : Opens file for reading in synchronous mode
    
* **rs+** : Opens file for reading and writing, asking the OS to open it synchronously. See notes for 'rs' about using this with caution.
    
* **w** : Opens file for writing. The file is created (if it does not exist) or truncated (if it exists).
    
* **wx** : Like 'w' but fails if the path exists.
    
* **w+** : Opens file for reading and writing. The file is created (if it does not exist) or truncated (if it exists).
    
* **wx+** : Like 'w+' but fails if path exists.
    
* **a** : Opens file for appending. The file is created if it does not exist.
    
* **ax** : Like 'a' but fails if the path exists.
    
* **a+** : Opens file for reading and appending. The file is created if it does not exist.
    
* **ax+** : Like 'a+' but fails if the the path exists.
    

```javascript
var fs = require("fs");

// Asynchronous - Opening File
console.log("Going to open file!");
fs.open('input.txt', 'r+', function(err, fd) {
   if (err) {
      return console.error(err);
   }
   console.log("File opened successfully!");     
});
```

In this example it opens a file

Getting file information: `fs.stat(path, callback)`

These methods are given the following list:

* **stats.isFile()** : Returns true if file type of a simple file.
    
* **stats.isDirectory()** : Returns true if file type of a directory.
    
* **stats.isBlockDevice()** : Returns true if file type of a block device.
    
* **stats.isCharacterDevice()** : Returns true if file type of a character device.
    
* **stats.isSymbolicLink()** : Returns true if file type of a symbolic link.
    
* **stats.isFIFO()** : Returns true if file type of a FIFO.
    
* **stats.isSocket()** : Returns true if file type of asocket.
    

Global objects

\_\_filename- this refers to the filename of the code being executed.( `C:\Users\user\OneDrive\Desktop\gomycode\nodepractice\main.js`) it prints out the file name path of main.js

\_\_dirname -represents the name of the directory thus printing out the path

`C:\Users\user\OneDrive\Desktop\gomycode\nodepractice`

setTimeout(cb,ms)

A global function is used to run callback (cb) after at least ms (millisecond)

```javascript
function printHello() {
  console.log("Hello, World");
}
setTimeout(printHello, 2000);
clearTimeout(t);- this clears the timeout
```

In the example above we have set a timer for 2 seconds

setInterval(cb,ms)

The global function is used to run a call back function repeatedly after a few millisecond

```javascript
function printHello() {
  console.log("Hello, World");
}
setInterval(printHello, 2000);// The program executes printHello() after 
//every 2 seconds
```

### Utility models.

* [OS Module](https://nodejs.org/api/os.html):  
    Provides basic operating-system related utility functions.  
    ​
    
* [Path Module](https://nodejs.org/api/path.html):  
    Provides utilities for handling and transforming file paths.  
    ​
    
* [Net Module](https://nodejs.org/api/net.html):  
    Provides both servers and clients as streams. Acts as a network wrapper.  
    ​
    
* [DNS Module](https://nodejs.org/api/dns.html):  
    Provides functions to do actual DNS lookup as well as to use underlying operating system name resolution functionalities.  
    ​
    
* [Domain Module](https://nodejs.org/api/domain.html):  
    Provides ways to handle multiple different I/O operations as a single group
    

### Web server

This is a s<mark>oftware application which handles HTTP requests</mark> by the HTTP client like web browsers and returns web pages in response to the clients

A web app is ussually divide into:

1. Client- consists of web browsers, mobile browsers or applications which can make HTTP request to web server
    
2. Server- This layer has the web server which can intercept the requests made by the clients and pass them the response.
    
3. Business layer- contains application server which is utilized by the web server to do required processing
    
4. Data - This layer contains the database or any source of data.
    

### Creating a web server using node

```javascript
var http = require("http");
var fs = require("fs");
var url = require("url");

// Create a server
http
  .createServer(function (request, response) {
    // Parse the request containing file name
    var pathname = url.parse(request.url).pathname;

    // Print the name of the file for which request is made.
    console.log("Request for " + pathname + " received.");

    // Read the requested file content from file system
    fs.readFile(pathname.substr(1), function (err, data) {
      if (err) {
        console.log(err);

        // HTTP Status: 404 : NOT FOUND
        // Content Type: text/plain
        response.writeHead(404, { "Content-Type": "text/html" });
      } else {
        //Page found
        // HTTP Status: 200 : OK
        // Content Type: text/plain
        response.writeHead(200, { "Content-Type": "text/html" });

        // Write the content of the file to response body
        response.write(data.toString());
      }

      // Send the response body
      response.end();
    });
  })
  .listen(8081);

// Console will print the message
console.log("Server running at http://127.0.0.1:8081/");
```