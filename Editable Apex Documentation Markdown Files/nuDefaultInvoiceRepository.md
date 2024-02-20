### Description
This Apex class acts as a repository layer for handling various operations related to invoices in a Salesforce system. It implements the `nuIInvoiceRepository` interface, indicating that it provides concrete implementations for fetching invoices, getting invoice details by ID, converting invoice records to Data Transfer Objects (DTOs), and fetching related credit memos.

### Methods
- **fetchInvoicesWithWorklogs(Id agencyId, Id worklocationId):** Fetches a list of invoices based on either agency Id or work location Id along with associated worklog details.
- **getInvoiceById(Id recordId):** Retrieves invoice details for a specified invoice ID.
- **convertInvoiceRecordToDTO(nuInvoice__c invoice):** Converts an `nuInvoice__c` object into its corresponding DTO representation.
- **fetchRelatedCreditMemos(Id invoiceId):** Fetches credit memos associated with a given invoice Id.
- **convertCreditMemoRecordToDTO(nuCredit_Memo__c cm):** Converts a `nuCredit_Memo__c` object into its corresponding DTO representation.

### Properties
This class does not explicitly declare properties but works with fields and relationships defined in the `nuInvoice__c`, `nuInvoice`, and `nuCreditMemo` custom objects.

### Use Case
This repository is designed to facilitate operations on invoice data required by various business processes. For instance, it can be used to:
- Retrieve all invoices related to a specific agency or work location, which is essential for accounting and auditing purposes.
- Get detailed information on a particular invoice, including related worklogs and expenses, which helps in invoice validation and reconciliation.
- Fetch credit memos linked to an invoice, aiding in financial adjustments and record-keeping.

### Important Notes
- The class is declared as `without sharing` which means it does not enforce the sharing rules of the current user. This is critical for data access in applications where invoices need to be retrieved irrespective of the viewer's permissions.
- It handles `null` values gracefully, especially when splitting strings or accessing related records, to avoid `NullPointerException`.
- All database operations are enclosed within `try-catch` blocks to handle exceptions properly, ensuring that any errors are caught and handled appropriately, especially crucial for user-facing applications to avoid unexpected crashes.
- The method `convertInvoiceRecordToDTO` is overloaded for converting different types of invoice records (`nuInvoice__c`, `nuCredit_Memo__c`) into their corresponding DTOs, highlighting a use of the pattern to abstract the transformation logic and ensure consistency in data representation.
- The repository directly queries and operates on Salesforce object data using SOQL queries, illustrating direct interaction with the Salesforce database and the use of nested queries to fetch related records.