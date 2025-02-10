---
title: "Mongoose & MongoDB vs Node Js"
datePublished: Mon Nov 25 2024 11:15:38 GMT+0000 (Coordinated Universal Time)
cuid: cm3wxm7nm000c09mq2g87amqf
slug: mongoose-mongodb-vs-node-js
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/LJ9KY8pIH3E/upload/3dd55142fba0eb7526e9de72474d85b5.jpeg
tags: mongodb, nodejs, mongoose, mongodbshell

---

Mongo DB Node.js applications must use the official driver

Mongo DB drivers simplify connecting to and interacting with your database from your application

Drivers simplify connecting to and interacting with a MongoDB database

Driver- works in tandem with the built in Node.js Bson package to interact with your Mongo Db server.

## Connecting to an Atlas Cluster in Node.js Applications

Create a new folder called test install the following dependencies: npm init -y (package.json) npm installs mongodb.

Create a file called atlas\_uri.js and add the following codemodule.export = uri =

```javascript
const uri =
  "mongodb+srv://kinungijames129:Gomycode2023@cluster0.befj3.mongodb.net";
module.exports = uri;
```

Create an app.js file and add the following, run the code it should print success

```javascript
const { MongoClient } = require("mongodb");
const uri = require("./atlas_uri");

console.log("success");
```

Continue in app.js file and input the following code

Note be sure to use backticks when using template literals.

```javascript
const { MongoClient } = require("mongodb");
const uri = require("./atlas_uri");

console.log("success");

const client = new MongoClient(uri);
const dbname = "bank";

const connectToDatabase = async () => {
  try {
    await client.connect();
    console.log(`Connected to ${dbname} database`); // Use backticks for template literals
  } catch (err) {
    console.error(`Error connecting to the database: ${err}`); // Use backticks
  }
};

const main = async () => {
  try {
    await connectToDatabase();
    console.log(`Connected to ${dbname} database`); // Use backticks
  } catch (err) {
    console.error(`Error connecting to the database: ${err}`); // Use backticks
  } finally {
    await client.close();
  }
};

main();
```

Take Note:

An application should use a single Mongo Client instance for all database requests

We must have a valid connection string to connect to our database via the driver which can be found in the Atlas dashboard

If you experience a problem with connection try checking your IP address

### Working with MongoDB documents in Node.js

Binary Json or Bson is a data format used by Mongo DB, It is optimized for storage, retrival and transmission across the wire.

Bson is more secure than plain text JSON

### Inserting a document in Node js application

We use the insert One() to insert a single document into a collection

Be sure to check we are using the correct database and collection.

Pass in the insertOne method the insertOne() method accepts a document as an argument and returns a promise. In this example, the document that's being inserted is stored in a variable called sampleAccount, which is declared just above the main() function.

```javascript
const dbname = "bank"

const collection_name = "accounts"

 

const accountsCollection = client.db(dbname).collection(collection_name)



const sampleAccount = {

 account_holder: "Linus Torvalds",

 account_id: "MDB829001337",

 account_type: "checking",

 balance: 50352434,

}



const main = async () => {

 try {

   await connectToDatabase()

   // insertOne method is used here to insert the sampleAccount document

   let result = await accountsCollection.insertOne(sampleAccount)

   console.log(`Inserted document: ${result.insertedId}`)

 } catch (err) {

   console.error(`Error inserting document: ${err}`)

 } finally {

   await client.close()

 }

}
```

### Insert Many documents

To append the insertMany() method to the collection object, and then pass an array of documents to the insertMany() method. The insertMany() method returns a promise. We await the promise to get the result of the operation, which we then use to log the number of documents that are inserted to the console. In this example, the accounts to be inserted are stored in an array variable called sampleAccounts. This variable is defined just above the main() function.

