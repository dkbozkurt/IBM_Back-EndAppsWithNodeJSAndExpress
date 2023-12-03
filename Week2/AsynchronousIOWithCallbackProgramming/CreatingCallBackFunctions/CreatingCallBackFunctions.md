## Create a callback function to intercept HTTP method calls

Node.js makes extensive use of callback functions to return the result to the calling function

Mode.js modules pass an error object as the first parameter in a callback function.


### Passing an error object

```JavaScript
exports.current = function (location, resultCallback)
{
    . . .
    http.request(options, function(response){
        let buffer = '';
        let result = '';

        response.on('data',function(chunk){
            buffer += chunk;
        });

        response.on('end' function()
        {
            parseString(buffer, function(error,result){
                if(error)
                {
                    resultCallback(error);
                    return;
                }
                resultCallback(null, result.current_observation.temp_f[0]);
            });
        });
    });
}
```

If parseString passes an error object, pass the error back to the resultCallback callback function of the original caller(main app)

Set the first parameter as null if there is no error

### One callback at each level
When one Node.js application calls a module in a non-blocking manner, the application must provide a callback function to process the result.

If the main application calls http.request(), it must provide a callback handler to process the HTTP response message

If the main application calls a function that calls http.request(), two callback functions are involved:

* The custom module has a callback function to handle the HTTP response message from http.request()
* The main application has a callback function that processes the result that is captured in the first callback function

### Main application with callback

```JavaScript
let weather = require('./weather');
let location = 'KSFO';

weather.current (location, function(temp_f){
    console.log(temp_f)
});
```

When the main application calls weather.current(),it passes an anonymous callback function to process the result from the call.

``` JavaScript
exports.current = function(location,resultCallback){
    ...
    http.request = (options, function(response)
    {
        ...
        response.on('end',function()
        {
            resultCallback(...);
        });
    }).end();
}
```

The resultCallback callback function in the function of the custom Node.js module links to the anonymous callback function <b> function(temp_f) </b> of the weather.current function in the main application.

### Return a result with callback

```JavaScript
exports.current = function(location,resultCallback)
{
    let options = {
        host: 'w1.weather.gov',
        path: '/xml/current_obs/' + location + '.xml'
    };

    http.request(options, function(response)
    {
        let buffer = '';
        response.on('data',function(chunk)
        {
            buffer += chunk;
        });
        response.on('end',function()
        {
            parseString(buffer, function(error,result){
                ...
                resultCallback(null,result. current_observation.temp_f[0]);
            });
        });
    })
}
```

The resultCallback parameter stores the anonymous callback function from the main application.

The http.request() callback function calls resultCallback to return the result to the main application
