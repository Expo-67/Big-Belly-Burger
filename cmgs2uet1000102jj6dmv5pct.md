---
title: "Object-Oriented Programming (OOP) Concepts"
datePublished: Wed Oct 15 2025 14:19:18 GMT+0000 (Coordinated Universal Time)
cuid: cmgs2uet1000102jj6dmv5pct
slug: object-oriented-programming-oop-concepts
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/8qEB0fTe9Vw/upload/96dafd0187726f5dd0517034ddc7c913.jpeg
tags: oop, object-oriented-programming

---

## **🧱 What Is Object-Oriented Programming?**

Object-Oriented Programming (OOP) is a way of structuring code by grouping related **data** (called *properties*) and **functions** (called *methods*) into reusable units called **objects**. These objects often model real-world things—like cars, users, or bank accounts—and help make your code more organized, scalable, and intuitive.

Think of it like building with LEGO: each block (object) has its own shape and purpose, but they can connect to form something bigger.

## **🔐 Encapsulation**

**Encapsulation** means bundling data and behavior inside a single unit (usually a class), and hiding internal details from the outside world. Each object manages its own state and logic.

### **Example:**

```javascript
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
    this.gear = 'P';
  }

  startEngine() {
    console.log(`${this.make} ${this.model} engine started`);
  }

  changeGear(newGear) {
    this.gear = newGear;
    console.log(`Gear changed to ${this.gear}`);
  }
}

const myCar = new Car('Toyota', 'Corolla');
myCar.startEngine();
```

## 🧼 Abstraction

**Abstraction** means exposing only the necessary parts of an object and hiding the complex implementation. You interact with a clean interface without worrying about how things work under the hood.

### Example:

Monday, Sep 22

how to install jwt

To install JWT (JSON Web Token) support in your project, you'll typically use a library depending on your programming language. Here's how to do it for a few popular environments:

### 🟦 Node.js (JavaScript/TypeScript)

Use the `jsonwebtoken` package:

bash

```javascript
npm install jsonwebtoken
```

Or with Yarn:

bash

```javascript
yarn add jsonwebtoken
```

Then in your code:

js

```javascript
const jwt = require('jsonwebtoken'); // CommonJS
// or
import jwt from 'jsonwebtoken'; // ES6 modules
```

### 🐍 Python

Use the `PyJWT` library:

bash

```javascript
pip install PyJWT
```

Then:

python

```javascript
import jwt
```

### 🟪 PHP

Use Firebase JWT via Composer:

bash

```javascript
composer require firebase/php-jwt
```

Then:

php

```javascript
use \Firebase\JWT\JWT;
```

### 🔷 .NET (C#)

Install via NuGet:

bash

```javascript
dotnet add package System.IdentityModel.Tokens.Jwt
```

Then:

csharp

```javascript
using System.IdentityModel.Tokens.Jwt;
```

Let me know your tech stack and I can tailor the setup and usage examples for your project. Want help generating or verifying tokens next?

Today

make this summarry better and add code examples: Concepts to look at are Encapsulation- Giving each object its own little space (each object handles its own task ) example we have a class called car in your code all the details like start engine, change gears happens inside that class Abstraction- Simplifying things you only interact with parts needed Inheritance - A family tree in code that can help you reuse code and extend Polymorphism- having an interface and interact with many forms In OOP we combine a group of related variables and functions into a unit we call that unit an object Structuring your code around objects, it can be things you want to model in real world its kinda like building with lego. We refer to these variables as properties and the functions as methods Think of a car which has a properties of make,model, color and also methods like start(), stop () and move()

Here’s a polished and more structured summary of core **Object-Oriented Programming (OOP)** concepts, complete with clear explanations and code examples to make each idea stick:

## 🧱 What Is Object-Oriented Programming?

Object-Oriented Programming (OOP) is a way of structuring code by grouping related **data** (called *properties*) and **functions** (called *methods*) into reusable units called **objects**. These objects often model real-world things—like cars, users, or bank accounts—and help make your code more organized, scalable, and intuitive.

Think of it like building with LEGO: each block (object) has its own shape and purpose, but they can connect to form something bigger.

## 🔐 Encapsulation

**Encapsulation** means bundling data and behavior inside a single unit (usually a class), and hiding internal details from the outside world. Each object manages its own state and logic.

### Example:

js

```javascript
class Car {
  constructor(make, model) {
    this.make = make;
    this.model = model;
    this.gear = 'P';
  }

  startEngine() {
    console.log(`${this.make} ${this.model} engine started`);
  }

  changeGear(newGear) {
    this.gear = newGear;
    console.log(`Gear changed to ${this.gear}`);
  }
}

const myCar = new Car('Toyota', 'Corolla');
myCar.startEngine();
myCar.changeGear('D');
```

Here, all car-related logic is encapsulated within the `Car` class.

## 🧼 Abstraction

**Abstraction** means exposing only the necessary parts of an object and hiding the complex implementation. You interact with a clean interface without worrying about how things work under the hood.

### Example:

js

```javascript
class CoffeeMachine {
  #heatWater() {
    console.log('Heating water...');
  }

  #grindBeans() {
    console.log('Grinding beans...');
  }

  makeCoffee() {
    this.#heatWater();
    this.#grindBeans();
    console.log('Coffee is ready!');
  }
}

const machine = new CoffeeMachine();
machine.makeCoffee
```

## 🧬 Inheritance

**Inheritance** allows one class to inherit properties and methods from another. It’s like a family tree—child classes reuse and extend the behavior of parent classes.

```javascript
class Animal {
  speak() {
    console.log('Animal makes a sound');
  }
}

class Dog extends Animal {
  speak() {
    console.log('Dog barks');
  }
}

const pet = new Dog();
pet.speak(); // Dog barks
```

`Dog` inherits from `Animal` but overrides the `speak()` method.

## 🌀 Polymorphism

**Polymorphism** means “many forms.” It allows different classes to be treated through the same interface, even if they behave differently.

```javascript
class Fish {
  move() {
    console.log('Fish swims');
  }
}

function travel(animal) {
  animal.move();
}

const parrot = new Bird();
const goldfish = new Fish();

travel(parrot);   // Bird flies
travel(goldfish); // Fish swims
```

Both `Bird` and `Fish` implement `move()`, and the `travel()` function works with either.

```javascript
class Car {
  constructor(make, model, color) {
    this.make = make;
    this.model = model;
    this.color = color;
  }

  start() {
    console.log('Car started');
  }

  stop() {
    console.log('Car stopped');
  }

  move() {
    console.log('Car is moving');
  }
}
```

* **Properties**: `make`, `model`, `color`
    
* **Methods**: `start()`, `stop()`, `move()`