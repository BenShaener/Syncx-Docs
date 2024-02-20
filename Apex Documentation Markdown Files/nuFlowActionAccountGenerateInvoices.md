### Description
This Apex class provides functionality for generating invoices based on specific parameters. It is designed to be called from Salesforce's process automation tools, such as Process Builder or Flow, due to its use of the `@InvocableMethod` annotation. This class does not enforce sharing rules, ensuring that the method has access to all relevant data, regardless of the user's permissions.

### Methods
- **generateInvoices(List<String> params)**: This is an invocable method that takes a list of strings as parameters. These parameters should include the weekend date and the work location ID, separated by a semicolon. The method parses these parameters, logs them for debugging purposes, and triggers a batch process to generate invoices based on the provided date and location.

### Properties
This class does not explicitly define properties but utilizes local variables within the `generateInvoices` method to process the input parameters.

### Use Case
A typical use case for this class is to automate the generation of invoices for work completed up to a certain week's end date at a specific work location. By setting up a process or flow in Salesforce that triggers this class, businesses can automatically initiate the invoice generation process based on the defined criteria. This automation is particularly useful in scenarios where invoice generation is a regular, time-bound process that is dependent on two key pieces of information: the date marking the end of the workweek and the unique identifier of the work location.

### Important Notes
- The class is declared as `public without sharing`, which means it does not automatically enforce the sharing rules of the running user. This is an important consideration for organizations that are concerned with data security and access control. 
- The `generateInvoices` method expects a specific format for its input parameter: a list containing a single string, where the desired week's end date and the work location ID are concatenated and separated by a semicolon. It's crucial to adhere to this format to ensure the correct operation of the method.
- The batch process is executed with a batch size of 1, indicating that records will be processed one at a time. Depending on the volume of data and the complexity of the batch class `nuBatchable_GenerateInvoices`, this setting could impact performance and may need adjustment.
- Since the method uses `Database.executeBatch`, it's necessary to have a corresponding batch class (`nuBatchable_GenerateInvoices`) implemented and ready. This class is responsible for the actual logic of generating invoices, while `nuFlowActionAccountGenerateInvoices` serves as a trigger mechanism.