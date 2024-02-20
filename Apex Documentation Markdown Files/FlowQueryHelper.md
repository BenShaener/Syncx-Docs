### Description
This class provides functionality for querying records dynamically based on provided Salesforce Object IDs. It allows users to retrieve records from any object by passing a collection of IDs through a Flow or other processes that can call invocable methods.

### Methods

- `public static List<Output> getRecordsInColletion(List<Input> params)`: Main method that takes a list of `Input` objects, each containing a list of record IDs, and returns a list of `Output` objects containing the queried sObject records. It dynamically determines the object type based on the ID and retrieves all fields for the records.

- `private static String getObjectName(String objId)`: Helper method that takes an object ID as a string and returns the name of the Salesforce object associated with the ID.

- `private static String getObjectFields(String objectName)`: Helper method that returns a comma-separated string of all field names for a given object name.

### Properties

- `Input`: Inner class used for input parameters. It has one property, `ids`, which is a list of strings representing the Salesforce record IDs that need to be queried.
  
- `Output`: Inner class used for the method output. It contains one property, `records`, which is a list of sObject records retrieved based on the IDs provided in the `Input` class.

### Use Case
This helper class can be particularly useful in Salesforce Flows where there is a need to dynamically retrieve records from different objects without knowing the object type in advance. It can be used to process records in bulk by passing their IDs and subsequently working with the returned records in the Flow.

### Important Notes

- This class uses Salesforce SOQL dynamic query and the `Database.query` method to retrieve records. It's essential to properly handle the dynamic nature of the query to avoid injection vulnerabilities. The class takes this into account by using `String.escapeSingleQuotes` to mitigate SOQL injection risks.

- The performance of this class depends on the number of fields on the objects being queried. Retrieving all fields (`SELECT *`) for objects with a large number of fields can impact performance and consume more SOQL resources.

- The class is designed to work within the confines of Salesforce governor limits, but excessive use in a single transaction context (e.g., querying a large number of different objects with many records) could lead to hitting those limits.
