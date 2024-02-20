### Description
This class is designed to merge date components from a given `DateTime` (the "future date") with time components from a `Time` field in Salesforce's Task object (specifically, the "Follow_Up_Time__c" field). It packages this functionality into an invocable method, making it suitable for use in Salesforce's process builder, flows, or Apex triggers where complex logic is required. 

### Methods

- **createDateTime(List<Wrapper> inputList):** This static method takes a list of `Wrapper` objects as input. Each `Wrapper` includes a Task ID (`taskId`) and a future `DateTime`. The method queries the Task records corresponding to the provided Task IDs, extracts the follow-up time from each Task, combines this time with the date part of the provided future `DateTime`, and returns a list of these combined DateTime values.

### Properties

- **Wrapper:** An inner class used to encapsulate and transport the Task ID and future date-time information into the `createDateTime` method. It includes two properties:
  - `taskId` (Id): The ID of the Task record.
  - `futureDate` (DateTime): The future date to which the follow-up time will be added.

### Use Case
This class can be particularly useful in automation scenarios where you need to schedule follow-up tasks or reminders at specific times of future dates. For example, if your process involves setting up future meetings or calls at the same time as an initial task but on different days, this utility can dynamically create the appropriate DateTime for each future event based directly on Salesforce data.

### Important Notes

- The `createDateTime` method executes a SOQL query to fetch Task records based on the provided list of IDs. Ensure that the size of the input list does not exceed governor limits for SOQL queries.
- The method assumes that all Task records found will have a non-null "Follow_Up_Time__c" field. If this field is null for any reason (such as not being set or the Task not requiring a follow-up time), the method will likely throw a null pointer exception. Proper error handling or pre-validation may be required depending on the use case.
- Usage of this invocable method in Salesforce's automation tools (like Process Builder or Flow) allows for complex logic to be implemented without writing additional Apex code, making automation processes more powerful and adaptable.
- It's essential to maintain the focus on bulkification principles. Even though this invocable method is designed to handle lists of inputs, excessive volume might still hit governor limits due to the SOQL query inside the loop. Always test with large data volumes expected in production environments.