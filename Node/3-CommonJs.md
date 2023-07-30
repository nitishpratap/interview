**CommonJS: A Complete Documentation**

**What is CommonJS?**
CommonJS is a module specification for JavaScript that provides a standardized way to define and load modules in a server-side environment. It was introduced to tackle the lack of native module support in JavaScript, especially in early versions of Node.js. The CommonJS module format is used extensively in Node.js for organizing and managing code into reusable and maintainable modules.

**Defining a Module:**
In CommonJS, a module is a separate file that encapsulates a piece of functionality or a set of related functionalities. Each module can expose specific properties or functions to be used by other modules. A module is defined using the `module.exports` object, which is a central part of the CommonJS module system.

Example of a CommonJS module:
```javascript
// exampleModule.js
const sayHello = () => {
  return "Hello, CommonJS!";
};

module.exports = {
  sayHello,
};
```

**Loading a Module:**
To use the functionality provided by a module, you need to load it using the `require` function. The `require` function takes the path to the module file and returns the exported object.

Example of loading a module:
```javascript
// main.js
const exampleModule = require('./exampleModule');

console.log(exampleModule.sayHello()); // Output: "Hello, CommonJS!"
```

**Module Exports:**
The `module.exports` object is used to expose values or functionalities from a module. It can be assigned an object, function, class, or any other JavaScript value that you want to make available to other modules.

Example of exporting multiple functions from a module:
```javascript
// mathUtils.js
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

module.exports = {
  add,
  subtract,
};
```

**Module Imports:**
When using a module, you can import specific properties or functions using destructuring or import the entire module as an object.

Example of importing specific functions from a module:
```javascript
// app.js
const { add, subtract } = require('./mathUtils');

console.log(add(5, 3)); // Output: 8
console.log(subtract(10, 4)); // Output: 6
```

**Circular Dependencies:**
CommonJS handles circular dependencies gracefully. If Module A depends on Module B, and Module B depends on Module A, Node.js ensures that the circular reference is resolved correctly, and the modules are loaded without any issues.

**Asynchronous Module Loading:**
CommonJS follows synchronous module loading, which means that the `require` function blocks the execution until the required module is fully loaded. Asynchronous module loading is not supported natively by CommonJS.

**Browser Support:**
CommonJS is designed for server-side environments like Node.js, and it is not natively supported in web browsers. However, tools like Browserify or Webpack can be used to bundle CommonJS modules into a single file that can be used in the browser.

**Summary:**
- CommonJS is a module specification for JavaScript that provides a standardized way to define and load modules in a server-side environment like Node.js.
- Modules are defined using the `module.exports` object and can expose specific properties or functions to be used by other modules.
- Modules are loaded using the `require` function, which returns the exported object.
- Circular dependencies are handled gracefully in CommonJS.
- CommonJS follows synchronous module loading, which may lead to performance issues in certain situations.
- CommonJS is not natively supported in web browsers, but it can be used with bundlers like Browserify or Webpack for browser compatibility.

CommonJS has been instrumental in organizing and structuring large-scale applications in Node.js and remains a fundamental module system in server-side JavaScript development. However, with the advent of ECMAScript modules (ESM) introduced in ECMAScript 6 (ES6), JavaScript has adopted a more standardized approach to modules that natively supports both browser and server-side environments.

**ES Module (ECMAScript Module) - Complete Documentation**

**What are ES Modules?**
ES Modules, also known as ECMAScript Modules, are a standardized module system introduced in ECMAScript 6 (ES6) to allow developers to organize and share code in a more structured and reusable manner in both browser and server-side environments. ES Modules provide a way to define and load modules using the `import` and `export` keywords.

**Defining an ES Module:**
In an ES Module, each file is considered a module, and you can export specific values or functionalities from a module using the `export` keyword. You can also import these exported values into other modules using the `import` keyword.

Example of exporting from an ES Module:
```javascript
// mathUtils.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

**Importing from an ES Module:**
To use the exported values from a module, you can import them into another module using the `import` keyword.

Example of importing from an ES Module:
```javascript
// app.js
import { add, subtract } from './mathUtils';

console.log(add(5, 3)); // Output: 8
console.log(subtract(10, 4)); // Output: 6
```

**Default Exports:**
In addition to named exports, ES Modules also support default exports. You can export a default value from a module using the `export default` syntax. When importing a default export, you can choose any name for the import, making it more flexible.

Example of exporting and importing a default value:
```javascript
// logger.js
const logger = (message) => {
  console.log(message);
};

export default logger;
```

```javascript
// app.js
import customLogger from './logger';

customLogger('Hello, ES Modules!'); // Output: "Hello, ES Modules!"
```

**Exporting All from a Module:**
You can export all values from a module using the `* as` syntax. It allows you to import all the exported values as properties of a single object.

Example of exporting and importing all values from a module:
```javascript
// utils.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
export const multiply = (a, b) => a * b;
```

```javascript
// app.js
import * as utils from './utils';

console.log(utils.add(5, 3)); // Output: 8
console.log(utils.subtract(10, 4)); // Output: 6
console.log(utils.multiply(2, 3)); // Output: 6
```

**Dynamic Imports:**
ES Modules also support dynamic imports, allowing you to import modules conditionally or lazily during runtime using the `import()` function.

Example of dynamic import:
```javascript
// app.js
const dynamicModule = 'mathUtils';
import(`./${dynamicModule}`).then((module) => {
  console.log(module.add(5, 3)); // Output: 8
});
```

**Browser Support:**
Modern browsers natively support ES Modules using the `type="module"` attribute in the script tag.

```html
<script type="module" src="app.js"></script>
```

**Node.js Support:**
Node.js natively supports ES Modules starting from version 12.x. To use ES Modules in Node.js, you can use the `.mjs` file extension for your module files, or set `"type": "module"` in your `package.json`.

```json
{
  "type": "module"
}
```

**Summary:**
- ES Modules (ECMAScript Modules) are a standardized module system introduced in ECMAScript 6 (ES6) for organizing and sharing code in both browser and server-side environments.
- Modules are defined using the `export` keyword to expose values or functionalities and can be imported using the `import` keyword.
- ES Modules support named exports, default exports, and exporting all values from a module.
- Dynamic imports allow for conditional or lazy loading of modules during runtime.
- Modern browsers and Node.js (starting from version 12.x) natively support ES Modules.

ES Modules have become the de facto module system for modern JavaScript development, providing a more structured and standardized approach to managing code dependencies across various environments. With broad support across both browsers and server-side platforms, ES Modules offer a powerful tool for building scalable and maintainable applications.