```javascript
const dbname = "bank"

const collection_name = "accounts"

 

const accountsCollection = client.db(dbname).collection(collection_name)



const sampleAccounts = [

 {

   account_id: "MDB011235813",

   account_holder: "Ada Lovelace",

   account_type: "checking",

   balance: 60218,

 },

 {

   account_id: "MDB829000001",

   account_holder: "Muhammad ibn Musa al-Khwarizmi",

   account_type: "savings",

   balance: 267914296,

 },

]

 

const main = async () => {

 try {

   await connectToDatabase()

   let result = await accountsCollection.insertMany(sampleAccounts)

   console.log(`Inserted ${result.insertedCount} documents`)

   console.log(result)

 } catch (err) {

   console.error(`Error inserting documents: ${err}`)

 } finally {

   await client.close()

 }

}


main()
```

### Using find()

The find () method takes a query or filter document as an argument if you do not specify a query document the find(), method returns all documents in the collection.

In the example we find all accounts that have a balance greater than or equal to 4700. The find() method accepts a query filter, which we assign to a variable called documentsToFind. We process each document that’s returned from the find() method by iterating the cursor, which is assigned to the variable result.

```javascript
const dbname = "bank"

const collection_name = "accounts"

 

const accountsCollection = client.db(dbname).collection(collection_name)



// Document used as a filter for the find() method

const documentsToFind = { balance: { $gt: 4700 } }

 

const main = async () => {

 try {

   await connectToDatabase()

   // find() method is used here to find documents that match the filter

   let result = accountsCollection.find(documentsToFind)

   let docCount = accountsCollection.countDocuments(documentsToFind)

   await result.forEach((doc) => console.log(doc))

   console.log(`Found ${await docCount} documents`)

 } catch (err) {

   console.error(`Error finding documents: ${err}`)

 } finally {

   await client.close()

 }

}



main()
```

Updating documents

The update one() updates only one update the syntax is `<collection>.updateOne(<filter>, <update>);`

```javascript
const dbname = "bank"

const collection_name = "accounts"



const accountsCollection = client.db(dbname).collection(collection_name)



const documentToUpdate = { _id: ObjectId("62d6e04ecab6d8e130497482") }



const update = { $inc: { balance: 100 } }





const main = async () => {

  try {

    await connectToDatabase()

    let result = await accountsCollection.updateOne(documentToUpdate, update)

    result.modifiedCount === 1

      ? console.log("Updated one document")

      : console.log("No documents updated")

  } catch (err) {

    console.error(`Error updating document: ${err}`)

  } finally {

    await client.close()

  }

}

main()
```

using updateMany()

The update many() updates many documents the syntax is `<collection>.updateMany(<filter>, <update>);`

```javascript
const database = client.db(dbname);

const bank = database.collection(collection_name);



const documentsToUpdate = { account_type: "checking" };



const update = { $push: { transfers_complete: "TR413308000" } }



const main = async () => {

  try {

    await connectToDatabase()

    let result = await accountsCollection.updateMany(documentsToUpdate, update)

    result.modifiedCount > 0

      ? console.log(`Updated ${result.modifiedCount} documents`)

      : console.log("No documents updated")

  } catch (err) {

    console.error(`Error updating documents: ${err}`)

  } finally {

    await client.close()

  }

}



main()

main()
```

## Using deleteOne()

To delete a single document from a collection, use the deleteOne() method on a collection object. This method accepts a query filter that matches the document that you want to delete. If you do not specify a filter, MongoDB matches and deletes the first document in the collection. The syntax is `collection.deleteOne(<filter>);`Her's an example:

```javascript
const dbname = "bank"

const collection_name = "accounts"



const accountsCollection = client.db(dbname).collection(collection_name)



const documentToDelete = { _id: ObjectId("62d6e04ecab6d8e13049749c") }



const main = async () => {

  try {

    await connectToDatabase()

    let result = await accountsCollection.deleteOne(documentToDelete)

    result.deletedCount === 1

      ? console.log("Deleted one document")

      : console.log("No documents deleted")

  } catch (err) {

    console.error(`Error deleting documents: ${err}`)

  } finally {

    await client.close()

  }

}



main()
```

## Using deleteMany()

You can delete multiple documents from a collection in a single operation by calling the deleteMany() method on a collection object. To specify which documents to delete, pass a query filter that matches the documents that you want to delete. If you provide an empty document, MongoDB matches all documents in the collection and deletes them. In the following example, we delete all accounts with a balance of less than 500 by using a query filter. Then, we print the total number of deleted documents.

