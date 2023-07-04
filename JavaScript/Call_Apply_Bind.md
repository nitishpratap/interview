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

# bind()

The bind() method in JavaScript is used to create a new function with a specified this value and an optional set of arguments. When you call bind() on a function, it returns a new function that, when executed, has its this keyword set to the provided value, and any arguments passed to bind() are prepended to the arguments provided to the bound function when it is called.

```javascript
function.bind(thisArg[, arg1[, arg2[, ...]]])
```
* thisArg: The value to be passed as the this parameter to the function when the bound function is called.<br/>
* arg1, arg2, ...: Optional arguments that are prepended to the arguments passed to the bound function when it is invoked.

```javascript
const person = {
  name: 'John',
  greet: function(message) {
    console.log(`${message}, ${this.name}!`);
  }
};

const greetFunction = person.greet.bind(person, 'Hello');
greetFunction(); // Output: Hello, John!

```

# apply()
The apply in Javascript is used to call a function in a different object with the given this value, and the arguments are passed in the form of an array. This method allows us to write methods that can be used on different objects and hence increase the reusability of code.

## What is apply() in Javascript?
The apply in Javascript is used when we need to call a method on object x with a different object y.

```javascript
const car = {
    'name': 'Altos',
    'speed': '120 KMPH',
    'drive': function() { 
        console.log(this.name + ' runs at ' + this.speed); 
    }
}

car.drive();

const bike = {
    'name': 'Jawa',
    'speed': '100 KMPH',
    'drive': function() { 
        console.log(this.name + ' runs at ' + this.speed); 
    }
}
Altos runs at 120 KMPH
Jawa runs at 100 KMPH

```

## Syntax of apply() in Javascript
The apply in Javascript accepts two arguments, the this value (object on which the function is to be called) and the list of the arguments (optional) that will be passed to the method it calls (fn).
```javascript
fn.apply(thisArg)
fn.apply(thisArg, argumentsList)

```
```javascript
function intro(message) {
    console.log(message + ' ' + this.firstname + ' ' + this.lastname);
}

const student1 = {
    'firstname': 'Tony',
    'lastname': 'Stark'
};

const student2 = {
    'firstname': 'Steve',
    'lastname': 'Rogers'
}

intro.apply(student1, ['Hello! I am']);
intro.apply(student2, ['Hi! I am']);

Hello! I am Tony Stark
Hi! I am Steve Rogers

```

```javascript
const mobile = {
    'ram': '8 GB',
    'storage': '256 GB',
    'display': 'IPS',
    'model': 'Pixel 3',
    'specs': function() {
        console.log('Model: ' + this.model + '\n'
                   + 'RAM: ' + this.ram + '\n'
                   + 'Storage: ' + this.storage + '\n'
                   + 'Display: ' + this.display + '\n');
    }
}

const laptop = {
    'ram': '16 GB',
    'storage': '512 GB',
    'display': 'Retina',
    'model': 'Macbook Pro'
}

mobile.specs.apply(laptop);

Model: Macbook Pro
RAM: 16 GB
Storage: 512 GB
Display: Retina

```
