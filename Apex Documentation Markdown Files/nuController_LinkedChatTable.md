### Description
This Apex class provides functionality related to chat records in a Salesforce environment. It is designed to facilitate operations such as retrieving linked chat records for a particular record, fetching community user IDs based on contact IDs, and creating new chat records between portal users and other records. The class includes methods that are exposed to Aura and Lightning Web Components (LWC) for use in Salesforce UIs.

### Methods

1. **getLinkedChatTable(String recordId)**
   - Returns a list of `chatTableWrapper` objects containing chat details linked to the specified record ID.
   - **Parameters:**
     - `String recordId`: The ID of the record to find linked chats for.
   - **Return Type:** `List<chatTableWrapper>`

2. **getCommunityUserIdByContactId(List<Id> contactId)**
   - Fetches community user information based on provided contact IDs.
   - **Parameters:**
     - `List<Id> contactId`: A list containing IDs of the contacts whose community user information is needed.
   - **Return Type:** `list<Map<string,string>>`

3. **createChatRecord(Id portalUserId, Id recordId)**
   - Creates a new `Chat__c` record between a portal user and the target record, returning the new chat record's ID.
   - **Parameters:**
     - `Id portalUserId`: The user ID of the portal user in the chat.
     - `Id recordId`: The record ID that the chat is associated with.
   - **Return Type:** `Id`

### Properties

- **chatTableWrapper**
  - A wrapper class to store chat information for UI presentation.
  - **Fields:**
    - `String id`: The ID of the chat record.
    - `String name`: The name of the chat.
    - `String nameUrl`: A URL constructed from the chat's ID.

### Use Case
This Apex class can be used in a Salesforce Community or any Salesforce org where chat functionality is required. It allows for displaying linked chats on record detail pages, creating new chat records based on user interactions, and listing community users as options for chat creation. This can enhance communication paths within the Salesforce environment for users and contacts alike.

### Important Notes
- This class does not handle permissions or sharing, as it is declared `without sharing`. Ensure to review and implement the necessary sharing and security aspects as per the Salesforce org's requirements.
- The methods are annotated with `@AuraEnabled`, making them accessible from Aura and LWC components, allowing for easy integration into Salesforce Lightning Experience.
- Exception handling is limited to throwing the exception message to the Aura handler, which might require enhancement for production use, including logging and more detailed user feedback.
- Dynamic SOQL is used in the creation of chat records; ensure to handle or sanitize inputs correctly to prevent SOQL injection vulnerabilities.