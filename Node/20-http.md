# HTTP 
## introduction

HTTP stands for Hypertext Transfer Protocol, and it is an application layer protocol that is predominantly used with the WWW (World Wide Web) in the client-server architecture, where a web browser is a client interacting with the webserver that is hosting the website.

An HTTP server is a computer program or a software component of another program that acts as a server in a client-server model by implementing the server portion of the HTTP and/or HTTPS network protocols.

An HTTP server waits for incoming client requests and responds to each one by returning desired information, including the delivery of the requested web page, or by returning an HTTP error message.

To support program-to-program communications, an HTTP server may also contain bindings to manage protocol extensions to HTTP or messages of other protocols enveloped in HTTP messages.

The HTTP or web server processes HTTP requests, which is a network protocol used to communicate data on the World Wide Web (WWW). An HTTP server's primary duty is to store, process, and distribute web pages to clients. Pages are often given as HTML documents that may include graphics, style sheets, and scripts in addition to text content. You explain how a page should look, what fonts to use, what color the text should be, where paragraph marks should appear, and many other features of the content using HTML.

## Creating a Basic HTTP Server
Now let’s start by building a server that returns plain text to the user. This will cover the fundamental concepts required to build up a server, which will lay the groundwork for returning more complicated data types.

You need to have Node.js installed in your system. You can easily install Node.js with the help of the installer provided on the official Node.js website.

Next, create a directory for this project and name it node-http-server. You can use the following command for this task:
```javascript
mkdir node-http-server
```

Then switch to that folder :

```cd node-http-server```

Now create a file server.js in which you will be writing the code.


In the file write the code as we discuss below.

First load the http module which is a core Node.js module and hence doesn't require installation. Add the following line to server.js :

```javascript
const http = require("http");
```

The http module has the required functions for creating the server. Now create two constants two stores of the value of the hostname and the port:

```javascript
const host = 'localhost';
const port = 8000;

```
Web servers, as previously stated, accept requests from browsers and other clients. We can communicate with a web server by entering a domain name, which a DNS server converts to an IP address. An IP address is a unique sequence of characters that identifies a computer on a network such as the internet.

The localhost is a private address used by computers to refer to themselves. It is equivalent to the internal IP address 127.0.0.1 and is only accessible to the local computer and not to any local networks connected or to the internet.

The port is a number that servers use to connect to a specific process on our IP address as an endpoint or door. In this example, we will run our web server on port 8000. Ports 8080 and 8000 are commonly used as default ports in development, and most developers will use them for HTTP servers rather than other ports. The server is bound to the host and port, and hence you will be able to access it on http://localhost:8000.

Create a function requestListener to handle the incoming requests. This function requires two parameters: a request object and a response object. The request object stores all of the data from the incoming HTTP request. The response object is responsible for returning HTTP responses to the server, and it contains all the details about the response.

```javascript
const requestListener = function (req, res) {
res.writeHead(200)
res.end('Welcome user!!')
}
```

The function will return Welcome user!! as a response to the client.

In Node.js, all request listener functions take two arguments: req and res . The user's HTTP request is stored in the Request object (req) which is the first argument. We generate the HTTP response that we return to the user by modifying the Response object (res) in the second argument.

The first line of code, res.writeHead(200), specifies the HTTP status code of the response. HTTP status codes represent how well a server handled an HTTP request. The status code 200 corresponds to OK in this instance. The function's next line, res.end("Welcome user!!"), returns the HTTP response to the client who requested it. This function returns any data to be sent from the server. It is returning text data in this case.

Now add the following code in the file to create the server :

```javascript
const server = http.createServer(requestListener)
server.listen(port, host, () => {
console.log(`Server is running on http://${host}:${port}`)
})
```

First, the server object is created using the createServer() function. The server object accepts all the requests and passes them to the requestListener() function. The server is then attached to the port and host using the server.listen to () function. The listen to () function takes the port, host and the callback function as arguments. The callback function is called when the server begins to listen.

Now your final code in the file should be :

Example :

```javascript
const http = require('http')

const host = 'localhost'
const port = 8000

