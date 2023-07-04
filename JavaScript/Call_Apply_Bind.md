# call()
A function/method belonging to one object can be assigned to and invoked for another object using the call() method. It can be used for constructor chaining, invoking anonymous functions,
## Syntax of Function call() in Javascript

```javascript
myFunction.call()
myFunction.call(thisArg)
myFunction.call(thisArg, arg1)
myFunction.call(thisArg, arg1, arg2)
myFunction.call(thisArg, arg1, arg2, …, argN)

```
## Parameters of Function call() in Javascript
The following are the parameters of call() in javascript:

thisArg (optional) : the this value (context) when invoking the function.<br/>
...argN (optional) : function arguments as they are present in the calling function.

## Return Value of Function call() in Javascript
Return Type: same as the return type of the calling function

The return value of the call method is the return value of the calling function with the passed thisArg value and the arguments.

```javascript
let obj = {
    sal: "hello"
}
function greet(name) {
    console.log(this.sal + " " + name);
}
greet.call(obj, "Michael"); // hello Michael

```

## What is call()
In JavaScript, the call() method is used to invoke a function and explicitly specify the context (i.e., the value of this) within which the function should be executed. It allows you to borrow a method from one object and use it for another object.
```javascript
const person1 = {
  name: 'Alice',
  greet: function() {
    console.log(`Hello, ${this.name}!`);
  }
};

const person2 = {
  name: 'Bob'
};

person1.greet(); // Output: Hello, Alice!

person1.greet.call(person2); // Output: Hello, Bob!

```
