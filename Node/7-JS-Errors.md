# JavaScript Errors 

**What are JavaScript Errors?**
JavaScript errors are issues that occur during the execution of a JavaScript program. When the JavaScript engine encounters an error, it throws an exception, which interrupts the normal flow of the program and can lead to unexpected behavior or crashes. Understanding and handling errors properly is crucial for building robust and reliable JavaScript applications.

**Types of JavaScript Errors:**
There are several types of JavaScript errors, some of the common ones include:

1. **SyntaxError:** Occurs when there is a syntax mistake in the code, such as missing brackets or invalid identifiers.

2. **ReferenceError:** Occurs when trying to access an undeclared or non-existent variable or function.

3. **TypeError:** Occurs when a value is of the wrong type or a method is called on an object that doesn't support it.

4. **RangeError:** Occurs when a value is not in the expected range, such as using an invalid index for an array.

5. **URIError:** Occurs when a global URI-related function is used incorrectly.

6. **EvalError:** Rarely used, occurs when using the `eval()` function incorrectly.

**Handling JavaScript Errors:**
Handling errors in JavaScript involves using `try-catch` blocks to catch exceptions and handle them gracefully. The `try` block contains the code that may throw an exception, and the `catch` block is used to define what happens when an exception occurs.

Example of handling a JavaScript error:
```javascript
try {
  // Code that may throw an error
  const result = someFunction();
} catch (error) {
  // Handle the error
  console.error('An error occurred:', error.message);
}
```

**Throwing Custom Errors:**
Developers can also throw custom errors using the `throw` keyword. Custom errors can provide more context about specific issues in the application and help with debugging.

Example of throwing a custom error:
```javascript
function divide(a, b) {
  if (b === 0) {
    throw new Error('Division by zero is not allowed.');
  }
  return a / b;
}

try {
  const result = divide(10, 0);
} catch (error) {
  console.error('An error occurred:', error.message);
}
```

**Global Error Event:**
In browser-based JavaScript, uncaught exceptions can be captured using the `window.onerror` event. It allows developers to handle uncaught exceptions globally and perform actions like logging the errors.

```javascript
window.onerror = function (message, source, lineno, colno, error) {
  console.error('Uncaught error:', message);
};
```

**Async/Await Error Handling:**
When using asynchronous code with `async/await`, it's essential to wrap the `await` calls in a `try-catch` block to handle errors effectively.

Example of error handling with `async/await`:
```javascript
async function getData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('An error occurred:', error.message);
    throw error; // Re-throw the error if needed
  }
}
```

**Summary:**
- JavaScript errors occur during the execution of a JavaScript program and can interrupt the normal flow of the application.
- Common types of JavaScript errors include SyntaxError, ReferenceError, TypeError, RangeError, URIError, and EvalError.
- Handling errors involves using `try-catch` blocks to catch exceptions and handle them gracefully.
- Developers can throw custom errors using the `throw` keyword to provide more context about specific issues.
- In browser-based JavaScript, uncaught exceptions can be captured using the `window.onerror` event for global error handling.
- When using asynchronous code with `async/await`, wrap the `await` calls in a `try-catch` block to handle errors effectively.

Properly handling JavaScript errors is crucial for building reliable and maintainable applications. By understanding the different types of errors and implementing appropriate error handling mechanisms, developers can improve the stability and user experience of their JavaScript applications.


# System Errors in Node.js 

**What are System Errors?**
System errors in Node.js are errors that occur due to issues with the underlying operating system or environment. These errors are thrown when the Node.js runtime encounters problems that are beyond the control of the application, such as file system issues, network problems, or resource limitations. System errors are also known as "operational errors" or "runtime errors."

**Types of System Errors:**
Node.js uses the `Error` class to represent system errors, and there are several built-in error classes that inherit from the `Error` class to represent different types of system errors:

1. **`Error`:** The base error class used for all errors in Node.js.

2. **`SystemError`:** A subclass of `Error` representing low-level system errors.

3. **`TypeError`:** A subclass of `Error` representing errors due to unexpected types.

4. **`RangeError`:** A subclass of `Error` representing errors due to an invalid range of values.

5. **`SyntaxError`:** A subclass of `Error` representing errors due to syntax mistakes.

6. **`ReferenceError`:** A subclass of `Error` representing errors when an invalid reference is accessed.

