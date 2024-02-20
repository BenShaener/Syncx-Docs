## Documentation for Salesforce Lightning Component: ClientScheduler

### Description

The `ClientScheduler` component allows Salesforce users to schedule, view, edit, and manage shifts within a calendar view. It supports various actions, including adding, removing, selecting claims, and canceling shifts based on specified criteria. It interacts with multiple Apex controllers to fetch and manipulate shift data, as well as user and account information.

### Methods

#### fetchProviders

Fetches a list of providers based on specified locations, types, and specialties. It updates the component's provider-related options for filtering and creating shifts.

```javascript
fetchProviders(locationOptionsIds);
```

#### computeTotalHours

Computes the total hours between the selected start and end times for a shift. It updates the `totalHours` property accordingly.

```javascript
computeTotalHours();
```

#### setEventsMap & getEventsMap

Stores selected events from the calendar in a map for easy retrieval and synchronization across different calendar views.

```javascript
setEventsMap(key, value);
getEventsMap(key);
```

### Properties

- `selectedRateType`: Holds the currently selected rate type for filtering or creating shifts.
- `selectedShiftType`: Holds the selected shift type from a predefined list of options.
- `selectedLocation`: Stores the ID of the currently selected location.
- `selectedProviderType`: Stores the provider type selected by the user.
- `selectedSpecialty`: Holds the selected medical specialty.
- `selectedProvider`: Stores the selected provider's information.
- `weekDaySelectedOptions`: An array of selected weekdays for filtering shifts.

### Use Case

A typical use case for the `ClientScheduler` component is within a Salesforce org where scheduling and managing shifts for healthcare providers or similar roles is required. This component caters to admins or managers who need to visualize shifts in a calendar view, perform actions like adding or removing shifts, and filter shifts based on various criteria such as location, provider type, or specialty.

### Important Notes

- Ensure that all required Apex controllers and methods are available and have the necessary permissions to be called from the component.
- The user's timezone is considered for displaying dates and times correctly. Make sure to handle timezone conversions accordingly.
- Custom styling and theming are supported. Modify CSS according to the organization's branding requirements.

This component provides a comprehensive interface for managing shifts, integrating with Salesforce data, and offering a user-friendly calendar view for scheduling. It leverages Lightning Web Components (LWC) and Apex to interact with Salesforce backend data, providing a powerful tool for shift management within Salesforce.