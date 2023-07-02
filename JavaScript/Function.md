# Define a function
Function is a set of statement that is used to perform a particualr task.

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
// A regular named function
function greet(name) {
    console.log("Hello, " + name + "!");
}

// Using an anonymous function
var greetAnonymous = function(name) {
    console.log("Hello, " + name + "!");
};
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

### Map() in js
The syntax of the map() method is:
```javascript
arr.map(callback(currentValue), thisArg)
```
#### map() Parameters
The map() method takes in:

1. **callback** - The function called for every array element. Its return values are added to the new array. It takes in: <br/>
   * **currentValue** - The current element being passed from the array.
   * **thisArg (optional)** - Value to use as this when executing callback. By default, it is undefined.

#### map() Return Value
Returns a new array with elements as the return values from the callback function for each element.
#### Notes:

* map() does not change the original array.
* map() executes callback once for each array element in order.
* map() does not execute callback for array elements without values.

```javascript
// An array of numbers
var numbers = [1, 2, 3, 4, 5];

// Doubling each number using map()
var doubledNumbers = numbers.map(function(num) {
  return num * 2;
});

console.log(doubledNumbers);
// Output: [2, 4, 6, 8, 10]

```

### Filter() in js
The filter() method returns a new array with all elements that pass the test defined by the given function.
#### filter() Syntax
```javascript
arr.filter(callback(element), thisArg)
```
#### filter() Parameters
The filter() method takes in:<br/>
1. **callback** - The test function to execute on each array element; returns true if element passes the test, else false. It takes in: <br/>
2. **element** - The current element being passed from the array.
3. **thisArg (optional)** - The value to use as this when executing callback. By default, it is undefined.

#### filter() Return Value
Returns a new array with only the elements that passed the test.
```javascript
// An array of numbers
var numbers = [1, 2, 3, 4, 5];

// Filtering even numbers using filter()
var evenNumbers = numbers.filter(function(num) {
  return num % 2 === 0;
});

console.log(evenNumbers);
// Output: [2, 4]

```

### reduce() in js
The reduce() method executes a reducer function on each element of the array and returns a single output value.
#### reduce() Syntax
```javascript
arr.reduce(callback(accumulator, currentValue), initialValue)
```
#### reduce() Parameters
The reduce() method takes in:<br/>
1. **callback -** The function to execute on each array element (except the first element if no initialValue is provided). It takes in <br/>
2. **accumulator -** It accumulates the callback's return values.<br/>
3. **currentValue -** The current element being passed from the array.<br/>
4. **initialValue (optional)** - A value that will be passed to callback() on first call. If not provided, the first element acts as the accumulator on the first call and callback() won't execute on it.<br/>
**Note:** `Calling reduce() on an empty array without initialValue will throw TypeError.`

#### reduce() Return Value
Returns the single value resulting after reducing the array.

**Notes:**

* reduce() executes the given function for each value from left to right.
* reduce() does not change the original array.
* It is almost always safer to provide initialValue.
```javascript
// An array of numbers
var numbers = [1, 2, 3, 4, 5];

// Summing all numbers using reduce()
var sum = numbers.reduce(function(acc, num) {
  return acc + num;
}, 0);

console.log(sum);
// Output: 15

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