```javascript
const dbname = "bank"

const collection_name = "accounts"



const accountsCollection = client.db(dbname).collection(collection_name)



const documentsToDelete = { balance: { $lt: 500 } }



const main = async () => {

 try {

   await connectToDatabase()

   let result = await accountsCollection.deleteMany(documentsToDelete)

   result.deletedCount > 0

     ? console.log(`Deleted ${result.deletedCount} documents`)

     : console.log("No documents deleted")

 } catch (err) {

   console.error(`Error deleting documents: ${err}`)

 } finally {

   await client.close()

 }

}

 

main()
```

## Creating a Transaction

In this section, we'll go through the code to create a transaction step by step. We start the transaction by using the session’s `withTransaction()` method. We then define the sequence of operations to perform inside the transactions, passing the `session` object to each operation in the transactions.

A multidocument transaction is a group of database operations that will be completed together as a unit or not at all they are used when a group of related operations must all succeed or fail togethor which is a property known as <mark>Atomicity</mark>

The steps to complete a transaction are:

1. Start a client session
    
2. Define the transaction options (optional)
    
3. Define the sequence of operations to perform inside the transsctions
    
4. Release the resources used by the transaction
    

Create variables used in the transaction.

```javascript
// Collections

const accounts = client.db("bank").collection("accounts")

const transfers = client.db("bank").collection("transfers")



// Account information

let account_id_sender = "MDB574189300"

let account_id_receiver = "MDB343652528"

let transaction_amount = 100
```

Start a new session.

`const session = client.startSession()`Begin a transaction with the `WithTransaction()` method on the session

```javascript
const transactionResults = await session.withTransaction(async () => {

  // Operations will go here

})
```

Update the `balance` field of the sender’s account by decrementing the `transaction_amount` from the balance field.

```javascript
const senderUpdate = await accounts.updateOne(

  { account_id: account_id_sender },

  { $inc: { balance: -transaction_amount } },

  { session }

)
```

Update the `balance` field of the receiver’s account by incrementing the `transaction_amount` to the balance field.

```javascript
const receiverUpdate = await accounts.updateOne(

  { account_id: account_id_receiver },

  { $inc: { balance: transaction_amount } },

  { session }

)
```

Create a transfer document and insert it into the transfers collection.

```javascript
const transfer = {

  transfer_id: "TR21872187",

  amount: 100,

  from_account: account_id_sender,

  to_account: account_id_receiver,

}



const insertTransferResults = await transfers.insertOne(transfer, { session })
```

Update the `transfers_complete` array of the sender’s account by adding the `transfer_id` to the array.

```javascript
const updateSenderTransferResults = await accounts.updateOne(

  { account_id: account_id_sender },

  { $push: { transfers_complete: transfer.transfer_id } },

  { session }

)
```

Update the `transfers_complete` array of the receiver’s account by adding the `transfer_id` to the array.

```javascript
const updateReceiverTransferResults = await accounts.updateOne(

  { account_id: account_id_receiver },

  { $push: { transfers_complete: transfer.transfer_id } },

  { session }

)
```

Log a message regarding the success or failure of the transaction.

```javascript
if (transactionResults) {

  console.log("Transaction completed successfully.")

} else {

  console.log("Transaction failed.")

}
```

Catch any errors and close the session.

```javascript
} catch (err) {

  console.error(`Transaction aborted: ${err}`)

  process.exit(1)

} finally {

  await session.endSession()

  await client.close()

}
```

### Building a MongoDB Aggregation Pipeline in Node js

When we build queries using the aggregation framework think of the query as comprising discreet stages, each stage provides output documents that act as input to the next stage the **sequence of data processing stages is reffered to as an <mark>aggregation pipline</mark>**

Aggregation pipelines include built in stages for finding sorting grouping and projecting documents

An aggregation pipeline can have one or more stages

Aggregation is a language for filtering, sorting, organizing and analysing data.

### Using MongoDB aggregation stages with Node.js:

