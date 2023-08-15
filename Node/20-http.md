# HTTP 
## introduction

HTTP stands for Hypertext Transfer Protocol, and it is an application layer protocol that is predominantly used with the WWW (World Wide Web) in the client-server architecture, where a web browser is a client interacting with the webserver that is hosting the website.

An HTTP server is a computer program or a software component of another program that acts as a server in a client-server model by implementing the server portion of the HTTP and/or HTTPS network protocols.

An HTTP server waits for incoming client requests and responds to each one by returning desired information, including the delivery of the requested web page, or by returning an HTTP error message.

To support program-to-program communications, an HTTP server may also contain bindings to manage protocol extensions to HTTP or messages of other protocols enveloped in HTTP messages.

The HTTP or web server processes HTTP requests, which is a network protocol used to communicate data on the World Wide Web (WWW). An HTTP server's primary duty is to store, process, and distribute web pages to clients. Pages are often given as HTML documents that may include graphics, style sheets, and scripts in addition to text content. You explain how a page should look, what fonts to use, what color the text should be, where paragraph marks should appear, and many other features of the content using HTML.

## Creating a Basic HTTP Server
Now let’s start by building a server that returns plain text to the user. This will cover the fundamental concepts required to build up a server, which will lay the groundwork for returning more complicated data types.

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

```javascript
id, name,email
1, John Doe,john@gmail.com

```

## Serving HTML

When we want users to communicate with our server via a web browser, we typically utilize HTML or HyperText Markup Language. Web browsers are designed to show HTML text as well as any CSS styles we add to our websites. CSS is another front-end web technology that allows us to modify the look of our websites.

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

## Handle Routes by HTTP Request Object
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
```javascript
Request received for '/'
Executing 'home' handler
Request received for '/post'
Executing 'post' handler
Data: { name: 'John Doe', postData: 'Sample Data' }
```

