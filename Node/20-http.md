**HTTP Module - Complete Documentation**

The `http` module is a core module in Node.js that provides functionality for creating HTTP servers and clients. It allows you to interact with the HTTP protocol, enabling you to build web servers, make HTTP requests, and handle HTTP responses.

**Importing the HTTP Module:**
To use the `http` module, you need to import it first. In Node.js, you can import core modules using the `require()` function:

```javascript
const http = require('Node/20-http');
```

**Creating an HTTP Server:**

1. **`http.createServer([options][, requestListener])`**:
   Creates an HTTP server that invokes the `requestListener` function for each incoming HTTP request.

   Example:
   ```javascript
   const server = http.createServer((req, res) => {
     res.writeHead(200, { 'Content-Type': 'text/plain' });
     res.end('Hello, World!');
   });
   ```

2. **`server.listen(port[, hostname][, backlog][, callback])`**:
   Binds the server to the specified port and hostname. It starts listening for incoming requests.

   Example:
   ```javascript
   const port = 3000;
   const host = 'localhost';

   server.listen(port, host, () => {
     console.log(`Server listening on http://${host}:${port}/`);
   });
   ```

**HTTP Request:**

1. **`http.request(options[, callback])`**:
   Sends an HTTP request to the server specified in the `options`.

   Example:
   ```javascript
   const options = {
     hostname: 'api.example.com',
     path: '/data',
     method: 'GET'
   };

   const req = http.request(options, (res) => {
     console.log(`Status Code: ${res.statusCode}`);
     res.on('data', (chunk) => {
       console.log(`Received data: ${chunk}`);
     });
   });

   req.end();
   ```

**HTTP Response:**

1. **`response.writeHead(statusCode[, statusMessage][, headers])`**:
   Sends an HTTP response header to the request. You can set the status code, status message, and additional headers.

2. **`response.write(chunk[, encoding])`**:
   Sends a part of the response body. This method can be called multiple times to send large responses.

3. **`response.end([data][, encoding][, callback])`**:
   Signals the end of the response. Optionally, you can send the last chunk of data and specify an encoding.

**Common HTTP Server Events:**

- **'request':** Emitted when a new HTTP request is received by the server.

- **'listening':** Emitted when the server starts listening for incoming connections.

- **'close':** Emitted when the server is fully closed and no longer accepts new connections.

- **'error':** Emitted when an error occurs on the server.

**Common HTTP Client Events:**

- **'response':** Emitted when an HTTP response is received from the server.

- **'error':** Emitted when an error occurs during the HTTP request.

**Summary:**
- The `http` module in Node.js provides functionality for creating HTTP servers and clients.
- It allows you to interact with the HTTP protocol, enabling you to build web servers, make HTTP requests, and handle HTTP responses.
- You can import the `http` module using `const http = require('http');`.
- The module provides methods like `createServer` and `request` for creating HTTP servers and making HTTP requests, respectively.
- HTTP servers can be bound to a specific port and hostname using `listen()`, and HTTP clients can send requests using `request()`.

The `http` module is essential for building web applications and making HTTP requests to external servers or APIs. It provides the foundation for handling HTTP communication in Node.js applications, making it possible to build web servers, RESTful APIs, and other HTTP-related functionality.



# HTTP Response Object:**
When handling incoming HTTP requests on the server, the `response` object is an instance of the `http.ServerResponse` class. It represents the server's response to the client's request and provides methods to send the response back to the client.

**Common Methods of HTTP Response:**

1. **`response.writeHead(statusCode[, statusMessage][, headers])`**:
   Sends an HTTP response header to the client. This method must be called before sending any response data. It sets the status code, status message (optional), and additional headers (optional).

   Example:
   ```javascript
   response.writeHead(200, { 'Content-Type': 'text/html' });
   ```

2. **`response.write(chunk[, encoding])`**:
   Sends a part of the response body to the client. This method can be called multiple times to send large responses in chunks.

   Example:
   ```javascript
   response.write('Hello, ');
   response.write('World!');
   ```

3. **`response.end([data][, encoding][, callback])`**:
   Signals the end of the response. Optionally, you can send the last chunk of data to the client. Calling this method is mandatory for the response to be sent to the client. If `data` is provided, it will be sent to the client as the last chunk of the response body.

   Example:
   ```javascript
   response.end();
   ```
   or
   ```javascript
   response.end('Thank you for visiting!');
   ```

**Common HTTP Response Properties:**

- **`response.statusCode`**:
  The HTTP status code that represents the result of the request. Common status codes include 200 (OK), 404 (Not Found), 500 (Internal Server Error), etc.

- **`response.statusMessage`**:
  An optional human-readable status message associated with the `statusCode`.

- **`response.headersSent`**:
  A boolean value indicating whether the response headers have been sent to the client.

**Example of Sending an HTTP Response:**
Here's an example of a simple HTTP server that responds with "Hello, World!" when a request is made:

```javascript
const http = require('Node/20-http');

const server = http.createServer((req, res) => {
   res.writeHead(200, {'Content-Type': 'text/plain'});
   res.write('Hello, ');
   res.end('World!');
});

server.listen(3000, () => {
   console.log('Server listening on port 3000');
});
```

In this example, whenever a client makes an HTTP request to the server, the server responds with a status code of 200 and a plain text "Hello, World!" as the response body.

**Summary:**
- An HTTP response is sent from the server to the client in response to an HTTP request.
- The `response` object in the `http` module represents the server's response to the client.
- The `response` object provides methods like `writeHead`, `write`, and `end` to construct and send the response back to the client.
- The HTTP response contains status codes, headers, and response data, which the client processes.

Handling HTTP responses is a fundamental aspect of building web servers and APIs. The `http` module in Node.js provides the necessary tools to create and customize HTTP responses, enabling you to build powerful and flexible web applications.