### $match and $group

## Using $match

The $match filters documents to pass only documents that match the specified conditions to the next stage of the pipeline.

Aggregation gives you a way to transform data from your collection by passing documents from one stage to another. These stages can consist of operators that transform or organize your data in a specific way. In this lesson, we used `$match` and `$group`.

The `$match` stage filters documents by using a simple equality match, like `$match: { author: "Dave"}`, or aggregation expressions using comparison operators, like `$match: { likes: { $gt: 100 } }`. This operator accepts a query document and passes the resulting documents to the next stage. $match should be placed early in your pipeline to reduce the number of documents to process.

To perform an aggregation use the syntax :

`const pipeline = [<stage 1>, <stage 2>, <stage 3>]`

`db.collection.aggregate(pipeline)`

## Using $group

The `$group` stage separates documents according to a group key and returns one document for every unique group key. The group key is usually a field in the document, but it can also be an expression that resolves to a field. The `$group` stage can be used with aggregation expressions to perform calculations on the grouped documents. An example of this is adding up the total number of movie tickets sold by using the `$sum` operator:

`$group: { _id: "$movie", totalTickets: { $sum: "$tickets" } }`

The "`$movie"` is the group key, and the `totalTickets` field is the result of the `$sum` operator.

In the following code, we assign our collection name to a variable for convenience. First, we declare some variables to hold the database connection and the collection we'll use:

```javascript
const client = new MongoClient(uri)

const dbname = "bank";

const collection_name = "accounts";

const accountsCollection = client.db(dbname).collection(collection_name);
```

Next, we build an aggregation pipeline that uses `$match` and `$group` and that will find accounts with a balance of less than $1,000. Then we group the results by the `account_type`, and calculate the `total_balance` and `avg_balance` for each type.

```javascript
const pipeline = [

  // Stage 1: match the accounts with a balance less than $1,000

  { $match: { balance: { $lt: 1000 } } },

  // Stage 2: Calculate average balance and total balance

  {

    $group: {

      _id: "$account_type",

      total_balance: { $sum: "$balance" },

      avg_balance: { $avg: "$balance" },

    },

  },

]
```

To run an aggregation pipeline, we append the aggregate method to the collection. The aggregate method takes an array of stages as an argument, which is stored in a variable. The aggregate method returns a cursor that we can iterate over to get the results.

```javascript
const main = async () => {

  try {

    await client.connect()

    console.log(`Connected to the database 🌍. \nFull connection string: ${safeURI}`)

    let result = await accountsCollection.aggregate(pipeline)

    for await (const doc of result) {

      console.log(doc)

    }

  } catch (err) {

    console.error(`Error connecting to the database: ${err}`)

  } finally {

    await client.close()

  }

}
main()
```

### Using MongoDB Aggregation stages with Node.js $sort and $project

## $sor

Aggregation is a powerful tool that gives us the ability to compute and transform our data. In this skill, we focused on the `$sort` and `$project` stages.

The `$sort` stage takes all the input documents and sorts them in a specific order. The documents can be sorted in numerical, alphabetical, ascending, or descending order.

The `$sort` stage accepts a sort key that specifies the field to sort on. The sort key can be 1 for ascending order or -1 for descending order. For example:

`{ $sort: { balance: 1 } }` sorts the documents in ascending order by the `balance` field.

`{ $sort: { balance: -1 } }` sorts the documents in descending order by the `balance` field.

## $project

The `$project` stage takes all the input documents and passes along only a subset of the fields in those documents by specifying the fields to include or exclude.

For example, if we want our resulting documents to include only the `account_id`, we write `{ $project: { _id: 0, account_id: 1 } }`. The \_id field is excluded by setting it to 0, and the `account_id` field is included by setting it to 1.

The `$project` stage can also create new computed fields based on data from the original documents. An example of this is creating a projected field that contains someone's full name, where only the first and last names are stored in the original document.

In the following example, we build an aggregation pipeline that uses `$match`, `$sort`, and `$project`, and that will find checking accounts with a balance of greater than or equal to $1,500. Then, we sort the results by the balance in descending order and return only the `account_id`, `account_type`, `balance`, and a new computed field named `gbp_balance`, which stands for Great British Pounds (GBP) balance.

```javascript
const pipeline = [

  // Stage 1: $match - filter the documents (checking, balance >= 1500)

  { $match: { account_type: "checking", balance: { $gte: 1500 } } },



  // Stage 2: $sort - sorts the documents in descending order (balance)

  { $sort: { balance: -1 } },



  // Stage 3: $project - project only the requested fields and one computed field (account_type, account_id, balance, gbp_balance)

  {

    $project: {

      _id: 0,

      account_id: 1,

      account_type: 1,

      balance: 1,

      // GBP stands for Great British Pound

      gbp_balance: { $divide: ["$balance", 1.3] },

    },

  },

]
```

To run an aggregation pipeline, we append the aggregate method to the collection. The aggregate method takes an array of stages as an argument, which is stored here as a variable. The aggregate method returns a cursor that we can iterate over to get the results.

```javascript
const main = async () => {

  try {

    await client.connect()

    console.log(`Connected to the database 🌍\n ${uri}`)

    let accounts = client.db("bank").collection("accounts")

    let result = await accounts.aggregate(pipeline)

    for await (const doc of result) {

      console.log(doc)

    }

  } catch (err) {

    console.error(`Error connecting to the database: ${err}`)

  } finally {

    await client.close()

  }

}



