## Runtime Environments

* Node.js <b>IS NOT</b> a web framework.
* Node.js <b>IS</b> a runtime environment that executes JavaScript on a server
* Runtime Environments are the hardware and software that can execute programs with a particular codebase.

## Node framework
* Web frameworks are the skeleton on which an application is built.
* Fundamental structure that supports the application
* Node.js requires a web framework to utilize it
* Node.js frameworks are called node frameworks

* Two approaches to building back ends:
    * Model-View-Controller (MVC)
    * Representational state transfer application programming interfaces ( REST API)

## Model-View-Controller (MVC)

* Model:
    * Manager data
    * Interacts with database and handless data logic

* View:
    * Renders presentation of the data

* Controller:
    * Regulates data flow
    * Processes data provided by user

### Popular frameworks that can implement MVC

Used for apps that need separation of the data, from the data presentation, and from the manipulation of data.

Koa, Django, Express, NestJS

### REST APIs
* Allow multiple web services to communicate with each other and the client
* RESTful APIs:
    * Client and server code are independent of each other
    * Client does not know the state of the server and vice versa <b>(stateless)</b>
    * Communicate via operations on resources
    * Communication does not rely on an implementation of the API

## Express

* One of the most popular node frameworks
* Primarily used for routing and middleware
* Small learning curve because it uses JavaScript
* Easy to implement an MVC architecture pattern
* Provides debugging mechanisms

## Express Advantages
* Handles multiple operations requests concurrently
* Has HTTP helpers for handling HTTP requests
* HElps facilitate communication between client and server
* Efficiently provides HTTP headers to URLS to get needed data requested by the client

