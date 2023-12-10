## Application framework for Node.js

* Express is a third-party module that provides a framework for building web applications
* The Express web application framework is one of the most popular building blocks for web applications

## Purposes of Express

* As an API
* Setup templates with server-side rendering (SSR)

## APIs with Express

* An Express API sets up an HTTP interface to interact with the data layer of the application.
* Data is sent back to the client in JSON format using a response, or res, object
* The res.json() method:
    * Notifies the client of the content type of the response being sent
    * Stringify data

## SSR with Express
* SSR is used to create templates
* Data is sent from the client to the server
* Templates use that data to create HTML,CSS, JavaScript
* Use the res.render() method

## Application framework for Node.js
* Express implements an app class that  you map to a web resource path
* The standard Node.js framework treats HTTP requests at a lower network level
* The http.createServer function relies on a custom callback function to parse through the web resource path
``` JavaScript
const express = require('express')
const app = express()
const port = 3000
...
let server = app.listen(port, function(){
    console.log(`Listening on URL http://localhost:${port}`);
})
```

## How Express works

1. Declare Express as a dependency in the package manifest of a Node.js project
2. Run the npm command to download any missing modules
3. Import the Express module and create an Express application
4. Create a new route handler
5. Start an HTTP server on a given port number

<b>Declare > Install > Require > Create > Start </b>

### Step 1: declare as dependency

* Create a <b> package.json </b> file in your project folder.
* The package.json file stores information about the contents of a Node.js module

<b> Name, Version, Description, Main, Dependencies</b>

Name: A name for the Node.js module

Version: A string that defines the major and minor version number of the module

Description: A sentence that describes the purpose of the module

Main: Identifies the Node.js script as the entry point into the module

Dependencies: Lists which Node.js modules the current module requires


```JSON
{
    "name": "temperature",
    "version": "1.0.0",
    "description": "Retrieve current weather conditions in the US",
    "main":"app.js",
    "dependencies": {
        "express":"4.x"
    }
}
```

### Step 2: run npm to download

* Run the npm install command inside the Node module directory to resolve any missing dependent Node modules
* The command downloads and saves any missing Node modules into its own <b>node_module</b> directory
* You can use different versions of the same Node module in different packages

Note: To install a Node.js module into the shared node_module directory, run 

```
npm install <module_name>
```
from the directory with your Node.js installation.


* The npm command download the Express framework and all of its dependent modules

```
npm install
```