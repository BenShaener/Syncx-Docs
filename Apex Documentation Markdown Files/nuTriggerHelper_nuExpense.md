### Description

This Apex class provides utility functions to assist with expense-related processes within a Salesforce instance. Specifically, it includes methods to process expense notifications, manage expense updates based on status changes (approval or rejection), and adjust administrative fees based on assignment audit records. The class is designed for use with custom objects and fields, indicating its tailored use for a specific organizational setup.

### Methods

- `fetchExpenseNotifications(List<nuExpense__c> newExpenses, Map<Id, nuExpense__c> oldMap)`: Processes expense records to send notifications and emails based on status changes to 'Approved' or 'Rejected'. It also updates expense records with approval details.
- `sendNotificationsToManagers(nuExpense__c expense, String body, Id clientManager, Id agencyManager, List<Messaging.SingleEmailMessage> allmsg)`: Sends custom notifications to specified managers regarding expense status updates.
- `buildNotificationForExpense(String title, String body, Id targetRecord, Id contactId, String tile, Boolean isAlert)`: Constructs a custom notification record for an expense.
- `buildEmailForExpense(String subject, String body, String target)`: Creates a single email message related to an expense, settings its subject, body, and target recipient.
- `setAdminFee(List<nuExpense__c> newList)`: Iterates through a list of expense records to update the administrative fee based on related audit records of assignment admin fees.

### Properties

- `notificationType`: Holds metadata about a specific Custom Notification Type queried based on DeveloperName 'Sync_Notification'.
- `owa`: Stores the selected Org-Wide Email Address based on DisplayName 'Syncx', used for sending emails.

### Use Case

This class is intended to be utilized as a helper within trigger frameworks for handling expenses (`nuExpense__c` custom object). It can be invoked when expenses are created or updated to manage notifications, emails, and data integrity tasks like updating administrative fees. The functionalities embedded are especially useful for workflows that involve expense approvals, rejections, and related audits.

### Important Notes

- The class operates without sharing mode (`without sharing`), implying that it doesn't enforce the sharing rules of the current user. This aspect is crucial for data access considerations, ensuring that the methods can be executed irrespective of the executor's permission set concerning the records in question.
- The operations related to sending emails and notifications are contingent on the existence and proper configuration of specific custom settings (`CustomNotificationType` and `OrgWideEmailAddress`), as well as the presence of certain fields on the Custom Objects involved (`nuExpense__c`, `Notification__c`, etc.).
- The method `setAdminFee` makes use of a nested querying pattern and conditional logic to update records based on related `Assignment_Audit__c` records' data, demonstrating a complex data manipulation scenario inherent to Salesforce Apex programming.