# Declare a function
To declare a `function`, you use the function keyword, followed by the function name, a list of parameters, and the function body as follows:
```javascript
function functionName(parameters) {
    // function body
    // ...
}
```
* A function can accept zero, one, or multiple parameters.

```javascript
function say() {
}
```
```javascript
function square(a) {
    
}
```
```javascript
function add(a, b) {
    
}
```
## Calling a function
```javascript
functionName(arguments);
```
### Parameters vs. Arguments
The terms parameters and arguments are often used interchangeably. However, they are essentially different.
When declaring a function, you specify the parameters. However, when calling a function, you pass the arguments that are corresponding to the parameters.
### Function Expression
```javascript
var add = function (num1, num2) {
    return num1 + num2;
};

var result = add(10, 20);//returns 30
```
### Anonymous Function
In JavaScript, you can also create anonymous functions, which are functions without a name. Anonymous functions are often used as arguments to other functions, and are
```javascript
let numbers = [10, 20, 30, 40, 50];

let squareNumbers = numbers.map(function(number) {
  return number * number;
})
```
### Arrow Functions
```javascript
const multiply = (a, b) => a * b;

console.log(multiply(2, 3)); // 6

```
### Higher-Order Functions
Higher-order functions are functions that can take other functions as arguments or return a function as a result. They are commonly used for functional programming and code abstraction.
```javascript
function applyOperation(x, y, operation) {
  return operation(x, y);
}

const sum = (a, b) => a + b;
const difference = (a, b) => a - b;

console.log(applyOperation(5, 3, sum)); // 8
console.log(applyOperation(5, 3, difference)); // 2
```
### immediately Invoked Function
It is a JavaScript function that is executed as soon as it is defined. It is commonly used to create a separate scope for variables and to avoid polluting the global scope.
```javascript
(function() {
  // Code inside the IIFE
  var name = 'John';
  console.log('Hello, ' + name);
})();

```
### Functions as first-class citizens
functions can be treated like a variable. Meaning, they can be passed as arguments to other functions. It can be assigned as a value to a variable or even return in a function

1. **Functions can be assigned to variables**:
```javascript
const greet = function() {
  console.log('Hello!');
};

// The function is assigned to the variable greet
greet();

```
2. **Functions can be passed as arguments to other functions**:
```javascript
function executeFunction(func) {
  func();
}

function greet() {
  console.log('Hello!');
}

executeFunction(greet);

```
3. **Functions can be returned as values from other functions**:
```javascript
function createGreeter() {
  return function() {
    console.log('Hello!');
  };
}

const greet = createGreeter();
greet();

```
4. **Functions can be stored in data structures, such as arrays or objects**:
```javascript
const functionsArray = [
  function() {
    console.log('Function 1');
  },
  function() {
    console.log('Function 2');
  }
];

functionsArray[0]();

```
5. **Functions can have properties and methods**:
```javascript
function greet() {
  console.log('Hello!');
}

greet.message = 'Welcome'; // Adding a property to the function
console.log(greet.message);

```
