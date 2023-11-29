## Node.js Packages

Every package has a package.json file that describes details about a Node.js module

### Example of package.json file

```JSON
{
    "name": "mod_today",
    "version":"1.0.0",
    "main": "./lib/today",
    "license":"Apache-2.0"
}
```

The name and version fields form a unique identifier for the module.

The main field lists a path to the main node.js script.

## Importing Node.js modules

Use require function to import a Node.js module

```JavaScript
let today = require('./today');
```

The require statement assumes that scripts have a file extension of .js

The require function creates an object that represents the imported Node.js module.

## Export functions and properties

Each Node.js module has an implicit exports object.

To make a function or a value available to Node.js applications that import your module, add a property to exports

```Javascript
let date= new Date();

let days = ['Monday','Tuesday','Wednesday','Thursday','Friday','Saturday','Sunday'];

exports.dayOfWeek = function() {
    return days [date.getDay()-1];
}
```

## Accessing exported properties

To access the properties of the module, retrieve the property from the variable

today.dayOfWeek represents the current exported property from the today Node.js module

```JavaScript
console.log("Happy %s!", today.dayOfWeek());
```