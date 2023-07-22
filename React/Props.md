# Props

## What are React Props?
Props in React are inputs that you pass into components. The props enable the component to access customised data, values, and pieces of information that the inputs hold.

## Example
```javascript
function Avatar() {
  return (
    <img
      className="avatar"
      src="https://i.imgur.com/1bX5QH6.jpg"
      alt="Lin Lanying"
      width={100}
      height={100}
    />
  );
}

export default function Profile() {
  return (
    <Avatar />
  );
}

```

## Structure of parent component
```javascript
import Product from "./Product"

function App() {
  return (
      <div>
      	<h1>PRODUCTS</h1>
      	<div className="App">
      		<Product />
      	</div>
      </div>
  )
}

export default App
```

## Structure of child component
```javascript
function Product() {
    return (
        <div>
            <img src="https://ng.jumia.is/unsafe/fit-in/300x300/filters:fill(white)/product/82/6142201/1.jpg?2933" alt="sneakers" />
            <h4>Cyxus</h4>
            <p>Non-Slip Fitness Leisure Running Sneakers</p>
            <h4>$29</h4>
        </div>
    );
}

export default Product
```

## How to Use React Props
Before we go deeper, it is important to note that React uses a one-way data flow. This means that data can only be transferred from the parent component to the child components. Also, all the data passed from the parent can't be changed by the child component.


## Destructuring Props in React

Props are objects. So to destructure objects in React, the first step is to group your properties within a set of curly braces. Then you can either store it into a variable called props within the body of the function or pass it directly as the function’s parameter.

```javascript
unction Product = (props) => {
//First Step: Destructuring within the body of the function
    const { img, name, desc, price} = props ;
    return (
      <div>
  		<img src={img} alt="products" />
//Second Step: receive the properties where you need them by stating the names of the properties without attaching the prefix ‘props.’
        <h4>{name}</h4>
        <p>{description}</p>
        <h4>{price}</h4>
      </div>
    );
}

export default Product
```

