# For Of loop
The "for...of" loop in JavaScript is used to iterate over iterable objects such as arrays, strings, maps, sets, and more. It provides a simpler and more readable syntax compared to traditional for loops or forEach loops. Here's an explanation and example of using the "for...of" loop:

```javascript
for (variable of iterable) {
  // Code to be executed for each iteration
}

```
1. The "variable" represents a new variable that will take on the value of each element in the iterable object during each iteration.
2. The "iterable" is an object that is iterable, meaning it has a defined iteration behavior. Examples of iterable objects include arrays, strings, maps, sets, etc.

```javascript
const fruits = ['apple', 'banana', 'orange'];

for (const fruit of fruits) {
  console.log(fruit);
}
//apple
//banana
//orange

```

```javascript
// Iterating over a string
const message = 'Hello';

for (const char of message) {
  console.log(char);
}
H
e
l
l
o

```

```javascript
// Iterating over a map
const map = new Map();
map.set(1, 'one');
map.set(2, 'two');
map.set(3, 'three');

for (const [key, value] of map) {
  console.log(key, value);
}

1 'one'
2 'two'
3 'three'

```