const requestListener = function (req, res) {
res.writeHead(200)
res.end('Welcome user!!')
}

const server = http.createServer(requestListener)
server.listen(port, host, () => {
console.log(`Server is running on http://${host}:${port}`)
})
```
```javascript
The server is running on http://localhost:8000
```


You have now set up your server. We used a browser to send a GET request to the server at http://localhost:8000. Our Node.js server was monitoring connections on this address. The request was passed to the requestListener() function by the server. With the status code 200, the method returned text data. After that, the server returned the response to the browser, which displayed the message.

You can use CTRL+C to shut down the server.

## Returning Different Types of Content
The format of the response we receive from a web server can vary. Text formats like JSON, CSV, XML, and HTML can be easily returned. Other than these, non-text data such as PDFs, compressed files, audio, and video can be returned by web servers. JSON, CSV, and HTML are all text-based data types. They are prominent web content delivery types. Many server-side development languages and tools enable returning these various data kinds.

In Node.js, you need to do the following two things :

Set the suitable value for the Content-Type header in your HTTP responses.
Check that res.end() receives the data in the correct format.
You will be making changes mostly in the requestListener to return different content types.


## Serving JSON
JavaScript Object Notation, or JSON for short, is a text-based data transmission standard. It is derived from JavaScript objects, as the name implies, but it is language-independent, which means it may be used by any programming language that can parse its syntax.

APIs frequently utilize JSON to accept and return data. Its popularity comes from its smaller data transfer size over previous data interchange formats, such as XML, as well as the availability of technology that allows applications to parse it with minimal effort.

Now to serve JSON, make the following changes to the requestListener:

```javascript
const requestListener = function (req, res) {
res.setHeader('Content-Type', 'application/json')
res.writeHead(200)
res.end(`{"message": "greeting", "value": "Hello user!!"}`)
}
```

The method res.setHeader() inserts an HTTP header to the response. HTTP headers are used to include additional information to request or respond. The res.setHeader() requires two parameters: the name and value of the header.

The Content-Type header is used to specify the data format or the media type, that is transmitted with the request or response. Our Content-Type in this example is application/json.

Now your code will become :

```javascript
const http = require('http')

const host = 'localhost'
const port = 8000

const requestListener = function (req, res) {
res.setHeader('Content-Type', 'application/json')
res.writeHead(200)
res.end(`{"message": "greeting", "value": "Hello user!!"}`)
}

const server = http.createServer(requestListener)
server.listen(port, host, () => {
console.log(`Server is running on http://${host}:${port}`)
})
```


```javascript
{ "message": "greeting", "value": "Hello user!!" }
```

## Serving CSV
The Comma Separated Values (CSV) file format is a text standard used to provide tabular data. Generally, in a CSV file, a newline separates each row, and a comma separates each item in the row.

In the case of a CSV file, the browser downloads the file automatically.

Make the following changes to the requestListener:

```javascript
const requestListener = function (req, res) {
res.setHeader('Content-Type', 'text/csv')
res.setHeader('Content-Disposition', 'attachment;filename=users.csv')
res.writeHead(200)
res.end(`id,name,email\n1,John Doe,john@gmail.com`)
}
```

The Content-Type shows that a CSV file is being sent this time, as the value is text/csv. Content-Disposition is the second header that is added. This header instructs the browser on how to display the data, whether in the browser or a separate file.

Even if the Content-Disposition header is not set most browsers download the file in the case of CSV. The header should be included as it allows us to set the name of the file that will be downloaded at the user's end. In this case, the name will be users.csv.

Now your complete code must be like this :

Example :

```javascript
const http = require('http')

const host = 'localhost'
const port = 8000

const requestListener = function (req, res) {
res.setHeader('Content-Type', 'text/csv')
res.setHeader('Content-Disposition', 'attachment;filename=users.csv')
res.writeHead(200)
res.end(`id,name,email\n1,John Doe,john@gmail.com`)
}

