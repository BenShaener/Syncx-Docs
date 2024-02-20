### Description

This class provides functionality related to credential checks and manipulations for placements tied to contacts in Salesforce. It includes methods for retrieving placements in the credentialing process based on contact ID, counting placements in credentialing, counting enrollments in process, retrieving application-related document URLs, updating credential versions, and deleting content document links.

### Methods

1. `getPlacementsInCredentialingProcessByContactId(Id contactId, Id recordId)`: Retrieves a list of placements that are in the credentialing process for a given contact.

```java
@AuraEnabled (cacheable = true)
public static List<nuPlacement> getPlacementsInCredentialingProcessByContactId(Id contactId, Id recordId)
```

2. `countPlacementsInCredentialingProcess(Id contactId)`: Counts the number of placements that are in the credentialing process for a given contact.

```java
@AuraEnabled (cacheable = true)
public static nuServiceResult countPlacementsInCredentialingProcess(Id contactId)
```

3. `countEnrollmentsInProcess(Id contactId)`: Counts the number of enrollments in the process for a given contact.

```java
@AuraEnabled (cacheable = true)
public static nuServiceResult countEnrollmentsInProcess(Id contactId)
```

4. `getApplication(String compcredId, String credId)`: Retrieves application-related document URLs based on compliance credential ID and credential ID.

```java
@AuraEnabled
public static CredentialFilesResult getApplication(String compcredId, String credId)
```

5. `updateCredentialVersion(Id oldDocId, Id newDocId)`: Updates a credential version document by creating a new version and deleting the old document.

```java
@AuraEnabled
public static Boolean updateCredentialVersion(Id oldDocId, Id newDocId)
```

6. `deleteLinks(Id recordId)`: Deletes content document links associated with a provided record ID.

```java
@AuraEnabled
public static void deleteLinks(Id recordId)
```

### Properties

The class contains an inner class `CredentialFilesResult` that holds properties relevant to document URLs and their IDs. The properties are:

- `requirementUrl`: URL of the requirement document.
- `requirementConDocId`: Content Document ID of the requirement document.
- `compCredUrl`: URL of the compliance credential document.
- `compCredConDocId`: Content Document ID of the compliance credential document.
- `credentialUrl`: URL of the credential document.
- `credentialConDocId`: Content Document ID of the credential document.

### Use Case

This class can be utilized in scenarios where there's a need to manage and monitor credential-related information for placements associated with a specific contact. This includes fetching placements under credentialing, counting such placements, handling document linkages and URLs for credentials, updating credential versions, and cleaning up document links.

### Important Notes

- It's crucial to be cautious when using methods that modify data (`updateCredentialVersion`, `deleteLinks`) to avoid unintended data loss.
- The methods are marked as `@AuraEnabled` and `cacheable`, indicating they are intended for use with Salesforce Lightning components and can benefit from client-side caching.