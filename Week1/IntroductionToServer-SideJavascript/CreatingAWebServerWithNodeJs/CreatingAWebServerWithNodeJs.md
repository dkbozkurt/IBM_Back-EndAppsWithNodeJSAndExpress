## Characteristics of Node.js

Node.js is single-threaded application that handles input/output(I/O) operations through events

Callback functions that handle results when they complete

### Node.js modules
Every JavaScript file in a module in Node.js
Multiple modules can be grouped into a package.

With the http Node.js module, you can develop an application that listens to HTTP requests and returns HTTP response messages

## Create a simple web server

With the http Node.js module, you can develop an application that listens to HTTP requests and returns HTTP response messages

```JavaScript
let server = http.createServer(function(request,response)
{
    let body = "Hello World!";

    response.writeHead(200,{
        'Content-Length':body.length,
        'Content-Type': 'text/plain'
    });

    response.end(body);
});

server.listen(8080);
```

Use the http.createServer function to create an instance of a web server application.

Web server stored in a variable called server.

Develop an anonymous function to handle the incoming request message and to send back a response message

After you create an instance of a server object, set the server to listen to a specific port: http.listen(8080);