# Event Propagation in React
Event propagation, also known as event bubbling and event capturing, is an essential concept in web development and React. It refers to the process by which events triggered on a particular element in the DOM (Document Object Model) are propagated through the DOM tree, potentially triggering the same event on parent elements or descending into child elements.


## 1. Event Propagation Basics
Event propagation refers to the mechanism that allows events to be dispatched and handled at different levels within the DOM hierarchy. When an event occurs on an element, it can trigger event listeners on that element itself, as well as its ancestor elements and descendants.
There are two main phases of event propagation:
1. Event Bubbling:
2. Event Capturing:

### Event Bubbling
Event bubbling is the most common phase of event propagation. In this phase, when an event is triggered on a DOM element, the event first fires on the element itself, then on its parent element, and continues to propagate up through the DOM tree until it reaches the root document object.
### Event Capturing
Event capturing is the opposite phase of event propagation, which is less commonly used. In this phase, the event is first captured by the root document object and then propagates down the DOM tree, triggering event listeners on each ancestor element before reaching the target element where the event originated.

## 2. Event Bubbling in React

React follows the event bubbling phase by default. When you handle an event in a React component, if the event is not explicitly stopped with stopPropagation(), it will propagate up the component tree. This means that parent components have the opportunity to handle the event after it has been processed by the target element and its immediate ancestors.

```javascript
import React from 'react';

const ParentComponent = () => {
  const handleParentClick = () => {
    console.log('Parent component clicked.');
  };

  return (
    <div onClick={handleParentClick}>
      <ChildComponent />
    </div>
  );
};

const ChildComponent = () => {
  const handleChildClick = () => {
    console.log('Child component clicked.');
  };

  return <button onClick={handleChildClick}>Click Me</button>;
};

export default ParentComponent;

```

In this example, when the button in the ChildComponent is clicked, both the handleChildClick function in the child and the handleParentClick function in the parent will be executed. This is because the click event bubbles up from the child to the parent.

## Controlling Event Propagation with stopPropagation()
If you want to prevent an event from propagating further up the DOM tree, you can use the stopPropagation() method available on the event object:


```javascript
import React from 'react';

const ChildComponent = () => {
  const handleChildClick = (e) => {
    e.stopPropagation();
    console.log('Child component clicked.');
  };

  return <button onClick={handleChildClick}>Click Me</button>;
};

```

In this updated example, when the button in the ChildComponent is clicked, only the handleChildClick function will be executed. The stopPropagation() call prevents the event from bubbling up to the parent component.

## 3. Event Capturing in React

While React primarily follows the event bubbling phase, it does support event capturing by using the useCapture option in event listeners:


```javascript
import React from 'react';

const ParentComponent = () => {
  const handleParentClick = () => {
    console.log('Parent component clicked.');
  };

  return (
    <div onClick={handleParentClick}>
      <ChildComponent />
    </div>
  );
};

const ChildComponent = () => {
  const handleChildClick = () => {
    console.log('Child component clicked.');
  };

  return <button onClick={handleChildClick} capture>Click Me</button>;
};

export default ParentComponent;

```
In this example, when the button in the ChildComponent is clicked, the handleChildClick function in the child will be executed first due to the capture option. Then, the event will propagate up to the parent, and the handleParentClick function will be executed.

## 4. Event Propagation in Nested Components
React components form a tree-like structure, and event propagation occurs naturally within this component tree. When an event is triggered in a child component, it bubbles up through its parent components until it reaches the root component.
```jsx
import React from 'react';

const ParentComponent = () => {
  const handleParentClick = () => {
    console.log('Parent component clicked.');
  };

  return (
    <div onClick={handleParentClick}>
      <ChildComponent />
    </div>
  );
};

const ChildComponent = () => {
  const handleChildClick = () => {
    console.log('Child component clicked.');
  };

  return <button onClick={handleChildClick}>Click Me</button>;
};

export default ParentComponent;

```

In this example, when the button in the ChildComponent is clicked, the following sequence of event handling occurs:

1. handleChildClick in the child component is executed.
2. The click event bubbles up to the parent component, and handleParentClick in the parent is executed.
Since the parent component contains the child component, it becomes the target for the event bubbling.



