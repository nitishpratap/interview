# What is this keyword
In general, the `this` references the object of which the function is a property. In other words, the `this` references the object that is currently calling the function.

Suppose you have an object called counter that has a method next(). When you call the next() method, you can access the this object.
```javascript
let counter = {
  count: 0,
  next: function () {
    return ++this.count;
  },
};

counter.next();
```

Inside the next() function, the `this` references the counter object. See the following method call:
```javascript
counter.next();
```

## Global context
In the global context, the `this` references the `global object`, which is the `window` object on the web browser or `global` object on Node.js.

This behavior is consistent in both strict and non-strict modes. Here’s the output on the web browser:
```javascript
console.log(this === window); // true
```
If you assign a property to this object in the global context, JavaScript will add the property to the global object as shown in the following example:
```javascript
this.color= 'Red';
console.log(window.color); // 'Red'
```

## Function context
In JavaScript, you can call a function in the following ways:
* Function invocation
* Method invocation
* Constructor invocation
* Indirect invocation

### 1) Simple function invocation

In the non-strict mode, the this references the global object when the function is called as follows:
```javascript
function show() {
   console.log(this === window); // true
}

show();
```

When you call the `show()` function, the `this` references the global object, which is the `window` on the web browser and `global` on Node.js.
Calling the `show()` function is the same as:
```javascript
window.show();
```
```javascript
"use strict";

function show() {
    console.log(this === undefined);
}

show();
```

### 2) Method invocation

When you call a method of an object, JavaScript sets this to the object that owns the method. See the following car object:
```javascript
let car = {
    brand: 'Honda',
    getBrand: function () {
        return this.brand;
    }
}

console.log(car.getBrand()); // Honda
```

In this example, the this object in the getBrand() method references the car object.

Since a method is a property of an object which is a value, you can store it in a variable.
```javascript
let brand = car.getBrand;
```
```javascript
console.log(brand()); // undefined
```
You get undefined instead of "Honda" because when you call a method without specifying its object, JavaScript sets this to the global object in non-strict mode and undefined in the strict mode.

To fix this issue, you use the bind() method of the Function.prototype object. The bind() method creates a new function whose the this keyword is set to a specified value.

```javascript
let brand = car.getBrand.bind(car);
console.log(brand()); // Honda

```

### 3) Constructor invocation
When you use the new keyword to create an instance of a function object, you use the function as a constructor.

The following example declares a Car function, then invokes it as a constructor:

```javascript
function Car(brand) {
    this.brand = brand;
}

Car.prototype.getBrand = function () {
    return this.brand;
}

let car = new Car('Honda');
console.log(car.getBrand());
```

### 4) Indirect Invocation
In JavaScript, functions are first-class citizens. In other words, functions are objects, which are instances of the Function type.

The Function type has two methods: call() and apply() . These methods allow you to set the this value when calling a function. For example:

```javascript
function getBrand(prefix) {
    console.log(prefix + this.brand);
}

let honda = {
    brand: 'Honda'
};
let audi = {
    brand: 'Audi'
};

getBrand.call(honda, "It's a ");
getBrand.call(audi, "It's an ");
```

```javascript
It's a Honda
It's an Audi
```

## Arrow functions
ES6 introduced a new concept called arrow function. In arrow functions, JavaScript sets the this lexically.

It means the arrow function does not create its own execution context but inherits the this from the outer function where the arrow function is defined. See the following example:

```javascript
let getThis = () => this;
console.log(getThis() === window); // true
```
In this example, the this value is set to the global object i.e., window in the web browser.

Since an arrow function does not create its own execution context, defining a method using an arrow function will cause an issue. For example:
```javascript
function Car() {
  this.speed = 120;
}

Car.prototype.getSpeed = () => {
  return this.speed;
};

var car = new Car();
console.log(car.getSpeed()); // 👉 undefined
```


