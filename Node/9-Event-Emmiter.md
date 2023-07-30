**Event Emitter - Complete Documentation**

**Introduction to Event Emitter:**
Event Emitter is a core module in Node.js that allows objects (instances of `EventEmitter`) to emit and handle custom events. It provides an implementation of the observer pattern, where an object (the event emitter) maintains a list of listeners (event handlers) for specific events. When an event is emitted, all registered listeners for that event are called asynchronously. Event Emitter plays a crucial role in building event-driven applications in Node.js.

**Creating an Event Emitter:**
To use Event Emitter, you first need to create an instance of the `EventEmitter` class:

```javascript
const {EventEmitter} = require('Node/19-Events');

const myEmitter = new EventEmitter();
```

**Event Emitter Methods:**

1. **`on(eventName, listener)` / `addListener(eventName, listener)`**:
   Adds a listener for a specific event. When the event is emitted, the listener function will be called.

   Example:
   ```javascript
   myEmitter.on('event', () => {
     console.log('Event emitted!');
   });
   ```

2. **`once(eventName, listener)`**:
   Adds a one-time listener for a specific event. The listener will be removed automatically after it is called once.

   Example:
   ```javascript
   myEmitter.once('event', () => {
     console.log('This listener will be called only once.');
   });
   ```

3. **`emit(eventName[, ...args])`**:
   Emits an event with the given name. When an event is emitted, all registered listeners for that event will be called asynchronously.

   Example:
   ```javascript
   myEmitter.emit('event');
   ```

4. **`removeListener(eventName, listener)`**:
   Removes a listener for a specific event.

   Example:
   ```javascript
   const listener = () => {
     console.log('This listener will be removed.');
   };

   myEmitter.on('event', listener);
   myEmitter.removeListener('event', listener);
   ```

5. **`off(eventName, listener)`**:
   An alias for `removeListener()`.

6. **`removeAllListeners([eventName])`**:
   Removes all listeners for a specific event. If no event name is provided, it removes all listeners for all events.

   Example:
   ```javascript
   myEmitter.removeAllListeners('event');
   ```

7. **`listenerCount(eventName)`**:
   Returns the number of listeners for a specific event.

   Example:
   ```javascript
   const count = myEmitter.listenerCount('event');
   console.log(count); // Outputs the number of listeners for the 'event' event.
   ```

**Inheritance from Event Emitter:**
You can create custom classes that inherit from the `EventEmitter` class to emit and handle custom events.

Example:

```javascript
const {EventEmitter} = require('Node/19-Events');

class MyCustomEmitter extends EventEmitter {
   constructor() {
      super();
   }

   performTask() {
      // Some task logic
      this.emit('taskCompleted', 'Task executed successfully');
   }
}

const myCustomEmitter = new MyCustomEmitter();

myCustomEmitter.on('taskCompleted', (message) => {
   console.log(message);
});

myCustomEmitter.performTask();
```

**Best Practices:**
1. Avoid excessive use of listeners, as it may impact the performance of your application.

2. Use meaningful and descriptive event names to make the code more readable and maintainable.

3. Always handle errors emitted by an `EventEmitter` to prevent uncaught exceptions.

4. Be cautious when using synchronous listeners, as they may block the event loop. Prefer asynchronous listeners when dealing with I/O operations.

**Summary:**
- Event Emitter is a core module in Node.js that allows objects to emit and handle custom events.
- To use Event Emitter, create an instance of the `EventEmitter` class using `const emitter = new EventEmitter();`.
- The methods of Event Emitter include `on()`, `once()`, `emit()`, `removeListener()`, `off()`, `removeAllListeners()`, and `listenerCount()`.
- You can create custom classes that inherit from `EventEmitter` to build custom event-driven components.
- Event Emitter is commonly used for building event-driven, asynchronous applications in Node.js.

Event Emitter is a powerful tool for building event-driven applications in Node.js. By leveraging the observer pattern, you can create decoupled, modular components that interact with each other through custom events, making your code more maintainable and scalable.
