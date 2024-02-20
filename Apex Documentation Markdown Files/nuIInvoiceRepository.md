### Description
This interface outlines the structure for a repository responsible for handling operations related to invoice data. It defines methods for fetching invoices with their associated worklogs based on specific criteria and for converting invoice records from Salesforce object to a data transfer object (DTO).

### Methods

- `List<nuInvoice> fetchInvoicesWithWorklogs(Id agencyId, Id worklocationId)`: Retrieves a list of `nuInvoice` objects that have associated worklogs, filtered by the provided agency ID and work location ID.

- `nuInvoice convertInvoiceRecordToDTO(nuInvoice__c invoice)`: Converts a given `nuInvoice__c` Salesforce object into a `nuInvoice` DTO for easier data manipulation and transfer.

### Properties
Not applicable for interfaces as properties are inherently part of implementing classes.

### Use Case
Implement this interface in classes that are designed to interact with invoice data within Salesforce, particularly when there's a need to:

- Efficiently fetch invoices related to specific agencies and work locations along with their worklogs for processing or reporting purposes.
- Convert Salesforce `nuInvoice__c` objects into a more flexible `nuInvoice` DTO format, perhaps for integration with external systems or for simplifying various operations within the Salesforce environment.

### Important Notes
- Implementing classes must provide concrete implementations for both methods defined in this interface.
- The `nuInvoice` DTO structure should be appropriately defined elsewhere in the codebase, ensuring it can accurately represent the data extracted from `nuInvoice__c` Salesforce objects.
- Care should be taken to efficiently query and handle Salesforce data to avoid hitting governor limits, particularly in `fetchInvoicesWithWorklogs` method where related data fetching might be extensive.
- The success of these operations may be dependent on the correct setup of Salesforce object relationships and fields, such as ensuring proper linking between invoices, worklogs, agencies, and work locations.