7. **`EvalError`:** A subclass of `Error` representing errors when using the `eval()` function incorrectly.

8. **`SystemError`:** A subclass of `Error` representing low-level system errors like I/O failures or resource limitations.

**Handling System Errors:**
Handling system errors involves using `try-catch` blocks to catch exceptions and handle the errors gracefully. However, unlike application errors that developers can anticipate and handle, system errors are usually unpredictable and may require different handling strategies.

When handling system errors, it's essential to:

1. **Log the Error:** Always log the error details when handling system errors. Logging helps with debugging and troubleshooting issues in the application.

2. **Handle Specific Errors:** Use the `instanceof` operator or check the error codes to identify specific system errors and handle them differently based on the error type.

3. **Perform Cleanup:** In the event of system errors like file system failures, it's crucial to perform cleanup tasks like closing files, releasing resources, or rolling back transactions if applicable.

4. **Graceful Shutdown:** In some cases, a system error may render the application unable to continue running correctly. In such scenarios, consider gracefully shutting down the application to avoid further issues.

**System Error Codes:**
System errors often come with error codes that provide additional information about the error type. The error codes can be accessed through the `code` property of the `SystemError` object.

Example of accessing the error code:

```javascript
const fs = require('Node/14-fs');

fs.readFile('nonexistent-file.txt', (err, data) => {
   if (err) {
      console.error('Error code:', err.code); // Outputs: 'ENOENT'
      console.error('Error message:', err.message); // Outputs: 'no such file or directory'
   }
});
```

**Summary:**
- System errors in Node.js are errors that occur due to issues with the underlying operating system or environment.
- Node.js uses the `Error` class and several built-in error classes to represent different types of system errors.
- Handling system errors involves using `try-catch` blocks to catch exceptions and handle them gracefully.
- Log the error details for debugging and troubleshooting purposes.
- Handle specific system errors differently based on their error type.
- Perform cleanup tasks and consider graceful shutdown when dealing with severe system errors.

System errors are an inherent part of Node.js application development, as they can occur due to various factors beyond the control of the application code. By handling system errors appropriately and implementing robust error handling strategies, developers can improve the stability and reliability of their Node.js applications.


# User-Specified Errors 

**What are User-Specified Errors?**
User-specified errors, also known as custom errors, are errors that developers define and throw in their code to represent specific exceptional scenarios or issues that may arise during the execution of a program. These errors are custom-tailored to the application's needs and provide more context and information about the error compared to built-in errors.

**Creating User-Specified Errors:**
In JavaScript, you can create user-specified errors by defining custom error classes that inherit from the built-in `Error` class. By extending the `Error` class, you can add custom properties and methods to the error object.

Example of creating a custom error class:
```javascript
class MyCustomError extends Error {
  constructor(message) {
    super(message);
    this.name = 'MyCustomError';
  }
}
```

In this example, `MyCustomError` is a custom error class that inherits from the `Error` class. It sets a custom name for the error to distinguish it from other errors.

**Throwing User-Specified Errors:**
Once you have defined a custom error class, you can throw instances of it in your code to represent specific error scenarios.

Example of throwing a user-specified error:
```javascript
function divide(a, b) {
  if (b === 0) {
    throw new MyCustomError('Division by zero is not allowed.');
  }
  return a / b;
}

try {
  const result = divide(10, 0);
} catch (error) {
  if (error instanceof MyCustomError) {
    console.error('Custom Error:', error.message);
  } else {
    console.error('Other Error:', error.message);
  }
}
```

In this example, when the `divide` function is called with `b` equal to 0, it throws a `MyCustomError` with the specified message.

**Custom Error Properties and Stack Traces:**
Custom errors can have additional properties to provide more context about the error. These properties can be added to the error class's constructor.

Example of adding custom properties to a user-specified error:
```javascript
class MyCustomError extends Error {
  constructor(message, errorCode) {
    super(message);
    this.name = 'MyCustomError';
    this.errorCode = errorCode;
    this.date = new Date();
  }
}
```

You can also access the stack trace of the custom error to get information about the call stack when the error was thrown.

Example of accessing the stack trace of a user-specified error:
```javascript
function doSomething() {
  throw new MyCustomError('Something went wrong.');
}

try {
  doSomething();
} catch (error) {
  console.error('Custom Error:', error.message);
  console.error('Stack Trace:', error.stack);
}
```

