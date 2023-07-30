**Custom Modules - Complete Documentation**

**What are Custom Modules?**
Custom Modules refer to user-defined modules in Node.js that encapsulate specific functionalities or pieces of code and can be reused across different parts of an application. In Node.js, creating custom modules allows developers to organize their code into smaller, manageable units and promotes code reusability and maintainability.

**Creating a Custom Module:**
To create a custom module in Node.js, follow these steps:

1. Create a new file with the functionality you want to export. For example, let's create a file named `mathUtils.js`:

```javascript
// mathUtils.js
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

module.exports = {
  add,
  subtract,
};
```

2. Export the desired functions or variables using the `module.exports` object. In the example above, we export the `add` and `subtract` functions.

**Using a Custom Module:**
Once you have created a custom module, you can use it in other parts of your application using the `require` function.

Example of using the `mathUtils` custom module:

```javascript
// app.js
const mathUtils = require('./mathUtils');

console.log(mathUtils.add(5, 3)); // Output: 8
console.log(mathUtils.subtract(10, 4)); // Output: 6
```

In this example, we import the `mathUtils` module using `require('./mathUtils')` and then use the exported functions `add` and `subtract`.

**Common Patterns for Custom Modules:**
Custom modules in Node.js often follow one of the following patterns:

1. Exporting a single function or value as the module:
```javascript
// customModule.js
const someFunction = () => {
  // ...
};

module.exports = someFunction;
```

```javascript
// app.js
const myFunction = require('./customModule');
myFunction();
```

2. Exporting multiple functions or values as an object:
```javascript
// customModule.js
const func1 = () => {
  // ...
};

const func2 = () => {
  // ...
};

module.exports = {
  func1,
  func2,
};
```

```javascript
// app.js
const customModule = require('./customModule');
customModule.func1();
customModule.func2();
```

3. Using named exports and destructuring:
```javascript
// customModule.js
const func1 = () => {
  // ...
};

const func2 = () => {
  // ...
};

module.exports = {
  func1,
  func2,
};
```

```javascript
// app.js
const { func1, func2 } = require('./customModule');
func1();
func2();
```

**Directory-Based Custom Modules:**
In larger applications, it is common to organize related modules into directories. Node.js allows you to define custom modules in a directory by including an `index.js` file within that directory. When requiring the directory, Node.js will automatically look for the `index.js` file.

Example directory structure:

```
myModule/
  index.js
  subModule1.js
  subModule2.js
```

Contents of `index.js`:

```javascript
// myModule/index.js
const subModule1 = require('./subModule1');
const subModule2 = require('./subModule2');

module.exports = {
  subModule1,
  subModule2,
};
```

Now you can require the entire `myModule` directory as a custom module:

```javascript
// app.js
const myModule = require('./myModule');

myModule.subModule1.someFunction();
myModule.subModule2.anotherFunction();
```

**Summary:**
- Custom Modules in Node.js allow developers to organize code into smaller, reusable units.
- To create a custom module, define the desired functionality in a separate file and use `module.exports` to export the functions or values you want to expose.
- Use the `require` function to import the custom module in other parts of your application.
- Common patterns for custom modules include exporting a single function or multiple functions as an object, using named exports and destructuring, and organizing related modules into directories with an `index.js` file.
- Directory-based custom modules can help structure larger applications by grouping related modules together.

Custom Modules are a fundamental part of Node.js development, enabling developers to create modular and maintainable applications. By breaking down functionalities into separate modules, you can better organize your code and promote code reuse across different parts of your Node.js project.
