### Description
This class is designed to send emails to the appropriate contacts when a claim on a scheduled event has been declined. It utilizes an `EmailTemplate` specific for declined claims and sends these emails from a designated `OrgWideEmailAddress`.

### Methods
- `sendOpenScheduledEventEmail(List<Scheduled_Event_Claim__c> claimList)`: This method is an `@InvocableMethod` which means it can be called by Salesforce flows or process builder. It iterates over a list of `Scheduled_Event_Claim__c` records and invokes the `sendOpenScheduledEventEmailFuture` method for each claim by passing the list of claim IDs.

- `sendOpenScheduledEventEmailFuture(List<Id> claimIdList)`: Marked with `@future(callout=true)`, indicating it can handle callouts to external systems asynchronously and avoids governor limits. This method retrieves the relevant claim record and all matching `nuPlacement__c` records based on criteria (e.g., Specialty, Provider Type, and Work Location). For each contact related to a matching `nuPlacement__c`, it sends a templated email if they haven't already received one.

### Properties
- `openJOtemplate`: A static `EmailTemplate` object loaded with an email template designated for notifying about declined claims.
- `owa`: A static `OrgWideEmailAddress` object used as the sender address for the emails dispatched.

### Use Case
Use this class when you need to notify agency contacts about declined claims on scheduled events. It could be leveraged in scenarios where it's critical to communicate quickly and efficiently with external staffing agencies about changes in claim status, ensuring all parties are up-to-date with the latest scheduling information.

### Important Notes
- The `sendOpenScheduledEventEmail` method is designed to be invoked from automated processes in Salesforce, offering flexibility in how and when email notifications are sent.
- The `sendOpenScheduledEventEmailFuture` method enforces a one-time email rule per claim per contact, reducing the risk of spamming contacts with duplicate notifications.
- It's important to ensure the `EmailTemplate` and `OrgWideEmailAddress` are correctly set up in Salesforce before using this class to prevent errors in sending emails.
- This class does not directly execute `Messaging.sendEmail(emailList);` to send the emails. Un-comment this line when you're ready to send emails after testing.

