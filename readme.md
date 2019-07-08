# Node JS

## Overview
1. [What is node JS?](#what-is-node-js)
2. [Architecture](#architecture)
    1. Web UI
    2. Node JS
    3. Mongo DB
3. [Tutorial overview](#tutorial-overview)
4. [Getting started](#getting-started)
5. [Coding time](#time-for-coding)
6. [What is next](#what-is-next)


## What is Node JS

Node.js is an open-source, cross-platform JavaScript run-time environment that executes JavaScript code outside the browser. Historically, JavaScript was used primarily for client-side scripting, in which scripts written in JavaScript are embedded in a webpage's HTML and run client-side by a JavaScript engine in the user's web browser. Consequently, Node.js represents a "JavaScript everywhere" paradigm, unifying web application development around a single programming language, rather than different languages for server side and client side scripts.

Remember that nodeJS is a run-time environment that enables javascript frameworks/libraries.
As a metaphor imagine nodeJS is which makes it possible to create a web of different nodes, those nodes can be any javascript-code you want to link to your app.

NodeJS’s most popular used framework is ExpressJS (imagine Express JS being one of NodeJS nodes for your app).

So how does NodeJS make it possible to attach nodes to your app? Well actually, it's all about NPM. Known as the Node Package Manager. (It would sound silly as Node Nodes Manager, but I hope you get the gist).


## Architecture

![3-tier](https://raw.githubusercontent.com/komushi/gnavi-mongo/master/images/architecture.png)

### Web UI
An app's client, user interface, front-end, the web UI. Maybe you are familliar with HTML being rendered from the back-end, as does for example PHP or Rails, in the image above the client is a seperate tier. Why? Because today the day there is a lot of optimization potential doing it this way, MVC clients.
The web UI communicated with node JS (the back-end) in JSON format and the different kinds of data requests represent the M (model) in MVC.
A web UI's client also has a structure to orchestrate incoming data, more than just displaying it, that's the C (controller) in MVC.
The web UI's rendering of HTML (+ data) is what we call the V (view) in MVC.

### Node JS
Client <-> Server communication does so through API endpoints. In the chart's example the API is designed RESTfully. This makes routes in your app rather predictable structure and better dev-team synergy. REST is the most common used API design.
The importance of using node for Javascript projects equals needing solid earth before building a house. We take the earth beneath us for granted, don't do the same for node.
Like most tech-stacks MERN (Mongo, Express, React, Node), MEAN (Mongo, Express, Angular, Node) and other tech-stacks. Node JS is the industry standard and it's not going anywhere, worth learning!

### Mongo DB
The DB of choice is Mongo (no-sql). Though any kind of Database can communicate with Express, choose the right parser/sequalizer for when you decide to go SQL. A data-entry in NO-SQL is a document, i.e. a user, a car, etc. Grouping this documents is a collection. An app's Database in no-sql has many collections, and those collections contain documents.


## Tutorial overview

  * How to initialise the node package manager
  * What is a package.json
  * How to initialise an express server available for local host
  * Test API endpoints with Postman
  * CRUD API routes
  * Read/Write data to a local json file
  * Server Side redirects
  * Construct a mongoose schema
  * Environment variables to secure sensitive credentials
  * Mongoose Object modeling for MongoDB
  * Read/Write data on a remote database (as json, no-sql)
  * Mongoose validation
  * Mongoose pre-post document save hooks use-cases
  * Seed fake data
  * Render HTML
  * Deploy to Heroku
  * Happy path end-to-end testing with Cypress

## Getting started
First and foremost make sure that Node is installed on your machine.
To do so run `node -v` as a terminal command, it should return the current version installed.
If your installed version is < 8.0.0 or if it is not installed at all, visit https://nodejs.org/en/download/ and follow the steps. Afterwards check the node version.

## Time for coding

* [First app](./first_app)
* [Second app](./second_app)
