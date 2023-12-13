## What is Authentication?

The process of confirming a user`s identity by obtaining credentials and using those credentials to validate their identity.

### Three approaches to authentication
1. Session based authentication
2. Token based authentication
3. Passwordless authentication

### Advantages of token-based authentication

* Scalable
* Flexible
* Secure

### Create the server

This code creates a web server module by calling the "express()" function and assigning it to the constant “myapp."

```JavaScript
const express = require('express');
const myapp = express();

myapp.get('/employees', (req, res) => {
    return res
        .status(401)
        .json({message: "Please login to access this resource"});
});

myapp.listen(5000, ()=>
{
    console.log("API Server is localhost:5000");
});
```

### Verify the endpoint with cURL
* To execute the API, save the file and name it apiServer.js
* Then run the command:

```
node apiServer.js
```

* To verify that the endpoint cannot be accessed unless the user is authorized, run thus cURL command

```
curl -i localhost:5000/employee
```
## Generate a JSON web token(JWT)

### Install jsonwebtoken package
Generate JWTs with jsonwebtoken npm package
```
npm install -save jsonwebtoken

```

### Require the JWT module

```JavaScript
const express = require("express");
const jsonwebtoken = require("jsonwebtoken");

const JWT_SECRET = "aVeryVerySecretString";
```
### Define POST API method

```JavaScript
const myapp = express();
myapp.use(express.json());

myapp.post("/signin",(req,res) => {
    const { uname, pwd} = req.body; // This is a wrong usage !!!
    ...
```

### Return the JWT token
```JavaScript
if(uname === "user" && pwd ===  "password"){
    return res.json({
        token: jsonwebtoken.sign({user:"user"},JWT_SECRET),
    });
    }
    return res
        .stats(401)
        .json({message: "Invalid username and/or password"});
});
```

### Define GET API method

```JavaScript
myapp.get("/employees",(req,res) => {
    let tkn = req.header('Authorization');
    if(! tkn)
        return res.status(401).send("No Token");
    if(tkn.startsWith('Bearer ')){
        tokenValue = tkn.slice(7,tkn.length).trimleft();
    }
...

```

### Verify the JWT

``` JavaScript
...
const verificationStatus =
    jsonwebtoken.verify(tokenValue,"aVeryVerySecretString");
    if(verificationStatus.user === "user"){
        return res.status(200).json({message: "Access Successful to Employee Endpoint"});
    }
return res
```

### Verify the JWT and listen

``` JavaScript
...
.status(401)
.json({message: "Please login to access this resource"});
});

myapp.listen(5000,()=>
{
    console.log(`API Server is localhost:5000`);
});
```

## Functionality summary

1. API endpoint: signin
2. Reads username and password from the request body
3. Validates against the database
4. If there is a match use the jsonwebtoken.sign() method to generate the token
5. Send the token as a response

## NOTES:

* Advantages of token-based authentication include scalability, flexibility and security
* The POST API is used during authentication to log a user in to an application
* The GET API is used in authorization to determine which resources a user can access
* A JSON web token is used to authenticate a user and authorize which resources they have access to use




