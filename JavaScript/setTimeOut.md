# Javascript setTimeout()

The setTimeout() method executes a block of code after the specified time. The method executes the code only once.

The commonly used syntax of JavaScript setTimeout is:

```javascript
setTimeout(function, milliseconds);

```

Its parameters are:

* function - a function containing a block of code
* milliseconds - the time after which the function is executed
The setTimeout() method returns an intervalID, which is a positive integer.

```javascript
// program to display a text using setTimeout method
function greet() {
    console.log('Hello world');
}

setTimeout(greet, 3000);
console.log('This message is shown first');
//This message is shown first
//Hello world
```

## Question: Can you explain the setTimeout() function and how it is used in JavaScript?
The setTimeout() function is a built-in JavaScript function that allows you to schedule the execution of a function after a specified delay, measured in milliseconds. It takes two parameters: a callback function and a delay value.
```javascript
setTimeout(callback, delay);
```
* callback: A function to be executed after the delay has elapsed.<br/>
* delay: The delay, in milliseconds, before the callback function is invoked.

```javascript
function sayHello() {
  console.log("Hello, world!");
}

setTimeout(sayHello, 2000); // Executes sayHello() after a 2-second delay

```
