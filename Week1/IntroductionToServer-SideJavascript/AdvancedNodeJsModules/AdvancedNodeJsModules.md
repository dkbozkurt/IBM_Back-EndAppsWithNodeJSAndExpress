# Advanced Note.js Modules

Libraries are the same thing as modules in regard to Node.js. Libraries contain code that has been developed that can be reused throughout an application.

There are three types of modules: core, local, and third-party.

### Core
Core Node.js modules form a minimal library. They contain the minimal functionality needed to develop Node.js applications.

### Local
Local modules are the next type of Node.js module. Local modules are the modules written by you and the development team as part of creating your Node.js application.

### Third-party
Third-party modules are available online and have been created by the back-end Node.js community.

The most important of the core modules are http, path, fs, os, util, url, and querystring. Let's briefly discuss each of these and provide code examples.

## HTTP
The HTTP module provides methods to <b>transfer data over HTTP</b>.

Here is sample code that creates an instance of a server using the http module. This code makes use of the http.createServer() method to create the server instance.

```JavaScript
let http = require('http');
http.createServer(function (req, res) {
    res.write('hello from server');//write a response to the client
    res.end();//end of response from server
}).listen(6000);//the server instance listens for http requests on port 6000
```

## Fs
The fs module is used to interact with a <b>file system</b>

The following code sample reads a local file synchronously using the fs module and prints the file contents to the console.

```JavaScript
// sample code to read a file synchronously using the fs.readFile() method
const fs = require('fs');
const data = fs.readFile('sample.txt', 'utf8');
// print contents of the file "sample.txt" to console
console.log(data);
```
The fs module can also be used for input and output, known as I/O. The fs module methods can be used to retrieve information from or write data to an external file.

```JavaScript
const fs = require(‘fs’);
const data = fs.readFileSync(‘/content.md’); // blocks here until file is read
console.log(data);//writes data in the content.md file to the console

```

## OS
The OS module provides methods to <b>retrieve information from the operating system</b> that the application is running on and interact with it.

This is sample code from the OS module that gets the computer's platform and architecture.

```JavaScript
let os = require('os');
console.log("Computer OS Platform Info : " + os.platform());
console.log("Computer OS Architecture Info: " + os.arch());
```

## Path
The path module allows you to <b>retrieve and manipulate directory and file paths</b>.

The following code retrieves the last portion of a given file path and prints that value to the console:

```JavaScript
const path = require('path');
let result = path.basename('/content/index/home.html');
console.log(result); //outputs home.html to the console
```

## Util
The Node.js util module is intended for internal use for <b>accomplishing</b> such tasks as <b>debugging and deprecating functions</b>.

Say you want to debug a program to count the number of iterations in a loop. You could use util.format() method as follows:

```JavaScript
let util = require('util');
let str = 'The loop has executed %d time(s).';
for (let i = 1; i <= 10; i++) {
    console.log(util.format(str, i)); //outputs 'The loop has executed i time(s)'
}
```

## URL
The URL module is used to <b>divide up a web address into readable parts</b>.

Here is a sample code that returns the value of the "firstName" query object from the given URL.

```JavaScript
const url = require('url');
let webAddress = 'http://localhost:2000/index.html?lastName=Kent&firstName=Clark';
let qry = url.parse(webAddress, true);
let qrydata = qry.query; //returns an object: {lastName: 'Kent', firstName: 'Clark'}
console.log(qrydata.firstName); //outputs Clark
```

## querystring
The querystring module provides methods to <b>parse through the query string of a URL</b>.

For example,

```JavaScript
let qry = require('querystring');
let qryParams = qry.parse('lastName=Kent&firstName=Clark');
console.log(qryParams.firstName); //returns Clark
```