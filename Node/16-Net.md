# net Module 

The `net` module is a core module in Node.js that provides an API for creating TCP (Transmission Control Protocol) servers and clients. It allows you to implement networking applications that communicate over TCP, which is a widely used network protocol for reliable and connection-oriented communication.

**Importing the net Module:**
To use the `net` module, you need to import it first. In Node.js, you can import core modules using the `require()` function:

```javascript
const net = require('Node/16-Net');
```

**TCP Server:**

1. **Creating a TCP Server:**
   To create a TCP server, use the `net.createServer()` method:

   ```javascript
   const server = net.createServer((socket) => {
     // 'socket' represents the connection between the server and the client
     console.log('Client connected!');
   });
   ```

2. **Listening for Connections:**
   To start listening for incoming connections, use the `server.listen()` method:

   ```javascript
   const port = 3000;
   const host = 'localhost';

   server.listen(port, host, () => {
     console.log(`Server listening on ${host}:${port}`);
   });
   ```

3. **Handling Incoming Data:**
   To handle data received from clients, listen for the 'data' event on the socket:

   ```javascript
   server.on('connection', (socket) => {
     socket.on('data', (data) => {
       console.log(`Received data from client: ${data}`);
     });
   });
   ```

**TCP Client:**

1. **Creating a TCP Client:**
   To create a TCP client, use the `net.createConnection()` method:

   ```javascript
   const client = net.createConnection({ port: 3000, host: 'localhost' }, () => {
     console.log('Connected to server!');
   });
   ```

2. **Sending Data to the Server:**
   To send data to the server, use the `write()` method on the client socket:

   ```javascript
   client.write('Hello, server!');
   ```

3. **Handling Incoming Data from Server:**
   To handle data received from the server, listen for the 'data' event on the client socket:

   ```javascript
   client.on('data', (data) => {
     console.log(`Received data from server: ${data}`);
   });
   ```

**Common TCP Server Events:**

- **'listening':** Emitted when the server starts listening for connections.

- **'connection':** Emitted when a new connection is established with a client. The callback function receives the client socket as an argument.

- **'close':** Emitted when the server is fully closed and no longer accepts new connections.

- **'error':** Emitted when an error occurs on the server.

**Common TCP Client Events:**

- **'connect':** Emitted when the client successfully connects to the server.

- **'data':** Emitted when data is received from the server.

- **'end':** Emitted when the server sends a FIN packet, indicating the end of data transmission.

- **'close':** Emitted when the client's connection to the server is fully closed.

- **'error':** Emitted when an error occurs on the client.

**Summary:**
- The `net` module in Node.js provides an API for creating TCP servers and clients.
- TCP servers can be created using `net.createServer()` and listening for connections using `server.listen()`.
- TCP clients can be created using `net.createConnection()`.
- TCP servers and clients can exchange data using the `socket.write()` method and listening for the 'data' event.
- TCP servers emit events like 'listening', 'connection', 'close', and 'error'.
- TCP clients emit events like 'connect', 'data', 'end', 'close', and 'error'.

The `net` module allows you to implement TCP-based networking applications in Node.js. It is commonly used for building server-client architectures and network communication where reliable, connection-oriented communication is required.

## Creating a server

```jsx
const net = require('Node/16-Net');

const port = 3000;
const host = 'localhost';

// Create a TCP server
const server = net.createServer((socket) => {
   // 'socket' represents the connection between the server and the client

   console.log('Client connected!');

   // Handle data received from clients
   socket.on('data', (data) => {
      console.log(`Received data from client: ${data}`);

      // Echo back the received data to the client
      socket.write(`Server echoing back: ${data}`);
   });

   // Handle client disconnection
   socket.on('end', () => {
      console.log('Client disconnected!');
   });

   // Handle errors on the socket
   socket.on('error', (err) => {
      console.error('Socket error:', err.message);
   });
});

// Start listening for connections
server.listen(port, host, () => {
   console.log(`Server listening on ${host}:${port}`);
});

// Handle server startup errors
server.on('error', (err) => {
   console.error('Server error:', err.message);
});

```

```jsx
node server.js
```
