### Description
This class provides functionality to process name clearance requests for candidates associated with agencies. It handles the logic to determine whether a candidate is clear or not clear based on various factors including agency ownership, name clearance status from other agencies, hiring audit records, and rules set on the client's account. Additionally, it contains utility methods to add business days and to find the root parent ID of an account within a hierarchy.

### Methods

- `performNameClear(List<InvocableNameClearRequest> requests)`: Processes name clearance requests. It updates the status of `Name_Clear__c` records and related `Contact` and `Hiring_Audit__c` records based on the provided requests. Returns a list of `InvocableNameClearResponse` indicating the outcome of each request.

- `addBussinessDays(Date startDate, Integer iDays)`: Adds business days to a given start date, excluding weekends. Returns the resulting date after adding the specified number of business days.

- `getRootParentId(Id accountId)`: Recursively retrieves the root parent ID for a given account ID, navigating up the account hierarchy. Returns the root parent ID of the account.

### Properties
This class operates on custom objects and fields, including `Name_Clear__c`, `Contact`, and `Hiring_Audit__c`, using fields like `Status__c`, `Agency_Owned_Candidate__c`, `Agency_Release_On__c`, and `Name_Clear_Rule__c` on `Account`.

### Use Case
This class is intended to be used in scenarios where automated processing of candidate name clearance is required, such as when a candidate applies for a position and the agency wants to check if the candidate is already cleared by another agency or if there are any restrictions on hiring. It simplifies the name clearance process by automating checks and updates based on predefined rules and existing data.

### Important Notes
- The method `performNameClear` is designed to be invoked from Salesforce flows or processes because it's annotated with `@InvocableMethod`.
- It's crucial to ensure data consistency and accuracy in `Contact`, `Name_Clear__c`, and `Hiring_Audit__c` records for the name clearance logic to work as expected.
- Given the usage of SOQL queries within loops and recursive method calls (`getRootParentId`), care should be taken to optimize and review SOQL governor limits.
- The method `addBussinessDays` calculates business days by skipping weekends but does not account for public holidays or other non-working days specific to an organization or locale.