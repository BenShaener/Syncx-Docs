### Description

This Salesforce Lightning Web Component (LWC) named `NuQuickActionCloneJobOrder` provides functionality to clone a Job Order record in Salesforce. It displays a modal window with a dynamic form, allowing users to submit new Job Order records with pre-populated fields based on the original record's data. The component also offers customization options for handling specific fields differently, such as conditionally displaying Start Date and End Date fields.

### Methods

- **closeQuickAction:** Closes the quick action modal without submitting any data.
- **connectedCallback:** Lifecycle hook that runs when the component is inserted into the DOM. It fetches the Job Order's details and prepares the fields for cloning.
- **renderedCallback:** Lifecycle hook that runs after every render of the component. It customizes the options for the 'Is_End_Date_Known_or_Estimate__c' field.
- **doSubmit:** Programmatically clicks the hidden submit button to initiate form submission.
- **handleFormSubmit:** Handles the form submission event, creates a new Job Order record, and navigates to the new record's page upon success.
- **handleFieldChange:** Handles changes to any of the field inputs in the form, specifically adjusting the display of date fields based on certain conditions.

### Properties

- **recordId:** The ID of the Job Order record being cloned (@api).
- **showEndDate:** Determines whether to show the end date based on a condition (@api).
- **showStartDate:** Determines whether to show the start date based on a condition (@api).
- **fieldsBySection:** Tracks the dynamically constructed fields and their organization for rendering in the form (@track).

### Use Case

To use this component, you should have a Job Order (`Job_Order__c`) record which you intend to clone. This component is designed to be initiated as a quick action from a Job Order's detail page. It dynamically fetches the Job Order's fields, excluding certain fields defined in the `FIELDS_TO_EXCLUDE` constant, and presents them in an accordion-style input form within a modal. The user can submit this form to create a new Job Order record that clones data from the original, with options to manage the inclusion of Start and End Date fields.

### Important Notes

- The component makes use of the `lightning-record-edit-form` to leverage Salesforce's built-in record editing functionality, making it efficient in handling field data types and validations without extra code.
- Dynamic handling of the Start Date and End Date visibility is provided based on the component's `showStartDate` and `showEndDate` properties.
- Custom logic is included to filter out certain fields from cloning (defined in `FIELDS_TO_EXCLUDE`) and to mark specific fields as required (using `requiredLabels`).
- Upon submission, a new Job Order record is created with the provided data, excluding specific system fields, and the user is navigated to the newly created record's detail page.

### Example

Using this component as a quick action on the Job Order object page allows users to quickly clone Job Orders with much of the data pre-populated, streamlining the process of creating similar Job Orders.