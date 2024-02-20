### Description

This Salesforce Lightning Web Component (LWC) named `SynchScheduler` is designed to create a complex scheduling and filtering system. The component features a spinner while loading data, a selection sidebar for filtering shifts based on type, location, candidate type, and specialty, a main content area that lists available shifts in a calendar format, and modals for adding availability, claiming shifts, confirming shifts, and cancelling shifts. Additionally, it supports dynamic styling based on account-specific settings.

### Methods

#### Public Methods

No public methods are exposed by this component.

#### Private Methods

- `handleShiftTypeListboxChange`: Invoked when the shift type selection changes.
- `handleLocationListboxChange`: Invoked when the location selection changes.
- `handleProviderTypeListboxChange`: Invoked when the provider type selection changes.
- `handleSpecialtyListboxChange`: Invoked when the specialty selection changes.
- `handleProviderListboxChange`: Invoked when the provider selection changes.
- `handleClearFiltersClick`: Clears all selected filters.
- `handleColorButtonClick`: Toggles the color state of the scheduler.
- `handlePreviousButtonClick`: Shifts the calendar view to the previous period.
- `handleNextButtonClick`: Shifts the calendar view to the next period.
- `handleRefreshButtonClick`: Refreshes the calendar based on current filters.
- `handleTodayButtonClick`: Sets the calendar view to today.
- `computeTotalHours`: Computes total hours between start and end times.
- `subtractDays`: Subtracts a specified number of days from a date.
- `setEventsMap`: Stores events in the component's internal state.
- `getEventsMap`: Retrieves events from the component's internal state based on a key.

### Properties

- `selectedRateType`: Tracks the selected rate type.
- `selectedShiftType`: Tracks the selected shift type.
- `selectedLocation`: Tracks the selected location.
- `selectedLocations`: An array of selected locations.
- `selectedProviderType`: Tracks the selected provider type.
- `selectedSpecialty`: Tracks the selected specialty.
- `selectedProvider`: Tracks the selected provider.
- `selectedProviders`: An array of selected providers.
- `selectedEvents`: An array of selected events.
- `colorState`: Boolean indicating the state of the color toggle.
- `locationOptions`: Contains options for the location filter.
- `shiftTypeOptions`: Contains options for shift types.
- `providerTypeOptions`: Contains options for provider types.
- `specialtyOptions`: Contains options for specialties.
- `autoSelectRate`: Boolean to auto-select the rate.

### Use Case

The component is designed to be used in scheduling scenarios where users need to filter and select shifts based on various criteria such as shift type, location, candidate type, and specialty. It provides a comprehensive scheduler interface for managing availability, claiming shifts, and handling other shift-related actions.

### Important Notes

- It uses a combination of custom events and wire service to fetch data and respond to user interactions.
- The component's layout and appearance can be customized based on account-specific settings like theme color and text color.
- Dynamic imports are used for CSS and utility JavaScript modules to enhance performance and modularity.
- The component makes extensive use of SLDS (Salesforce Lightning Design System) for styling.
- Modals are used for critical actions such as adding availability, claiming, confirming, cancelling, and releasing shifts, enhancing the UX by providing contextual actions within the same interface.