main()
```

$sort

Aggregation is a powerful tool that gives us the ability to compute and transform our data. In this skill, we focused on the `$sort` and `$project` stages.

The `$sort` stage takes all the input documents and sorts them in a specific order. The documents can be sorted in numerical, alphabetical, ascending, or descending order.

The `$sort` stage accepts a sort key that specifies the field to sort on. The sort key can be 1 for ascending order or -1 for descending order. For example:

`{ $sort: { balance: 1 } }` sorts the documents in ascending order by the `balance` field.

`{ $sort: { balance: -1 } }` sorts the documents in descending order by the `balance` field.

## $project

The `$project` stage takes all the input documents and passes along only a subset of the fields in those documents by specifying the fields to include or exclude.

For example, if we want our resulting documents to include only the `account_id`, we write `{ $project: { _id: 0, account_id: 1 } }`. The \_id field is excluded by setting it to 0, and the `account_id` field is included by setting it to 1.

The `$project` stage can also create new computed fields based on data from the original documents. An example of this is creating a projected field that contains someone's full name, where only the first and last names are stored in the original document.

In the following example, we build an aggregation pipeline that uses `$match`, `$sort`, and `$project`, and that will find checking accounts with a balance of greater than or equal to $1,500. Then, we sort the results by the balance in descending order and return only the `account_id`, `account_type`, `balance`, and a new computed field named `gbp_balance`, which stands for Great British Pounds (GBP) balance.

```javascript
const pipeline = [

  // Stage 1: $match - filter the documents (checking, balance >= 1500)

  { $match: { account_type: "checking", balance: { $gte: 1500 } } },



  // Stage 2: $sort - sorts the documents in descending order (balance)

  { $sort: { balance: -1 } },



  // Stage 3: $project - project only the requested fields and one computed field (account_type, account_id, balance, gbp_balance)

  {

    $project: {

      _id: 0,

      account_id: 1,

      account_type: 1,

      balance: 1,

      // GBP stands for Great British Pound

      gbp_balance: { $divide: ["$balance", 1.3] },

    },

  },

]
```

To run an aggregation pipeline, we append the aggregate method to the collection. The aggregate method takes an array of stages as an argument, which is stored here as a variable. The aggregate method returns a cursor that we can iterate over to get the results.

```javascript
const main = async () => {

  try {

    await client.connect()

    console.log(`Connected to the database 🌍\n ${uri}`)

    let accounts = client.db("bank").collection("accounts")

    let result = await accounts.aggregate(pipeline)

    for await (const doc of result) {

      console.log(doc)

    }

  } catch (err) {

    console.error(`Error connecting to the database: ${err}`)

  } finally {

    await client.close()

  }

}
main()
```

# What's mongoose?

**Mongoose** is an **Object Data Modeling** (ODM) library for MongoDB and Node.JS. It is responsible for:  
\- Managing data relationships.

\-Providing schema validation.

\-Implementing the translation between code objects and the representation of those objects in MongoDB.

# Mongodb vs SQL

You know by now that MongoDB is a **schema-less NoSQL document database**. It means you can store JSON documents on it. The structure of these documents can vary as it is **not enforced** like SQL databases. This is one of the advantages of using NoSQL as it speeds up application development and reduces the complexity of deployments.

Just as a reminder,

here are some terminologies used with the NoSQL database:

* **Collections**: Collections in Mongo are the equivalent of tables in relational databases. They can hold multiple JSON documents.
    
* **Documents**: Documents are the equivalent of records or data rows in SQL. While an SQL row can reference data in other tables, Mongo documents usually combine them in one document.
    
* **Fields**: Fields or attributes that are similar to columns in an SQL table.
    
* **Schema**: While Mongo is schema-less, SQL defines a schema via the table definition. A Mongoose ‘schema’ is a document data structure (or a shape of the document) that is enforced via the application layer.
    
* **Models**: Models are higher-order constructors that take a schema and create an instance of a document equivalent to records in a relational database.
    
* **References**: References are referred from one document to another using the value of the referenced (parent) document.
    

### Getting started

Mongooose installation- start by initializing the project in the folder `npm init -y`, we install mongoose and a validation library using `npm install mongoose validator`

# **Database Connection**

Create a file `./src/database.js` under the project's root.  
Next, we will add a simple class with a method that connects to the database.  
Your connection string will vary based on your installation.

```javascript
let mongoose = require('mongoose');