const server = http.createServer(requestListener)
server.listen(port, host, () => {
console.log(`Server is running on http://${host}:${port}`)
})
```

On running the code your browser will download the file users.csv if you visit the http://localhost:8000.

The file will have the following contents when opened using a text editor :

id, name,email
1, John Doe,john@gmail.com
Serving HTML
When we want users to communicate with our server via a web browser, we typically utilize HTML or HyperText Markup Language. Web browsers are designed to show HTML text as well as any CSS styles we add to our websites. CSS is another front-end web technology that allows us to modify the look of our websites.

Make the following changes to the requestListener:

```javascript
const requestListener = function (req, res) {
res.setHeader('Content-Type', 'text/html')
res.writeHead(200)
res.end(`<html><body><p>This is an HTML page.</p></body></html>`)
}
```

First, we include the HTTP status code. Then, using a string argument containing valid HTML, we call the response.end() function. When we use the browser to connect to our server, we will see an HTML page with one paragraph tag that says This is an HTML page.

Now your complete code must be like this :

Example :
```javascript
const http = require('http')

const host = 'localhost'
const port = 8000

const requestListener = function (req, res) {
res.setHeader('Content-Type', 'text/html')
res.writeHead(200)
res.end(`<html><body><p>This is an HTML page.</p></body></html>`)
}

const server = http.createServer(requestListener)
server.listen(port, host, () => {
console.log(`Server is running on http://${host}:${port}`)
})

```
On running the code your browser will display the following on http://localhost:8000.

This is an HTML page.

## Serving HTML Page from a File
we can also serve an html page from a file as the response. We utilize the fs module to load the HTML file and use its data while generating our HTTP response to deliver HTML files.

Consider the case of a sample HTML page hello.html that needs to be displayed.

```jsx
<!DOCTYPE html>
<html>
    <head>
    </head>
    <body>
        <H1> This is an HTML page with predefined contents </H1>
    </body>
</html>
```

We must now read the file before we can import it, which is accomplished with the help of the fs module.

```javascript
const http = require('http')
const fs = require('fs')
```

A function called readFile() is available in the fs module and is typically used to load HTML files. We import the promised variation of the call to stay current with contemporary JavaScript conventions. Additionally, in many situations, it is superior to callbacks.

After updating the running js file with this information, we must return the page using it.

Example :

```javascript
const requestListener = function (req, res) {
fs.readFile(__dirname + '/hello.html')
.then((contents) => {
res.setHeader('Content-Type', 'text/html')
res.writeHead(200)
res.end(contents)
})
.catch((err) => {
res.writeHead(500)
res.end(err)
return
})
}
```

Here, the file is loaded using the fs.readFile() method. __dirname and /samplePage.html are its two inputs. The absolute path, where Node.js code is now being executed, is represented here by the variable __dirname. To load the HTML file we want to serve, we can then add /samplePage.html to this route.

The data will be returned once the fs.readFile() promise has been successfully resolved. Then, to handle this follow-up situation, we use the then() method. The HTML file's real data is located in the contents parameter.

Handle Routes by HTTP Request Object
The majority of websites and APIs that we visit or use typically have many url endpoints so that we can access the various resources that are offered on the same platform. An inventory management scenario, such as one that might be employed in a warehouse, is a typical example.

To handle requests whose URL contains other destinations, we have not yet implemented any extra routing logic inside the requestListener() function.

In the following example, we will be constructing a new server for a simple inventory system, which can return 2 different sorts of data.

Server’s address endpoint at:

/manufacturers will provide a list of manufacturers' information in JSON.
/items will provide a list of items with their respective quantities in JSON.
Let's take two variables:

The items variable is a string containing JSON for a collection of item objects.
The manufacturers is a string containing the JSON for an array of manufacturer objects.
We will receive that in response now that we have included the data in the responses. To do that, we must edit the requestListener() function. However, before we can do that, we must make sure that every server answer contains the appropriate Content-Type header, in this case, a JSON header. The correct JSON must then be returned based on the user's chosen URL route. We must access the property 'url' in the request object to obtain a URL path. We may build the following switch statement on the request's URL based on this differentiator :

Example :

```javascript
const requestListener = function (req, res) {
res.setHeader('Content-Type', 'application/json')
switch (req.url) {
case '/items':
res.writeHead(200)
res.end(items)
break
case '/manufacturers':
res.writeHead(200)
res.end(manufacturers)
break
default:
res.writeHead(404)
res.end(JSON.stringify({ error: 'Resource not found' }))
}
}
```

Similar to what we did earlier when a call is successful, we set the response code to 200 and return the JSON. An error for the same can be denoted by the Default case. Here, the meaning of 404, which means resource not found, is clearer.


## Listening and Handling Connections
The server.listen() is a built-in application programming interface of the Socket class that is within the tls module that is used to start the server and listen for encrypted connections. It is used to accept connections on the specified port and host. If the hostname is not specified, the server will accept connections to any IPv4 address (INADDR ANY). A port value of zero generates a random port.

Syntax:

```javascript
const server.listen([port[, host[, backlog]]][, callback])

