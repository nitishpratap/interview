## Cookies in Express.js 

Cookies are small pieces of data stored in the client's browser and are commonly used for maintaining user sessions, user preferences, and other client-specific information. In Express.js, you can easily set and retrieve cookies using the `cookie-parser` middleware. This guide will provide a complete overview of how to work with cookies in Express.js:

**Step 1: Install the `cookie-parser` Middleware**

First, install the `cookie-parser` middleware using npm or yarn:

```bash
npm install cookie-parser
```

or

```bash
yarn add cookie-parser
```

**Step 2: Set Up the `cookie-parser` Middleware**

In your Express.js application, require and use the `cookie-parser` middleware before defining your routes:

```javascript
const express = require('express');
const cookieParser = require('cookie-parser');
const app = express();

app.use(cookieParser());

// Define your routes and other middleware here
```

**Step 3: Setting a Cookie**

To set a cookie in Express.js, use the `res.cookie()` method. This method takes three arguments: the name of the cookie, the value to be stored, and an optional options object.

```javascript
app.get('/set-cookie', (req, res) => {
  res.cookie('username', 'john_doe', { maxAge: 900000, httpOnly: true });
  res.send('Cookie has been set.');
});
```

In this example, a cookie named "username" is set with the value "john_doe". The `maxAge` option specifies the cookie's expiration time in milliseconds (in this case, 900,000 milliseconds, which is equal to 15 minutes), and the `httpOnly` option makes the cookie accessible only through HTTP requests and not JavaScript, providing some level of security.

**Step 4: Retrieving a Cookie**

To retrieve a cookie in Express.js, access the `req.cookies` object, which is provided by the `cookie-parser` middleware. This object contains key-value pairs representing the client's cookies.

```javascript
app.get('/get-cookie', (req, res) => {
  const username = req.cookies.username;
  res.send(`Hello, ${username}!`);
});
```

In this example, the "username" cookie value is retrieved from the `req.cookies` object and used in the response.

**Step 5: Clearing a Cookie**

To clear a cookie, use the `res.clearCookie()` method. This method takes the name of the cookie as its argument.

```javascript
app.get('/clear-cookie', (req, res) => {
  res.clearCookie('username');
  res.send('Cookie has been cleared.');
});
```

In this example, the "username" cookie is cleared, effectively removing it from the client's browser.

