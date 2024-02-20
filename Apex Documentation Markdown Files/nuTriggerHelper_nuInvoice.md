**Description:**
This class is designed to handle the generation and sending of notifications and emails for invoice-related events in the Salesforce platform. Specifically, it supports the creation and dispute notification process for `nuInvoice__c` objects. It utilizes custom notifications and email messages to notify relevant contacts about new or disputed invoices.

**Methods:**

- `handleInvoiceNotifications(List<nuInvoice__c> newInvoices, Map<Id, nuInvoice__c> oldMap)`: This method accepts a list of `nuInvoice__c` records and an optional map of old `nuInvoice__c` records. It queries for necessary fields, processes each invoice to determine if a notification and email should be sent, and finally inserts notifications and potentially sends emails based on invoice conditions.

- `private Notification__c buildNotificationForInvoice(String title, String body, Id targetRecord, Id contactId, Boolean isAlert)`: Constructs a `Notification__c` object for an invoice event. This object contains details like the title, body, target record ID, contact ID, dashboard tile, and alert status.

- `private Messaging.SingleEmailMessage buildEmailForInvoice(String subject, String body, String target)`: Prepares a `Messaging.SingleEmailMessage` object for an invoice event. This method sets the email subject, body, target object ID, uses an organization-wide email address for sending, and ensures the email is not logged as an activity.

**Properties:**

- `notificationType`: Static final property that holds the custom notification type used for sending out custom notifications. This is fetched from the `CustomNotificationType` object where the `DeveloperName` equals 'Sync_Notification'.

- `owa`: Holds the `OrgWideEmailAddress` object used when sending emails. It selects the first org-wide email address where the display name equals 'Syncx'.

**Use Case:**

This helper class is used in scenarios where there’s a need to automate the notification and communication process regarding invoice creation and disputes within a Salesforce organization. It can be called upon invoice record creation or update to generate custom notifications and emails targeted at specific contacts associated with the invoice (either client-side or agency-side contacts).

**Important Notes:**

- The `handleInvoiceNotifications` method conditionally processes invoices based on whether they are new or have had their status updated to "Invoice Disputed". The behavior varies significantly based on these conditions.

- The method bypasses the sending of emails (`Messaging.sendEmail`) and logging the result as this section of the code is commented out. Implementers looking to activate email functionality should un-comment and handle potential exceptions or failures.

- Use of `nuHelper_Queues.filterSet` in sending custom notifications is noted but commented out in the code, indicating it's a placeholder for filtering target recipient IDs based on specific criteria (like the Synchronized Account Manager for an agency or client). Proper implementation is necessary to utilize this functionality.

- The class uses a static query to assign the `notificationType` and `owa` properties, which may throw exceptions if the expected records are not found. Error handling for these queries should be considered during implementation for robustness.