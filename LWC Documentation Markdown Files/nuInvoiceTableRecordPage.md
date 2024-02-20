This documentation outlines the structure and functionality of a Salesforce Lightning Web Component (LWC) designed for managing, displaying, and interacting with invoice records, including detailed work logs and expenses.


### Description

The `NuInvoiceTableRecordPage` component displays a table of invoices with detailed information such as invoice number, client, agency, amount, status, etc. It allows users to expand each invoice to view associated work logs and expenses. The table supports actions like invoice selection for further details, PO Number editing, work log selection, slot selection, dispute entry, and downloading attachments. It utilizes Salesforce's Lightning Design System (SLDS) for styling and layout.


### Methods

- **runGetInvoices**: Fetches invoices by ID and processes them for display.
- **doSelectInvoice**: Handles the action when an invoice is selected to toggle the visibility of associated work logs.
- **poNumberHandler**: Toggles the read-only state of the PO Number input field, allowing editing.
- **poNumberChange**: Updates the PO Number field in the database when changed.
- **doSelectWorklog**: Fetches and displays entries associated with a selected work log.
- **doOpenDisputeModal**: Opens the modal to dispute entries for a work log.
- **doOpenExpenseDisputeModal**: Opens the modal to dispute expenses.
- **doDispute**: Handles disputing the selected entries.
- **doDisputeExpense**: Handles disputing the selected expenses.
- **doSelectAllSlots**: Selects all time slots for disputing within a worklog.
- **doSelectAllExpenses**: Selects all expenses for disputing within an invoice.
- **doSelectSlot**: Handles the selection of an individual time slot for disputing.
- **doSelectExpense**: Handles the selection of an individual expense for disputing.
- **doCloseModal**: Closes the dispute modal dialog.
- **doCloseExpenseModal**: Closes the dispute expenses modal dialog.
- **onPdfClick**: Initiates PDF generation for the invoice.
- **onDetailsClick**: Navigates to a detailed view of the invoice.
- **doExpandExpenses**: Toggles the display of detailed expenses associated with an invoice.
- **onDownloadAllClick**: Initiates downloading of all documents associated with the invoice.
- **navigateToPlacement**: Navigates to the placement record associated with a work log or expense.


### Properties

- **agencyId**: Stores the agency ID if applicable.
- **containerStyle**: Style for the container housing the component.
- **recordId**: The ID of the currently viewed record.
- **isReadOnly**: Indicates if the component should be in read-only mode.
- **showDisputeModal**: Controls the visibility of the dispute modal.
- **showExpenseDisputeModal**: Controls the visibility of the expense dispute modal.
- **filteredInvoices**: Contains the processed invoices for display in the UI.


### Use Case

Ideal for use in environments where invoice management is critical, such as staffing agencies or professional services firms. The component provides a detailed, interactive view of invoicing data, allowing for comprehensive management actions such as disputing entries or expenses, editing PO numbers, and downloading associated documents.


### Important Notes

- The component relies heavily on Apex controllers for backend data processing and actions like disputing entries or generating PDFs, ensure controllers are properly configured and have necessary permissions.
- Before using in production, thoroughly test all interactive features such as disputing entries or expenses, and downloading PDFs to ensure they meet your organization's requirements.
- Consider customizing dispute reasons and options based on your specific business processes.
- Ensure that record type names and field API names used in the component match those in your Salesforce org to avoid runtime errors.