# Templating in Express

In Express.js, templating engines are used to render dynamic HTML pages on the server-side and send them as responses to client requests. Templating allows you to generate dynamic content by embedding data into HTML templates. There are several popular templating engines that can be used with Express.js, such as EJS, Pug (formerly Jade), Handlebars, and more. This guide will cover how to use templating engines in Express.js and provide a complete guide on using the EJS templating engine.

**Step 1: Install EJS**

First, install the EJS templating engine using npm or yarn:

```bash
npm install ejs
```

or

```bash
yarn add ejs
```

**Step 2: Set Up Templating Engine**

In your Express.js application, set EJS as the templating engine using the `app.set()` method:

```javascript
const express = require('express');
const app = express();

// Set EJS as the templating engine
app.set('view engine', 'ejs');
```

**Step 3: Create a Views Directory**

Next, create a directory named `views` in your project root to store your EJS templates.

**Step 4: Create EJS Templates**

Inside the `views` directory, create EJS templates with a `.ejs` extension. These templates will contain the HTML structure with embedded JavaScript code to render dynamic data.

```html
<!-- views/home.ejs -->
<!DOCTYPE html>
<html>
<head>
  <title><%= title %></title>
</head>
<body>
  <h1>Hello, <%= name %>!</h1>
</body>
</html>
```

**Step 5: Render the EJS Template**

In your route handlers, use the `res.render()` method to render the EJS templates and send them as responses.

```javascript
app.get('/', (req, res) => {
  const title = 'Express Templating';
  const name = 'John Doe';
  res.render('home', { title, name }); // Render the 'home' template with the provided data
});
```

The `res.render()` method takes two arguments: the name of the EJS template file without the `.ejs` extension and an object containing the data to be embedded in the template.

**Step 6: Render EJS Partial Templates (Optional)**

You can create partial templates in EJS to reuse common HTML components across multiple views. Partial templates are reusable chunks of HTML code that can be included in other EJS templates.

**views/header.ejs**
```html
<!-- views/header.ejs -->
<!DOCTYPE html>
<html>
<head>
  <title><%= title %></title>
</head>
<body>
```

**views/footer.ejs**
```html
<!-- views/footer.ejs -->
</body>
</html>
```

**views/home.ejs**
```html
<!-- views/home.ejs -->
<%- include('header', { title: 'Home Page' }) %>

<h1>Hello, <%= name %>!</h1>

<%- include('footer') %>
```

In this example, the `include()` method is used to include the `header` and `footer` partial templates into the `home` template.

