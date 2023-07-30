# URL Module 

The `url` module is a core module in Node.js that provides utilities for working with URLs (Uniform Resource Locators). It allows you to parse, format, and manipulate URLs and their components.

**Importing the URL Module:**
To use the `url` module, you need to import it first. In Node.js, you can import core modules using the `require()` function:

```javascript
const url = require('Node/18-url');
```

**Common URL Methods:**

1. **`url.parse(urlString[, parseQueryString[, slashesDenoteHost]])`**:
   Parses a URL string and returns an object with its various components.

   Example:
   ```javascript
   const urlString = 'https://www.example.com:8080/path/to/resource?query=param';
   const parsedUrl = url.parse(urlString, true);
   /*
   Output:
   {
     protocol: 'https:',
     slashes: true,
     host: 'www.example.com:8080',
     hostname: 'www.example.com',
     port: '8080',
     path: '/path/to/resource',
     search: '?query=param',
     query: { query: 'param' },
     pathname: '/path/to/resource',
     href: 'https://www.example.com:8080/path/to/resource?query=param'
   }
   */
   ```

2. **`url.format(urlObject)`**:
   Takes a URL object and returns the formatted URL string.

   Example:
   ```javascript
   const urlObject = {
     protocol: 'https:',
     slashes: true,
     host: 'www.example.com',
     pathname: '/path/to/resource',
     search: '?query=param'
   };
   const formattedUrl = url.format(urlObject);
   // Output: 'https://www.example.com/path/to/resource?query=param'
   ```

3. **`url.resolve(from, to)`**:
   Resolves a relative URL `to` against a base URL `from`.

   Example:
   ```javascript
   const baseUrl = 'https://www.example.com';
   const relativeUrl = '/path/to/resource';
   const resolvedUrl = url.resolve(baseUrl, relativeUrl);
   // Output: 'https://www.example.com/path/to/resource'
   ```

**Summary:**
- The `url` module in Node.js provides utilities for working with URLs (Uniform Resource Locators).
- It allows you to parse, format, and manipulate URLs and their components.
- You can import the `url` module using `const url = require('url');`.
- The module provides methods like `parse`, `format`, and `resolve` to work with URLs.

The `url` module is useful for dealing with URLs in Node.js applications, such as parsing query parameters from URLs, resolving relative URLs, and constructing or formatting URLs based on components. It simplifies URL manipulation and is particularly valuable for web applications and APIs that involve URL handling and routing.