**Best Practices for User-Specified Errors:**
When creating and using user-specified errors, consider the following best practices:

1. **Use Descriptive Names:** Give custom error classes descriptive names that reflect the specific error scenario they represent.

2. **Include Relevant Information:** Add custom properties to the error class to include relevant information about the error.

3. **Handle Custom Errors Appropriately:** Handle user-specified errors separately from other errors using `instanceof` or custom properties.

4. **Include Stack Traces:** Including stack traces in custom errors helps with debugging and provides additional context about the error.

5. **Document Custom Errors:** Document the custom errors you define in your application, explaining when and why they are thrown and the information they provide.

**Summary:**
- User-specified errors, or custom errors, are errors created by developers to represent specific exceptional scenarios in their applications.
- Custom errors are created by defining custom error classes that inherit from the built-in `Error` class.
- Custom error classes can have additional properties to provide more context about the error.
- To use a custom error, throw an instance of the custom error class in your code.
- Best practices for user-specified errors include using descriptive names, including relevant information and stack traces, and proper handling and documentation.

User-specified errors allow developers to add context and specificity to error scenarios, making it easier to understand and handle exceptional cases in their applications. By defining and using custom error classes, developers can improve the error handling and debugging process, resulting in more reliable and maintainable applications.



# Async Errors 

**What are Async Errors?**
Async errors, also known as unhandled promise rejections, occur when a Promise is rejected, but there is no corresponding `.catch()` or `.then()` with a rejection handler to handle the error. In asynchronous JavaScript code, Promises and async/await are commonly used to handle asynchronous operations. If a Promise is rejected and its rejection is not caught, it becomes an unhandled async error.

**Handling Async Errors:**
Handling async errors is essential to prevent unhandled promise rejections and crashes in your applications. There are several ways to handle async errors effectively:

1. **Using `.catch()` Method:**
   One way to handle async errors is to use the `.catch()` method on a Promise or an async function to catch any rejected Promise and handle the error.

Example of handling async errors with `.catch()`:
```javascript
async function getData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error fetching data:', error.message);
    throw error; // Re-throw the error if needed
  }
}
```

2. **Using Promise Rejection Handling:**
   In cases where you don't use async/await, you can handle async errors by chaining `.then()` and `.catch()` methods on Promises.

Example of handling async errors with `.then()` and `.catch()`:
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error fetching data:', error.message));
```

3. **Using Node.js Unhandled Rejection Event:**
   In Node.js, you can listen for the `unhandledRejection` event to catch and handle unhandled Promise rejections globally.

Example of handling async errors using the `unhandledRejection` event:
```javascript
process.on('unhandledRejection', (reason, promise) => {
  console.error('Unhandled Rejection:', reason);
});
```

However, it's important to note that using the `unhandledRejection` event is considered a last resort, and it's better to handle async errors at the source with `.catch()` or `.then()`.

**Best Practices for Handling Async Errors:**
When dealing with async errors, consider the following best practices:

1. **Always Handle Async Errors:** Ensure that every Promise rejection is caught and handled using `.catch()` or `.then()`.

2. **Use `try-catch` with `async/await`:** When using async/await, wrap the `await` calls in a `try-catch` block to handle errors effectively.

3. **Avoid Silent Failures:** Never ignore Promise rejections, as silent failures can lead to difficult-to-debug issues in your application.

4. **Use Linting Rules:** Use linting tools like ESLint with appropriate rules to enforce handling of unhandled promise rejections.

**Summary:**
- Async errors, or unhandled promise rejections, occur when a Promise is rejected, but its rejection is not caught or handled.
- Handle async errors by using `.catch()` with Promises and async/await or chaining `.then()` and `.catch()` methods.
- In Node.js, you can listen for the `unhandledRejection` event to handle unhandled Promise rejections globally, but it's better to handle them at the source.
- Always handle async errors to prevent uncaught promise rejections and silent failures.
- Use `try-catch` blocks with async/await to handle errors effectively and avoid silent failures.

Handling async errors properly is crucial for writing robust and reliable asynchronous JavaScript code. By being proactive and handling Promise rejections appropriately, you can ensure that your application handles errors gracefully and maintains a stable and predictable behavior.
