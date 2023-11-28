## What is a module

File containing related JavaScript functions that serves a specific purpose

Related, encapsulated JavaScript code.

Serves a single purpose.

Can be a single file or a folder containing files

Reusable

Breaks down complex code into manageable chunks


## What is a module specification

Conventions and standards used to create packages

* CommonJS - require()
* ES - import()

## Differences between import and require statements

require()

* Can be called anywhere in the code
* Can be called within conditionals and functions
* Dynamic
* Binding errors not identified until run-time
* Synchronous

import()
* Can only be called at the beginning of the file
* Cannot be called within conditionals or functions
* Binding errors identified at compile-time
* Asynchronous