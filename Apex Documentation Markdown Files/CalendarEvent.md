### Description

This class is designed to model calendar events, encapsulating key information about an event such as the associated contact or lead ("who"), the related Salesforce object ("what"), timing (start and end datetime), along with additional attributes like subject, color, and a unique event identifier. It supports both default instantiation and parameterized construction to populate its properties.

### Methods

- **CalendarEvent()**: Default constructor that initializes a new instance without setting any properties.
  
- **CalendarEvent(String whoName, String whoUrl, String whatName, String whatUrl, DateTime startDateTime, DateTime endDateTime, String eventId, String subject, String color)**: A parameterized constructor that initializes a new instance of the class with details about the event, including names and URLs for the related contact and object, start and end times, an event ID, subject, and color.

### Properties

- **WhoName (String)**: The name of the related contact or lead.
- **WhoUrl (String)**: The Salesforce URL for the related contact or lead.
- **WhatName (String)**: The name of the related Salesforce object.
- **WhatUrl (String)**: The Salesforce URL for the related object.
- **StartDateTime (DateTime)**: The starting date and time of the event.
- **EndDateTime (DateTime)**: The ending date and time of the event.
- **EventId (String)**: A unique identifier for the event.
- **Subject (String)**: The subject or title of the event.
- **Color (String)**: A string representing the color associated with the event.

### Use Case

This class can be employed in Salesforce Lightning Components or Aura-enabled methods to represent and handle calendar events within a custom user interface. It allows for the convenient packaging of event-related data, which can be easily passed between the Salesforce backend and a frontend application, thus facilitating the creation, display, or editing of calendar events within a Salesforce org.

### Important Notes

- All properties are annotated with `@AuraEnabled`, making them accessible for Aura and Lightning Web Components. This is essential for using this class within the Salesforce Lightning Experience, as it enables data exchange between Apex and the frontend.
- This class is declared with `with sharing`, which means it adheres to the sharing and user access rules defined in Salesforce, affecting how records are accessed via this class in a multi-tenant environment.
- The design of this class assumes the existence of related contacts or leads and Salesforce objects, as indicated by the inclusion of URLs and names for these entities, underlining the importance of these records being present and accessible in the org.