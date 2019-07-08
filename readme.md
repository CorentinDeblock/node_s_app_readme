# The App

We'll build a very simple pet management app. With no UI other than the API endpoints we'll design in a RESTfull manner and the data stored remotely through mongoose objects on mlab, a MONGODB BAAS (Backend As A Service).
At multiple steps we'll be making use of postman, our favorite API development environment.
The example folder is the app in it's finished state with commented code.

## Create the neccessary App folders and files:

Your app folder should be structured like this

```
node_first_app
│   index.js
│   readme.md
|   .gitignore
|
└───routes
│   │   petRoutes.js
│
└───models
    │   Pet.js

```

## Initialize NPM and install node_modules
Also for this app our Node dependancies will be managed with use of NPM. To initiate NPM onto our project there is a simple command which is, from the root of your project, `npm init`.
You will notice that the terminal will ask for information about the kind of app, ignore that, press return for all of them (about 10 times) and remember to add `node_modules` to the `.gitignore`!
To install the express and body-parser modules run `npm i --save express body-parser`

Now commit- and push your new project github.

## Express

index.js

```
const express     = require("express");
const bodyParser  = require("body-parser");

const app = express();

app.use(bodyParser.json());

require("./models/Pet")(app);
require("./routes/petRoutes")(app);

const PORT = 5000;

app.listen(PORT, () => {
  console.log(`Server running`);
});
```

If you remember how to run the app in its setup you may guess `node index.js` like the previous app, which is correct. Though, our express app won't be satisfied requiring empty files and will throw an error.
To fix this, we have to do something with `Pet.js` and `petRoutes.js`.
We're going to install mongoose and a mongoDB connection to mlab.
After completing the setup of no-sql we'll create our Schema and Object interfaces.

## Mongoose

Mongoose is an Object Data Modeling (ODM) library for MongoDB and Node.js. It manages relationships between data, provides schema validation, and is used to translate between objects in code and the representation of those objects in MongoDB.

