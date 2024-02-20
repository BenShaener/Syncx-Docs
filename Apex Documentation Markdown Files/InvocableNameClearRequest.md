### Description

This class defines a request structure used to clear names based on various criteria such as agency, client, candidate, and hiring audits. It is tailored to work with Salesforce's invocable methods, making it ideal for automation processes and flows where a clear and structured request format is necessary.

### Methods

This class does not define any methods. It serves as a data structure for passing parameters to invocable methods.

### Properties

- `agencyId`: An ID indicating the specific agency involved in the process. Marked as required.
  
  ```java
  global ID agencyId;
  ```

- `clientId`: An ID indicating the specific client involved in the process. Marked as required.
  
  ```java
  global ID clientId;
  ```

- `candidateId`: An ID indicating the specific candidate involved in the process. Marked as required.
  
  ```java
  global ID candidateId;
  ```

- `hiringAuditId`: An optional ID for the hiring audit associated with the request.
  
  ```java
  global ID hiringAuditId;
  ```

- `intention`: A string detailing the intent behind the name clear request. Marked as required.
  
  ```java
  global String intention;
  ```

- `fromDate`: An optional Date marking the starting point for the action requested.
  
  ```java
  global Date fromDate;
  ```

### Use Case

This class is particularly useful in Salesforce automation processes, such as workflows, process builders, or Apex invocable methods that require a detailed context of an operation that involves clearing names based on agency, client, and candidate data. It can be used in scenarios like cleaning up records after a hiring process ends or when auditing and compliance checks are required to clear candidate names from specific lists.

### Important Notes

- The `@InvocableVariable` annotations mark the required fields which must be provided for the request to be valid. This ensures that essential information is not omitted when the class is instantiated.
- The `required=false` attribute on some variables allows for flexible use of this class in various scenarios where not all information is readily available or needed.
- This class is designed to work with Salesforce's invocable methods, meaning it should be instantiated and used within the context of Salesforce automation tools or custom Apex code that interfaces with such tools.