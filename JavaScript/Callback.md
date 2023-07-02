# What are callbacks
a callback is a function that is passed as an argument to another function and is invoked (called) by that function at a specific time or in response to a certain event. 

Callbacks are commonly used in scenarios where the order of execution is not linear or predictable, such as asynchronous operations, event handling, or when working with APIs that require waiting for a response.
The following defines a filter() function that accepts an array of numbers and returns a new array of odd numbers:
```javascript
function isOdd(number) {
    return number % 2 != 0;
}

function filter(numbers, fn) {
    let results = [];
    Ffor (const number of numbers) {
        if (fn(number)) {
            results.push(number);
        }
    }
    return results;
}
let numbers = [1, 2, 4, 7, 3, 5, 6];
console.log(filter(numbers, isOdd));
```
**There are two types of callbacks: synchronous and asynchronous callbacks.**

## Synchronous callbacks
Synchronous callbacks refer to a type of callback function that is executed immediately within the same execution context or thread of the calling function. In other words, the execution of the callback blocks the further execution of the program until the callback function has completed its execution.


```javascript
function calculateSquare(number, callback) {
    const square = number * number;
    callback(square);
}

function displayResult(result) {
    console.log("The result is: " + result);
}

calculateSquare(5, displayResult);
console.log("End of script");
//The result is: 25
//End of script

```
## Asynchronous callbacks
Asynchronous callbacks refer to a type of callback function that  allow the program to continue its execution without waiting for the callback to complete. It enables non-blocking behavior and is commonly used in scenarios where tasks take longer to complete or involve I/O operations.
Asynchronicity means that if JavaScript has to wait for an operation to complete, it will execute the rest of the code while waiting.
Note that JavaScript is a single-threaded programming language. It carries asynchronous operations via the callback queue and event loop.

Suppose that you need to develop a script that downloads a picture from a remote server and process it after the download completes:

```javascript
function download(url) {
    // ...
}

function process(picture) {
    // ...
}

download(url);
process(picture);
```
However, downloading a picture from a remote server takes time depending on the network speed and the size of the picture.

The following download() function uses the setTimeout() function to simulate the network request:
```javascript
function download(url) {
    setTimeout(() => {
        // script to download the picture here
        console.log(`Downloading ${url} ...`);
    },1000);
}
```
And this code emulates the process() function:

```javascript
function process(picture) {
    console.log(`Processing ${picture}`);
}
```
When you execute the following code:
```javascript
let url = 'https://www.javascripttutorial.net/pic.jpg';

download(url);
process(url);
```
you will get the following output:
```javascript
//      Processing https://javascripttutorial.net/pic.jpg
//      Downloading https://javascripttutorial.net/pic.jpg ...
```
This is not what you expected because the process() function executes before the download() function. The correct sequence should be:
* Download the picture and wait for the download completes.
Process the picture.
* Process the picture.



To resolve this issue, you can pass the process() function to the download() function and execute the process() function inside the download() function once the download completes, like this:

```javascript
function download(url, callback) {
    setTimeout(() => {
        // script to download the picture here
        console.log(`Downloading ${url} ...`);
        
        // process the picture once it is completed
        callback(url);
    }, 1000);
}

function process(picture) {
    console.log(`Processing ${picture}`);
}

let url = 'https://wwww.javascripttutorial.net/pic.jpg';
download(url, process);

/// Output:
//  Downloading https://www.javascripttutorial.net/pic.jpg ...
//    Processing https://www.javascripttutorial.net/pic.jpg
```

### Nesting callbacks and the Pyramid of Doom
```javascript
function download(url, callback) {
  setTimeout(() => {
    console.log(`Downloading ${url} ...`);
    callback(url);
  }, 1000);
}

const url1 = 'https://www.javascripttutorial.net/pic1.jpg';
const url2 = 'https://www.javascripttutorial.net/pic2.jpg';
const url3 = 'https://www.javascripttutorial.net/pic3.jpg';

download(url1, function (url) {
  console.log(`Processing ${url}`);
  download(url2, function (url) {
    console.log(`Processing ${url}`);
    download(url3, function (url) {
      console.log(`Processing ${url}`);
    });
  });
});

```

**Nesting many asynchronous functions inside callbacks is known as the pyramid of doom or the callback hell:**

```javascript
asyncFunction(function(){
    asyncFunction(function(){
        asyncFunction(function(){
            asyncFunction(function(){
                asyncFunction(function(){
                    ....
                });
            });
        });
    });
});

```
