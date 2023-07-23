# Writing Custom Hooks in React

Custom hooks are a powerful and flexible way to extract reusable logic from React components. They allow you to share stateful logic between different components without the need for inheritance or additional complexity. Custom hooks follow a specific naming convention by prefixing the function name with "use," making them easy to identify.

## Creating a Custom Hook

To create a custom hook, you simply write a regular JavaScript function that uses built-in React hooks or other custom hooks. There are two essential rules to remember when creating custom hooks:

1. The name of the custom hook must start with "use" (React convention).
2. Custom hooks can call other hooks, but they cannot be called conditionally, as React relies on the order of hooks to maintain state between renders.

Let's walk through the process of creating a custom hook step-by-step.

### Step 1: Identify the Logic to Extract

The first step is to identify the logic you want to extract from your components. It could be state management, side effects, or any other reusable logic that can benefit multiple components.

### Step 2: Create the Custom Hook Function

Create a new JavaScript file (or use an existing one) and write the custom hook function following the "use" naming convention. Inside the function, you can use any existing React hooks or other custom hooks.

Example: A simple custom hook to handle form input state:

```javascript
// useInputState.js
import { useState } from 'react';

const useInputState = (initialValue) => {
  const [value, setValue] = useState(initialValue);

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  const reset = () => {
    setValue(initialValue);
  };

  return [value, handleChange, reset];
};

export default useInputState;
```

### Step 3: Use the Custom Hook in Components

Once your custom hook is created, you can use it in your components just like any other React hook. Import the custom hook and use it in your component function.

Example: Using the custom hook to manage input state in a component:

```javascript
// MyComponent.js
import React from 'react';
import useInputState from './useInputState';

const MyComponent = () => {
  const [name, setName, resetName] = useInputState('');

  return (
    <div>
      <input type="text" value={name} onChange={setName} />
      <button onClick={resetName}>Reset</button>
      <p>Hello, {name}!</p>
    </div>
  );
};

export default MyComponent;
```

### Step 4: Reuse the Custom Hook in Other Components

One of the main benefits of custom hooks is their reusability. You can use the same custom hook in multiple components, which makes it easy to share complex logic across your application.

## Custom Hook Best Practices

- Name your custom hooks descriptively to make their purpose clear.
- Ensure the custom hook is self-contained and independent, not relying on any external state from the components using it.
- Remember that custom hooks can call other hooks, allowing you to compose multiple hooks together for complex functionality.
