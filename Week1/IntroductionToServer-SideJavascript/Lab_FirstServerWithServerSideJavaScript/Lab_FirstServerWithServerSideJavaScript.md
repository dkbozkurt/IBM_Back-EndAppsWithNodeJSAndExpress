## Objective for Exercise:

= Use the terminal to git clone and get Node.JS server code

= Create a web server using Server side Java script

= Run the server

= Access the server from the client and get a response from server

## Step 1: Verify Environment and Command-line tools

Verify that node CLI is installed.

```
node --version
```

Change to your project folder.

```
cd /home/project
```

Clone the git repository that contains the artifacts needed for this lab, if it doesn’t already exist.

```
git clone https://github.com/ibm-developer-skills-network/lkpho-Cloud-applications-with-Node.js-and-React.git
```

Change to the directory for this lab.

```
cd lkpho-Cloud-applications-with-Node.js-and-React/CD220Labs/http_server
```
List the contents of this directory to see the artifacts for this lab.

```
ls
```

Check the content of index.js. This is the server side script we will run in the next section.

```
cat index.js
```

You should see output similar to this.
```JavaScript
const http = require('http');

const requestListener = function (req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}

const port = 8080;
const server = http.createServer(requestListener);
console.log('server listening on port: ' + port);
```

## Step 2: Use the node CLI

In order to start the server, we run the index.js file with the node command.

```
node index.js
```

You should see output similar to this.

```
server listening on port: 8080
```

To split the terminal, click <b>Terminal > Split Terminal</b>.

In the second terminal window, use the curl command to ping the application.

```
curl localhost:8080
```

You should see output similar to this.
```
Hello, World!
```

<b>It should indicate that your app is up and running.</b>

### Step 3: Use the node CLI to run server script which requires another module

In the same terminal, check the content of today.js.
```
cat today.js
```

Check the content of index-with-require.js. As you will observe, this script requires the module today whose content we saw in the previous step.
```
cat index-with-require.js
```

In order to start the server, we run the index-with-require.js file with the node command.

```
node index-with-require.js
```

You should see output similar to this.

```
server listening on port: 8080
```

In the second terminal window which you opened earlier, use the curl command to ping the application.

```
curl localhost:8080
```

You should see output similar to this.

```
Hello, World! The date today is Wed Oct 14 2020 14:56:42 GMT+1030 (Australian Eastern Standard Time)
```

<b>It should indicate that your app is up and running.</b>

### Challenge:

Make changes in challenge-index-with-require.js to greet the user depending on the time of the day.

