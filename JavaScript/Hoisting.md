# Introduction to the JavaScript hoisting
When the JavaScript engine executes the JavaScript code, it creates the global execution context. The global execution context has two phases:
* Creation
* Execution

During the creation phase, the JavaScript engine moves the variable and function declarations to the top of your code. This is known as hoisting in JavaScript.
## Variable hoisting
Variable hoisting means the JavaScript engine moves the variable declarations to the top of the script.
```javascript
console.log(counter); // 👉 undefined
var counter = 1;
```
Technically, the code looks like the following in the execution phase:
```javascript
var counter;

console.log(counter); // 👉 undefined
counter = 1;

```
## The let keyword
The following declares the variable counter with the let keyword:
```javascript
console.log(counter);
let counter = 1;
```
```javascript
"ReferenceError: Cannot access 'counter' before initialization"
```

## Function hoisting
Like variables, the JavaScript engine also hoists the function declarations. This means that the JavaScript engine also moves the function declarations to the top of the script. For example:
```javascript
let x = 20,
  y = 10;

let result = add(x, y); 
console.log(result); // 👉 30

function add(a, b) {
  return a + b;
}
//output 30
```
## Note
* JavaScript hoisting occurs during the creation phase of the execution context that moves the variable and function declarations to the top of the script.
* The JavaScript engine hoists the variables declared using the let keyword, but it doesn’t initialize them as the variables declared with the var keyword.
* The JavaScript engine doesn’t hoist the function expressions and arrow functions.
