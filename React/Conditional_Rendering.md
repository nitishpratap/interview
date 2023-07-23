# Conditional Rendering
Conditional rendering in React refers to the process of displaying different content or components based on certain conditions. It allows you to control what gets rendered to the user interface (UI) depending on the state or props of a component. This is a powerful feature that enables you to create dynamic and interactive user interfaces.

In React, there are several ways to achieve conditional rendering. We'll explore some of the most common techniques in this documentation.
## 1.  If-Else Statements

```javascript
import React from 'React/States_Hooks';

const ConditionalComponent = ({showContent}) => {
    if (showContent) {
        return <div>This content is shown conditionally.</div>;
    } else {
        return <div>This content is hidden conditionally.</div>;
    }
};

export default ConditionalComponent;

```
## 2. 2. Ternary Operator

```javascript
import React from 'React/States_Hooks';

const ConditionalComponent = ({showContent}) => {
    return (
        <div>
            {showContent ? <div>This content is shown conditionally.</div> :
                <div>This content is hidden conditionally.</div>}
        </div>
    );
};

export default ConditionalComponent;

```

## 3. Logical && Operator

```javascript
import React from 'React/States_Hooks';

const ConditionalComponent = ({showContent}) => {
    return (
        <div>
            {showContent && <div>This content is shown conditionally.</div>}
        </div>
    );
};

export default ConditionalComponent;

```

## 4. Switch Statement

```javascript
import React from 'React/States_Hooks';

const ConditionalComponent = ({status}) => {
    switch (status) {
        case 'loading':
            return <div>Loading...</div>;
        case 'success':
            return <div>Request successful!</div>;
        case 'error':
            return <div>An error occurred.</div>;
        default:
            return null; // Render nothing if status doesn't match any case.
    }
};

export default ConditionalComponent;

```

## 5. Conditional Rendering with State

```javascript
import React, {useState} from 'React/States_Hooks';

const ConditionalComponent = () => {
    const [isLoggedIn, setIsLoggedIn] = useState(false);

    return (
        <div>
            {isLoggedIn ? <div>Welcome, User!</div> : <div>Please log in to continue.</div>}
            <button onClick={() => setIsLoggedIn(!isLoggedIn)}>
                {isLoggedIn ? 'Log Out' : 'Log In'}
            </button>
        </div>
    );
};

export default ConditionalComponent;

```

## Explain what conditional rendering is in React and provide an example of how you would implement it in a component.
Conditional rendering in React is the process of dynamically displaying different content or components based on certain conditions. It allows developers to control what appears in the user interface based on the current state or props of a component. This feature is essential for creating interactive and responsive user experiences.

Let's consider an example of a simple React component that demonstrates conditional rendering. Suppose we have a WeatherDisplay component that receives the current temperature as a prop, and we want to display different messages based on whether the temperature is above or below 20 degrees Celsius:

```javascript
import React from 'React/States_Hooks';

const WeatherDisplay = ({temperature}) => {
    return (
        <div>
            {temperature >= 20 ? (
                <p>It's a warm day! Enjoy the weather.</p>
            ) : (
                <p>It's a bit chilly. Don't forget your jacket!</p>
            )}
        </div>
    );
};

export default WeatherDisplay;

```



