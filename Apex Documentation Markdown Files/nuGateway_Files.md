### Description
This class provides methods related to file management, expense tracking, and handling invoices, job orders, and presentations linked to specific records within Salesforce. It includes functionalities to get, update, and delete files and expenses, check for duplicate expenses, get lists of providers and locations based on a contact, and generate presentation attachments. The class operates without sharing to ensure that it respects the organization-wide default and sharing settings for the records it accesses.

### Methods
1. `getContactId()`: Retrieves the Contact ID associated with the current user.
2. `getFiles(String recordId)`: Fetches files related to a specific record ID.
3. `getExpenses(String recordId)`: Retrieves expenses associated with a given record ID. 
4. `getDuplicateExpenses(Id timesheetId, String expenseType, Date expenseDate, Decimal expenseAmount, String providerId, String locationId)`: Checks for duplicate expenses.
5. `updateFiles(String documentId, String title, String description, String recordId, String note, Decimal amount, String add, Decimal mileage, Date enteredDate, String loc, String prov, String poNum)`: Updates file metadata and expense records.
6. `deleteExpense(String recordId, String expenseId)`: Deletes an expense by setting its status to 'Removed'.
7. `UpdateFilesEdit(String documentId, String recordId, String documentName, String description)`: Edits files related to a specific record ID.
8. `getExpenseType(Id timesheetId)`: Retrieves the types of expenses based on timesheet ID.
9. `fetchStipendOption(Id contactId)`: Retrieves stipend options for a given contact ID.
10. `fetchProviders(Id contactId)`: Gets a list of providers based on the contact ID.
11. `fetchLocations(Id contactId, String mode)`: Retrieves locations linked to a given contact, filtered by mode.
12. `UpdateExpense(String title, String description, String expenseId, String note, Decimal amount, Decimal mileage, Date enteredDate, String resubmission, Boolean submit)`: Updates an expense based on provided parameters.
13. `UpdateResubmitExpense(String title, String description, String expenseId, String note, Decimal amount, Decimal mileage, Date enteredDate, String resubmission, Boolean submit)`: Updates and submits an expense for approval.
14. `createpdf(Id cdId, Id expId)`: Generates a PDF for a given content document ID and expense ID.
15. `getInvoiceAttachments(Id recordId)`: Fetches invoice attachments for a given record ID.
16. `getJobOrderAttachments(Id recordId)`: Retrieves job order attachments based on the provided record ID.
17. `getPresentationAttachments(Id recordId)`: Gets presentation attachments linked to a specific record ID.

### Properties
Not explicitly defined in the provided code, but the class operates on several Salesforce standard and custom objects such as `ContentDocument`, `ContentDocumentLink`, `nuExpense__c`, `nuTimesheet__c`, etc.

### Use Case
This class can be used in scenarios involving document management, expense tracking, and generating attachments for various records in Salesforce. It can assist in managing finances linked to timesheets, handling job-related documents, and supporting the preparation of presentations or invoices by fetching and updating related files and records.

### Important Notes
- The class is declared `without sharing`, which means it does not enforce sharing rules and could access any data visible to the running user.
- Error handling is implemented in some methods but not consistently across all. Consider adding try-catch blocks where missing.
- The methods use SOQL queries inside loops in some instances, which might hit governor limits for large data volumes. Optimizations may be required to ensure bulk operation support.
- Some methods contain commented-out code blocks that seem to be alternate or previous versions of the logic. Cleaning this up could improve readability and maintainability.
- The `createpdf` method assumes the existence of a Visualforce page named `convertToPdfVF`, which must exist in your org for this functionality to work.
