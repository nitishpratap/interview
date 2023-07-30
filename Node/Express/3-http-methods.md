In Express.js, you can handle different HTTP methods using corresponding functions provided by the Express application object. Here are the commonly used HTTP methods in Express.js along with their corresponding functions:

1. **GET Method:**

   To handle a GET request, use `app.get()`:

   ```javascript
   app.get('/users', (req, res) => {
     // Handle GET request to /users
     // Fetch users data from database and send it as a response
   });
   ```

2. **POST Method:**

   To handle a POST request, use `app.post()`:

   ```javascript
   app.post('/users', (req, res) => {
     // Handle POST request to /users
     // Create a new user based on request body and send a response
   });
   ```

3. **PUT Method:**

   To handle a PUT request, use `app.put()`:

   ```javascript
   app.put('/users/:id', (req, res) => {
     const userId = req.params.id;
     // Handle PUT request to /users/:id
     // Update user with specified ID based on request body and send a response
   });
   ```

4. **DELETE Method:**

   To handle a DELETE request, use `app.delete()`:

   ```javascript
   app.delete('/users/:id', (req, res) => {
     const userId = req.params.id;
     // Handle DELETE request to /users/:id
     // Delete user with specified ID and send a response
   });
   ```

5. **PATCH Method:**

   To handle a PATCH request, use `app.patch()`:

   ```javascript
   app.patch('/users/:id', (req, res) => {
     const userId = req.params.id;
     // Handle PATCH request to /users/:id
     // Partially update user with specified ID based on request body and send a response
   });
   ```

6. **OPTIONS Method:**

   To handle an OPTIONS request, use `app.options()`:

   ```javascript
   app.options('/users', (req, res) => {
     // Handle OPTIONS request to /users
     // Provide information about allowed methods and headers and send a response
   });
   ```

7. **HEAD Method:**

   To handle a HEAD request, use `app.head()`:

   ```javascript
   app.head('/users', (req, res) => {
     // Handle HEAD request to /users
     // Respond with headers only, without the actual response body
   });
   ```

These are the most commonly used HTTP methods in Express.js. Express.js allows you to handle each method by specifying the corresponding route and providing a callback function to handle the request and response for that route. You can use these methods to build RESTful APIs and handle various types of client requests in your Express.js application.
