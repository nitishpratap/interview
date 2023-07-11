
## Sort Data from the dictionary swift with example
```javascript
var dictionary = ["John": 25, "Alice": 30, "Bob": 20, "David": 35]

// Sort the dictionary by keys
let sortedByKey = dictionary.sorted(by: { $0.key < $1.key })
print(sortedByKey)

// Sort the dictionary by values
let sortedByValue = dictionary.sorted(by: { $0.value < $1.value })
print(sortedByValue)

```

## Read concurrency in swift

## Tuple
Tuples in Swift are a lightweight way to group multiple values into a single compound value. They are useful when you want to return multiple values from a function, pass multiple values as a single parameter, or store related values together.

1. Declaration and Initialization:
   Tuples can be declared and initialized using parentheses. The types of the tuple elements can be explicitly defined or inferred by the compiler.
```javascript
let person = ("John", 25)
let coordinates: (Double, Double) = (latitude, longitude)

```

2. Accessing Tuple Elements:
```javascript
let person = ("John", 25)
let name = person.0
let age = person.1

```

3. Naming Tuple Elements:


```javascript
let person = (name: "John", age: 25)
let name = person.name
let age = person.age

```
4. Decomposing Tuples:
   Tuples can be decomposed into individual constants or variables using the assignment operator.
```javascript
let person = (name: "John", age: 25)
let (name, age) = person

```
5. Function Returning Tuples:
   Functions can return tuples to provide multiple values as a result.
```javascript
func getPerson() -> (String, Int) {
    return ("John", 25)
}
let person = getPerson()

```

### Swapping 2 values using a tuple 

```javascript
var a = 10
var b = 20

// Swapping using a tuple
(a, b) = (b, a)

print("a: \(a), b: \(b)")

```
In this example, we have two variables a and b with initial values 10 and 20, respectively. To swap the values, we create a tuple (b, a) where the values are reversed. By assigning this tuple to (a, b), the values of a and b are swapped.

After the swap, the values of a and b are 20 and 10, respectively, as printed in the output.