```
Parameters: This method takes the following arguments as parameters.

host: It is the IP address we want to listen to.
port: The port number on which the server will listen.
Return Value: This method returns a callback function.
Here is an example of the server.listen(). To run the code on your system you need to generate a pair of public and private keys. You can generate them using online tools or using openssl commands.

```javascript
// The use of server.listen() method.

var tls = require("tls"),
fs = require("fs"),
// Port and host address for server
PORT = 8000,
HOST = "127.0.0.1",
value = null;

// Private key and public certificate for access
var options = {
key: fs.readFileSync("private-key.pem"),
cert: fs.readFileSync("public-cert.pem"),
rejectUnauthorized: false,
};

// Creating and initializing server
var server = tls.createServer(options, function (socket) {
// Print the data that we received on the server
socket.on("data", function (data) {
console.log("\nReceived: %s ", data.toString());
});

// Stopping the server
// by using the close() method
server.close();
});

// Getting session key
// by using getTicketKeys() method
value = server.getTicketKeys();

// Start listening on a specific port and address
// by using listen() method
server.listen(PORT, HOST, function () {
console.log("I'm listening at %s, on port %s", HOST, PORT);
});

// Creating and initializing client
var client = tls.connect(PORT, HOST, options, function () {
client.write("Session key : " + value[0]);
client.end();
});

```
In the above code snippet, a server has been created using the createServer() method, and the listen() method is used to specify the host and the port number. A TLS client is created. AS TLS relies on public key infrastructure (PKI) to enable secure communication between a client and a server, hence the use of a public certificate and a private key is done. The client gets a session key from the server. You will receive the output similar to the following : I'm listening at 127.0.0.1, on port 8000

Received: Session key : 93

HTTP Request Parsing
The extra details you want to send to the server are kept in the request body. Because it specifies the information one intends to send, the body is crucial. The request body can be used to hold user data, such as a user's username and password when they attempt to log into our system.

Node.js utilizes streams to read data because it reads data in chunks. We can use the requested data after the node has finished reading it for our purposes. The request body of a POST or PUT request could be significant to your application. It takes a little more work to get the body data than it does to retrieve the request headers. The ReadableStream interface is implemented by the request object that is delivered to a handler. Like any other stream, this one can be listened to or piped to another location. By paying attention to the stream's data and end events, we can take the data directly out of the stream.

So you can create an array first in which you can store all the chunks of the request body. For this, you need to create a .on handler for the data to get every chunk.
```javascript
const requestBody = [];
req.on(‘data’, (chunks)=>{
requestBody.push(chunks);
});

```
The incoming http request has a data event bound to it. Data will continue to stream from this event and be pushed to the requestBody variable.

Combine all the request body chunks appended in the array.

When the receiving of data is finished, we will transform it to a string with the use of the end event.

```javascript
req.on(‘end’, ()=>{
const parsedData = Buffer.concat(requestBody).toString();
});
```

The request parameters are returned to us as key-value pairs. To save or make use of the values, we must divide it. We can split the string to get the value.

```javascript
const name = parsedData.split(‘=’)[1];
```

Write the following code in a file server.js :

```javascript
const http = require("http");
const PORT = 8000;

