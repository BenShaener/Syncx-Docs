### Description
This Apex class is designed for tracking changes in Salesforce records by creating audit history records. It captures modifications to specified fields across different Salesforce objects and logs these changes into a custom object `Audit_History__c`.

### Methods

- `createAuditHistory(List<SObject> newRecords, Map<Id,SObject> oldRecordsMap, String objectName, String objectDeveloperName, String fieldCustomMetadata)`: This static method takes a list of updated records (`newRecords`), a map of old record states (`oldRecordsMap`), the label and API name of the object being audited (`objectName` and `objectDeveloperName` respectively), and the API name of a custom metadata field (`fieldCustomMetadata`) which stores CSV values representing the fields to be monitored. It generates audit records detailing changes to the specified fields.

- `private static void assignObjectLookup(Audit_History__c auditHistory)`: A helper method that dynamically assigns a lookup field on the `Audit_History__c` object based on the type of Salesforce object being audited.

- `private static Map<Id, String> getRelatedRecords(Set<Id> recordIds)`: Retrieves the names of records associated with a set of record IDs, used for populating the `New_Value__c` and `Previous_Value__c` fields of the `Audit_History__c` records with human-readable names instead of just IDs.

### Properties
Not directly applicable, as this class primarily focuses on static methods to process and log audit histories rather than exposing properties.

### Use Case
An organization wishes to maintain an audit trail of specific field changes across different objects such as Contacts, Accounts, Leads, and Opportunities. This solution dynamically captures modifications, enabling admins and developers to track changes over time for compliance, debugging, or data monitoring purposes.

### Important Notes

1. The method dynamically constructs SOQL queries and performs DML operations; ensure callouts are made before these operations to avoid mixed DML errors in transactional contexts.

2. It presumes the presence of an `Audit_History__c` custom object with specific fields such as `Date_Ocurred__c`, `Field_Name__c`, etc., and appropriate lookup fields for related objects like `Contact__c`, `Account__c`, etc.

3. The method for capturing changes might not capture changes to complex fields such as rich text fields or handle very large text areas optimally due to Salesforce's governor limits on SOQL query lengths and DML statement sizes.

4. It queries a custom metadata type `Global_Settings_Metadata__mdt` assuming there's a single record named `Global_Settings_Metadata` used to store settings, which might not be optimal for all orgs and may require adjustments based on actual implementation needs.