# Map
## Issue with objects
1. Object keys can only be of type string.
2. Objects don't maintain the order of the elements inserted into them.
3. Objects lack some useful methods, which makes them difficult to use in some situations. For example, you can't compute the size (length) of an object easily. Also, enumerating an object is not that straightforward.
4. Arrays are collections of elements that allow duplicates. Supporting arrays that only have distinct elements requires extra logic and code.

_Map is a collection of key-value pairs where the key can be of any type. Map remembers the original order in which the elements were added to it, which means data can be retrieved in the same order it was inserted in._
Map has characteristics of both Object and Array:
* Like an object, it supports the key-value pair structure.
* Like an array, it remembers the insertion order.

## How to Create and Initialize a Map in JavaScript
```javascript
const map = new Map();
```
_Another way of creating a Map is with initial values. Here's how to create a Map with three key-value pairs:_
```javascript
const freeCodeCampBlog = new Map([
  ['name', 'freeCodeCamp'],
  ['type', 'blog'],
  ['writer', 'Tapas Adhikary'],
]);
```
Which returns a Map with three elements:
```javascript
Map(3) {"name" => "freeCodeCamp", "type" => "blog", "writer" => "Tapas Adhikary"}
```
## How to Add values to a Map in JavaScript
To add value to a Map, use the set(key, value) method.
The set(key, value) method takes two parameters, key and value, where the key and value can be of any type, a primitive (boolean, string, number, etc.) or an object:

```javascript
// create a map
const map = new Map();

// Add values to the map
map.set('name', 'freeCodeCamp');
map.set('type', 'blog');
map.set('writer', 'Tapas Adhikary');

```
Output:
```javascript
Map(3) {"name" => "freeCodeCamp", "type" => "blog", "writer" => "Tapas Adhikary"}

```
Please note, if you use the same key to add a value to a Map multiple times, it'll always replace the previous value:
```javascript
// Add a different writer
map.set('writer', 'Someone else!');
```
```javascript
Map(3) 
{"name" => "freeCodeCamp", "type" => "blog", "writer" => "Someone else!"}
```
## How to Get values from a Map in JavaScript
To get a value from a Map, use the get(key) method:
```javascript
map.get('name'); // 
```
## All About Map Keys in JavaScript
Map keys can be of any type, a primitive, or an object. This is one of the major differences between Map and regular JavaScript objects where the key can only be a string:
```javascript
const funMap = new Map();

funMap.set(360, 'My House Number'); // number as key
funMap.set(true, 'I write blogs!'); // boolean as key

let obj = {'name': 'tapas'}
funMap.set(obj, true); // object as key

console.log(funMap);
```
Here is output
```javascript
Map(3)
{
    360 => "My House Number",
    true => "I write blogs!",
    {…} => true
}
```
* A regular JavaScript object always treats the key as a string. Even when you pass it a primitive or object, it internally converts the key into a string:

## Map Properties and Methods in JavaScript
JavaScript's Map has in-built properties and methods that make it easy to use. Here are some of the common ones:

* Use the size property to know how many elements are in a Map:
```javascript
const map1 = new Map();

map1.set('a', 'alpha');
map1.set('b', 'beta');
map1.set('g', 'gamma');


console.log(map1.size);
// Expected output: 3

```
* Search an element with the has(key) method:
* Remove an element with the delete(key) method:
* Use the clear() method to remove all the elements from the Map at once:

```javascript
console.log('size of the map is', map.size);
// returns true, if map has an element with the key, 'John'
console.log(map.has('John')); 


// returns false, if map doesn't have an element with the key, 'Tapas'
console.log(map.has('Tapas')); 
map.delete('Sam'); // removes the element with key, 'Sam'.
// Clear the map by removing all the elements
map.clear(); 

map.size // It will return, 0
```

## MapIterator: keys(), values(), and entries() in JavaScript
The methods keys(), values() and entries() methods return a MapIterator, which is excellent because you can use a for-of or forEach loop directly on it.
Let a map as 
```javascript
const ageMap = new Map([
  ['Jack', 20],
  ['Alan', 34],
  ['Bill', 10],
  ['Sam', 9]
]);
```
* Get all the keys:
* Get all the values:
* Get all the entries (key-value pairs):

```javascript
console.log(ageMap.keys());

// Output:

// MapIterator {"Jack", "Alan", "Bill", "Sam"}
console.log(ageMap.values());

// Output

// MapIterator {20, 34, 10, 9}
console.log(ageMap.entries());

// Output

// MapIterator {"Jack" => 20, "Alan" => 34, "Bill" => 10, "Sam" => 9}
```

## How to Iterate Over a Map in JavaScript
You can use either the forEach or for-of loop to iterate over a Map:

