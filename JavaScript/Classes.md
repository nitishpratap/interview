# Classes
Classes are blueprints of an Object. A class can have many Objects because the class is a template while Objects are instances of the class or the concrete implementation.
JavaScript is a prototype-based Object Oriented Language, which means it doesn’t have classes, rather it defines behaviors using a constructor function and then reuses it using the prototype. 
```javascript
// Defining class using es6
class Vehicle {
	constructor(name, maker, engine) {
		this.name = name;
		this.maker = maker;
		this.engine = engine;
	}
	getDetails() {
		return (`The name of the bike is ${this.name}.`)
	}
}
// Making object with the help of the constructor
let bike1 = new Vehicle('Hayabusa', 'Suzuki', '1340cc');
let bike2 = new Vehicle('Ninja', 'Kawasaki', '998cc');

console.log(bike1.name); // Hayabusa
console.log(bike2.maker); // Kawasaki
console.log(bike1.getDetails());

```
## Inheritance in JS Class
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name);
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog("Buddy", "Golden Retriever");
dog.speak(); // Output: "Buddy barks."

```

## Method overriding in JS
```javascript
class Shape {
  constructor() {
    this.name = "Shape";
  }

  draw() {
    console.log(`Drawing a ${this.name}`);
  }
}

class Circle extends Shape {
  constructor() {
    super();
    this.name = "Circle";
  }

  draw() {
    console.log(`Drawing a ${this.name} with a specific radius.`);
  }
}

const shape = new Shape();
shape.draw(); // Output: "Drawing a Shape"

const circle = new Circle();
circle.draw(); // Output: "Drawing a Circle with a specific radius."

```
