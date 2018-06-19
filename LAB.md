## Submission Instructions
* Create a PR to your master from your working branch.
* Submit on canvas:
  * a question and observation
  * how long you spent
  * link to your pull request
  * **Travis CI not required for this lab as you are not writing tests**

## Configuration 
Configure the root of your repository with the following files and directories. Thoughfully name and organize any aditional configuration or module files.
* **README.md** - contains documentation
* **.env** - contains env variables (should be git ignored)
* **.gitignore** - contains a [robust](http://gitignore.io) `.gitignore` file 
* **.eslintrc** - contains the course linter configuratoin
* **.eslintignore** - contains the course linter ignore configuration
* **package.json** - contains npm package config
  * create a `lint` script for running eslint (eslint **/*.js)
  * create a `start` script for running your server
* **index.js** - the entry point for your application
* **src/** - contains your core application files and folders
* **src/app.js** - (or main.js) contains your core application bootstrap
* **src/lib/** - contains module definitions

## Feature Tasks  
For this assignment, you will be building a TCP chatroom. Clients should be able to connect to the chatroom through the use of telnet. Clients should also be able to run special commands to exit the chatroom, list all users, reset their nickname, and send direct messages. You may add as many features to this application as you would like. Do not use any third party libraries and testing is *not* required.

##### Minimum Requirements 
* Create a TCP Server using the NodeJS `net` module
* Create a Client constructor that models an individual connection 
  * Each client instance should contain (at least) `_id`, `nickname`, and `socket` properties
* Clients should be able to send messages to all other clients by sending it to the server
* Clients should be able to run special commands by sending messages that start with a command name
  * The client should send `@quit` to disconnect
  * The client should send `@list` to list all connected users
  * The client should send `@nickname <new-name>` to change their nickname
  * The client should send `@dm <to-username> <message>` to send a message directly to another user by their nickname

* Connected clients should be maintained in an in-memory collection called the `clientPool`
  * When a socket emits the `close` event, the socket should be removed from the client pool
  * When a socket emits the `error` event, the error should be logged on the server
  * When a socket emits the `data` event, the data should be logged on the server and the commands above should be implemented
  
## Stretch Goals
* Modularize your chatroom.js module so that you have separated out events and helper functions into their own separate modules.
* Add some error handling so that you cannot have duplicate users with the same nickname (this code is not set up to prevent that). 
* Currently, the way this code is set up, you'll have to do an O(n) lookup in order to DM a user or delete a user from your client pool. Reformat your code so that you can do these operations in O(1) time instead of O(n) time. **You may need to take up O(n) more space to get this done, but that's OK. This is a good tradeoff.** 

##  Documentation  
Write documention for starting your server connection and using the chatroom application.  Write this documentation as if you are directing someone who has no idea of the tools you are using (netcat, Putty, etc.) how to go through all the steps *from the start* with installing the right dependencies, etc. Be sure to use proper markdown constructs and `highlight blocks of code`.
