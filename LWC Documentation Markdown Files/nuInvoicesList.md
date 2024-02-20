### Description

This Salesforce Lightning Web Component (LWC) provides functionality for displaying a list of invoices in a datatable, with options to view detail, generate a PDF version, and dispute invoice entries. It leverages Apex controllers for fetching data, performing updates, and handling the dispute logic. The component dynamically updates styles based on Account record type and configurations. It supports navigation between the list view and detail view of invoices and includes modal dialogs for disputing entries and generating PDFs.

### Methods

**connectedCallback()**: Initialization method that fetches contact, account details, and sets up initial UI settings like styles based on the account's configuration. It enables the display of either agency or bill amounts in the invoice table based on the account type.

**handleInvoiceSelect(event)**: Handles the selection of an invoice from the list, fetching detailed invoice data including work logs.

**setRecordCount(event)**: Updates the component with the number of records in the table view.

**onPdfClick(event)**: Triggers the PDF generation for the selected invoice.

**onDisputeClick(event)**: Opens the modal to initiate the dispute process for selected time entries.

**doDispute(event)**: performs the dispute operation by calling an Apex method with selected entries and user-provided reasons.

**saveInvoice(event)**: Saves any edits made to the invoice in detail view.

**closeModal(event)**: Closes any open modal dialogs.

**goBack(event)**: Navigates back to the list view from the invoice detail view, resetting the view state.

**getInvoice()**: Fetches detailed information about a selected invoice, including work logs and timesheet entry slots.

### Properties

- **selectedInvoiceId**: The ID of the currently selected invoice.
- **selectedInvoice**: Detailed information about the selected invoice.
- **workLogs**: Collection of work logs related to the selected invoice.
- **invoices**: Collection of invoice summaries for display in the list view.
- **recordCount**: The number of records displayed in the list view.
- **agencyId**: The ID of the agency, if applicable.
- **accountId**: The ID of the account associated with the invoices.
- **status**: The filtering status for displayed invoices.
- **readOnly**: Boolean indicating if the detail view is read-only.
- **isReadOnly**: Boolean indicating if the invoices table is read-only.
- **columns**: Configuration for the columns in the datatable.
- **containerStyle**: Dynamic styling for the container based on account.
- **sectionHeadingStyle**: Dynamic styling for section headings.
- **title**: The title displayed in the header, dynamic based on the context.
- **showSpinner**: Indicates whether the loading spinner should be shown.
- **openDisputeModal**: Controls the visibility of the dispute modal.
- **showTable**: Controls the visibility of the invoices table.

### Use Case

This component is suitable for use in an application where managing invoices, viewing invoice details, and performing operations like disputing charges or generating PDFs of invoices are required. It can be customized to handle different types of invoices and associated workflows based on the user's account type, such as distinguishing between agency invoices and other invoices.

### Important Notes

- This component relies on several Apex controllers not included in the snippet, which must be implemented in the Salesforce org.
- The component uses dynamic styling, which requires setting up corresponding fields and styles in the Account object.
- Given the complex UI interactions, thorough testing is recommended to ensure behavior aligns with user expectations, particularly around error handling and state management across calls to Salesforce Apex.
- To use custom events like `onrecordcount` and `oninvoiceselect`, ensure the corresponding event handlers are correctly set up in the child components.