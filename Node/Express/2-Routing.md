# Routing in Express.js 

Routing in Express.js refers to the process of defining different routes in your web application and handling HTTP requests for those routes. Express.js provides a simple and straightforward way to define routes using various HTTP methods (GET, POST, PUT, DELETE, etc.) and URL patterns. This guide will cover everything you need to know about routing in Express.js.

**Basic Routing:**

To create a basic route in Express.js, you can use the `app.METHOD()` functions, where `METHOD` is the HTTP method (e.g., get, post, put, delete, etc.).

```javascript
const express = require('express');
const app = express();

// GET request to the root URL
app.get('/', (req, res) => {
  res.send('Hello, World!');
});

// POST request to /users
app.post('/users', (req, res) => {
  res.send('Creating a new user...');
});

// PUT request to /users/:id
app.put('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`Updating user with ID ${userId}...`);
});

// DELETE request to /users/:id
app.delete('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`Deleting user with ID ${userId}...`);
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

**Route Parameters:**

You can define route parameters in the URL to capture dynamic values from the URL.

```javascript
app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  res.send(`User ID: ${userId}`);
});
```

**Query Parameters:**

You can access query parameters sent in the URL using the `req.query` object.

```javascript
app.get('/search', (req, res) => {
  const query = req.query.q;
  res.send(`Search query: ${query}`);
});
```

**Multiple Route Handlers:**

You can have multiple route handlers for a single route by passing an array of handler functions.

```javascript
const authenticate = (req, res, next) => {
  // Middleware to check authentication
  next();
};

app.get('/secret', authenticate, (req, res) => {
  res.send('Welcome to the secret page!');
});
```

**Route Middleware:**

Middleware functions can be used to perform tasks before the final route handler is executed. Middleware functions have access to the `req` and `res` objects, and they can also modify the request and response objects.

```javascript
const logger = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
};

app.use(logger);
```

**Express Router:**

Express Router allows you to modularize your routes into separate files and then use them in your main application.

```javascript
// usersRouter.js
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => {
  // Handle GET request to /users
});

router.post('/', (req, res) => {
  // Handle POST request to /users
});

module.exports = router;

// app.js
const usersRouter = require('./usersRouter');
app.use('/users', usersRouter);
```

**Error Handling:**

You can handle errors in Express.js using middleware functions that have four parameters (err, req, res, next).

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something went wrong!');
});
```

