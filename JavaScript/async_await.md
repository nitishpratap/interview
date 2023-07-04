# Introduction to JavaScript async / await keywords
To avoid this callback hell issue, ES6 introduced the promises that allow you to write asynchronous code in more manageable ways.

First, you need to return a Promise in each function:

ES2017 introduced the async/await keywords that build on top of promises, allowing you to write asynchronous code that looks more like synchronous code and is more readable. Technically speaking, the async / await is syntactic sugar for promises.

If a function returns a Promise, you can place the await keyword in front of the function call, like this:

```javascript
let result = await f();
```

The await will wait for the Promise returned from the f() to settle. The await keyword can be used only inside the async functions.

The following defines an async function that calls the three asynchronous operations in sequence:

```javascript

async function showServiceCost() {
    let user = await getUser(100);
    let services = await getServices(user);
    let cost = await getServiceCost(services);
    console.log(`The service cost is ${cost}`);
}

showServiceCost();
```

## The async keyword
The async keyword allows you to define a function that handles asynchronous operations.

To define an async function, you place the async keyword in front of the function keyword as follows:

```javascript
async function sayHi() {
    return 'Hi';
}
```

Asynchronous functions execute asynchronously via the event loop. It always returns a Promise.

```javascript
sayHi().then(console.log);
```
You can also explicitly return a Promise from the sayHi() function as shown in the following code:
```javascript
async function sayHi() {
    return Promise.resolve('Hi');
}
```

## The await keyword

You use the await keyword to wait for a Promise to settle either in resolved or rejected state. And you can use the await keyword only inside an async function:

```javascript
async function display() {
    let result = await sayHi();
    console.log(result);
}
```

In this example, the await keyword instructs the JavaScript engine to wait for the sayHi() function to complete before displaying the message.

Note that if you use the await operator outside of an async function, you will get an error.

## Error handling
If a promise resolves, the await promise returns the result. However, when the promise rejects, the await promise will throw an error as if there were a throw statement.
```javascript
async function getUser(userId) {
     await Promise.reject(new Error('Invalid User Id'));
}
```
Same way
```javascript
async function getUser(userId) {
    throw new Error('Invalid User Id');
}
```
You can catch the error by using the try...catch statement, the same way as a regular throw statement:

```javascript
async function getUser(userId) {
    try {
       const user = await Promise.reject(new Error('Invalid User Id'));
    } catch(error) {
       console.log(error);
    }
}
```

## What is async/await in JavaScript, and how does it work?
ES2017 introduced the async/await keywords that build on top of promises, allowing you to write asynchronous code that looks more like synchronous code and is more readable. Technically speaking, the async / await is syntactic sugar for promises.

The async keyword is used to define an asynchronous function, which always returns a promise. Within an async function, you can use the await keyword to pause the execution and wait for a promise to resolve or reject before proceeding to the next line.
