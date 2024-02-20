**Description:**  
This Apex class is designed to handle notification-related functionalities within Salesforce. It encapsulates properties for managing and displaying notifications, such as title, body, and read status, among others. The class is marked as `without sharing` ensuring that it does not enforce the sharing rules of the running user.

**Methods:**  
This class does not contain any methods. It only includes properties for handling notification data.

**Properties:**  

- `notificationId` (String): Unique identifier for the notification.
- `contactId` (String): Identifier for the contact associated with the notification.
- `title` (String): Title of the notification.
- `body` (String): Body text of the notification.
- `readOn` (Datetime): Timestamp when the notification was read.
- `referenceText` (String): Optional reference text related to the notification.
- `referenceUrl` (String): Optional URL for additional information related to the notification.
- `dashboardTile` (String): Identifier for a dashboard tile associated with the notification, if any.
- `targetId` (String): Identifier for the target record related to the notification.
- `isAlert` (Boolean): Flag indicating if the notification is an alert.
- `isNew` (Boolean): Flag indicating if the notification is new.

**Use Case:**  
This class is ideal for managing user notifications within a Salesforce org. It could be used to represent notifications in a custom notification center, providing users with personalized alerts, messages, and updates related to their accounts, contacts, or other relevant records. The class allows for easy tracking of whether notifications have been read and supports including actionable items through reference URLs.

**Important Notes:**

- Given that the class is marked with `without sharing`, it does not respect record-level security. This should be carefully considered when accessing or modifying data to ensure compliance with the organization's data security policies.
- The class is designed to work with Aura components, as indicated by the `@AuraEnabled` annotations. This makes it suitable for use in Lightning Web Components (LWC) as well, with minor adjustments if necessary.
- The absence of methods suggests this class is primarily used for data representation rather than encompassing business logic.

