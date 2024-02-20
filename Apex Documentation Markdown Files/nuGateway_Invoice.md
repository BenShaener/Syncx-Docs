### Description
This class serves as a gateway for various functionalities related to fetching invoices, credit memos, and associated worklogs (agency and company) leveraging specific repository classes.

### Methods
- `List<nuInvoice> fetchInvoicesWithWorklogs(Id agencyId, Id workLocationId)`
  Fetches a list of invoices associated with a particular agency and work location that include worklog information.

- `List<nuInvoice> getInvoiceById(Id recordId)`
  Retrieves a list of invoices based on a specific invoice ID.

- `List<nuCreditMemo> fetchRelatedCreditMemos(Id invoiceId)`
  Obtains a list of credit memos related to a given invoice ID.

- `List<nuTimesheet> fetchRelatedAgencyWorklogs(Id invoiceId)`
  Fetches a list of timesheets (agency worklogs) associated with a specific invoice.

- `List<nuTimesheet> fetchRelatedCompanyWorklogs(Id invoiceId)`
  Retrieves timesheets (company worklogs) related to a given invoice ID.

### Properties
No public properties are defined within the class itself as it primarily utilizes methods for its operations.

### Use Case
A typical use case for this class would be when an application needs to compile detailed invoice reports, inclusive of related credit memos and worklog entries (both from agencies and companies). This is particularly useful in financial or project management systems where such granular detail is necessary for billing, audit, or project tracking purposes.

### Important Notes
- The class is defined as `without sharing` to ensure that it adheres to the system's data access rules; thus, it does not enforce row-level sharing rules.
- Each method instantiates its respective repository class (`nuDefaultInvoiceRepository` or `nuDefaultTimesheetRepository`) to perform the actual data fetch operations.
- It is important to ensure that the `Id` parameters provided to the methods are valid and correspond to the correct records in the system to avoid unexpected results.