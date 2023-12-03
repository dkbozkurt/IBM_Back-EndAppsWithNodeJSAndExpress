## Definition of Promises

* An <b>object returned by an asynchronous method.</b>
* States : Pending, Resolved, Rejected
* Uses: API requests, I/O operations
* You can create a promise if you know that the operations could be blocking.

## The different states of promises

Initial state of the promise is <b>Pending</b> state.
If the operation ends with successfully, end state will be <b>Resolved</b> state.
When there is an error, end state will be <b>Rejected</b> state.

## How to use promises with asynchronous methods

### User-defined promise

```JavaScript
let prompt = require('prompt-sync')();
let fs = require('fs');

const methCall = new Promise((resolve, reject) => {
    setTimeOut(()=>
    {
        let filename = prompt('What is the name of the file?');
        try{
            const data = fs.readFileSync(filename,{encoding:'utf8', flag:'r'});
            resolve(data);
        }
        catch(err)
        {
            reject(err)
        }
    },3000);
});

console.log(methCall);

methCall.then(
    (data) => console.log(data),
    (err) => console.log("Error reading file");
);
```

### Axios request

The axios package is used in Node.js to handle HTTP requests

``` JavaScript
const axios = require('axios').default;

const connectToURL = (url)=>
{
    const req = axios.get(url);
    console.log(req);
    req.then(resp=> {
        console.log("Fulfilled");
        console.log(resp.data);
    })
    .catch(err => {
        console.log("Rejected");
    });
}

// Valid URL
connectToURL('validURL.json');

// Invalid URL
connectToURL('invalidURL.json');
```