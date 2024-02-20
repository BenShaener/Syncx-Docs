### Description

This utility class provides a comprehensive solution for accessing picklist values within Salesforce. It covers various scenarios, from basic retrieval of picklist values using dynamic Apex to leveraging the UI API for accessing picklist values with support for record types. Additionally, it features specialized methods for fetching case status values, catering to both open and closed cases. The class emphasizes efficiency and performance by implementing caching mechanisms for both Apex and UI API calls, ensuring that the retrieval of picklist values is optimized.

### Methods

- **`getPicklistValues(sObjectType, Schema.sObjectField)`**: Retrieves picklist values for a specified object and field using dynamic Apex.
    ```java
    public static List<Schema.PicklistEntry> getPicklistValues(sObjectType sObjectType, Schema.sObjectField field);
    ```
    
- **`getPicklistValues(String objectName, String fieldName)`**: Retrieves picklist values by invoking dynamic Apex based on the object and field name strings. Supports error handling for invalid parameters.
    ```java
    global static List<Schema.PicklistEntry> getPicklistValues(String objectName, String fieldName);
    ```

- **`getPicklistValues(String objectName, Id recordTypeId, String fieldName)`**: Leverages the UI API to fetch picklist values considering the record type. It constructs and executes an HTTP request to the UI API.
    ```java
    global static PicklistEntries getPicklistValues(String objectName, Id recordTypeId, String fieldName);
    ```

- **`getCaseStatusValues()`**: Provides access to all case status values, including those for both open and closed cases.
    ```java
    global static List<CaseStatus> getCaseStatusValues();
    ```

- **`getCaseStatusValues(Boolean isCaseClosed)`**: Filters case status values based on the specified case closure state—open or closed.
    ```java
    global static List<CaseStatus> getCaseStatusValues(Boolean isCaseClosed);
    ```
    
- **`getActivePicklistEntries(List<Schema.PicklistEntry> entries)`**: Utility method that filters a list of picklist entries, returning only the active ones.
    ```java
    private static List<Schema.PicklistEntry> getActivePicklistEntries(List<Schema.PicklistEntry> entries);
    ```

### Properties

- **`apexCache`**: A static map used for caching picklist entries fetched through dynamic Apex to optimize performance.
- **`uiApiCache`**: A static map intended for caching responses from the UI API to reduce the number of outbound calls.
- **`caseStatuses`**: A static list holding cached case status values to avoid repeated queries.

### Use Case

This utility class is ideal for developers working with dynamic forms or components in Salesforce, where there is a need to present or process picklist values dynamically based on the object and field context or specific criteria like case status. It can be significantly useful in scenarios requiring optimized performance through caching mechanisms, especially in high-volume, dynamically driven applications or processes.

### Important Notes

- The `getPicklistValues` methods utilizing dynamic Apex do **not** support record types due to their implementation. For record-type-specific picklist values, the method that accesses the UI API (supporting record types) should be used.
- The caching implementation is crucial for enhancing performance by minimizing repetitive calls for the same picklist or case status values.
- Error handling is provided in the dynamic Apex version of `getPicklistValues`, throwing specific exceptions for invalid object or field names, ensuring robustness and easier debugging.
- The class does **not** inherently handle UI API callout limits or Salesforce governor limits; proper usage and limit checks should be considered when integrating into larger applications.