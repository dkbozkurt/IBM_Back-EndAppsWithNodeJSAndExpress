## Concept of asynchronous callback functions
Node.js makes all network operations in a non-blocking manner

Every network operation returns immediately

To handle the result from a network call, you can write a callback function that Node.js calls when the network operation completes

## Sending an HTTP request call from a function inside a NodeJs module

```JavaScript
let options = {
    host:'w1.weather.gov',
    path:'/xml/current_obs/KSFO.xml'
};

http.request(options,
    function(response){ // callback anon function
        let buffer ='';
        let result ='';

        response.on('data',function(chunk){
            buffer += chunk;
        });

        response.on('end',function(){
            console.log(buffer);
        });

}).end();
```

## HTTP method calls for a server resource

### http.request options and callback

The http.request function calls the <b>callback function</b> parameter when it receiver part of the HTTP response message

The callback function parameter is optional; you can send an HTTP request and disregard the response message(object).

```JavaScript
http.request(options,[callback function]);
```

When http.request calls the callback function, it passes a <b>response</b> object in the first parameter.

```JavaScript
http.request(options, function(response){...});
```

### Handling response events

In Node.js, the object.on() function defines an event handler that the framework calls when an event occurs.

The response object emits a 'data' event when Node.js module receives a part of the HTTP response message

```JavaScript
response.on('data',function(chunk)
{
    buffer+= chunk;
});
```

When the Node.js module receives the last part of the HTTP response message, the HTTP response message, the response object emits an 'end' event.

```JavaScript
response.on('end',function()
{
    console.log(buffer);
});
```

### Handling error events

If the request fails, there is an 'error' event followed by the 'close' event

Call clientRequest.end() to complete sending the request

```JavaScript
let request = http.request(options,function(response){...});

request.on('error',function(e){
    resultCallback(e.message);
});
request.end();
```

With the http.clientRequest object you can,
* Write data to the HTTP request message body
* Add headers to the HTTP request message
* Define an event handler for errors that Node.js encounters while sending the request message

```JavaScript
let options= {
    hostname: 'www.ibm.com',
    port:80,
    method:'POST',
    headers:{
        'Content-Type':'application/x-www-form-urlencoded',
        'Content-Length':data.length
    }
};

let req = http.request(options, function(res){...})
```
