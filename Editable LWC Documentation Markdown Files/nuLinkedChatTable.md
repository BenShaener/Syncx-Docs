### Description

This component, named `NuLinkedChatTable`, is a Salesforce Lightning Web Component (LWC) designed to display a table of linked chats related to a specific record, and provides the functionality to create new chat records by selecting a contact. The component makes use of `lightning-datatable` for showcasing the data, a custom modal for creating new chats, and interacts with an Apex controller for data retrieval and creation of chat records.

### Methods

- **handleNewChat:** Opens the modal to create a new chat.
- **handleComboChange:** Handles the selection change in the combobox within the modal, updates the selected contact value.
- **handleSave:** Handles the save action within the modal. It creates a new chat record based on the selected contact and navigates to the newly created chat's record page.
- **handleCancel:** Closes the modal without performing any action.
- **LinkedChatTable:** Invokes an Apex method to retrieve linked chat records for displaying in the datatable.
- **renderedCallback:** Lifecycle hook used for fetching and displaying the linked chat table data once the component is rendered.

### Properties

- **recordId:** Record ID of the parent record. It's an `@api` property meaning it can be set from outside the component.
- **objectApiName:** Object API name, another `@api` property for dynamic binding.
- **initialised:** Indicator to prevent re-fetching data on every component re-render.
- **data:** Holds the data for the datatable.
- **columns:** Column definitions for the datatable.
- **selectedOption:** Tracks the selected contact option from the modal's combobox.
- **allFields, filteredFields, contactFields:** Used for managing the selectable options based on the record's available contact fields and processing them accordingly.
- **isModalOpen:** Controls the visibility of the modal for creating a new chat.

### Use Case

The component is ideal for use cases where there is a need to display related chat records in a table format within a Salesforce record page and provide users with an ability to create new chat records by picking a contact. Such functionality can be useful in CRM scenarios where managing communication history and initiating new conversations directly from the CRM platform are required.

### Important Notes

- The component requires Apex controller methods (`getLinkedChatTable`, `createChatRecord`, `getCommunityUserIdByContactId`) to be defined and accessible.
- The `@wire` decorators are used for reactive data fetching based on the component's reactive properties (`recordId`, `objectApiName`).
- Utilizes the `NavigationMixin` for navigating to the newly created chat record page upon successful creation.
- The modal operation is handled purely on the client side, with its visibility toggled by the `isModalOpen` property.
- Custom styling and layout are managed through inline styles and SLDS (Salesforce Lightning Design System) classes.

### Example:
Embedding the component within a Salesforce record page:

```xml
<c-nu-linked-chat-table record-id={recordId} object-api-name="YourObjectName"></c-nu-linked-chat-table>
```

This enables users on the specified record page to view linked chats and initiate new chats as needed.