### Description
This class provides functionality for managing notifications and email communications related to changes in `nuTimesheet__c` records. Additionally, it handles the setting of administration fees for timesheet records based on assignment audits.

### Methods

- `fetchTimesheetNotifications(List<nuTimesheet__c> newWorkRecords, Map<Id, nuTimesheet__c> oldMap)`: Fetches and generates email and platform notifications for new or updated timesheet records based on their status changes.

- `buildNotificationForWorkRecord(String title, String body, Id targetRecord, Id contactId, String tile, Boolean isAlert)`: Builds a custom notification object for work records.

- `buildEmailForWorkRecord(String subject, String body, String target)`: Constructs an email message targeting a specific user based on a work record event.

- `setAdminFee(List<nuTimesheet__c> newList)`: Adjusts the administration fee on timesheet records using the most recent audit data and placement records.

### Properties
- `notificationType`: A `CustomNotificationType` record storing the developer name 'Sync_Notification' used for sending out custom notifications.
- `owa`: An `OrgWideEmailAddress` record referenced by display name 'Syncx' used as the sender for outgoing emails.

### Use Case
Use this class when you need to automate the process of sending notifications and emails in response to timesheet record submissions, approval, rejections, or updates. You can also utilize it to dynamically update administrative fees on timesheet records based on their associated placement records and assignment audits.

### Important Notes
- The method `sendNotificationsToManagers` is intended for sending notifications to managers but is currently commented out in certain places within `fetchTimesheetNotifications`. Ensure to configure or extend this functionality as per your requirements.
- `fetchTimesheetNotifications` handles different timesheet statuses ('Submitted', 'Approved', 'Rejected') and decides whether to send notifications and emails based on these statuses. This logic relies on the provided `oldMap` to detect status changes.
- The method `setAdminFee` makes use of historical audit data and current placement data to determine the appropriate administration fee for a timesheet. This method requires a proper setup of `Placement__c` and `Assignment_Audit__c` objects and fields.