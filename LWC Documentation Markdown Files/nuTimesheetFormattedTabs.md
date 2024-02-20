## Description

This Salesforce Lightning Web Component (LWC) named `NuTimesheetFormattedTabs` is designed to display timesheet data across different tabs categorizing them based on their status: Action Required, Submitted, Approved, and All. Each tab contains a nested custom component `<c-nu-timesheets-formatted>` which is responsible for rendering the timesheet data according to the given filters and settings.

## Methods

- `connectedCallback()`: This lifecycle hook gets called when the component is inserted into the DOM. In this example, it is used to log the values of `showWorkLocation` and `workLocationLabel` to the console.


```js
connectedCallback() {
    console.log(this.showWorkLocation);
    console.log(this.workLocationLabel);
}
```

## Properties

The component has several public properties (decorated with `@api`) which allow customization and control from the parent component:

- `testContactId`: Allows the identification of a specific contact.
- `renderMode`: Determines how the component should be rendered.
- `positionLabel`: Label for the position field (default: "Position").
- `weekStartLabel`: Label for the week starting date field (default: "Week Starting").
- `weekEndLabel`: Label for the week ending date field (default: "Week Ending").
- `totalHoursLabel`: Label for the total hours field (default: "Total Hours").
- `guaranteedHoursLabel`: Label for the guaranteed hours field (default: "Guaranteed Hours").
- `fileAttachmentsPageName`: The name of the page for file attachments (default: 'timesheet-files').
- `showFiles`: Controls whether file attachments are shown or not.
- `title`: The title of the component (default: 'Timesheets').
- `clockInClockOut`, `showUnpaidBreak`, `autoBreakValue`, `showNote`, `showShift`, `showPosition`, `showWeekStart`, `showWeekEnd`, `mode`, `showTotalHours`, `showGuaranteedHours`: Various settings to control the visibility and behavior of timesheet entry fields.
- `statusFilter`: Set to 'All' by default, used to filter timesheet entries in the "All" tab.
- `showWorkLocation`: Boolean indicating if the work location should be shown (default: false).
- `workLocationLabel`: Label for the work location field.

```js
@api showWorkLocation=false;
@api workLocationLabel;
```

## Use Case

This component is ideal for use in Salesforce applications where managing timesheets and tracking employee work hours are required. Specifically, it allows for the organization of timesheets based on their submission status, making it easier for users to navigate through and manage timesheets accordingly.

## Important Notes

- Since `@api` properties are exposed, they can be set and modified by the parent component that includes `<c-nu-timesheet-formatted-tabs>`, allowing for flexible customization according to specific requirements.
- The `connectedCallback()` method is useful for initializing the component with specific logic but should be used cautiously as it fires every time the component is inserted into the DOM.

Here's an example of how the component can be utilized in a parent component:

```html
<c-nu-timesheet-formatted-tabs 
    test-contact-id="003xx000004TmiZAAS" 
    render-mode="compact" 
    show-files={true}>
</c-nu-timesheet-formatted-tabs>
```

This snippet demonstrates how a parent component can pass specific properties to customize the `NuTimesheetFormattedTabs` component, like setting a contact ID, rendering mode, and controlling the visibility of file attachments.