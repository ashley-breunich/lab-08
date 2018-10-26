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
I am still finishing up this lab and will complete the README once I am done.

I do want to note that I rewatched the video from lecture and followed along to get the write and read functions and the model finder working. I will write in recaps of what each function is doing once I do my final submit.

Hai helped me figure out why my delete function was throwing an error.