const server = '127.0.0.1:27017'; // REPLACE WITH YOUR DB SERVER

const database = 'myDB';      // REPLACE WITH YOUR DB NAME

class Database {

  constructor() {

    this._connect()
  }

_connect() {
  mongoose.connect(`mongodb://${server}/${database}`)

       .then(() => {

         console.log('Database connection successful')

       })

       .catch(err => {

         console.error('Database connection error')

       })

  }

}

module.exports = new Database()
```

The `require(‘mongoose’)` call above returns a Singleton object. It means that when you call `require(‘mongoose’)` for the first time, it creates an instance of the Mongoose class and returns it. On subsequent calls, it will return the same instance that was created and returned to you the first time because of how module import/export works in ES6.

# Mongoose Schema vs. Model

A **Mongoose model** is a **wrapper** on the **Mongoose schema**. A Mongoose schema **<mark>defines the structure</mark>** <mark>of the document,</mark> default values, validators, etc... whereas a Mongoose model **provides an interface** to the database for creating, querying, updating, deleting records, etc.

Creating a Mongoose model comprises primarily of three parts:

## 1\. Referencing Mongoose

```javascript
let mongoose = require('mongoose')
```

This reference will be the same as the one that was returned when we connected to the database, which means the schema and model definitions will not need to explicitly connect to the database.

## 2\. Defining the Schema

A schema defines document properties through an object where the key name corresponds to the property name in the collection.

```javascript
let emailSchema = new mongoose.Schema({

  email: String

})
```

Here we define a property called **email** with a schema type **String** which maps to an internal validator that will be triggered when the model is saved to the database. It will fail if the data type of the value is not a string type.  
The following Schema Types are permitted:

* Array
    
* Boolean
    
* Buffer
    
* Date
    
* Mixed (A generic / flexible data type)
    
* Number
    
* ObjectId
    
* String
    

Mixed and ObjectId are defined under `require(‘mongoose’).Schema.Types`.

## 3\. Exporting a Model

We need to call the model constructor on the Mongoose instance and pass it the name of the collection and a reference to the schema definition.

```javascript
module.exports = mongoose.model('Email', emailSchema)
```

Let’s combine the code above into `./src/models/email.js` to define the contents of a basic email model:

```javascript
let mongoose = require('mongoose')

let emailSchema = new mongoose.Schema({

  email: String

})

