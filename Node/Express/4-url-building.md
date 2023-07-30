In Express.js, URL building or creating URLs for different routes can be achieved using the `express.Router()` object and route handlers. The `express.Router()` allows you to modularize your routes and create reusable route handlers, making URL building more organized and manageable. Here's a complete guide on how to do URL building in Express.js:

**Step 1: Create a Router**

First, create a new router using `express.Router()`:

```javascript
const express = require('express');
const router = express.Router();
```

**Step 2: Define Route Handlers**

Next, define route handlers for different routes within the router. These route handlers will be responsible for handling specific HTTP methods and building the URLs for those routes.

```javascript
// Route handler for the root URL '/'
router.get('/', (req, res) => {
  res.send('Hello, World!');
});

// Route handler for '/users'
router.get('/users', (req, res) => {
  // Fetch users data from database
  // Build the URL for this route using res.locals
  const usersUrl = res.locals.baseUrl + '/users';
  res.send(`Users URL: ${usersUrl}`);
});

// Route handler for '/posts'
router.get('/posts', (req, res) => {
  // Fetch posts data from database
  // Build the URL for this route using res.locals
  const postsUrl = res.locals.baseUrl + '/posts';
  res.send(`Posts URL: ${postsUrl}`);
});
```

**Step 3: Mount the Router**

After defining route handlers, mount the router in your main application using `app.use()`:

```javascript
const app = express();

// Mount the router at '/api'
app.use('/api', router);
```

With the router mounted at `/api`, the complete URLs for the defined routes will be:

- Root URL: `/api/`
- Users URL: `/api/users`
- Posts URL: `/api/posts`

**Step 4: Centralized URL Building**

You can further enhance URL building by using a centralized approach with middleware. Create a middleware function that sets the base URL using `res.locals`. This way, you can build URLs in any route handler without repeating the base URL.

```javascript
// Centralized URL building middleware
const setBaseUrl = (req, res, next) => {
  res.locals.baseUrl = req.protocol + '://' + req.get('host') + req.originalUrl;
  next();
};

app.use('/api', setBaseUrl, router);
```

Now, in any route handler within the router, you can build URLs using `res.locals.baseUrl` without hardcoding the base URL.

**Summary:**

URL building in Express.js involves defining route handlers for different routes and using a centralized approach to build URLs. Here are the key steps:

1. Create a router using `express.Router()`.
2. Define route handlers within the router for different routes.
3. Mount the router in your main application using `app.use()`.
4. Optionally, use a centralized middleware function to set the base URL for URL building.

Using this approach, you can build URLs in a clean and organized manner, making your Express.js application more maintainable and scalable.
