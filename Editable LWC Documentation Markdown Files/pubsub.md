### Description

This JavaScript module implements a basic publish-subscribe (pub-sub) mechanism focused on sibling component communication within Salesforce Lightning components. Its primary function is to allow for the decoupled interaction between components, where events can be published by one component and subscribed to by another, without requiring a direct relationship between them. This approach enhances the modularity and reusability of components by adhering to a loosely coupled architecture.

### Methods

#### `registerListener`
Registers a callback function to be invoked when a specific event is published.
```javascript
registerListener(eventName, callback, thisArg)
```
- **Parameters:**
  - `eventName`: The name of the event to listen to.
  - `callback`: The function to be called when the event occurs.
  - `thisArg`: The context in which to invoke the callback.

#### `unregisterListener`
Unregisters a callback function, removing it from the list of listeners for a specific event.
```javascript
unregisterListener(eventName, callback, thisArg)
```
- **Parameters:**
  - `eventName`: The name of the event to stop listening to.
  - `callback`: The function to be removed from the list of listener callbacks.
  - `thisArg`: The context in which the callback was to be invoked.

#### `unregisterAllListeners`
Unregisters all event listeners associated with a given context.
```javascript
unregisterAllListeners(thisArg)
```
- **Parameters:**
  - `thisArg`: The context whose listeners should be removed.

#### `fireEvent`
Publishes an event, invoking all registered callbacks for that event.
```javascript
fireEvent(pageRef, eventName, payload)
```
- **Parameters:**
  - `pageRef`: The page reference that indicates the scope of the event.
  - `eventName`: The name of the event to be published.
  - `payload`: The data to be passed to the listener callbacks.

### Properties

While this module doesn't define properties in the traditional sense, it internally manages the `events` object, a dictionary where each key is an event name and its value is an array of listener objects. Each listener object contains a `callback` function and the `thisArg` context in which to call it.

### Use Case

This pub-sub mechanism can be utilized in a Salesforce Lightning application where multiple components need to communicate or share data without being directly coupled. For example, it can be used in a dashboard where different components (e.g., charts, filters, lists) must react to changes made in one of the components (e.g., a filter change) without needing a direct reference to each other.

### Important Notes

- Before using `registerListener`, ensure the component has a `@wire(CurrentPageReference) pageRef` property, as it's critical for filtering events to the correct listener scope.
- The `samePageRef` function ensures that only components on the same page reference react to the published event, preventing unintended cross-talk between pages or components that should not be listening to the event.