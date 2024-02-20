### Description
A global class designed to send batch emails to a list of `Contact` records using a predefined email template and organizational-wide email address. This class implements the `Database.Batchable<SObject>` interface, allowing it to process a large number of records in batches, making it efficient for operations that need to send emails to a large number of contacts in Salesforce. It supports customizing the email template, the related object ID (`whatId`) for template merging, and the sender email address through an organizational-wide email address ID.

### Methods
- **nuBatchEmail(List<Contact> contacts):** Constructor to initialize the batch process with a list of contacts to whom the emails will be sent.
- **start(Database.BatchableContext BC):** Initializes the batch job, returning a list of `Contact` records to process.
- **execute(Database.BatchableContext BC, List<SObject> scope):** Takes a batch of `Contact` records and sends an email to each contact using the defined email template and organizational-wide email address ID.
- **finish(Database.BatchableContext BC):** Placeholder for any logic that needs to be executed after all the batches are processed.

### Properties
- **contactList:** Stores the list of `Contact` records to be processed by the batch class.
- **templateId:** ID of the email template to be used for sending emails.
- **whatId:** ID of the object that the email template is related to, for template field merging.
- **orgWideEmailAddressId:** ID of the organizational-wide email address to be used as the sender email.

### Use Case
This class is particularly useful when needing to send a mass email to a group of contacts in Salesforce, using a single email template and ensuring the emails are sent from an official or organizational-wide email address. A possible scenario includes sending monthly newsletters, updates on services or products, or any communication that needs to leverage Salesforce's email capabilities at scale.

### Important Notes
- Ensure that the `templateId`, `orgWideEmailAddressId`, and (if applicable) the `whatId` are correctly set before executing the batch job to avoid sending out incorrect or incomplete emails.
- The `Database.Batchable<SObject>` interface allows handling of large datasets by breaking the operation into smaller batches, thereby respecting Salesforce governor limits.
- The actual sending of emails is contingent on the organization's email limits and the proper configuration of the email template and the organizational-wide email address.
- It's important to have the necessary permissions and the organizational-wide email address properly set up in Salesforce to use this functionality.
