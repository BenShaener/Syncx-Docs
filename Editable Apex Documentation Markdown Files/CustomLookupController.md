**Description:**  
This class provides functionality to perform custom lookup operations within Salesforce. It allows fetching search results based on user input for specific sObject types and record types, fetching a list of candidates with specific criteria, and fetching a specific default record by its ID. The class operates without sharing, enforcing the running user's permissions, and is designed to be consumed by Lightning Web Components (LWCs).

**Methods:**  
1. **fetchLookupData**
   - Parameters: `String searchKey, String sObjectApiName, String recordType`
   - Returns: `List<sObject>`
   - Description: Retrieves a list of sObjects based on a search key, sObject API name, and an optional record type. The method filters results by account relationships and limits the output to 5 records sorted by creation date.

```java
@AuraEnabled(cacheable=true)
public static List<sObject> fetchLookupData(String searchKey, String sObjectApiName, String recordType)
```

2. **fetchCandidate**
   - Parameters: `String searchKey, String sObjectApiName, String recordType, String specialty, String agencyId, String credential`
   - Returns: `List<sObject>`
   - Description: Fetches a list of candidates that match the given criteria including search key, record type, specialties, agency ID, and credentials. Results are limited to 5 records sorted by creation date.

```java
@AuraEnabled(cacheable=true)
public static List<sObject> fetchCandidate(String searchKey, String sObjectApiName, String recordType, String specialty, String agencyId, String credential)
```

3. **fetchDefaultRecord**
   - Parameters: `String recordId, String sObjectApiName`
   - Returns: `sObject`
   - Description: Retrieves a single sObject record based on the provided record ID and sObject API name. Intended to fetch a default record for lookup fields.

```java
@AuraEnabled
public static sObject fetchDefaultRecord(String recordId, String sObjectApiName)
```

**Use Case:**  
Ideal for developing custom lookup components in Salesforce Lightning Web Components (LWC). These methods can be used to:
- Dynamically search for records based on user input, filtering results for specific requirements.
- Obtain a default record for initializing forms or display purposes.
- Create more complex search functionality that incorporates record types, relationships, and custom criteria like specialties or credentials.

**Important Notes:**  
- This class does not enforce sharing rules, meaning it does not respect the organization's record visibility settings.
- The returned lists from `fetchLookupData` and `fetchCandidate` methods are limited to 5 items to ensure performance. Adjust this limit as necessary considering governor limits.
- Dynamic SOQL queries are used; ensure that the input to these methods is properly sanitized to prevent SOQL injection risks.
- Debug statements are present for troubleshooting but should be removed or commented out in production environments to reduce log verbosity and improve performance.