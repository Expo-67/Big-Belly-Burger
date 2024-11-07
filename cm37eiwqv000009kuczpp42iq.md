---
title: "Comprehensive Guide to Using Postman for API Testing"
datePublished: Thu Nov 07 2024 14:26:57 GMT+0000 (Coordinated Universal Time)
cuid: cm37eiwqv000009kuczpp42iq
slug: comprehensive-guide-to-using-postman-for-api-testing
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/KSQgzzn3dW0/upload/1c37180f2f8ff1634e54e3b75232424e.jpeg
tags: postman

---

API (Application Programming Interface)

This is <mark>a contract that allows code to talk to another code</mark>.APIs allow the sharing of resources and services across applications and devices

Have you ever made a payment on a website? Checked the weather on a mobile app? Listened to Spotify on both your desktop and your phone? Used Google Maps inside another app? Whether you know it or not, you are using APIs every day

### Why are APIs important?

1.APIs help developers integrate exciting features and build automation without reinventing the wheel example:*using a Weather API instead of launching your weather balloons*

2. APIs allow enterprises to open up their product for faster innovation ex: a*pps that interact with Twitter or Meta APIs by posting on your behalf or reading tweets*
    

You can think of APIs as being like a waiter at a restaurant, serving as a go-between for the customer and the kitchen.

A customer who wants soup doesn't go into the kitchen to cook. They don't even have to know how to make soup! They only have to know *how to <mark>ask</mark>* *<mark>the waiter(Request)</mark>* for soup\*, expecting the waiter to\* <mark>bring back soup</mark>\*<mark>.(Response)</mark>

\*APIs work the same way, but there are different names for the players involved. Instead of soup, the requester might ask for data or execution of a service

Client - the requester (web browser, mobile app) <mark>customer</mark>

API - simplified interface for interacting with the backend <mark>waiter</mark>

Server- backend where processing happens <mark>Kitchen</mark>

There is more than one way to build and consume APIs. Some architecture types you may come across are:

* REST (Representational State Transfer)
    
* GraphQL
    
* WebSockets
    
* webhooks
    
* SOAP (Simple Object Access Protocol)
    
* gRPC (Google Remote Procedure Call)
    
* MQTT (MQ Telemetry Transport)
    

### Access

APIs also vary in the scope of who can access them.

* Public APIs (aka Open APIs)  
    \*\*Consumed by anyone who discovers the API
    
* Private APIs  
    \*\*Consumed only within an organization and not made public
    
* Partner APIs  
    Consumed between one or more organizations that have an established relationship
    

Postman is an API platform for building and using APIs

before postman, you could make an API call in the terminal using the curl commands, it works well but the API response data is lost in the riverof the terminal

The Rest API allows you to CRUD(Create Read Update Delete)

### Request methods

The HTTP methods are :

1. GET -retrieve data (Read)
    
2. POST- send data ( Create)
    
3. PUT/PATCH- update data ( PUT- replaces an entire resource while PATCH is for partial updates)
    
4. DELETE- delete data
    

