### Description
This class provides functionality for managing `Notification__c` records within a Salesforce org. It includes methods to fetch notifications for a specific contact or account, update the read status of a notification, and build a notification instance.

### Methods

- `fetchNotifications(String contactId)`: Fetches notifications related to a specific contact ID.
    ```java
    public static nuServiceResult fetchNotifications(String contactId)
    ```
- `fetchNotificationsForAccount(String accountId)`: Fetches a list of notifications for all contacts under a specific account ID, limited to the 100 most recent entries.
    ```java
    public static nuServiceResult fetchNotificationsForAccount(String accountId)
    ```
- `updateReadOn(String notificationId)`: Updates the `Read_On__c` field of a specific `Notification__c` record with the current date and time.
    ```java
    public static nuServiceResult updateReadOn(String notificationId)
    ```
- `buildNotification(String contactId, String body, String title, String targetId, String dashboardTile)`: Creates an instance of a `Notification__c` record with provided details. It does not perform DML operations.
    ```java
    public static Notification__c buildNotification(String contactId, String body, String title, String targetId, String dashboardTile)
    ```

### Properties
No explicit properties are defined or used outside the methods. Objects and their fields are interacted with directly within method scopes.

### Use Case
Use this class to interact with notification records in applications, especially in the context of Salesforce Lightning Components or Salesforce Lightning Web Components. It can be utilized to display notifications to a contact or to aggregate notifications at an account level, mark notifications as read, or construct new notification objects for further processing.

### Important Notes
- Make sure that `Notification__c` custom object and its fields such as `Read_On__c`, `Body__c`, `Title__c`, `Dashboard_Tile__c`, `Contact__c`, `Is_Alert__c`, and `Target_Record_Id__c` are defined in your Salesforce org.
- The `@AuraEnabled` annotation makes these methods accessible from Lightning components, ensuring they can be called from the client side.
- The `nuServiceResult` type used for returning data from the methods suggests a custom wrapper class designed for handling operation outcomes, including success data or errors, but its structure isn't provided here.
- Operations like fetching notifications and marking them as read perform SOQL queries and DML operations, respectively, which count towards your org's governor limits.
- There’s inline exception handling in `updateReadOn`, which catches `DmlException` and stores the error message. Ensure proper error handling in the client-side implementation to maintain user experience.