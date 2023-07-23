`useRef` is a React hook used to create a mutable reference to an element or a value that persists across renders. Unlike `useState`, updating the value returned by `useRef` does not trigger a re-render of the component. This makes it suitable for managing non-reactive data and interacting with the DOM directly.

## Syntax

To use the `useRef` hook, import it from React:

```javascript
import React, { useRef } from 'react';
```

Then, you can create a ref by calling `useRef`:

```javascript
const refContainer = useRef(initialValue);
```

- `initialValue` (optional): The initial value to be assigned to the ref.

## Example: Ref to Access DOM Element

```javascript
import React, { useRef, useEffect } from 'react';

const MyComponent = () => {
  const inputRef = useRef(null);

  useEffect(() => {
    // Focus on the input element after the component mounts
    inputRef.current.focus();
  }, []);

  return (
    <div>
      <input ref={inputRef} type="text" />
    </div>
  );
};
```

In this example, we use `useRef` to create the `inputRef` ref and attach it to the input element using the `ref` attribute. The `useEffect` hook runs after the component mounts (due to the empty dependency array `[]`). It then calls `inputRef.current.focus()` to set the focus on the input element, showing a practical use case of using a ref to interact with the DOM.

## Example: Persisting a Value Across Renders

```javascript
import React, { useRef, useState } from 'react';

const MyComponent = () => {
  const [count, setCount] = useState(0);
  const prevCountRef = useRef();

  // Update the ref value to store the previous count
  useEffect(() => {
    prevCountRef.current = count;
  }, [count]);

  const handleIncrement = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <p>Current Count: {count}</p>
      <p>Previous Count: {prevCountRef.current}</p>
      <button onClick={handleIncrement}>Increment</button>
    </div>
  );
};
```

In this example, we use `useRef` to create the `prevCountRef` ref and initialize it with the initial value of `count`. In the `useEffect` hook, we update the ref value to store the previous count every time the `count` state changes. This allows us to persist the previous count across renders without causing a re-render when updating the ref.

## Note

- `useRef` returns an object with a property called `current`. You can access and modify the value of the ref using `refContainer.current`.
- The value of `refContainer.current` will persist across renders, but updating it will not trigger a re-render.
- Be cautious when using `useRef` to modify the DOM directly. In most cases, it's recommended to use React's declarative approach and manage the DOM through state and props.

Keep in mind that React's implementation and features might evolve over time. For the latest and most accurate information on `useRef` and other hooks, refer to the official React documentation.
