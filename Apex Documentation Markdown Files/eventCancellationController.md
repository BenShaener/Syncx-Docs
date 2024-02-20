### Description

The `eventCancellationController` Apex class is designed to manage the cancellation process of scheduled events, specifically by handling the workflow for sending cancellation emails and acknowledging cancellations. It interacts with Salesforce's `Scheduled_Event__c` custom object and utilizes Salesforce's email messaging service to notify relevant parties regarding event cancellations. This class is marked as `without sharing` to ensure it adheres to the organization-wide default sharing settings, providing controlled access to data based on the Salesforce sharing model.

### Methods

#### `manageCancelEmails(List<String> idInputs)`

Accepts a list of strings representing event IDs and processes cancellation requests or acknowledges cancellations by sending emails and updating event records in the database.

#### `cancelAndEmail(List<Scheduled_Event__c> events, String cancelledBy)`

Marks events as cancelled, constructs and sends a cancellation email to the relevant contact (either the client's clinical contact or the agency's recruiting contact), and creates a `Notification__c` record to log this action.

#### `acknowledgeAndEmail(List<Scheduled_Event__c> events)`

Updates events to mark them as acknowledged, constructs and sends an email to confirm the cancellation, and creates `Notification__c` records for both the client and agency's contacts to log the action.

### Properties

This class does not explicitly declare any properties outside of its methods.

### Use Case

The `eventCancellationController` class is specifically designed for the use case of managing scheduled events within a Salesforce organization that utilizes a custom object (`Scheduled_Event__c`) to track events. It is intended to be used in scenarios where events can be cancelled by either an agency or a client, requiring notifications and acknowledgements to be sent out accordingly. The class handles the intricacies of determining who needs to be notified, what information needs to be included in the notifications, and ensuring that all relevant records are updated appropriately.

### Important Notes

- The `@invocableMethod` annotation on `manageCancelEmails` allows this method to be called from Salesforce's process builder or flows, making it easily integrable into automated processes.
- The class makes use of dynamic SOQL queries and DML operations within loops, which could lead to governor limits being reached if not carefully managed.
- Since this class is marked as `without sharing`, it does not enforce record-level sharing rules. This means it will run in the system context and have access to all objects and fields—operation permissions dependent on the executing user's profile and permission sets still apply.
- Error handling is minimal in the provided methods, and enhancements may be required to robustly handle failures in production environments.
- The usage of hardcoded string lengths (e.g., `idInputs[0].length();i+=18`) for ID parsing assumes the standard Salesforce 18-character ID format, which may not be suitable for all potential use cases or future changes in ID format.