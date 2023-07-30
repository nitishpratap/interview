# Cluster Module - Complete Documentation**

The `cluster` module is a core module in Node.js that allows you to create multiple child processes (workers) that share the same server port. It is a way to take advantage of multi-core systems and improve the performance and scalability of your Node.js applications by distributing the workload across multiple processes.

**Importing the Cluster Module:**
To use the `cluster` module, you need to import it first. In Node.js, you can import core modules using the `require()` function:

```javascript
const cluster = require('Node/21-cluster');
```

**Cluster Properties:**

1. **`cluster.isMaster`**:
   A boolean value that indicates whether the current process is the master process (`true`) or a worker process (`false`).

2. **`cluster.isWorker`**:
   A boolean value that indicates whether the current process is a worker process (`true`) or the master process (`false`).

**Cluster Methods:**

1. **`cluster.setupMaster([settings])`**:
   Sets up the master process before it forks any worker processes. It can be used to define settings for the master process, such as the number of workers to fork.

   Example:
   ```javascript
   cluster.setupMaster({
     exec: 'worker.js',
     args: ['--use', 'https'],
     silent: true
   });
   ```

2. **`cluster.fork([env])`**:
   Forks a new worker process from the master process. The `env` parameter is an object that can be used to set environment variables for the worker.

   Example:
   ```javascript
   cluster.fork({ ENV_VAR: 'production' });
   ```

3. **`cluster.disconnect([callback])`**:
   Disconnects the master from the workers. The `callback` function is called once all workers have been disconnected.

   Example:
   ```javascript
   cluster.disconnect(() => {
     console.log('Master has disconnected from all workers.');
   });
   ```

**Cluster Events:**

1. **'online':** Emitted when a new worker is forked and is now online.

2. **'exit':** Emitted when a worker has exited. The event provides information about the exit code and reason for the exit.

**Example of Using Cluster:**
Here's an example of using the `cluster` module to create a simple HTTP server that utilizes multiple worker processes:

```javascript
const cluster = require('Node/21-cluster');
const http = require('Node/20-http');
const numCPUs = require('Node/15-os').cpus().length;

if (cluster.isMaster) {
   console.log(`Master process PID: ${process.pid}`);

   // Fork workers
   for (let i = 0; i < numCPUs; i++) {
      cluster.fork();
   }

   // Handle worker exit
   cluster.on('exit', (worker, code, signal) => {
      console.log(`Worker ${worker.process.pid} died with code ${code} and signal ${signal}`);
      // Fork a new worker if one exits
      cluster.fork();
   });
} else {
   // Worker process: create HTTP server
   http.createServer((req, res) => {
      res.writeHead(200);
      res.end('Hello, World!');
   }).listen(3000, () => {
      console.log(`Worker process PID: ${process.pid}`);
   });
}
```

In this example, the master process forks as many worker processes as there are CPU cores on the system. Each worker runs an HTTP server on port 3000, and the workload is distributed among the workers.

**Summary:**
- The `cluster` module in Node.js allows you to create multiple child processes (workers) that share the same server port.
- It improves performance and scalability by utilizing multiple cores on multi-core systems.
- You can import the `cluster` module using `const cluster = require('cluster');`.
- The module provides properties like `isMaster` and `isWorker` to identify the current process type.
- The module provides methods like `setupMaster`, `fork`, and `disconnect` for managing the cluster of workers.
- The `cluster` module emits events like 'online' and 'exit' for worker management.

The `cluster` module is useful for building high-performance web servers and scalable applications by leveraging the power of multiple cores. It simplifies the process of creating and managing multiple worker processes, making it easier to take advantage of multi-core systems in Node.js applications.
