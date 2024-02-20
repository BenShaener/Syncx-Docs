### Description
This batch class is designed to identify approved but not yet invoiced timesheets and expenses for clients and agencies and generate invoices based on the identified records. It primarily focuses on processing records related to '1099' billing type placements, creating invoices for both companies and agencies, and then updates the corresponding timesheets and expenses to link them to the newly created invoices. Additionally, in the `finish` method, it checks for invoices created without attached PDF files and generates those PDFs.

### Methods
- `start(Database.BatchableContext bc)`: Returns a `Database.QueryLocator` object for the query to select Accounts with the 'Candidate_Pool' DeveloperName.
- `execute(Database.BatchableContext bc, List<Account> scope)`: Processes approved timesheets and expenses, creates invoices, and updates related records.
- `finish(Database.BatchableContext bc)`: Searches for invoices created in the current batch process without attached PDF files and generates them.

### Properties
- `weekEnd`: Holds the end of the week date, defaulting to today's date.
- `worklocationId`: Represents the Id for the work location.
- `agencyInvoiceRtId`: Stores the Record Type ID for agency invoices.
- `companyInvoiceRtId`: Stores the Record Type ID for company invoices.

### Use Case
This batchable class can be scheduled or manually invoked to ensure that all billable 1099 expenses and timesheets approved within the last 50 days, but not yet invoiced, are processed. It ensures that both the company and agency invoices are created and appropriately linked to each timesheet and expense, streamlining the billing process. It is particularly useful for Salesforce instances managing agency and contractor relationships and financial transactions.

### Important Notes
- The class focuses on '1099' billing types, indicating a specific use case for independent contractors or agencies.
- In the `execute` method, an assumption is made that at least one invoice (company or agency) should always be created if eligible records are found. This might not be desired in all scenarios, requiring additional conditions or checks before invoice creation.
- The `execute` method assumes only one company (either 'UPMC' or 'Shondaland') for company invoice creation, which might need to be dynamic based on actual records processed.
- Error handling, especially in the PDF generation within the `finish` method, is minimal and could be enhanced for production use.
- There is a hard limit of generating PDFs for 20 invoices in the `finish` method, which may need adjustment based on actual needs.
- The batch class uses hardcoded LAST_N_DAYS:50 for querying records, which may need adjustment for different scenarios or business logic adjustments.
