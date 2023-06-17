# Primitive and Non-primitive Data Types in JavaScript

JavaScript has two types of data types: primitive and non-primitive.

## Primitive Data Types

Primitive data types are the predefined data types provided by the JavaScript language. They are also known as in-built data types. The primitive data types in JavaScript are:

1. **Number**: The number data type in JavaScript can hold both decimal and non-decimal values.

```javascript
let x = 250;
let y = 40.5;
console.log("Value of x=" + x);
console.log("Value of y=" + y);
```

2. **String**: The string data type in JavaScript represents a sequence of characters enclosed in single or double quotes.

```javascript
let str = 'Hello All';
let str1 = "Welcome to my new house";
console.log("Value of str=" + str);
console.log("Value of str1=" + str1);
```

3. **Undefined**: The undefined data type signifies that a value is not assigned to a variable.

4. **Boolean**: The boolean data type can have only two values: true and false.

5. **Null**: The null data type can hold only one value, which is null.

```javascript
let x = null;
console.log("Value of x=" + x);
```

6. **BigInt**: The bigint data type can represent numbers greater than 2^53-1 and is used for performing operations on large numbers. The number is specified by appending 'n' to the end of the value.

```javascript
let bigNum = 123422222222222222222222222222222222222n;
console.log(bigNum);
```

7. **Symbol**: The symbol data type is used to create unique objects. Symbols are created using the Symbol constructor.

```javascript
let sym = Symbol("Hello");
console.log(typeof(sym));
console.log(sym);
```

## Non-primitive Data Types

Non-primitive data types are derived from primitive data types in JavaScript. They are also known as derived or reference data types. The non-primitive data types in JavaScript are:

1. **Object**: An object in JavaScript is an entity that has properties and methods. In JavaScript, everything is an object.

2. **Array**: JavaScript arrays are used to store elements of different data types. Arrays are zero-indexed, and they are not associative in nature.

```javascript
// Creating an array using array literal:
let courses = ["HTML", "CSS", "JavaScript", "React"];
console.log(courses);

// Creating an array using the new keyword:
let arr1 = new Array(3);
arr1[0] = 10;
arr1[1] = 20;
arr1[2] = 30;
console.log("Array 1: ", arr1);

let arr2 = new Array(10, 20, 30, 40, 50);
console.log("Array 2: ", arr2);

let arr3 = new Array(5);
console.log("Array 3: ", arr3);

let arr4 = new Array("1BHK");
console.log("Array 4: ", arr4);
```

### Difference between Primitive and Non-primitive Data Types:

| Primitive                | Non-Primitive             |
|--------------------------|---------------------------|
| Predefined data types    | Created by the programmer |
| Has certain values       | Can be null               |
| Size depends on the data structure | Size is not fixed |
| Examples: numbers, strings | Examples: objects, arrays |

## Objects

Objects in JavaScript are entities that have properties and methods. There are multiple ways to create objects in JavaScript:

1. Object literal


```javascript
const firstObj = {
  1: "deepak",
  "age": 28
};
```

2. Object.create(): This method creates a new object with the specified prototype and properties of the old object.

```javascript
const newStudent = Object.create(student);
```

3. Object Instance: The use of Object constructor in conjunction with the "new" keyword allows us to initialize new objects.

```javascript
const newObj = new Object();
newObj.name = 'Deepak';
newObj.location = 'Delhi, India';
```

### Adding, Updating, and Removing Properties of an Object

Properties can be added to an object using dot notation or bracket notation.

```javascript
const a = {};
a.name = 'deepak';
a['city'] = 'delhi';
a[1] = 'dope';
```

To iterate over the properties of an object, you can use loops like for...in and for...of loops.

```javascript
for (const key in a) {
   console.log(key, a[key]);
}
```
Note we need to do a[key] to access value if i write a.key then it will `undefined`
## Shallow Copy and Deep Copy in JavaScript

In JavaScript, there are two ways to copy objects: shallow copy and deep copy.

### Shallow Copy

A shallow copy creates a new object, but any nested objects or arrays within the original object still reference the same memory location. Changes to the nested objects will affect both the original and copied objects. Here's an example of shallow copying using the spread operator:

```javascript
const originalObject = { a: 1, b: { c: 2 } };
const shallowCopy = { ...originalObject };
```

### Deep Copy

A deep copy creates a new object with new memory locations for all properties and nested objects or arrays. Changes made to the copied object or its nested objects will not affect the original object. Here's an example of deep copying using JSON methods:

```javascript
const originalObject = { a: 1, b: { c: 2 } };
const deepCopy = JSON.parse(JSON.stringify(originalObject));
```

## Spread Operator

The spread operator `...` is used to expand or spread an iterable or an array. It can be used to copy items into a single array or to clone arrays and objects. Examples:

```javascript
const arrValue = ['My', 'name', 'is', 'Jack'];
console.log(arrValue);   // ["My", "name", "is", "Jack"]
console.log(...arrValue); // My name is Jack

const arr1 = ['one', 'two'];
const arr2 = [...arr1, 'three', 'four', 'five'];
console.log(arr2);
// Output: ["one", "two", "three", "four", "five"]
```

To clone an array using the spread operator:

```javascript
let arr1 = [1, 2, 3];
let arr2 = [...arr1];
```

To clone an object using the spread operator:

```javascript
const obj1 = { x: 1, y: 2 };
const obj2 = { ...obj1 };
```

## Rest Parameter

The rest parameter allows a function to accept multiple arguments as an array. It uses the spread operator and is useful when the number of arguments is not known beforehand. Example:

```javascript
let func = function(...args) {
    console.log(args);
}

func(3);            // [3]
func(4, 5, 6);      // [4, 5, 6]
```
