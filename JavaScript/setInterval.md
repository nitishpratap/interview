# Javascript setInterval()

There are two methods for executing code at specific intervals. They are:

* setInterval()
* setTimeout()

## JavaScript setInterval()
The setInterval() method repeats a block of code at every given timing event.

The commonly used syntax of JavaScript setInterval is:

```javascript
setInterval(function, milliseconds);
```
Its parameters are:

* function - a function containing a block of code
* milliseconds - the time interval between the execution of the function 

The setInterval() method returns an intervalID which is a positive integer.

```javascript
// program to display a text using setInterval method
function greet() {
    console.log('Hello world');
}

setInterval(greet, 1000);
```



