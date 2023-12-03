### After completing this lab, you will be able to:

* Describe Promise callbacks
* Create a Node.js application with promises

### Task 1: Create and execute a script with promise

1. Open a terminal window by using the menu in the editor: Terminal > New Terminal.

2. Change to your project folder.

```
cd/home/project
```

3. Create a new file by running the following command.

```
touch promisescript.js
```

4. List the files in the current directory to see if the file has been created.

```
ls
```

5. Open the file <b> promisescript.js</b> and edit it.

6. Paste the following code in the file and save it. Are you able to look at the file and guess te order in which the console logs will be executed?

```JavaScript
//Creating a promise method. The promise will get resolved when timer times out after 6 seconds.
let myPromise = new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve("Promise resolved")
    },6000)})

//Console log before calling the promise
console.log("Before calling promise");

//Call the promise and wait for it to be resolved and then print a message.
myPromise.then((successMessage) => {
    console.log("From Callback " + successMessage)
  })

//Console log after calling the promise
  console.log("After calling promise");
```

7. Go to the terminal and run the file to verify your guess.
```
node promisescript.js
```

8. he order in which the console logs are executed tell you that the statements after the promise call are executed one after the other and the promise is simultaneouly getting resolved or rejected.

## Practice Exercise: Create and execute a script with two promises

### Challenges

1. Create a script which has two methods that return promises - One of the promises should get reolved after 6 seconds timeout and the other one after 3 seconds timeout. Call the promise in such a way that the second promise is invoked after the first promise is resolved.

```JavaScript
let myPromise1 = new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve("Promise 1 resolved")
    },6000)})

let myPromise2 = new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve("Promise 2 resolved")
    },3000)})

  myPromise1.then((successMessage) => {
    console.log("From Callback " + successMessage)
    myPromise2.then((successMessage) => {
      console.log("From Callback " + successMessage)
    })
  })
```

2. Change the code to call the promises sequentially and see how the output changes.

```Javascript
let myPromise1 = new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve("Promise 1 resolved")
    },6000)})

let myPromise2 = new Promise((resolve,reject) => {
    setTimeout(() => {
      resolve("Promise 2 resolved")
    },3000)})

  myPromise1.then((successMessage) => {
    console.log("From Callback " + successMessage)
  })

  myPromise2.then((successMessage) => {
  console.log("From Callback " + successMessage)
})
```