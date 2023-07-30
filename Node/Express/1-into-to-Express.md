**Express.js - Complete Documentation**

Express.js is a popular web application framework for Node.js. It provides a simple and minimalistic API to build web applications and APIs. Express.js is widely used due to its flexibility, extensibility, and ease of use. It allows developers to create robust web applications with a few lines of code.

**Installing Express.js:**

You can install Express.js using npm or yarn:

```bash
npm install express
```

or

```bash
yarn add express
```

**Importing Express.js:**

To use Express.js in your Node.js application, you need to import it as follows:

```javascript
const express = require('express');
const app = express();
```

**Basic Express Application:**

To create a basic Express.js application, you can use the following code:

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

**Routing:**

Express.js allows you to define routes for different HTTP methods (GET, POST, PUT, DELETE, etc.) and URLs. You can handle different routes using `app.get()`, `app.post()`, `app.put()`, `app.delete()`, etc.

```javascript
app.get('/users', (req, res) => {
  // Handle GET request to /users
  // Fetch users data from database and send it as a response
});

app.post('/users', (req, res) => {
  // Handle POST request to /users
  // Create a new user based on request body and send a response
});
```

**Middleware:**

Middleware functions are functions that have access to the request and response objects and can perform tasks before the final request handler is executed. Middleware functions can be used for authentication, logging, error handling, and more.

```javascript
// Custom middleware function
const logger = (req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
};

app.use(logger);
```

**Static Files:**

You can serve static files, such as CSS, images, and JavaScript, using the built-in `express.static()` middleware.

```javascript
app.use(express.static('public'));
```

**Request and Response:**

In Express.js, the `req` object represents the HTTP request, and the `res` object represents the HTTP response.

```javascript
app.get('/hello', (req, res) => {
  const name = req.query.name || 'Guest';
  res.send(`Hello, ${name}!`);
});
```

**Views and Templating Engines:**

Express.js supports rendering dynamic views using templating engines like EJS, Pug (formerly Jade), Handlebars, etc.

```javascript
// Using EJS templating engine
app.set('view engine', 'ejs');

app.get('/users/:id', (req, res) => {
  const userId = req.params.id;
  const user = // Fetch user data based on userId from database
  res.render('user', { user });
});
```

**Error Handling:**

You can handle errors in Express.js using middleware functions that have four parameters (err, req, res, next).

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something went wrong!');
});
```

**Express Router:**

You can modularize your routes using the Express Router.

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

**Summary:**
- Express.js is a popular web application framework for Node.js.
- You can install Express.js using npm or yarn and import it in your application.
- Express.js provides simple routing, middleware, request and response handling, static file serving, and support for templating engines.
- Middleware functions can be used for tasks like authentication, logging, and error handling.
- Express Router allows you to modularize your routes.

Express.js is widely used for building web applications and APIs due to its simplicity, flexibility, and strong community support. It simplifies the process of handling HTTP requests and responses and allows developers to create powerful and scalable web applications with ease.
