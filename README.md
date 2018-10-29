[![Build Status](https://www.travis-ci.com/ashley-breunich/lab-08.svg?branch=master)](https://www.travis-ci.com/ashley-breunich/lab-08)

![CF](http://i.imgur.com/7v5ASc8.png) LAB - Express Routing & Middleware
=======================================================

## Submission Instructions
* Follow the core Lab submission instructions. This must be fully tested and deployed at Heroku

## Before you begin
* You'll need to initialize this lab folder as a new node module, install your dependencies, setup your npm script commands, and pull in your config files
* Fire up RESTy ... you'll want to use this to test out your API!

## Overview
You have been provided a working and partially tested API server. The assignment for today is to extend that server's functionality by adding a new data model and an alternative storage mechanism.

## Assignment
#### Requirement 1: Add an additional model
* Add a second model called `users` to the API Server (in the `src/models` folder)
  * This model should expose the same interface as the `notes` model
  * This model should conform to the interface set forth by the memory data module
  * This model should contain the fields: _id, firstname, lastname, email, role
  * Perform the following data validations on save and update:
    * All fields are required
    * `email` is a valid email address
    * `role` is one of the following values: `user`, `editor`, `admin`
* Add a new route called `users` to the API Server (in the `src/api` folder)
  * This route should support all REST verbs for the `users` model

#### Requirement 2: Add an additional storage mechanism
* Currentlly, the models require a `storage` module called `memory`
* Create a new storage module called `file` and connect both models to it
  * This module should create and store the model database in a folder called `data` at the root of the project
* Implementation: comment/uncomment the models to switch between the 2 storage engines

###### Testing
* Minimal (happy path tests) have been provided for the `notes` routes
* Complete the tests for `notes` and write the tests for `users`
  * All REST methods should be exercised
  * Ensure good inputs and outputs (i.e. what if we have no id?)
    * This might lead you to change core code, which is good!
  * Seek out edge cases
* Your api tests should work the same regardless of which storage engine (`memory` or `file`) that you are using.
* There are currently no tests for the memory storage mechanism (or the file storage that you'll be creating)
  * Implement a test suite that covers the methods, return values, edge cases, and data integrity surrounding each of these.

###### Stretch Goals:
* Add a dynamic switch (maybe a setting in the .env file) that would switch out the storage engine dynamically based on a configuration
* Explore a way to unify the routes into ONE route that can access ANY model.
  * ... and along with that, a way to test the common route against any model and storage engine


##  Documentation

###### APP.JS MODULE:
Airty: 1
Expected Data: The data will be the PORT number so the program can run
Behavior: If the server isn't running, the program will run on the given port. If the server is already running, it will throw a console log alerting the user that the server is already running. 

###### MODELS/NOTES.JS MODULE:
Behavior: This module holds the NOTES class and all of the functions associated with it. These functions are called in the API associated file. 

###### MODELS/USERS.JS MODULE:
Behavior: This module holds the USERS class and all of the functions associated with it. These functions are called in the API associated file.

###### MODEL-FINDER MODULE:
Airty: 3
Expected Data: Request, Response, Next
Behavior: This module tells the program which model to use. When a model is found, it will set the req.model. When a model is not found, it will throw 'Invalid Model.' 

###### ERROR MODULE:
Airty: 4
Expected Data: Error, Request, Response, Next
Behavior: If there is a server error, it will go through this function and explain what the error is.  

###### 404 MODULE:
Airty: 3
Expected Data: Request, Response, Next
Behavior: If a page cannot be found, it will go through this function and throw a 404 error.

###### STORAGE MODULE:
Airty: 1
Expected Data: process.env.STORAGE
Behavior: This function takes in the process.env.STORAGE variable and uses a switch case to let the program know what kind of storage to use.  

###### MEMORY MODULE:
Airty: 1
Expected Data: Each funtion in this page takes in 1 paramater - either a query, ID or data
Behavior: Depending on which function is called, memory is accessed to either send data, resave data or delete data. 

###### FILE MODULE:
Airty: 1
Expected Data: Each funtion in this page takes in 1 paramater - either a query, ID or data
Behavior: Depending on which function is called, code runs that then saves the changes to the db.json file. 

###### V1 MODULE:
Airty: 3
Expected Data: Each funtion in this page takes in 3 parameters - Request, Response, Next
Behavior: This file interacts with the API. It makes API calls depending on which HTTP method is used (get, put, patch, delete, post). The JSON that is sent through the front end is stringified and then sent to whichever function is related. Then the appropriate save functions are called to accurately update the db.json file. 

#### Collaborations
Hai helped me figure out why my delete function was throwing an error. Nicholas, our substitute instructor, also assisted me with questions I had. 

I do want to note that I rewatched the video from lecture and followed along to get the write and read functions and the model finder working.