module.exports = mongoose.model('Email', emailSchema)
```

A schema definition should be simple, but its complexity is usually based on application requirements. Schemas can be reused and they can contain several child-schemas too. In the example above, the value of the email property is a simple value type. However, it can also be an object type with additional properties on it.

We can also create an instance of the model we've defined above and populate it using the following syntax:

```javascript
let EmailModel = require('./email')

let msg = new EmailModel({

  email: 'ada.lovelace@gmail.com'

})
```

Let’s enhance the email schema to make the email property a unique and required field. We can then convert the value to lowercase before saving it. We can also add a validation function that will ensure that the value is a valid email address. We will reference and use the validator library installed earlier.

```javascript
let mongoose = require('mongoose')

let validator = require('validator')

let emailSchema = new mongoose.Schema({

  email: {

    type: String,

    required: true,

    unique: true,

    lowercase: true,

    validate: (value) => {

      return validator.isEmail(value)

    }

  }

})

module.exports = mongoose.model('Email', emailSchema)
```

# Basic Operations

Mongoose has a flexible API and provides many ways to accomplish a task. We will not focus on the variations because that is out of the scope of this course. However, try to remember that most of the operations can be done in more than one way either syntactically or via the application's architecture

## Create Record

Let’s create an instance of the email model and save it to the database:

```javascript
let EmailModel = require('./email')

let msg = new EmailModel({

  email: 'ADA.LOVELACE@GMAIL.COM'

})

msg.save()

   .then(doc => {

     console.log(doc)

   })

   .catch(err => {

     console.error(err)

   })
```

The result is a document that is returned upon a successful save:

```javascript
{ 

  _id: 5a78fe3e2f44ba8f85a2409a,

  email: 'ada.lovelace@gmail.com',

  __v: 0 

}
```

​  
The following fields are returned (internal fields are prefixed with an underscore):

1. The `_id` field is auto-generated by Mongo and is a primary key of the collection. Its value is a unique identifier for the document.
    
2. The value of the `email` field is returned. Notice that it is lower-case because we specified the `lowercase:true` attribute in the schema.
    
3. `__v` is the versionKey property set on each document when first created by Mongoose. Its value contains the internal revision of the document.  
    ​  
    ***If you try to repeat the save operation above, you will get an error because we have specified that the email field should be unique.***  
    311790:0
    

## Fetch Record

Let’s try to retrieve the record we saved to the database earlier. The model class exposes several static and instance methods to perform operations on the database. We will now try to find the record that we have created previously using the find method and pass the email as the search term.

```javascript
EmailModel

  .find({

    email: 'ada.lovelace@gmail.com'   // search query

  })

  .then(doc => {

    console.log(doc)

  })

  .catch(err => {

    console.error(err)

  })
```

The document returned will be similar to what was displayed when we created the record:

```javascript
{ 

  _id: 5a78fe3e2f44ba8f85a2409a,

  email: 'ada.lovelace@gmail.com',

  __v: 0 

}
```

## Update Record

Let’s modify the record above by changing the email address and adding another field to it, all in a single operation. For performance reasons, Mongoose won’t return the updated document so we need to pass an additional parameter to ask for it:

```javascript
EmailModel

  .findOneAndUpdate(

    {

      email: 'ada.lovelace@gmail.com'  // search query

    }, 

    {

      email: 'theoutlander@live.com'   // field:values to update

    },

    {

      new: true,                       // return updated doc

      runValidators: true              // validate before update

    })

  .then(doc => {

    console.log(doc)

  })

  .catch(err => {

    console.error(err)

  })
```

The document returned will contain the updated email:

```javascript
{ 

  _id: 5a78fe3e2f44ba8f85a2409a,

  email: 'theoutlander@live.com',

  __v: 0 

}
```

## Delete Record

We will use the `findOneAndRemove` call to delete a record. It returns the original document that was removed:

```javascript
EmailModel

  .findOneAndRemove({

    email: 'theoutlander@live.com'

  })

  .then(response => {

    console.log(response)

  })

  .catch(err => {

    console.error(err)

  })
