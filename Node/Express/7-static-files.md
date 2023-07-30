# Serving Static Files in Express.js

In Express.js, you can serve static files, such as CSS, JavaScript, images, and other assets, using the built-in middleware function `express.static()`. This middleware function makes it easy to serve static files from a directory in your application. Here's a complete guide on serving static files in Express.js:

**Step 1: Create a `public` Directory**

First, create a directory named `public` in your project root. This directory will store all the static files you want to serve.

**Step 2: Add Static Files**

Place all your static files, such as CSS, JavaScript, images, and other assets, inside the `public` directory.

```
- project/
  - public/
    - css/
      - styles.css
    - js/
      - script.js
    - images/
      - logo.png
    - ...
```

**Step 3: Use the `express.static()` Middleware**

In your Express.js application, use the `express.static()` middleware function to serve the static files from the `public` directory. You should add this middleware function before defining your routes to ensure that it applies to all routes.

```javascript
const express = require('express');
const app = express();

// Serve static files from the 'public' directory
app.use(express.static('public'));

// Define your routes and other middleware here
```

**Step 4: Accessing Static Files**

With the `express.static()` middleware configured, you can access the static files directly from the client-side using their relative paths. For example, to access the `styles.css` file, you would use the following in your HTML file:

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="/css/styles.css">
</head>
<body>
  <!-- Your HTML content here -->
</body>
</html>
```

Similarly, you can access images and other assets:

```html
<!DOCTYPE html>
<html>
<head>
  <!-- Your HTML content here -->
</head>
<body>
  <img src="/images/logo.png" alt="Logo">
</body>
</html>
```

**Using a Custom Directory Path:**

If your static files are located in a directory other than `public`, you can specify the directory path when using the `express.static()` middleware:

```javascript
app.use('/assets', express.static('my-assets'));
```

With this setup, your static files will be served from the `my-assets` directory, and you would access them using `/assets` as the base URL:

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="/assets/css/styles.css">
</head>
<body>
  <!-- Your HTML content here -->
</body>
</html>
```

**Adding Multiple Static Directories:**

You can also add multiple static directories using `express.static()`. Express.js will search for the requested file in each directory in the order they are defined.

```javascript
app.use(express.static('public'));
app.use(express.static('assets'));
```
