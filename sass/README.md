# MERN Stack

## What is MERN?

M - Mongo: Document database
E - Express: Back-End web application framework
R - React: Front-End web applicaiton framework
N - Node: JavaScript runtime environment

## Pros & Cons of MERN

### Pros

* All JavaScript all the time
* Code sharing (business logic, validation)
* Object representation is always JSON from end to end
* Node is a fast and resilient web server

### Cons

* MongoDB/NoSQL database

## Building with the MERN Stack

## Before we Begin

This site is using Create React App with some additional modifications to make it so we can use an Express server as well.

## NPM Packages

Be sure to install the following packages before running this code:

* express
* body-parser
* mongoose
* react
* axios

## Set Up Server.js

Make sure you've required express, body-parser, mongoose, and your routes folder

const express = require("express");
const bodyParser = require("body-parser");
const mongoose = require("mongoose");
const routes = require("./routes");

Now we're going to set up Express for use in our app. Express is our web framework for Node.js, and we'll use it later to set up our API routes. For now set up an instance of express

const app = express();

Now add the following lines of code to your server.js file. This code tells Express to use body-parser, an express middleware that parses incoming req.body's for use in your app.
Then we tell express where to find the static files (css, images, etc.)
Then tell Express to use our routes directory

app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());
app.use(express.static("client/build"));
app.use(routes);

Now let's set up MongoDB. MongoDB is a document-based database. We'll go into more detail later, but for now, add the following code to set up your database

// If deployed, use the deployed database. Otherwise use the local va-parks database
var MONGODB_URI = process.env.MONGODB_URI || "mongodb://localhost/va-parks";

// Set mongoose to leverage built in JavaScript ES6 Promises
// Connect to the Mongo DB
mongoose.Promise = Promise;
mongoose.connect(MONGODB_URI);

Finally, lets set up our server-side PORT
const PORT = process.env.PORT || 3001;

app.listen(PORT, function() {
console.log(`🌎 ==> API Server now listening on PORT ${PORT}!`);
});

## Set Up Your Models

For this project we'll need two models: one for the national parks, and one for park comments.
In your models folder, create 3 files

MongoDB is a NoSQL database. This means that instead of tables with rows and columns, we have a json-like file that lists a series of key value pairs

## Build your Controllers

## Set Up Your routes

## Axios

## Resources

https://expressjs.com/en/guide/routing.html
http://mongoosejs.com/docs/guide.html
https://www.mongodb.com/mongodb-3.6
https://www.npmjs.com/package/body-parser
https://www.npmjs.com/package/axios
