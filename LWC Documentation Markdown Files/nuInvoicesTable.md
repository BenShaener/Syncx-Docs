### Description

This Lightning Web Component (LWC) named `NuInvoicesTable` is designed to list invoices with various filtering and action capabilities such as dispute handling, PDF generation, and downloading attachments. It includes functionality to filter invoices by dates, numbers, and several picklists including status, candidates, and work locations. The component provides a rich user interface for viewing detailed invoice and worklog information. Users can also dispute invoice entries and expenses with reasons and comments.

### Methods

#### `runGetInvoices`
Fetches invoices based on agency and work location IDs. It processes fetched invoices for display and initializes options for picklists.

#### `doFilter`
Applies various filters to invoice data, including agency, company, date range, status, classification, specialty, and candidate filters.

#### `handleDateChange`
Handles changes in date filters and applies the date filter.

#### `doSelectInvoice`
Handles the selection of an invoice to toggle the display of its worklog details.

#### `poNumberHandler`, `WRpoNumberHandler`, `EXPpoNumberHandler`
Handles enabling editing for PO numbers on invoices, worklogs, and expenses, respectively.

#### `updateInvPO`, `updateWR`, `updateExp`
Updates PO numbers for invoices, worklogs, and expenses, respectively.

#### `doSelectWorklog`
Fetches and displays slots for a selected worklog.

#### `doOpenDisputeModal`, `doDispute`, `doOpenExpenseDisputeModal`, `doDisputeExpense`
Controls the opening of dispute modals and processing of disputes for either worklog entries or expenses.

#### `doSelectAllSlots`, `doSelectSlot`
Handles the selection of all slots or individual slots for disputing within a worklog.

#### `doSelectAllExpenses`, `doSelectExpense`
Handles the selection of all expenses or individual expenses for disputing.

#### `doCloseModal`, `doCloseExpenseModal`
Handles the closing of the dispute modals.

#### `onPdfClick`, `onDownloadAllClick`
Initiate PDF generation and downloading of invoice attachments.

#### `updateStatus`
Updates the status of an invoice based on user actions.

#### `doExpandExpenses`, `navigateToPlacement`
Controls expanding and collapsing expense details and navigating to placement records.

### Properties

- `agencyId`, `accountId`, `containerStyle`, `status`, `isReadOnly`
  Configuration properties to adapt component behavior and display.
  
- `invoices`, `filteredInvoices`, `slotCols`, `classificationOptions`, `specialtyOptions`
  Hold the data processed for display or selection within the component.
  
- `showDisputeModal`, `showExpenseDisputeModal`, `showSpinner`
  Control visibility of modals and loading spinner.

- `selectedDisputeReason`, `slotsForDispute`, `expsForDispute`
  Track selected reasons for disputes and IDs of entries or expenses selected for disputing.

### Use Case

The `NuInvoicesTable` component is intended for use within a Salesforce Lightning environment where an organization needs to manage, display, and action on invoices. It is particularly useful for agencies or companies that handle numerous invoices with the need for detailed tracking and action capabilities like disputing charges.

### Important Notes

1. **Apex Classes Dependency**: This component depends on Apex classes (`nuController_InvoicesList`, `nuController_TimeSheetPDF`, `nuController_Files`, `nuService_Contact`) for backend data operations. Ensure these classes are present and accessible in your org.

2. **Custom Sub-Components**: The component uses custom sub-components (ex: `c-nu-searchable-picklist`, `c-nu-searchable-multi-picklist`, `c-nuUtils`). Ensure these components are deployed in your org for this component to function correctly.

3. **Community and Standard Navigation**: The component uses `NavigationMixin` for navigation. Ensure URLs and navigation targets are properly configured, especially when deploying in Salesforce Communities vs. the standard Salesforce environment.

4. **Data Security**: Ensure proper security settings are applied to the data accessed by this component to avoid unauthorized data exposure.

5. **Input Field Validations**: The component implements input validations especially for dispute reasons and comments. Ensure input criteria meet your organizational requirements.

This component is a comprehensive solution for managing invoices within a Salesforce Lightning environment, providing robust filtering, viewing, and action capabilities.