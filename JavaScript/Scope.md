# Scope and Scope Chain in JavaScript
## What is Scope?
Scope in JavaScript refers to the accessibility or visibility of variables. That is, which parts of a program have access to the variable or where the variable is visible.

## Why is Scope Important?
1. *The main benefit of scope is security. That is, the variables can be accessed from only a certain area of the program. Using scope, we can avoid unintended modifications to the variables from other parts of the program.*
2. *The scope also reduces the namespace collisions. That is, we can use the same variable names in different scopes.*

## Types of Scope
There are three types of scope in JavaScript — 1) **Global Scope**, 2) **Function Scope**, and, 3) **Block Scope**.
### 1. Global Scope
Any variable that’s not inside any function or block (a pair of curly braces), is inside the global scope. The variables in global scope can be accessed from anywhere in the program. For example:
```javascript
var greeting = 'Hello World!';
function greet() {
  console.log(greeting);
}
// Prints 'Hello World!'
greet();
```
### 2. Local Scope or Function Scope
Variables declared inside a function is inside the local scope. They can only be accessed from within that function, that means they can’t be accessed from the outside code. For example:
```javascript
function greet() {
  var greeting = 'Hello World!';
  console.log(greeting);
}
// Prints 'Hello World!'
greet();
// Uncaught ReferenceError: greeting is not defined
console.log(greeting);

```
### 3. Block Scope
ES6 introduced let and const variables, unlike var variables, they can be scoped to the nearest pair of curly braces. That means, they can’t be accessed from outside that pair of curly braces. For example:
```javascript
{
  let greeting = 'Hello World!';
  var lang = 'English';
  console.log(greeting); // Prints 'Hello World!'
}
// Prints 'English'
console.log(lang);
// Uncaught ReferenceError: greeting is not defined
console.log(greeting);
```
## Lexical Scope
Lexical Scope (also known as Static Scope) literally means that scope is determined at the lexing time (generally referred to as compiling) rather than at runtime. For example:
```javascript
let number = 42;
function printNumber() {
  console.log(number);
}
function log() {
  let number = 54;
  printNumber();
}
// Prints 42
log();
```
## Scope Chain
When a variable is used in JavaScript, the JavaScript engine will try to find the variable’s value in the current scope. If it could not find the variable, it will look into the outer scope and will continue to do so until it finds the variable or reaches global scope.

If it’s still could not find the variable, it will either implicitly declare the variable in the global scope (if not in strict mode) or return an error.
```javascript
let foo = 'foo';
function bar() {
  let baz = 'baz';
  // Prints 'baz'
  console.log(baz);
  // Prints 'foo'
  console.log(foo);
  number = 42;
  console.log(number);  // Prints 42
}
bar();

```

If the script is not in strict mode, the engine will create a new variable named number and assign 42 to it or return an error (if not in strict mode).

## What is a Lexical Environment?
A lexical environment is a structure that holds identifier-variable mapping. (here identifier refers to the name of variables/functions, and the variable is the reference to actual object [including function object and array object] or primitive value).

Simply put, a lexical environment is a place where variables and references to the objects are stored.

Note — Don’t confuse lexical scope with the lexical environment, lexical scope is a scope that is determined at compile time and a lexical environment is a place where variables are stored during the program execution.

Conceptually a lexical environment looks like this:
```javascript
lexicalEnvironment = {
  a: 25,
  obj: <ref. to the object>
}

```

A new lexical environment is created for each lexical scope but only when the code in that scope is executed. The lexical environment also has a reference to its outer lexical environment ( i.e outer scope). For example:

