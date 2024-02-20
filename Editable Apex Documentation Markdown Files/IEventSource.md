**Description**:  
This interface defines the structure for classes that aim to retrieve events related to a specific record. Implementing classes will provide the logic to fetch events based on a record identifier and a perspective.

**Methods**:  
- `List<CalendarEvent> getEvents(string recordId, string perspective)`:  
  - **Parameters**:
    - `recordId` (string): The unique identifier of the record for which events are to be fetched.
    - `perspective` (string): A parameter to define the context or viewpoint from which events should be gathered.
  - **Returns**: A list of `CalendarEvent` objects that represent the events associated with the specified record and perspective.
  - **Description**: This method is responsible for gathering and returning a list of events based on the provided record identifier and perspective.

**Properties**:  
There are no properties defined in this interface.

**Use Case**:  
An implementation of the `IEventSource` interface could be used in a calendar application where events need to be fetched from various sources (e.g., Salesforce records like Opportunities, Cases) based on different perspectives (e.g., daily, weekly, monthly views). Each source would implement this interface to return events in a unified format that the calendar application can render.

**Important Notes**:  
- Classes implementing this interface must provide a concrete implementation of the `getEvents` method, determining how events are fetched and processed.
- The `perspective` parameter allows for flexible implementations that can tailor the fetched events based on the required context or view.
- This interface does not enforce any specific logic for fetching events, leaving the implementation details up to the developer.