const server = http.createServer((req, res) => {
const url = req.url;
if (url === "/") {

    res.write('<html><head> <title> Parsing Request Body </title> </head><body> <form action="/name" method="POST"> Enter your name: <input type="text" name="name" /><button type="submit">Submit</button> </body></html>');
    
    return res.end();
}
if (url === "/name" && req.method === "POST") {
const requestBody = [];

    req.on("data", (chunk) => {
      requestBody.push(chunk);
    });
 
    req.on("end", () => {
      const parsedData = Buffer.concat(requestBody).toString();
      console.log("Parsed data:", parsedData);
      const username = parsedData.split("=")[1];
      console.log("Username:", username);
    });
    //redirect the client
    res.statusCode = 302;
    res.setHeader("Location", "/");
    return res.end();
}
// For some other url or request type.
res.write("<html>");
res.write("<head> <title> Parsing Request Body </title> </head>");
res.write(" <body> Hello </body>");
res.write("</html>");
res.end();
});
server.listen(PORT, () => {
console.log("Server listening on PORT :", PORT);
});

```
In the above code snippet, first, the http module has been imported. The PORT is set as 8000.

Then the createServer() method is used to create a server. The incoming request’s URL is checked. If the URL is / then an HTML file is served to contain a form. In the form, the user can enter his name and submit it. Submitting the form creates a POST request to the /name endpoint. .on() listeners for data are used to get the body chunks. .on() for the end event concatenates all the chunks and forms a string. The string is broken and the name of the user is stored in the username variable. For any other endpoint HTML with a hello is sent.

Now, as you have seen how to create an HTTP server and how to parse the body of an HTTP request, let us now create a simple application using an HTTP server. We will create a simple application in which one can create simple posts.

The first step is to create an HTTP server. So create a file server.js. Create the server by calling the createServer() function on the HTTP module after requiring it. The server object that these function returns allows us to select the port on which the server should listen for requests using a method called listen.

The requestListener() function that manages requests and responses is the only argument required by the createServer function. With the help of this callback function, we can use the asynchronous event-driven architecture in Node to process requests as they come in and continue running other code while we wait for a request without blocking.

```javascript
const http = require("http");
const port = process.env.PORT || 8000;
const html = `<header><h1>Welcome to Server</h1></header>`;

const server = http.createServer(function (req, res) {
res.writeHead(200, { "Content-Type": "text/html" });
res.write(html);
res.end();
});

server.listen(port, () => {
console.log(`App running on port ${port}`);
});

```
With the code shown above, an HTTP server will be created that will be listening on port 8000 and will have a response defined for all incoming requests. The request URL value is stored in the req object's url property, therefore a request made to http://localhost:8000 would have the value / in it. An HTTP status code and headers for a response are defined by the writeHead method on the response object. We then include some HTML in the response before concluding it with res.end().

We have created a simple server till now. Now we need to create an html file that we will send as a response. The HTML file will contain the form through which users will provide the data for the post. So create a file index.html and write the following code in it.

```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Node.js Application</title>
  </head>
  <body>
    <h1>Create A Post</h1>
    <form
      action="/post"
      method="POST"
      style="display: flex; flex-direction: column; max-width: 30ch"
    >
      <label for="name">Name</label>
      <input
        type="text"
        name="name"
        id="name"
        placeholder="Enter name..."
      /><br />
      <label for="postData">Post Data</label>
      <textarea
        name="postData"
        id="postData"
        rows="40"
        cols="10"
        style="resize: vertical; height: 8rem"
        placeholder="Enter post Data..."
      ></textarea
      ><br />
      <button type="submit">Submit</button>
    </form>
  </body>
</html>

```
The HTML file contains a form with two fields: a name and a postData field. Now we need to modify the server.js file to serve the index.html file. So now make the changes in the server.js file as in the following code :

```javascript
const http = require("http");
const fs = require("fs");

const port = process.env.PORT || 8000;

const server = http.createServer(function (req, res) {
console.log(`Request received for '${req.url}'`);
fs.readFile(__dirname + "/index.html", function (err, data) {
if (err) {
res.writeHead(404);
res.end(JSON.stringify(err));
return;
}
res.writeHead(200, { "Content-Type": "text/html" });
res.end(data);
});
});

