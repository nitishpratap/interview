# What is component?
Everything is a component in react
A component is an independent, reusable bit of code which divides the UI into smaller pieces. 

Components are of two types in react
1. Functional component
2. Class based component

<br/>

1. **Functional Component**
* It is nothing but a javascript function.
* It returns some piece of react element (JSX)

```javascript
function NumberList(props) {
  const numbers = props.numbers;
  return (
    <ul>
      {numbers.map((number) =>
        <ListItem key={number.toString()}
                  value={number} />
      )}
    </ul>
  );
}
```







