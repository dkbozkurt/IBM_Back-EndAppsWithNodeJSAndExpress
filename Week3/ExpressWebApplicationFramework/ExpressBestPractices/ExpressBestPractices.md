## Web framework directory structures

* Most web framework have required directory structure
* Express does not require a particular directory structure
* Best to define a structure in advance for growth and maintenance

## Suggested Express folder structure
* node_modules
* config
* models
* routes
* views
* public

### Node_modules

* Contains application`s modules and packages
* Automatically created after running the npm install command

### Config

* Contains configuration files such as
    * Database connections
    * Environment variables
    * Credential files including API keys for external services

### Models

* Contains data models
* Data models specify the type of data store defined by an ORM library

### Routes

* Specifies routes for all entities
* One file for each logical set of routes

### Views

* Contains templates
* Templates dynamically write HTML,CSS, and JavaScript for the client.

### Public

* Contains static content such as images, CSS, and JavaScript
* Helpful to have a sub-folder for each type of content

## Project Folder
Project Folder should also contain a few files

* app.js
    * Main configuration file for  your application

* routes.js
    * Central location to access routes
    * Imports all files from routes folder
    * Exports them as a single module to app.js
    * Creates a single point of entry for all routes

* package.json
    * Contains metadata used to manage dependencies

## API directory structure
* node_modules
* config
* models
* routes
* app.js
* routes.js
* package.json

### Naming routes

<table>
  <tr>
    <th>HTTP method and route</th>
    <th>Action</th>
  </tr>
  <tr>
    <td>POST/employee or PUT/employee:id</td>
    <td>Create a new employee</td>
  </tr>
  <tr>
    <td>GET/employees</td>
    <td>Retrieve a list of employees</td>
  </tr>
  <tr>
    <td>GET/employee/:id</td>
    <td>Retrieve an employee</td>
  </tr>
  <tr>
    <td>PATCH/employee/:id</td>
    <td>Modify an employee record</td>
  </tr>
  <tr>
    <td>DELETE/employee/:id</td>
    <td>Remove an employee</td>
  </tr>
</table>

### Using HTTP status codes
<table>
  <tr>
    <th>Status code</th>
    <th>Meaning</th>
  </tr>
  <tr>
    <td>200s</td>
    <td>Everything is OK</td>
  </tr>
  <tr>
    <td>300s</td>
    <td>Resource has been moved</td>
  </tr>
  <tr>
    <td>400s</td>
    <td>Client-side error</td>
  </tr>
  <tr>
    <td>500s</td>
    <td>Server-side error</td>
  </tr>
</table>

## Testing REST APIs

* Black-box test REST APIs
* Test as a whole without stubbed dependencies
* Mocha framework contains a module called SuperTest

## API authentication

* Use JWT based stateless authentication
* User properties are provided on the client-side

## API documentation

* Provide appropriate documentation for your REST APIs
* Documentation open-source projects:
    * API blueprint (apiblueprint.org)
    * Swagger (swagger.io)

## Using Node Package Manager (npm)

* Use npm init when initializing
* Use --save or --save-dev when installing
* The --save and --save-dev commands make sure correct dependencies are installed when moving to a different platform
* Never push a node_modules
* Always use npm to install packages

## Naming Conventions

<table>
  <tr>
    <th>Naming description</th>
    <th>Example</th>
  </tr>


  <tr>
    <td>Use lowercase for file names</td>
    <td>myfile.js</td>
  </tr>
  <tr>
    <td>Use camel case for variables</td>
    <td>myVariable</td>
  </tr>
  <tr>
    <td>Use lowercase separated by dashes for npm modules</td>
    <td>my-npm-module</td>
  </tr>
  <tr>
    <td>Use camel case when requiring npm modules</td>
    <td>require('myModule')</td>
  </tr>
</table>