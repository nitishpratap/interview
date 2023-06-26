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
```