```

# Helpers

So far, we have looked at some of the basic functionalities known as CRUD (Create, Read, Update, Delete) operations, but Mongoose also provides the ability to configure several types of helper methods and properties. These can be used to further simplify working with data.

Let’s create a user schema in `./src/models/user.js` with the fields `firstName` and `lastName`:

```javascript
let mongoose = require('mongoose')

let userSchema = new mongoose.Schema({

  firstName: String,

  lastName: String

})

module.exports = mongoose.model('User', userSchema)
```

## Virtual Property

A virtual property is not restricted the database. We can add it to our schema as a helper to get and set values.  
Let’s create a virtual property called `fullName` which can be used to set values on `firstName` and `lastName` and retrieve them as a combined value when read:

```javascript
userSchema.virtual('fullName').get(function() {

  return this.firstName + ' ' + this.lastName

})

userSchema.virtual('fullName').set(function(name) {

  let str = name.split(' ')

  

  this.firstName = str[0]

  this.lastName = str[1]

})
```

Callbacks for get and set must use the function keyword as we need to access the model via the **this** keyword. Using fat arrow functions will change what **this** refers to.

Now, we can set `firstName` and `lastName` by assigning a value to `fullName`:

```javascript
let model = new UserModel()

model.fullName = 'Thomas Anderson'

console.log(model.toJSON())  // Output model fields as JSON

console.log()

console.log(model.fullName)  // Output the full name
```

The code above will output the following:

```javascript
{ _id: 5a7a4248550ebb9fafd898cf,

  firstName: 'Thomas',

  lastName: 'Anderson' }

Thomas Anderson
```

## Instance Methods

We can create custom helper methods on the schema and access them via the model instance. These methods will have access to the model object and they can be used quite creatively. For instance, we could create a method to find all the people who have the same first name as the current instance.  
In this example, let’s create a function to return the initials for the current user. Let’s add a custom helper method called `getInitials` to the schema:

```javascript
userSchema.methods.getInitials = function() {

  return this.firstName[0] + this.lastName[0]

}
```

This method will be accessible via a model instance:

```javascript
let model = new UserModel({

  firstName: 'Thomas',

  lastName: 'Anderson'

})

let initials = model.getInitials()

console.log(initials) // This will output: TA
```

### Static Methods

Similar to instance methods, we can create static methods on the schema. Let’s create a method to retrieve all users in the database:

```javascript
userSchema.statics.getUsers = function() {

  return new Promise((resolve, reject) => {

    this.find((err, docs) => {

      if(err) {

        console.error(err)

        return reject(err)

      }

      resolve(docs)

    })

  })

}
```

Calling `getUsers` on the Model class will return all the users in the database:

```javascript
UserModel.getUsers()

  .then(docs => {

    console.log(docs)

  })

  .catch(err => {

    console.error(err)

  })
```

Adding instance and static methods is a nice approach to implement an interface to database interactions on collections and records.

## Middleware

Middleware is a set of functions that run at specific stages of a pipeline. Mongoose supports middleware for the following operations:

* Aggregate
    
* Document
    
* Model
    
* Query
    

For instance, models have `pre` and `post` functions that take two parameters:

1. Type of event (‘init’, ‘validate’, ‘save’, ‘remove’)
    
2. A callback that is executed with **this** referencing the model instance
    

Example of Middleware (a.k.a. pre and post hooks):

Query Building

Mongoose has a very rich API that handles many complex operations supported by MongoDB. Let's take for example a query where we can incrementally build query components.

In this example, we are going to:

1. Find all users.
    
2. Skip the first 100 records.
    
3. Limit the results to 10 records.
    
4. Sort the results by the firstName field.
    
5. Select the firstName.
    
6. Execute that query.
    

```javascript
UserModel.find()                   // find all users

         .skip(100)                // skip the first 100 items

         .limit(10)                // limit to 10 items

         .sort({firstName: 1}      // sort ascending by firstName

         .select({firstName: true} // select firstName only

         .exec()                   // execute the query

         .then(docs => {

            console.log(docs)

          })

         .catch(err => {

            console.error(err)

          })
```