![mongoose](https://cdn-images-1.medium.com/max/2000/0*b5piDNW1dqlkJWKe.)

MongoDB is a schema-less NoSQL document database. It means you can store JSON documents in it, and the structure of these documents can vary as it is not enforced like SQL databases. This is one of the advantages of using NoSQL as it speeds up application development and reduces the complexity of deployments.

### Object Model Interface

Mongoose's utility, with this app, is to be the interface for MongoDB.
Next we're going to create blueprints of data that the remote database allows, also known as a Mongoose schema.
A Mongoose schema defines the structure of the document, default values, validators, etc.,

Mongoose blueprint

```
  let mongoose = require('mongoose')
  let ExampleSchema = new mongoose.Schema({
    fieldName: Type,
    fieldName: Type,
    fieldName: Type
  })
  module.exports = mongoose.model('ExampleSchema', ExampleSchema)
```

The following Schema Types are permitted:

* Array
* Boolean
* Buffer
* Date
* Mixed (A generic / flexible data type)
* Number
* ObjectId
* String

### Create Pet Model

Inside of `Pet.js` within the models folder add the following code:
```
  let mongoose = require('mongoose')
  let EmailSchema = new mongoose.Schema({
    name: String,
    age: Number,
    gender: String,
    species: String,
    primaryColor: String
  })
  module.exports = mongoose.model('EmailSchema', EmailSchema)
```

### An example of how stored data differs in Mongo(no-sql) vs. SQL Database:

![nosqlvssql](https://image.ibb.co/mWKZS9/sqlvsnosql.png)

### Terminologies

#### Collections
`Collections` in Mongo are equivalent to tables in relational databases. They can hold multiple JSON documents.

#### Documents
`Documents` are equivalent to records or rows of data in SQL. While a SQL row can reference data in other tables, Mongo documents usually combine that in a document.

#### Fields
`Fields` or attributes are similar to columns in a SQL table.

#### Schema
While Mongo is schema-less, SQL defines a schema via the table definition. A Mongoose `schema` is a document data structure (or shape of the document) that is enforced via the application layer.

#### Models
`Models` are higher-order constructors that take a schema and create an instance of a document equivalent to records in a relational database.

install mongoose on your project by running `npm i --save mongoose`

## Mongo

### Getting started

* Step 1 : Go to [MLAB STARTER TUTORIAL](https://www.google.com) create- or login to your mlab account.
* Step 2 : [CREATE NEW MLAB DB](https://mlab.com/create/wizard) choose AWS as the cloud provider and the free plan. Follow the steps until you made the order for the free database.

Completing step 2 redirects you to your MLAB dashboard, where you will now find your newly created mongoDB.

* Step 3 : Create an admin user for your database. From the MLAB dashboard, click on the server you created earlier. Next, click on the Users tab and add a new Database user.

![likethis](https://image.ibb.co/bU0KC9/create_user_mlab.png)

For dev/tes/- or tutorial purposes I personally use dummy login credentials:
  username: username
  password: 123password

Your newly created database user should appear on the mlab page, keep this tab open as we need it later.

### Connect your app to the remote MLAB Database

index.js

* add `const mongoose = require("mongoose")` at the top of the file.
* after the models- and routes import, use mongoose to add the link which is to connect your user credentials to the mlab database.

For me line 16 of `index.js` looks like this:
```mongoose.connect("mongodb://username:123password@ds251902.mlab.com:51902/testerino");```

Find the connect URI on the mlab tab you should have left open!
![righthere](https://image.ibb.co/b6BO5U/mlabconnecturi.png)

Your app now has capabilities to connect to MLAB. Though, first we need to build an interface to that Database.

### You have learned:
  * Construct a mongoose schema
  * Environment variables to secure sensitive credentials
  * Mongoose Object modeling for MongoDB
  * Read/Write data on a remote database (as json, no-sql)
  * Mongoose validation
  * Mongoose pre-post document save hooks use-cases
  * Seed fake data

### Update to mongoDB/atlas

Mlab dosen't exist anymore you need to use mongoDB with atlas

[official website](https://www.mongodb.com/cloud/atlas)

### Choosing a cloud provider.

Register to atlas and connect to your account. After that you will be granted to this page

![image](https://www.mongodb.com/assets/images/cloud/atlas/2018/cloud-provider.png)

If you dont want to aws (amazon) to be your cloud provider, you can always choose a different cloud provider but most of the time amazon will be the best choice.

Then choose the server you want your database to be located. (i use free tier available).

(By default the option you have choiced is a free option).

When you are fixed, you can confirm your choice.

### Create your user account and whitelist your ip

First we we're gonna make you a user account to connect to your database.

Go to database access and you will be granted with this page.

![createUser](https://i.stack.imgur.com/Vo9og.jpg)

On this page click on "add new user" and then enter a username and a password.

After you confirm your account.We need to
whitelist your ip address and then you can have access to your database.

### whitelist your ip

To whitelist your ip address go to network access(dont search for the link on the image, search for network access tab).

![allowIP](https://sjc1.discourse-cdn.com/business6/uploads/glitch/eac53ae6d71589dd32d270c3df593febfc411b85)

After that you can click on "add ip address".
Then you will be prompted with this message witch ask you for your ip address.

![promptIP](https://i.ytimg.com/vi/leNNivaQbDY/maxresdefault.jpg)

#### What to choose ? :

- Choose "add current ip address" if you want to access only on this computer (take care because some internet provider use dynamic ip witch mean that you will need to change everytime they reset your ip).

- Choose "allow access from anywhere" if you want to access on all remote computer.

### Connect your application to your cluster(database)

To connect your application to your database, you will need to go on cluster tab and then click on connect.

![connectButton](https://i.stack.imgur.com/6YpWO.jpg)

After that you will need to choose a type of connection (we will choose "Connect your application").

![connectCluster](https://cdn-web.studio3t.com/knowledge-base/wp-content/uploads/connect-your-application.png?x46272)

Check for "Connection String" tab, when you find it. Copy it and paste on mongoose.connect(stringurl)

![stringConnect](https://docs.atlas.mongodb.com/_images/gswa-driver-cso-example.png)

**DONT FORGET TO PUT YOUR PASSWORD ON ":password" AND ALSO TO CHOOSE NODE JS DRIVER.**

You are now ready to use your database with nodejs and mongoose.

