# Props

## What are React Props?
Props in React are inputs that you pass into components. The props enable the component to access customised data, values, and pieces of information that the inputs hold.

## Example
```javascript
const myElement = <Car brand="Ford" />;
```
```jsx
function Car(props) {
  return <h2>I am a { props.brand }!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand="Ford" />
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Garage />);
```


## How to Use React Props
Before we go deeper, it is important to note that React uses a one-way data flow. This means that data can only be transferred from the parent component to the child components. Also, all the data passed from the parent can't be changed by the child component.


## Destructuring Props in React

Props are objects. So to destructure objects in React, the first step is to group your properties within a set of curly braces. Then you can either store it into a variable called props within the body of the function or pass it directly as the function’s parameter.

```javascript
function Product = (props) => {
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

