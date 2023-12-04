### After completing this lab, you will be able to:

* Describe asynchronous callbacks
* Create a Node.js application

## Task 1: Set-up - Check for the cloned files

1. Open a terminal window by using the menu in the editor: Terminal > New Terminal.

2. Change to your project folder.

```
cd /home/project
```

3. Check if you have the folder lkpho-Cloud-applications-with-Node.js-and-React

```
ls /home/project
```

If you do, you can skip to step 5.

4. Clone the git repository that contains the artifacts needed for this lab, if it doesn’t already exist.

```
git clone https://github.com/ibm-developer-skills-network/lkpho-Cloud-applications-with-Node.js-and-React.git
```

5. Change to the directory for this lab.
```
cd lkpho-Cloud-applications-with-Node.js-and-React/CD220Labs/async_callback/
```

6. List the contents of this directory to see the artifacts for this lab.
```
ls
```

## Task 2: Synchronous I/O
In the files explorer view ExampleSyncIO.js. It would appear like this.

``` JavaScript
// Requiring fs module - fs is used for File I/O
let fs = require('fs');

let filename1 = "courseDetails.json"
let filename2 = "sampleData.json"

function readFile1(filename1) {
   // Reading the file Synchronously - Blocking rest of execution
   let data = fs.readFileSync(filename1);
   console.log("\n\nThe content of the file is \n\n"+data);
   console.log("Completed reading file1");
}

function readFile2(filename2) {
   // Reading the file Synchronously - Blocking rest of execution
   let data = fs.readFileSync(filename2);
   console.log("\n\nThe content of the file is \n\n"+data);
   console.log("Completed reading file2");
}

console.log('Before the reading the file-1');
readFile1(filename1);

console.log('Before the reading the file-2');
readFile2(filename2);

console.log('All done!');
```

2. In the terminal window run the server with the following command.

```
node ExampleSyncIO.js
```

Observe that the two files are being read synchronously, one after the other. This will be evident from the order in which the console log appears.

## Task 3: Asynchronous IO
1. In the files explorer view ExampleAsyncIO.js. It would appear like this.

``` JavaScript
// Requiring fs module - fs is used for File I/O
let fs = require('fs');

let filename1 = "courseDetails.json"
let filename2 = "sampleData.json"

// Reading the file Asynchronously - Not blocking rest of execution
function readFile1(filename1) {
    fs.readFile(filename1, (err, data) => {
        if (err) {
            console.log(err);
        } else {
            console.log("\n\nThe content of the file is \n\n"+data);
            console.log("Completed reading file1");
        }
    });
}

function readFile2(filename2) {
    fs.readFile(filename2, (err, data) => {
        if (err) {
            console.log(err);
        } else {
            console.log("\n\nThe content of the file is \n\n"+data);
            console.log("Completed reading file2");
        }
    });
}

console.log('Before the reading the file-1');
readFile1(filename1);

console.log('Before the reading the file-2');
readFile2(filename2);

console.log('All done!');
```

2. In the terminal window run the server with the following command.

```
node ExampleAsyncIO.js
```

Observe that the two files are being read asynchronously. This will be evident from the order in which the console log appears. The following three console log appears before the file content is printed though the logs are called in the code in different order.

```
Before the reading the file-1
Before the reading the file-2
All done!
```

## Task 4: Creating Callback Functions
1.In the files explorer view ExampleAsyncCallBack.js. It would appear like this.

``` JavaScript
//This method will be provided as a parameter
function firstCallBackMethod() {
    console.log("Inside the first call back method")
}

console.log("Going to call setTimeOut with a delay of 5 seconds")
//Call the function firstCallBackMethod after a delay using setTimeOut
setTimeout(firstCallBackMethod,5000);
```

2. In the terminal window run the server with the following command.

```
node ExampleAsyncCallBack.js
```
setTimeout is a built-in library method which allows you to pass a method which needs to be called on timeout, as parameter. Here firstCallBackMethod is defined and then passed as a parameter to setTimeOut. As you may have observed, the method will be called after 5 seconds. This is called <.b>callback.</b>


## Task 5: Promises

1. In the files explorer view asyncPromise.js. It would appear like this.

``` JavaScript
let prompt = require('prompt-sync')();
let fs = require('fs');

const methCall = new Promise((resolve,reject)=>{
    let filename = prompt('What is the name of the file ?');
    try {
      const data = fs.readFileSync(filename, {encoding:'utf8', flag:'r'}); 
      resolve(data);
    } catch(err) {
      reject(err)
    }
});

console.log(methCall);

methCall.then(
  (data) => console.log(data),
  (err) => console.log("Error reading file")
);
```

2. In the terminal window run the following command to install prompt-sync. Using --save ensures that the package.json file is updated for dependencies.

```
npm install --save prompt-sync
```

3. In the terminal window run the server with the following command. It will ask you for a filename. Enter a valid filename from the current directory.

```
node asyncPromise.js
```
methCall here is a promise object. When the promise is full-filled, the console log will be printed. Run the above command again and try to pass an invalid filename. See the console log printed out as the promise is being rejected.

### Task 6: AsyncAxiosRequest

1. In the files explorer view asyncAxiosRequest.js. It would appear like this.

``` JavaScript
const axios = require('axios').default;

const connectToURL = (url)=>{
    const req = axios.get(url);
    console.log(req);
    req.then(resp => {
        console.log("Fulfilled")
        console.log(resp.data);
    })
    .catch(err => {
        console.log("Rejected for url "+url)
        console.log(err.toString())
    });
}
//Valid URL
connectToURL('https://raw.githubusercontent.com/ibm-developer-skills-network/lkpho-Cloud-applications-with-Node.js-and-React/master/CD220Labs/async_callback/sampleData.json');
//Invali URL
connectToURL('https://raw.githubusercontent.com/ibm-developer-skills-network/lkpho-Cloud-applications-with-Node.js-and-React/master/CD220Labs/async_callback/sampleDate.json');
```

2.To run this code, we need to install axios package. Run the following command to install axios.
```
npm install --save axios
```
3. In the terminal window run the code with the following command.
```
node asyncAxiosRequest.js
```

When you run the code, the first connectToURL is an axios request to a valid URL which will return JSON object. The second connectToURL is an axiosRequest to an invalid URL. This will return appropriate error message.

## Task 7: Working with JSON
1. In the files explorer view jsonParse.js. It would appear like this.
``` JavaScript
const axios = require('axios').default;

const req = axios.get("https://raw.githubusercontent.com/ibm-developer-skills-network/lkpho-Cloud-applications-with-Node.js-and-React/master/CD220Labs/async_callback/courseDetails.json");
console.log(req);
req.then(resp => {
    let courseDetails = resp.data;
    console.log(JSON.stringify(courseDetails,null,4))
})
.catch(err => {
    console.log(err.toString())
    //This will console log the error withe the code. eg. Error: Request failed with status code 404
});
```
2. To run this code, we need to install axios package. You will be having the axios module that you installed in the previous exercise. If not, run the following command to install axios.
```
npm install --save axios
```
3. In the terminal window run the code with the following command.
```
node jsonParse.js
```
When you run the code, an axios request is made to a remote URL which returns a JSON object. This JSON object is stringified(or formatted in a readble form) and logged on the console. The output will be as below.

## Summary 
Now that you have have learned how to use Async Callback programming we will go further and extend the capabilities of our server side.