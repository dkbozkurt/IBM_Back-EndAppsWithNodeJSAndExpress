* Run the npm install command.
* Create a mynodeserver.js file

### Step 3:Import the module

* Create an instance of the app object from the Express web application framework

```JavaScript
let express = require('express');

let app = express();

```

### Step 4:Create new route handler

* To handle web application requests, map an HTTP method and a web resource path to a JavaScript function

``` JavaScript
// Listen to incoming HTTP GET requests, which requests to the /temperature resource path
app.get('/temperature/:location_code', function(request, response) {
    let location = request.params.location_code;

    // Run the weather.current function with a location parameter taken from the resource path
    weather.current(location,function(error,temp_f){
        ...
    });
});

```

### Step 5: Start HTTP server on port

* Call app.listen to create a web server object (instance) that listens to incoming requests on the specified port

```JavaScript
    let server = app.listen( port, function()
    {
        console.log(`Listening on URL http://localhost:${port}`);
    })
```

* Example : the app listens to incoming requests on 8080

* The second parameter defines an anonymous function that the Express framework calls when it creates an instance of the server object.

* Enter http://localhost:8080/temperature/KSFO in a browser and get the result