server.listen(port, () => {
console.log(`App running on port ${port}`);
});
```

The above code will serve the currently selected directory's index.html file. The __dirname is an environment variable that gives the absolute path of the currently executing file.

In the above example res.end() is used to send the response data. Alternatively, you could use the same result by first using res.send(data) or res.write(data), then res.end(). The .send() method, which has the syntax .send([body]), sends the HTTP response, and the body parameter accepts one of the following values: a Buffer object, a String, an object, or an array. The response process will be ended by the .end() method.

The HTML page shown above will be returned as the response when you send a request to the / route on the HTTP server we built. Every path accessed on the server will return the same result because we haven't set up any routing.

The application we are creating will have two endpoints only: one / for serving the form page and one /post for POST requests where form data will be handled. So now create a file handlers.js where we will be keeping the logic for both endpoints. Write the following code in the handlers.js file.

Example:

```javascript
const fs = require("fs");

function home(req, res) {
console.log("Executing 'home' handler");
fs.readFile(__dirname + "/index.html", function (err, data) {
if (err) {
res.writeHead(404);
res.end(JSON.stringify(err));
return;
}
res.writeHead(200, { "Content-Type": "text/html" });
res.end(data);
});
}

function post(req, res) {
console.log("Executing 'post' handler");
let payload = "";

req.on("data", (chunk) => {
payload += chunk;
});

req.on("end", () => {
let query = new URLSearchParams(payload);
let data = {
name: query.get("name"),
postData: query.get("postData"),
};
console.log("Data:", data);
res.writeHead(200, { "Content-Type": "application/json" });
res.write(JSON.stringify(data));
res.end();
});
}

module.exports = {
home,
post,
};
```

In the above code snippet, we have two functions one having the logic for the home page and one having the logic for the post endpoint. The home method uses the same implementation as in displaying the response to read a file's contents and serve them. The post function is an endpoint that shows the form submission from the home page on /post after receiving a POST request from the form submission. The action attribute of the form element equals /post, which indicates that when the form is submitted then the page gets forwarded to http://localhost:8000/post.

In the post method the .on() listener for the data event is used to form a string of request body. This string is similar to the query string of a URL. The query string used to represent the form data is delivered to the server as the post body when a form is submitted.

We can utilize URLSearchParams now that the URLSearchParams interface is available. To extract the values from the query string, the .get() is used. In the end, an object with the name and data is sent as a response.

Now you need to make changes in the server.js file to introduce the routing of requests to the correct handler. The primary responsibility of the router is to "route" requests to a specified handler, who subsequently sends a response. So make the changes in the server.js file as n the below code :

```javascript
const http = require("http");
const { home, post } = require("./handlers");

const port = process.env.PORT || 8000;

const requestListener = (req, res) => {
const url = req.url;
console.log(`Request received for '${url}'`);

switch (url) {
case "/":
home(req, res);
break;
case "/post":
post(req, res);
break;
default:
res.writeHead(404);
res.end(`No handler found for '${url}'`);
break;
}
};

const server = http.createServer(requestListener);

server.listen(port, () => {
console.log(`App running on port ${port}`);
});

```
In the above code, the two handlers have been imported. A requestListener function is created. All the code related to routing is written in the requestListener function. A switch statement has been used. For the / path the home() function has been called. Similarly for /post, the post() function has been called. For all the other cases a message has been returned.

The requestListener function is passed in the createServer() function. Now the App is functional. Use the below command to run the server :

$ node server

You will get the following output in the terminal :

App running on port 8000

Now open http://localhost:8000/ in any browser. You must see the following screen:

output requestlistener function

Enter some data and press submit. Now the url will change to http://localhost:8000/post and you will see the following output :

output after entering data

Also in the terminal, the following logs will appear :

```javascript
Request received for '/'
Executing 'home' handler
Request received for '/post'
Executing 'post' handler
Data: { name: 'John Doe', postData: 'Sample Data' }
```

Hence, our application is functional and the use of an HTTP server is being made.
