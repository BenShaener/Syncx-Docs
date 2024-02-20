### Description

This class is designed to manage the creation and updating of `Summary_Junction_Record__c` records based on related placement, timesheet, and expense records. It handles the aggregation of data from these related records to form a comprehensive summary record that can be used for reporting or further processing. The class provides functionality to create summary records when given a list of SObject records and also update summary records when related timesheet or expense records are updated.

### Methods

- `createSummary(List<SObject> records)`: Creates `Summary_Junction_Record__c` entries based on provided `SObject` records that can be either timesheets or expenses. It fetches related `nuPlacement__c` records to populate the summary records accurately.
  
  ```java
  public static void createSummary(List<SObject> records)
  ```

- `updateClientInvoiceTimesheet(Map<Id,nuTimesheet__c> newMap, Map<Id,nuTimesheet__c> oldMap)`: Updates `Summary_Junction_Record__c` entries when associated `nuTimesheet__c` records are modified in regards to invoice details.
  
  ```java
  public static void updateClientInvoiceTimesheet(Map<Id,nuTimesheet__c> newMap, Map<Id,nuTimesheet__c> oldMap)
  ```

- `updateClientInvoiceExpense(Map<Id,nuExpense__c> newMap, Map<Id,nuExpense__c> oldMap)`: Similar to `updateClientInvoiceTimesheet`, but targets changes in `nuExpense__c` records, specifically in relation to invoice information.
  
  ```java
  public static void updateClientInvoiceExpense(Map<Id,nuExpense__c> newMap, Map<Id,nuExpense__c> oldMap)
  ```

### Properties

This class does not explicitly declare any properties, instead, it operates directly on the input provided to its methods and does not maintain state.

### Use Case

A practical use case for this class involves scenarios where there is a requirement to generate consolidated summary records for placements along with their related timesheets and expenses. This can facilitate reporting and invoicing processes by having a unified record that encapsulates all relevant information. For instance, after generating timesheets and expense records for a period, this class’s methods can be invoked to create or update summaries for easy access to aggregated information.

### Important Notes

- The class operates without sharing, meaning it does not enforce user permissions or field-level security which should be considered when accessing sensitive information.
- It expects that the SObjects provided to the `createSummary` method have a `Placement__c` field that is crucial for associating the summary records with their corresponding placements.
- It is reliant on specific SObject types (`nuTimesheet__c` and `nuExpense__c`) and fields (such as `Invoice__c`, `Agency_Invoice__c`, etc.), indicating that it is tailored to a particular org's schema and may require adjustments if reused in a different org.
- The use of dynamic SOQL in the methods necessitates careful testing, especially regarding the volume of records processed, to avoid governor limits.
- Batch processing or future methods should be considered for handling large datasets to ensure the scalability of these operations.