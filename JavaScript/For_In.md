# The For In Loop
### Syntax
```javascript
for (key in object) {
  // code block to be executed
}
```
### Example
```javascript
const person = {fname:"John", lname:"Doe", age:25};

let text = "";
for (let x in person) {
  text += person[x];
}
```
## For In Over Arrays
### Syntax
```javascript
for (variable in array) {
  code
}
```

### Example
```javascript
const numbers = [45, 4, 9, 16, 25];

let txt = "";
for (let x in numbers) {
  txt += numbers[x];
}
```
