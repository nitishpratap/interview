# What is a Higher Order Function?
A higher order function is a function that takes one or more functions as arguments, or returns a function as its result.
There are several different types of higher order functions like map and reduce. 
```javascript
// Callback function, passed as a parameter in the higher order function
function callbackFunction(){
    console.log('I am  a callback function');
}

// higher order function
function higherOrderFunction(func){
    console.log('I am higher order function')
    func()
}

higherOrderFunction(callbackFunction);
```
In the above code higherOrderFunction() is an HOF because we are passing a callback function as a parameter to it.
## How Higher Order Functions Work

So, suppose I want you to write a function that calculates the area and diameter of a circle. As a beginner, the first solution that comes to our mind is to write each separate function to calculate area or diameter.
```javascript
const radius = [1, 2, 3];
```
```javascript
// function to calculate area of the circle
const calculateArea =  function (radius) {
    const output = [];
    for(let i = 0; i< radius.length; i++){
        output.push(Math.PI * radius[i] * radius[i]);
    }
    return output;
}
```
```javascript
// function to calculate diameter of the circle
const calculateDiameter =  function (radius) {
    const output = [];
    for(let i = 0; i< radius.length; i++){
        output.push(2 * radius[i]);
    }
    return output;
}
```
```javascript
console.log(calculateArea(radius));
console.log(calculateDiameter(radius))
```
But have you noticed the problem with the above code? Aren't we writing almost the same function again and again with slightly different logic? Also, the functions we have written aren't reusable, are they?
So, let's see how we can write the same code using HOFs:

```javascript
const radius = [1, 2, 3];

```
```javascript
// logic to clculate area
const area = function(radius){
    return Math.PI * radius * radius;
}

```
```javascript
// logic to calculate diameter
const diameter = function(radius){
    return 2 * radius;
}

```
```javascript
// a reusable function to calculate area, diameter, etc
const calculate = function(radius, logic){ 
    const output = [];
    for(let i = 0; i < radius.length; i++){
        output.push(logic(radius[i]))
    }
    return output;
}

```
```javascript
console.log(calculate(radius, area));
console.log(calculate(radius, diameter));

```
Suppose in the future if we want to write a program to calculate the circumference of the circle. We can simply write the logic to calculate the circumference and pass it to the calculate() function.
```javascript
const circumeference = function(radius){
    return 2 * Math.PI * radius;
}
```
```javascript
console.log(calculate(radius, circumeference));
```
## How to Use Higher Order Functions
* When working with arrays, you can use the map(), reduce(), filter(), and sort() functions to manipulate and transform data in an array.
* When working with objects, you can use the Object.entries() function to create a new array from an object.
* When working with functions, you can use the compose() function to create complex functions from simpler ones.

## How to use map() in JavaScript
The map() function takes an array of values and applies a transformation to each value in the array. It does not mutate the original array. It is often used to transform an array of data into a new array with a different structure.
**Example 1**: Suppose we want to add 10 to every element in a array. We can use the map() method to map over every element in the array to add 10 to it.
```javascript
const arr = [1, 2, 3, 4, 5];
const output = arr.map((num) => num += 10)
console.log(arr); // [1, 2, 3, 4, 5]
console.log(output); // [11, 12, 13, 14, 15]
```
**Example 2**: Here we have an array of users. Suppose we only want their first and last name. We can simply use the map() method to extract it from the users array.
```javascript
const users = [
    {firstName: 'John', lastName: 'Doe', age: 25},
    {firstName: 'Jane', lastName: 'Doe', age: 30},
    {firstName: 'Jack', lastName: 'Doe', age: 35},
    {firstName: 'Jill', lastName: 'Doe', age: 40},
    {firstName: 'Joe', lastName: 'Doe', age: 45},
]

const result = users.map((user) => user.firstName + ' ' + user.lastName)
console.log(result); // ['John Doe', 'Jane Doe', 'Jack Doe', 'Jill Doe', 'Joe Doe']
```
## How to Use filter() in JavaScript
The filter() function takes an array and returns a new array with only the values that meet certain criteria. It also does not mutate the original array. It is often used to select a subset of data from an array based on certain criteria.
**Example 1**: You can use filter() to return only the odd numbers from an array of numbers.
```javascript
const arr = [1, 2, 3, 4, 5];
const output = arr.filter((num) => num % 2) // filter out odd numbers
console.log(arr); // [1, 2, 3, 4, 5]
console.log(output); // [1, 3, 5]
```
**Example 2**: You can use filter() to return only the users having age greater than 30 in an array.
```javascript
const users = [
    {firstName: 'John', lastName: 'Doe', age: 25},
    {firstName: 'Jane', lastName: 'Doe', age: 30},
    {firstName: 'Jack', lastName: 'Doe', age: 35},
    {firstName: 'Jill', lastName: 'Doe', age: 40},
    {firstName: 'Joe', lastName: 'Doe', age: 45},
]

// Find the users with age greater than 30
const output = users.filter(({age}) => age > 30)
console.log(output); // [{firstName: 'Jack', lastName: 'Doe', age: 35}, {firstName: 'Jill', lastName: 'Doe', age: 40}, {firstName: 'Joe', lastName: 'Doe', age: 45}]
```
## How to use reduce() in JavaScript
In the case of the reduce() method, you should is used it when you want to perform some operation on the elements of an array and return a single value as a result. The "single value" refers to the accumulated result of repeatedly applying a function to the elements of a sequence.
For example, you might use reduce() to sum up all the elements in an array, to find the maximum or minimum value, to merge multiple objects into a single object, or to group different elements in an array.
**Example 1**: Using reduce() to sum up all the elements in an array:

```javascript
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((total, currentValue) => {
    return total + currentValue;
}, 0)

console.log(sum); // 15

```
**Example 2**: Using reduce() to find the maximum value in an array:
```javascript
let numbers = [5, 20, 100, 60, 1];
const maxValue = numbers.reduce((max, curr) => {
    if(curr > max) max = curr;
    return max;
});
console.log(maxValue); // 100
```
