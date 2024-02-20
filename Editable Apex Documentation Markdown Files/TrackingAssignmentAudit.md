### Description

This class is designed to track and record changes in assignment (nuPlacement__c object) fields, focusing on the fields specified by the system and any custom reference fields related to contacts. It creates audit records for each field of `nuPlacement__c` that has been changed when comparing new values against old values, capturing the change's details, including the name of the changed field, the new and old values, the assignment associated with the change, and the time and user who made the change.

### Methods

- **`createAssignmentAuditRecords(List<nuPlacement__c> newPlacements, Map<Id, nuPlacement__c> oldPlacementsMap)`**
  - **Description**: Compares new and old placement records to find changes in specified fields, creates audit records for each change, and inserts these audit records into the database.
  - **Parameters**:
    - `newPlacements`: A list of new placement records to be audited against their old versions.
    - `oldPlacementsMap`: A map of old placement records keyed by their ID for comparison.

- **`getRelatedRecords(Set<Id> recordIds)`**
  - **Description**: Fetches the names of records given their Ids by grouping them by their object type, constructing dynamic SOSL queries, executing them, and returning a mapping between the record Ids and their corresponding names.
  - **Parameters**:
    - `recordIds`: A set of Salesforce record IDs whose names are to be fetched.
  - **Returns**: A map where the key is the record ID and the value is the record's name.

### Properties

- **No public properties defined as the methods are static and meant for direct utility usage rather than instantiation of the class object**.

### Use Case

Suppose an organization wants to keep a detailed audit trail of changes to specific fields in their custom placement object (`nuPlacement__c`). For instance, any changes to billing type, admin fee, associated contacts, or any custom fields specified in a separate metadata configuration. Whenever such changes occur, this class can be invoked to automatically generate human-readable audit records that capture who made the change, what the change was (both before and after values), and when the change occurred.

### Important Notes

- This class relies on a metadata record (`Global_Settings_Metadata__mdt`) to dynamically determine which fields should be monitored for changes. However, these fields must be specified in a CSV format in the `Assignment_Audit_Fields__c` field of the metadata record.
- Modifications are also tracked for custom reference fields related to the `Contact` object, adding greater flexibility and depth to the kind of changes that can be audited.
- This audit trail functionality is critical for maintaining compliance, historical data accuracy, data analytics, and for debugging purposes.
- As the class is declared with `public without sharing`, it does not enforce the sharing rules of the current user, thus it should be used cautiously, especially in contexts where record access and data security are concerns.