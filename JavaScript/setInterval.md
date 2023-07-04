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

## What is the setInterval() function in JavaScript, and how does it work?
The setInterval() function is a built-in JavaScript function used to repeatedly execute a specified function or code snippet at a defined interval. It takes two parameters: a callback function and a delay value.
```javascript
setInterval(callback, delay);
```
* callback: A function to be executed repeatedly at the specified interval.<br/>
* delay: The delay, in milliseconds, between each execution of the callback function.

```javascript
function displayTime() {
  const currentTime = new Date().toLocaleTimeString();
  console.log(currentTime);
}

setInterval(displayTime, 1000); // Executes displayTime() every 1 second

```

## How to stop setInterval and setTimeout
The clearInterval() function in JavaScript is used to stop the execution of a recurring function that was previously scheduled using setInterval(). It takes one parameter, which is the interval ID returned by setInterval() when the recurring function was set up.

```javascript
clearInterval(intervalID);
```
* intervalID: The unique identifier (interval ID) returned by setInterval() that corresponds to the recurring function you want to stop.
```javascript
function displayTime() {
  const currentTime = new Date().toLocaleTimeString();
  console.log(currentTime);
}

const intervalID = setInterval(displayTime, 1000); // Executes displayTime() every 1 second

// After 5 seconds, stop the recurring execution
setTimeout(() => {
  clearInterval(intervalID);
  console.log('Interval stopped.');
}, 5000);

```
