## Routing

* Request to different routes
* GET, POST, PUT, DELETE
* App level and router level

### Routing at application level

* Handle different routes and requests

``` JavaScript
const express = require('express');
const app = express();

app.get('user/about/:id',(req, res) =>{
    res.send("Response about user:" + req.params.id);
});

app.post('user/about/:id',(req, res) =>{
    res.send("Response about user:" + req.params.id);
});

app.get('item/about/:id',(req, res) =>{
    res.send("Response about item:" + req.params.id);
});

app.post('item/about/:id',(req, res) =>{
    res.send("Response about item:" + req.params.id);
});

app.listen(3333, ()=>{
    console.log(`Listening at http://localhost:3333`);
})
```
### Routing with routers
Handle different routes and requests

``` JavaScript
const express = require('express');
const app = express();

let userRouter = express.Router();
let itemRouter = express.Router();

app.use("/item",itemRouter);
app.use("/user",userRouter);

userRouter.get("/about/:id",(req,res)=>{
    res.send("Response about user"+req.params.id);
});

userRouter.get("/details/:id",(req,res)=>{
    res.send("Details about user"+req.params.id);
});

itemRouter.get("/about/:id",(req,res)=>{
    res.send("Information about item"+req.params.id);
});

itemRouter.get("/details/:id",(req,res)=>{
    res.send("Details about item"+req.params.id);
});

app.listen(3333, ()=> {
    console.log(`Listening at http://localhost:3333`);
});

```

## Middleware
* Functions that have access to the request and response objects and the next function
* Can be chained
* Categorized based on purpose,use and source
* Useful to parse requests, add authentication, handle errors, and other common activities

### Application-level middleware
Bound with app.use()

```JavaScript
const express = require('express');
const app = express();

app.use(function(req, res,next) {
    if (req.query.password !== "pwd123") {
        return res.status(402).send("This user cannot login");
    }
    console.log('Time:', Date.now());
    next();
});

app.get("/",(req,res) => {
    return res.send("Hello Word");
});

app.listen(3333,()=>{
    console.log(`listening at http://localhost:3333`);
});
```

### Router-level middleware
Bound with router.use()

``` JavaScript
const express = require('express');
const app = new express();

let userRouter = express.Router();
let itemRouter= express.Router();

userRouter.use(function (req,res, next) {
    console.log('User query Time:', Date());
    next();
});

userRouter.get('/:id', function (req,res,next){
    res.send("User "+req.params.id+" last successful login "+Date());
});

itemRouter.use(function (req,res, next) {
    console.log('Item query Time:', Date());
    next();
});

itemRouter.get('/:id', function (req,res,next){
    res.send("Item "+req.params.id+" last enquiry "+Date());
});

app.use('/user',userRouter);
app.use('/item',itemRouter);

app.listen(3333,()=>{
    console.log('Listening at http://localhost:3333');
})
```

## Error-handling middleware

Bound with app.use or router.use()

``` JavaScript
const express = require('express');
const app = new express();

app.use("/user/:id",function(req, res, next)
{
    if(req.params.id == 1)
    {
        throw new Error("Trying to access admin login");
    }
    else{
        next();
    }
});

app.use(function(err, req, res, next){
    if(err != null)
    {
        res.status(500).send(err.toString());
    }
    else{
        next();
    }
});

app.get("/user/:id",(req, res)=>{
    return res.send("Hello! User Id ", req.params.id);
});

app.listen(3333.()=>
{
    console.log(`Listening at http://localhost:3333`);
});

```

## Built-in middleware

* Static files, cookie parse, JSON

``` JavaScript
const express = require('express');
const app = new express();

app.use(express.static('cad220_staticfiles'));

app.listen(3333.()=>
{
    console.log(`Listening at http://localhost:3333`);
});
```

## Third-party middleware
* Open source, third party, user defined

```JavaScript
const express = require('express');
const app = new express();

function myLogger(req, res, next){
    req.timeReceived = Date();
    next();
}

app.use(myLogger);

app.get("/",(req,res)=>{
    res.send("Request received at " + req.timeReceived+" is a success!");
});

app.listen(3333.()=>
{
    console.log(`Listening at http://localhost:3333`);
});
```

## Template rendering

Rendering dynamic content

```JavaScript
const express = require('express');
const app = new express();
const expressReactViews = require('expressReactViews');

const jsxEngine = expressReactViews.createEngine();

app.set('view engine', 'jsx');

app.set('views', 'myviews');

app.engine('jsx',jsxEngine);

app.get("/:name",(req,res) => {
    res.render('index',{name: req.params.name});
});

app.listen(3333.()=>
{
    console.log(`Listening at http://localhost:3333`);
});
```

### Notes:

* Routers are used for branching query handling
* Five types of middleware are application level, router level, error handling, built-in, and third party
* Template rendering is the ability of the server to fill in dynamic content in the HTML template



