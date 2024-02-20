### Description
This class provides functionalities for managing invoices, including fetching invoices by criteria (like IDs or status), disputing entries or expenses on invoices, and grouping worklogs by invoice with detailed timesheet entries. It serves as a controller that interacts with Salesforce's Lightning Aura Components, enabling client-side components to call its methods.

### Methods

- **getInvoices(Id agencyId, Id worklocationId)**: Fetches a list of invoices filtered by agency ID and work location ID.
  
- **getInvoiceById(Id recordId)**: Retrieves a specific invoice by its record ID.
  
- **countInvoices(Id agencyId, Id worklocationId, String status)**: Counts the number of invoices based on agency ID, work location ID, and status.
  
- **disputeEntries(String invoiceId, List<Id> entriesIds, Boolean isAgencyInvoice, String worklogId, String reason, String comments)**: Disputes specific timesheet entry slots linked to an invoice based on provided criteria and remarks.

- **disputeExpenses(String invoiceId, List<Id> expenseIds, Boolean isAgencyInvoice, String provider, String reason, String comments)**: Disputes specific expenses linked to an invoice based on provided IDs, with additional dispute-related information.

- **getWorklogsWithEntrySlotsGroupedByInvoice(Id invoiceId, Id agencyId, Id worklocationId)**: Groups worklogs with their respective timesheet entry slots by invoice, filtered by agency or work location ID.

- **fetchEntriesByWorklogId(String worklogId)**: Fetches all timesheet entry slots under a given worklog ID, with sorting by date and in-time.

### Properties
There are no explicit properties defined in this class except for the methods annotated with `@AuraEnabled` which expose functionalities to the Lightning Aura Components.

### Use Case
In a Salesforce environment, where tracking and managing invoices, timesheets, and expenses are critical, this class provides a bridge for Salesforce Lightning Aura Components to interact with backend logic. Specifically, it can be used in scenarios where administrative users need to:
- View lists or counts of invoices based on specific filters.
- Access detailed information about individual invoices or worklogs.
- Initiate disputes on invoice entries or expenses with detailed reasons and comments for further processing.
- Group worklogs by invoices for comprehensive overview and analysis, especially useful for client billing or internal audits.

### Important Notes
- Exceptions are handled by throwing `AuraHandledException`, ensuring that error messages are properly propagated to the Aura Components, which eases debugging and user feedback.
- It's vital to consider sharing and visibility settings in Salesforce, as this class uses `without sharing`, which means it does not enforce record-level permissions. Ensure it aligns with your organization's data security policies.
- Given the dependency on specific custom objects and fields (e.g., `nuInvoice__c`, `nuTimesheet__c`), ensuring these custom objects and fields exist and are accessible is crucial for the class to function correctly.
- Consumption of these methods by Aura Components requires corresponding Aura or Lightning Web Component implementations that handle UI interactions and display.