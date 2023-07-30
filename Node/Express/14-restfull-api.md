# RESTful APIs in Express.js

RESTful APIs are a popular architectural style for building web services that allow clients to interact with the server using standard HTTP methods (GET, POST, PUT, DELETE). In Express.js, you can easily create RESTful APIs using the HTTP methods and route handling capabilities provided by the framework. This guide will provide a complete overview of how to build RESTful APIs in Express.js:

**Step 1: Set Up the Express Application**

Initialize a new Node.js project and install Express.js:

```bash
npm init -y
npm install express
```

**Step 2: Define the Routes for the API**

Create a file (e.g., `api.js`) to define the routes for your RESTful API:

```javascript
// api.js
const express = require('express');
const router = express.Router();

// Sample data (replace with your data source or database)
let books = [
  { id: 1, title: 'Book 1', author: 'Author 1' },
  { id: 2, title: 'Book 2', author: 'Author 2' },
  { id: 3, title: 'Book 3', author: 'Author 3' },
];

// Routes for handling books
router.get('/books', (req, res) => {
  res.json(books);
});

router.get('/books/:id', (req, res) => {
  const id = parseInt(req.params.id);
  const book = books.find(b => b.id === id);
  if (book) {
    res.json(book);
  } else {
    res.status(404).json({ message: 'Book not found' });
  }
});

router.post('/books', (req, res) => {
  const { title, author } = req.body;
  const id = books.length + 1;
  const newBook = { id, title, author };
  books.push(newBook);
  res.status(201).json(newBook);
});

router.put('/books/:id', (req, res) => {
  const id = parseInt(req.params.id);
  const { title, author } = req.body;
  const bookIndex = books.findIndex(b => b.id === id);
  if (bookIndex !== -1) {
    books[bookIndex].title = title;
    books[bookIndex].author = author;
    res.json(books[bookIndex]);
  } else {
    res.status(404).json({ message: 'Book not found' });
  }
});

router.delete('/books/:id', (req, res) => {
  const id = parseInt(req.params.id);
  const bookIndex = books.findIndex(b => b.id === id);
  if (bookIndex !== -1) {
    const deletedBook = books.splice(bookIndex, 1);
    res.json(deletedBook[0]);
  } else {
    res.status(404).json({ message: 'Book not found' });
  }
});

module.exports = router;
```

**Step 3: Use the API Routes in the Main Application**

In your main application file (e.g., `app.js`), use the API routes defined in the `api.js` file:

```javascript
// app.js
const express = require('express');
const apiRoutes = require('./api');

const app = express();

app.use(express.json());

// Use the API routes
app.use('/api', apiRoutes);

// Other routes and middleware

app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

**Step 4: Test the RESTful API**

With the above implementation, you can use tools like Postman or a front-end application to test the RESTful API:

1. Send a GET request to `/api/books` to get a list of all books.
2. Send a GET request to `/api/books/1` to get details of a specific book with ID 1.
3. Send a POST request to `/api/books` with JSON data in the request body to create a new book.
4. Send a PUT request to `/api/books/1` with updated JSON data in the request body to update the book with ID 1.
5. Send a DELETE request to `/api/books/1` to delete the book with ID 1.

