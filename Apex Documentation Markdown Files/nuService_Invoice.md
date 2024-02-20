### Description
This class is designed to serve as a service layer for fetching invoice records related to a specific agency and work location. It acts as a bridge between the UI layer (likely exposed via Aura or Lightning Web Components) and the back-end logic encapsulated in another class (`nuGateway_Invoice`). It utilizes Salesforce's "without sharing" context to ensure that it runs with the full permissions of the system, regardless of the user's permissions.

### Methods

- `fetchInvoicesWithWorklogs(Id agencyId, Id worklocationId)`: This is a static method that is exposed to the Aura framework (and could be exposed to Lightning Web Components via the `@AuraEnabled` annotation). It takes two parameters: `agencyId` and `worklocationId`, both of which are expected to be Salesforce record IDs in the string format. This method delegates the actual fetching of data to the `nuGateway_Invoice` class's `fetchInvoicesWithWorklogs` method, passing the same parameters it receives. It returns a List of `nuInvoice` objects. 

    ```java
    public static List<nuInvoice> fetchInvoicesWithWorklogs(Id agencyId, Id worklocationId){
        return nuGateway_Invoice.fetchInvoicesWithWorklogs(agencyId, worklocationId);
    }
    ```

### Properties
There are no properties explicitly defined within this class.

### Use Case
A common use case for this class would be to provide a backend service for a frontend Salesforce component (Aura or LWC) that needs to display a list of invoices along with their associated work logs. The component would invoke this class's `fetchInvoicesWithWorklogs` method, providing it with the necessary `agencyId` and `worklocationId` to fetch the relevant invoices.

### Important Notes
- Since this class is defined as `without sharing`, it does not enforce the sharing rules of the running user. This design decision should be carefully considered and reviewed to ensure it aligns with the application's security requirements.
- The class acts more as a pass-through or facade for `nuGateway_Invoice.fetchInvoicesWithWorklogs`, meaning any changes to the logic in `nuGateway_Invoice` will directly impact this class's behavior.
- This class relies heavily on the structure and functionality of the `nuInvoice` object and the `nuGateway_Invoice` class. Any modifications to these components could necessitate changes in this class.