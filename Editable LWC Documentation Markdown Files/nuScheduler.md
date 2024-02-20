### Description

This documentation covers a Salesforce Lightning Web Component (LWC) named `nuScheduler`. `nuScheduler` is designed to provide a comprehensive scheduling interface within the Salesforce platform, allowing users to create, view, and manage shifts or appointments. It supports different modes (e.g., Client, Agency), making it versatile for various business needs. The component integrates with custom Apex controllers to fetch relevant data, such as contacts, accounts, and placements, to populate its interface dynamically.

### Methods

1. **setColors()**: Determines the color scheme for the scheduler based on the selection and status of shifts or appointments. It adjusts the colors for confirmed, unconfirmed, open, and available shifts.

2. **computeTotalHours()**: Calculates the total hours between the start and end times of a shift or appointment.

3. **formatTime(time)**: Formats a given time string to a more user-friendly format.

4. **handleSelectorChange(event)**: Handles changes in the shift or appointment type selector.

5. **handleLocationChange(event)**: Handles changes in the location selector.

6. **handleProviderTypeChange(event)**: Handles changes in the provider type selector.

7. **handleSpecialtyChange(event)**: Handles changes in the specialty selector.

8. **handleTimeChange(event)**: Handles changes in the start and end time inputs and recalculates the total hours.

9. **handleConfirmChange(event)**: Handles changes in the confirmation status of a shift or appointment.

10. **lookupRecord(event)**: Handles the selection of a record from the provider lookup component.

11. **previousHandler()**, **nextHandler()**, **refresh()**, **today()**: Navigation and refresh controls for the calendar views.

### Properties

1. **selectedLocationOption**: Tracks the currently selected location option.

2. **selectedProviderTypeOption**: Tracks the currently selected provider type option.

3. **selectedSpecialtyOption**: Tracks the currently selected specialty.

4. **selectedOption**: Tracks the currently selected shift or appointment option.

5. **confirmed**: Tracks the confirmation status of the shift or appointment.

6. **colors**: Tracks the current color theme for shifts or appointments based on their status.

7. **colorState**: A boolean flag used to toggle between color states.

8. **mode**: Indicates the mode in which the scheduler is operating, e.g., "Client" or "Agency".

9. **totalHours**: Stores the computed total hours for a shift or appointment.

10. **providerTypeOptions**, **specialtyOptions**, **locationOptions**: Store dynamic options for the related selectors fetched from the backend.

### Use Case

`nuScheduler` can be utilized in scenarios where scheduling and time management are crucial, such as in staffing agencies, healthcare facilities, or any organization that needs to manage shifts, appointments, or resource allocations. Its dynamic fetching of contacts, accounts, and customizable options makes it adaptable to specific business models and requirements.

### Important Notes

- The component is tightly coupled with custom Apex controllers for fetching required data, meaning that those controllers must be correctly set up and configured in the Salesforce org where the component is deployed.
- The component uses sessionStorage and localStorage for persisting some states across page reloads. This behavior is essential for understanding how user selections are retained.
- CSS classes in the component leverage the Salesforce Lightning Design System (SLDS) for styling, ensuring a consistent look and feel with the Salesforce platform.

The component's dynamic nature, combined with its integration into Salesforce's ecosystem, makes it a powerful tool for managing scheduling needs within a Salesforce org.