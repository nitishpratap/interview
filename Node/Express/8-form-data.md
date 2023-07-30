In Express.js, you can handle form data submitted from HTML forms using the `body-parser` middleware. The `body-parser` middleware is responsible for parsing the request body and making it available in the `req.body` object. This allows you to access the form data and use it in your Express.js application. Here's a guide on how to handle form data in Express.js using the `body-parser` middleware:

**Step 1: Install body-parser**

First, install the `body-parser` middleware using npm or yarn:

```bash
npm install body-parser
```

or

```bash
yarn add body-parser
```

**Step 2: Import body-parser and Set it Up**

In your Express.js application, import the `body-parser` middleware and set it up using `app.use()`:

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const app = express();

// Set up body-parser middleware
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

// Define your routes and other middleware here
```

The `bodyParser.urlencoded()` middleware is used to parse form data submitted via the URL-encoded format, and `bodyParser.json()` is used to parse JSON data.

**Step 3: Create an HTML Form**

In your HTML file, create a form that sends data to the server. The form should have an `action` attribute specifying the server route to which the form data will be submitted, and a `method` attribute set to "POST" or "GET" to specify the HTTP method for the form submission.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Form Data in Express.js</title>
</head>
<body>
  <form action="/submit" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>

    <button type="submit">Submit</button>
  </form>
</body>
</html>
```

**Step 4: Handle the Form Submission**

In your Express.js application, define a route to handle the form submission. Use the `req.body` object to access the form data submitted by the user.

```javascript
app.post('/submit', (req, res) => {
  const name = req.body.name;
  const email = req.body.email;

  // Do something with the form data
  console.log(`Name: ${name}`);
  console.log(`Email: ${email}`);

  res.send('Form data received successfully!');
});
```

In this example, when the form is submitted, the data will be sent to the `/submit` route using the HTTP POST method. The form data will be available in `req.body`, and we extract the `name` and `email` fields.

