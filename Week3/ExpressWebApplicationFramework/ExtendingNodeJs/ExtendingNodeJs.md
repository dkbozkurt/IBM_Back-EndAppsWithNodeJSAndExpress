## Parse web service messages
Match a substring that starts and ends with the <temp_f> XML element tags

```JavaScript
response.on('data',function(chunk){
    buffer += chunk;
});

response.on('end',function(){
    let matches = buffer.match(/\<temp_f\>.+\<\/temp_f\>/g);
    if(null != matches || matches.length > 0)
    {
        let result = matches[0].replace(/\<temp_f\>/,"").replace(/\<\/temp_f\>/,"");
    }

    resultCallback(null,result);
});
```

## Disadvantages of manual parsing
* String matching ignores the structure of XML data
* The message body might contain malformed XML data
* Depending on the complexity of the XML data, string matching might be more efficient that building an XML tree of the data
* String matching is less tolerant to changes in the XML data structure
* If the message adds or removes any XML elements, you must change the regular expression on the strung match function

## Parse XML elements to JavaScript
* The xml2js Node.js package parses a string of XML elements into a JavaScript object
* Unlike other XML parsing Node.js packages, xml2js uses only JavaScript

### Install packages with npm

```
npm install xml2js
```

## Import the package
The parseString function runs the callback function when it finishes processing the XML tree in buffer

``` JavaScript
let parseString = require('xml2js').parseString;

exports.current = function(location,resultCallback){
    ...

    let request = https.request(options, function(response){
        ...

        response.on('end',function(){
            parseString(buffer, function(error,result)
            {
                if(error) {...}

                resultCallback(null, result.current_observation.temp_f[0]);
            });
        });
    });
}
```

### Recap

* String matching ignores the structure of XML data
* The xml2js Node.js package parses a string of XML elements into a JavaScript object