```javascript
// with forEach
ageMap.forEach((value, key) => {
   console.log(`${key} is ${value} years old!`);
});

// with for-of
for(const [key, value] of ageMap) {
  console.log(`${key} is ${value} years old!`);
}


    Jack is 20 years old!
    Alan is 34 years old!
    Bill is 10 years old!
    Sam is 9 years old!
```
## How to Convert an Object into a Map in JavaScript
```javascript
const address = {
  'Tapas': 'Bangalore',
  'James': 'Huston',
  'Selva': 'Srilanka'
};

const addressMap = new Map(Object.entries(address));
```
## How to Convert a Map into an Object in JavaScript
```javascript
Object.fromEntries(map)

```
## How to Convert a Map into an Array in JavaScript
There are a couple of ways to convert a map into an array:
1. Using Array.from(map):
2. Using the spread operator:
```javascript
const map = new Map();
map.set('milk', 200);
map.set("tea", 300);
map.set('coffee', 500);

console.log(Array.from(map));
//[ [ 'milk', 200 ], [ 'tea', 300 ], [ 'coffee', 500 ] ]
```

```javascript
console.log([...map]);
```

## Map vs. Object: When should you use them?
Use Map when:

* Your needs are not that simple. You may want to create keys that are non-strings. Storing an object as a key is a very powerful approach. Map gives you this ability by default.
* You need a data structure where elements can be ordered. Regular objects do not maintain the order of their entries.
* You are looking for flexibility without relying on an external library like lodash. You may end up using a library like lodash because we do not find methods like has(), values(), delete(), or a property like size with a regular object. Map makes this easy for you by providing all these methods by default.

Use an object when:

* You do not have any of the needs listed above.
* You rely on JSON.parse() as a Map cannot be parsed with it.

# Set in JS
A Set is a collection of unique elements that can be of any type. Set is also an ordered collection of elements, which means that elements will be retrieved in the same order that they were inserted in.
A Set in JavaScript behaves the same way as a mathematical set.

## How to Create and Initialize a Set in JavaScript
```javascript
const set = new Set();
console.log(set);


//Output Set(0) {}
```
```javascript
const fruteSet = new Set(['🍉', '🍎', '🍈', '🍏']);
console.log(fruteSet);

// Set(4) {"🍉", "🍎", "🍈", "🍏"}
```
## Set Properties and Methods in JavaScript
Set has methods to add an element to it, delete elements from it, check if an element exists in it, and to clear it completely:
* Use the size property to know the size of the Set. It returns the number of elements in it:
* Use the add(element) method to add an element to the Set:
```javascript
set.size
```
```javascript
// Create a set - saladSet
const saladSet = new Set();

// Add some vegetables to it
saladSet.add('🍅'); // tomato
saladSet.add('🥑'); // avocado
saladSet.add('🥕'); // carrot
saladSet.add('🥒'); // cucumber

console.log(saladSet);


// Output

// Set(4) {"🍅", "🥑", "🥕", "🥒"}

```

```javascript
saladSet.add('🥒');
console.log(saladSet);

```

* To remove elements there is `clear()` method

## How to Iterate Over a Set in JavaScript
Set has a method called values() which returns a SetIterator to get all its values:
```javascript
// Create a Set
const houseNos = new Set([360, 567, 101]);

// Get the SetIterator using the `values()` method
console.log(houseNos.values());

// SetIterator {360, 567, 101}
```
We can use a forEach or for-of loop on this to retrieve the values.
Interestingly, JavaScript tries to make Set compatible with Map. That's why we find two of the same methods as Map, keys() and entries().

As Set doesn't have keys, the keys() method returns a SetIterator to retrieve its values:

## Sets and Arrays in JavaScript
An array, like a Set, allows you to add and remove elements. But Set is quite different, and is not meant to replace arrays.

The major difference between an array and a Set is that arrays allow you to have duplicate elements. Also, some of the Set operations like delete() are faster than array operations like shift() or splice().

Think of Set as an extension of a regular array, just with more muscles. The Set data structure is not a replacement of the array. Both can solve interesting problems.

## How to Convert a Set into an array in JavaScript
```javascript
const arr = [...houseNos];
console.log(arr);
```
## Unique values from an array using the Set in JavaScript
Creating a Set is a really easy way to remove duplicate values from an array:
```javascript
// Create a mixedFruit array with a few duplicate fruits
const mixedFruit = ['🍉', '🍎', '🍉', '🍈', '🍏', '🍎', '🍈'];

// Pass the array to create a set of unique fruits
const mixedFruitSet = new Set(mixedFruit);

console.log(mixedFruitSet);

Output:

    Set(4) {"🍉", "🍎", "🍈", "🍏"}
```
