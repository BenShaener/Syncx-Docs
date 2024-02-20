**Description:**

This Apex class is designed to represent an invoice entity in a Salesforce environment, tailored specifically for use within an Aura component. It encapsulates various fields related to invoices, like `invoiceId`, `status`, `weekOf`, and others, making them accessible and modifiable in the context of Lightning Components. The class is marked as `with sharing`, ensuring that users only have access to records as per the organization's sharing policies.

**Methods:**

This class does not contain any explicit methods, but it utilizes `@AuraEnabled` annotations to expose its properties to Aura and Lightning Web Components, making them accessible via component markup or JavaScript.

**Properties:**

- `invoiceId`: Unique identifier of the invoice.
- `status`: Current status of the invoice.
- `weekOf`: Represents the starting week of the invoice period.
- `weekEnding`: The ending date of the invoicing period.
- `invoiceNumber`: Unique invoice number.
- `remmitanceNumber`: Remittance number associated with the invoice.
- `worklocationId`: Identifier for the work location.
- `worklocationName`: Name of the work location.
- `candidate`: Name or identifier of the candidate associated with the invoice.
- `agencyId`: Identifier for the agency.
- `agencyName`: Name of the agency.
- `poNumber`: Purchase Order number related to the invoice.
- `classification`: Classification of the invoice.
- `specialty`: Specialty field, possibly related to the type of work or service invoiced.
- `providerType`: Type of provider issuing the invoice.
- `agencyWorklogs`: A list of work logs associated with the agency.
- `worklogs`: A list of work logs associated with the work done.
- `expenses`: A list of expenses associated with the invoice.

**Use Case:**

This class is ideal for managing invoice data within Salesforce for business applications that involve invoicing, especially in scenarios involving agencies, work locations, candidates, and expenses. It can be used to display, create, or update invoices through Aura or Lightning Web Components by binding the properties directly to the component's markup.

**Important Notes:**

- The class is designed for use in Salesforce Lightning Experience and Salesforce Mobile App due to its use of Aura-enabled properties.
- Developers should ensure that the class adheres to the organization's sharing and data security policies, as the `with sharing` keyword enforces record level access according to the user's permissions.
- To make full use of this class's capabilities in Aura or Lightning Web Components, familiarity with the respective component's lifecycle, data binding, and server-side action handling is necessary.
- The correctness of field names, such as `remmitanceNumber` (which might be more accurately spelled as `remittanceNumber`), should be verified against actual Salesforce object and field names to ensure smooth integration.