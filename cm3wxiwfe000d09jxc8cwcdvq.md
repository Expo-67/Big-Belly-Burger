---
title: "Rest(Representational State Transfer) API"
datePublished: Mon Nov 25 2024 11:13:03 GMT+0000 (Coordinated Universal Time)
cuid: cm3wxiwfe000d09jxc8cwcdvq
slug: restrepresentational-state-transfer-api
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/4dR9LmMzhT0/upload/7b361081635a429afca10abcb9937a09.jpeg
tags: apis, rest-api, restful-apis

---

Imagine you have a restaurant. When you order food, you tell a waiter what you want, and the waiter takes your request to the kitchen. The kitchen then prepares the food and the waiter brings it back to you.

A **REST API** works in a similar way:

* You (the **client**) make a request for some data or information.
    
* The request is sent to a **server** (like the kitchen in the restaurant).
    
* The server processes the request, gathers the data (or performs an action), and then sends a **response** back to you.
    

In REST APIs:

* **Client**: The user or application making the request. For example, your web browser or a mobile app.
    
* **Server**: The system that stores the data and processes the request.
    
* **Request**: This is what you ask for. For instance, you might ask for a list of products or information about a specific user.
    
* **Response**: The data or message that the server sends back to you.
    

REST APIs use standard HTTP methods:

* **GET**: Ask for data (e.g., "Get a list of all products").
    
* **POST**: Send new data to the server (e.g., "Add a new product").
    
* **PUT**: Update existing data (e.g., "Update the price of a product").
    
* **DELETE**: Remove data (e.g., "Delete a product").
    

Think of REST APIs as the way apps "talk" to each other over the internet to share data and perform actions, similar to how a waiter communicates between you and the kitchen.

### REST: REpresentational State Transfer

Determines how the API looks like. It is a <mark> set of rules that developers follow when they create their API.</mark> One of these rules states that you should be able to get a piece of data (called a resource) when you link to a specific URL.

### API: Application Programming Interface

It is a <mark>set of rules that allows programs to talk to each other</mark>. The developer creates the API on the server and allows the client to talk to it.

### Request

Your browser needs to be able to send a request to the servers and display the resources for you.

HTTP(Hyper Text Transfer Protocol) this is the underlying format that is used to structure requests and responses for effective client-server communication.

To test HTTP use software like postman.

Poastman is an <mark>API platform for building and using APIs, </mark> Postman simplifies each step of the API lifecycle and streamlines collaboration so you can create better APIs -faster

### Request Headers

Headers are used to provide information to both the client and the server. It can be used for many purposes, such as authentication and providing information about the body content.

# Request Body

The body (sometimes called “data” or “message”) contains information you want to be sent to the server. This option is only used with POST, PUT or DELETE requests.

# HTTP Response

When a client (browser) makes a request to a server, the server responds with a reply including a status code.

HTTP response status codes indicate whether a specific HTTP request has been successfully completed. Responses are grouped in five classes:

Informational responses (100–199),  
Successful responses (200–299),  
Redirects (300–399),  
Client errors (400–499),  
and Server errors (500–599).

# GET Method

This method is used to <mark> get a resource from a server.</mark> If you perform a `GET` request, the server looks for the data you requested and sends it back to you. In other words, a `GET` request performs a `READ` operation. This is the default request method.

# POST Method

This request is used to <mark>create a new resource on a server</mark>. If you perform a `POST` request, the server creates a new entry in the database and tells you whether the creation is successful or not. In other words, a `POST` request performs an `CREATE` operation.

# PUT Method

This request is used to <mark>update a resource on a server</mark>. If you perform a `PUT` request, the server updates an entry in the database and tells you whether the update is successful or not. In other words, a `PUT` request performs an `UPDATE` operation.  
When sending a `PUT` request, we add a body containing the modification to be performed.

# DELETE Method

This request is used to delete a resource from a server. If you perform a `DELETE` request, the server deletes an entry in the database and tells you whether the deletion is successful or not. In other words, a `DELETE` request performs a `DELETE` operation.