The request url has three parts the protocol(**https://**), host ([**library-api.postmanlabs.com**](http://library-api.postmanlabs.com))and path (**/books**)

| **Code range** | **Meaning** | **Example** |
| --- | --- | --- |
| `2xx` | Success | `200` - OK |
| `201` - Created |  |  |
| `204` - No content (silent OK) |  |  |
| `3xx` | Redirection | `301` - Moved (path changed) |
| `4xx` | Client error | `400` - Bad request |
| `401` - Unauthorized |  |  |
| `403` - Not Permitted |  |  |
| `404` - Not Found |  |  |
| `5xx` | Server error | `500` - Internal server error |
| `502` - Bad gateway |  |  |

Variables in postman

Postman allows you to save values as variables

When setting variables they are case sensitive

Query parameters

remember the minimum ingridients to make a request are

* GET ,POST, PUT, PATCH and Delete
    

Query parameters are added to the end of the path, they start with a question mark followed by the key value pairs in the format: **&lt;key&gt;=&lt;value&gt;** an example would be **GET** [**https://some-api.com/photos?orientation=landscape**](https://some-api.com/photos?orientation=landscape)

Another way of passing request data to an API is through path variables( often used as IDs and entity names such as username

The path variable syntax is :

**GET** [**https://api.github.com/users/{username}**](https://api.github.com/users/%7Busername%7D)

an exmple would be the one below the API call with a value for username will fetch data about that user.

**GET** [**https://api.github.com/users/postmanlabs**](https://api.github.com/users/postmanlabs)

You can have multiple path variables in a single request, such as this endpoint for getting a user's GitHub code repository:

`GET` [`https://api.github.com/repos/{owner}/{repoName}`](https://api.github.com/repos/%7Bowner%7D/%7BrepoName%7D)

For example, to get information about the `newman` code repository from `postmanlabs`:

`GET` [`https://api.github.com/repos/postmanlabs/newman`](https://api.github.com/repos/postmanlabs/newman)

### Path vs. query parameters

At first, it is easy to confuse these two parameter types. Let's compare them side by side.

| **Path Variable** | **Query parameters** |
| --- | --- |
| ex: `/books/abc123` | ex: `/books?search=borges&checkedOut=false` |
| Located **directly after a slash** in the path. It can **be anywhere on the path** | Located only at the **end of a path**, right after a question mark `?` |
| Accepts **dynamic values** | Accepts **defined query keys** **with potentially dynamic values**. |
| \* Often used for IDs or entity names | \* Often used for options and filters |

You insert the path in the path variables an example **29cd820f-82f9-4b45-a7f4-0924111b5b89** when we run this in the id it brings out a field of the book

be sure to save and then send the request.

The body tab in postman enables you to specify the data you need to send with a request you can use diffrent types of raw data the format (**Text**, **JavaScript**, **JSON**, **HTML**, or **XML**),

### How to ADD POST

1. Hover over your **Postman Library API v2** Collection, click the three dots icon and select **Add request**. Name your new request "**add book**"
    
2. Set the request method to `POST` and the request URL to `{{baseUrl}}/books`
    
3. This endpoint requires adding a **body** to our request to send a payload. Our payload will be a JSON object containing the information about the book we are adding.
    
    Click the **Body** tab of the request and select that data type `raw > JSON`
    
4. Think of a book you love or have read recently.
    
    Inside the Body editor, add a JSON object with details about the new book's `title`, `author`, `genre` and `yearPublished`.
    
    You can copy this object and **replace the values with details about your book**!
    
    ```javascript
    {
      "title": "To Kill a Mockingbird",
      "author": "Harper Lee",
      "genre": "fiction",
      "yearPublished": 1960
    }
    ```
    
5. **Save and Send** your request.
    
    😱 Uh-oh!
    
    The response from the server came back with a status `401 Unauthorized`. Remember that 400-level errors are client errors, meaning we made a mistake in our request.   
    400- 401 (This error deals with authorization
    

The body of the response has a message explaining we need to add an `api-key` to the `headers` of the request.

Let's fix this error in our next lesson.

There are multiple methods for authorizing a request. Some examples are **Basic Auth** (username and password), **OAuth** (delegated authorization), and **API Keys** (secret strings registered to a developer from an API portal).

To fix the error go to headers add **api-key** and value to **postmanrulz**

### Getting an API key

The API key auth usually allow developers to sign up in a developer portal where they recieve a random API key used to authorize their requests

1. On your "**add a book**" request, click the **Headers** tab
    
2. In the Headers helper table, add the **key** `api-key` with a **value** of `postmanrulz`
    
3. **Save and Send** your request.
    

### 🚀 Success!

Your book was added! Now that your request is properly authorized in the header, you should get a **201 Created** response with a response body that is an object representing your newly added book!

1. Click on your collection "**Postman Library API v2**" and select the **Authorization** (or **Auth**) tab
    
2. Select **API Key** as the auth **Type**
    
3. Enter the API Key details in the fields below. **Key:** `api-key`**, Value:** `postmanrulz`, Add to: Header
    
4. **Save** the changes to your collection by clicking the floppy disk icon in the upper right (important!)
    

Go to authorization and set the key and value to verify go to headers and you will see it ontop

### Scripting

Postman allows you to add automation and dynamic behaviours to your collection with **scripting.**

1. Immediately before a request is sent: [pre-request script](https://learning.postman.com/docs/writing-scripts/pre-request-scripts/) (**Pre-request Script** of Scripts tab).
    
2. Immediately after a response comes back: [post-response script](https://learning.postman.com/docs/writing-scripts/test-scripts/) (**Post-response** of Scripts tab).
    

You can access the JSON response body from an API with (`pm.response.json()`)

When scripting you go to Scripts and add `console.log(pm.response.json())` when you save and run check on console you can see the scripted document.

The pm allows you to set and get collection variables

to set a collection variable use the `.set()` method the syntax is

```javascript
pm.collectionVariables.set("variableName", value)
```

To get a collection variable use .`get()` the syntax is

```javascript
pm.collectionVariables.get("variableName")
```

Forking means we can create a copy of this collection into our own workspace .