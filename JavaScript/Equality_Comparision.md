# Equality Comparison in JavaScript:
In JavaScript, there are two types of equality comparisons: strict equality and loose equality.

## 1. Strict Equality (===):

* The strict equality operator (===) compares the equality of two values without performing type coercion.
* It returns true if the operands are of the same type and have the same value, and false otherwise.
```javascript
5 === 5;        // true
'hello' === 'hello';    // true
5 === '5';      // false (different types)

```

## 2. Strict Inequality (!==):
* The strict inequality operator (!==) is the negation of strict equality. It checks if the operands are not equal without performing type coercion.
* It returns true if the operands are of different types or have different values, and false otherwise.
```javascript
5 !== 10;       // true
'hello' !== 'world';    // true
5 !== 5;        // false

```

## 3. Loose Equality (==):
* The loose equality operator (==) compares the equality of two values after performing type coercion.
* It allows for comparisons between different types by converting one or both operands to a common type before the comparison.

```javascript
5 == 5;         // true
'5' == 5;       // true (string '5' is converted to a number)
'hello' == 'hello';    // true
0 == false;     // true (boolean false is converted to number 0)

```
## 4. Loose Inequality (!=):
* The loose inequality operator (!=) is the negation of loose equality. It performs type coercion before checking for inequality.
* It returns true if the operands are of different types or have different values after type coercion, and false otherwise.
```javascript
5 != 10;        // true
'5' != 5;       // false (string '5' is converted to a number, equal to 5)
'hello' != 'world';    // true
0 != false;     // false (boolean false is converted to number 0, equal to 0)

```
### Note 
* It is generally recommended to use strict equality (===) for most comparisons as it avoids unexpected behavior due to type coercion.
* The loose equality (==) operator can lead to unexpected results when comparing values of different types, so use it with caution.

## Object Equality:
* The strict equality (===) and loose equality (==) operators behave differently when comparing objects.
* With  object comparisons, the equality operators check for reference equality rather than property values.
```javascript
const obj1 = { name: 'John' };
const obj2 = { name: 'John' };
const obj3 = obj1;

obj1 === obj2;      // false (different object references)
obj1 === obj3;      // true (same object reference)
obj1 == obj2;       // false

```

## NaN (Not-a-Number):
* NaN is a special numeric value in JavaScript that stands for "Not-a-Number."
* NaN is considered unequal to any other value, including itself.
```javascript
NaN === NaN;        // false
NaN == NaN;         // false

```

## Implicit Type Coercion:
* When using the loose equality (==) operator, JavaScript performs implicit type coercion before the comparison.
* This can lead to unexpected results, especially when comparing different types.
```javascript
0 == false;         // true (0 is coerced to false)
'' == false;        // true ('' is coerced to false)
null == undefined;  // true (null and undefined are coerced to each other)

```

## Strict Mode:

* In strict mode, JavaScript enforces stricter rules for equality comparisons, eliminating some of the behaviors that can lead to unexpected results.
* Strict mode can be enabled at the function level or at the script level by adding the directive 'use strict';.

```javascript
'use strict';
5 == '5';           // false (type coercion not allowed in strict mode)

```
