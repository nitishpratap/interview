# Events Module

The `events` module is a core module in Node.js that provides a mechanism for handling and emitting events. It allows you to create custom events and establish event-driven communication between different parts of your application.

**Importing the Events Module:**
To use the `events` module, you need to import it first. In Node.js, you can import core modules using the `require()` function:

```javascript
const EventEmitter = require('Node/19-Events');
```

**EventEmitter Class:**
The `EventEmitter` class is the key component of the `events` module. It provides methods to emit events and register listeners for events.

**Creating an EventEmitter:**
To create a new `EventEmitter` instance, you can extend the `EventEmitter` class or create an object directly from it:

```javascript
const {EventEmitter} = require('Node/19-Events');

// Extending the EventEmitter class
class MyEmitter extends EventEmitter {
   // Custom methods and properties can be added here
}

// Creating an object from the EventEmitter class
const myEmitter = new EventEmitter();
```

**EventEmitter Methods:**

1. **`eventEmitter.on(eventName, listener)`**:
   Adds a listener function for the specified event. The listener will be called every time the event is emitted.

   Example:
   ```javascript
   myEmitter.on('customEvent', (arg1, arg2) => {
     console.log(`Event emitted with arguments: ${arg1}, ${arg2}`);
   });
   ```

2. **`eventEmitter.once(eventName, listener)`**:
   Adds a one-time listener for the specified event. The listener will be called only once when the event is emitted, and then it will be automatically removed.

   Example:
   ```javascript
   myEmitter.once('oneTimeEvent', () => {
     console.log('This listener will be called only once.');
   });
   ```

3. **`eventEmitter.emit(eventName[, ...args])`**:
   Emits an event with the specified name, triggering all registered listeners for that event.

   Example:
   ```javascript
   myEmitter.emit('customEvent', 'arg1', 'arg2');
   ```

4. **`eventEmitter.removeListener(eventName, listener)`**:
   Removes a specific listener for the specified event.

   Example:
   ```javascript
   const listenerToRemove = () => {
     console.log('This listener will be removed.');
   };

   myEmitter.on('removeMe', listenerToRemove);
   myEmitter.removeListener('removeMe', listenerToRemove);
   ```

5. **`eventEmitter.removeAllListeners([eventName])`**:
   Removes all listeners for a specific event. If no event name is provided, it removes all listeners for all events.

   Example:
   ```javascript
   myEmitter.removeAllListeners('customEvent');
   ```

**Inheriting EventEmitter:**
You can create custom classes that inherit from `EventEmitter` to create your own event-driven objects:

```javascript
const {EventEmitter} = require('Node/19-Events');

class MyCustomEmitter extends EventEmitter {
   // Custom methods and properties can be added here
}

const myCustomEmitter = new MyCustomEmitter();
```

**Summary:**
- The `events` module in Node.js provides an `EventEmitter` class for handling and emitting events.
- The `EventEmitter` class allows you to register listeners for events using `on()` or `once()`.
- You can emit events using `emit()`, triggering all registered listeners for that event.
- `removeListener()` removes a specific listener, and `removeAllListeners()` removes all listeners for a specific event.
- The `events` module enables event-driven communication between different parts of your application, facilitating loose coupling and modular design.

Using the `events` module, you can build event-driven applications, where different parts of your code communicate and respond to events, making your code more modular, flexible, and easy to maintain.
