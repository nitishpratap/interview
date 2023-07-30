# Authentication in Express.js 

Authentication is a crucial aspect of web applications to ensure that only authorized users can access certain resources or perform specific actions. In Express.js, you can implement authentication using various strategies, such as sessions, JSON Web Tokens (JWT), or third-party authentication providers like OAuth. This documentation will cover the basics of implementing authentication in Express.js using sessions and JWT.

**Step 1: Set Up the Express Application**

Initialize a new Node.js project and install Express.js and other required dependencies:

```bash
npm init -y
npm install express express-session cookie-parser bcrypt jsonwebtoken
```

**Step 2: Create User Model**

Create a user model that represents your application's users. In this example, we'll use a simple array to store users for demonstration purposes, but in a real-world application, you would use a database like MongoDB.

```javascript
// models/user.js
const users = [];

class User {
  constructor(username, password) {
    this.username = username;
    this.password = password;
  }

  static findByUsername(username) {
    return users.find(user => user.username === username);
  }

  static create(username, password) {
    const user = new User(username, password);
    users.push(user);
    return user;
  }
}

module.exports = User;
```

**Step 3: Implement Registration and Login Routes**

Create routes for user registration and login. For demonstration purposes, we'll use simple routes to handle registration and login using sessions.

```javascript
// app.js
const express = require('express');
const session = require('express-session');
const cookieParser = require('cookie-parser');
const bcrypt = require('bcrypt');
const jwt = require('jsonwebtoken');
const User = require('./models/user');

const app = express();

app.use(cookieParser());
app.use(session({
  secret: 'my-secret-key',
  resave: false,
  saveUninitialized: false,
}));

app.use(express.json());

app.post('/register', async (req, res) => {
  const { username, password } = req.body;

  if (!username || !password) {
    return res.status(400).json({ message: 'Username and password are required' });
  }

  const existingUser = User.findByUsername(username);
  if (existingUser) {
    return res.status(409).json({ message: 'Username already exists' });
  }

  const hashedPassword = await bcrypt.hash(password, 10);
  const user = User.create(username, hashedPassword);

  res.json({ message: 'User registered successfully' });
});

app.post('/login', async (req, res) => {
  const { username, password } = req.body;

  if (!username || !password) {
    return res.status(400).json({ message: 'Username and password are required' });
  }

  const user = User.findByUsername(username);
  if (!user) {
    return res.status(401).json({ message: 'Invalid username or password' });
  }

  const isPasswordValid = await bcrypt.compare(password, user.password);
  if (!isPasswordValid) {
    return res.status(401).json({ message: 'Invalid username or password' });
  }

  req.session.user = { username: user.username };
  res.json({ message: 'Login successful' });
});
```

**Step 4: Implement Protected Routes**

Create protected routes that require authentication using sessions. In this example, we'll create a simple "profile" route that can only be accessed by authenticated users.

```javascript
// app.js (continued)

// Middleware to check if the user is authenticated
const requireAuth = (req, res, next) => {
  if (!req.session.user) {
    return res.status(401).json({ message: 'Authentication required' });
  }
  next();
};

app.get('/profile', requireAuth, (req, res) => {
  const { username } = req.session.user;
  res.json({ message: `Welcome, ${username}! This is your profile page.` });
});

// Other routes and middleware

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

**Step 5: Testing the Authentication**

With the above implementation, you can use tools like Postman or a front-end application to test the authentication. You can perform the following steps:

1. Register a user using the `/register` route with a POST request, providing a `username` and `password` in the request body.
2. Login as the registered user using the `/login` route with a POST request, providing the same `username` and `password` in the request body.
3. Access the protected `/profile` route with a GET request, and you should get a response with the user's profile information.
