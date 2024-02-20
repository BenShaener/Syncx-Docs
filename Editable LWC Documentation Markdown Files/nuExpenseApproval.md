### Description

The Lightning Web Component (LWC) `NuExpenseApproval` is designed for approving, rejecting, or viewing expenses in a Salesforce environment. This component utilizes Salesforce Lightning Design System (SLDS) for styling and `@salesforce/apex` to communicate with the Apex classes for CRUD operations on expense records. The component is divided into tabs (`Submitted`, `Approved`, `Rejected`) each displaying relevant expenses in an accordion layout. The component also features modal dialogs for additional interactions such as rejecting an expense with a reason.

### Methods

1. **handleRowAction**: Invoked when an action is performed on a row in the `lightning-datatable`. It handles different row actions like viewing the file associated with an expense.

    ```javascript
    handleRowAction(event) { ... }
    ```
   
2. **handleRejectClick & handleApproveClick**: These methods are triggered when the `Reject` or `Approve` button is clicked for an expense. They set up the UI and data for further operations.

    ```javascript
    handleRejectClick(event) { ... }
    handleApproveClick(event) { ... }
    ```

3. **handleApproveAllClick**: Invoked when the `Approve All` button is clicked, iterating over all submitted expenses and approving them.

    ```javascript
    handleApproveAllClick() { ... }
    ```

4. **handleInputChange**: Handles changes in input fields, specifically for updating the rejection reason.

    ```javascript
    handleInputChange(event) { ... }
    ```

5. **rejectExpense & closeModal**: `rejectExpense` is called to proceed with the rejection of an expense, while `closeModal` is called to close the modal dialog.

    ```javascript
    rejectExpense() { ... }
    closeModal() { ... }
    ```

6. **handleDateChange**: Handles changes in the date range filters.

    ```javascript
    handleDateChange(event) { ... }
    ```

### Properties

1. **expenses**: Getter property to check if there are any expenses in the list.
   
    ```javascript
    get expenses() { ... }
    ```
   
2. **showApproveAll**: Determines if the `Approve All` button should be visible based on whether there are submitted expenses.

    ```javascript
    get showApproveAll() { ... }
    ```

### Use Case

To utilize `NuExpenseApproval` in your Salesforce org, ensure that Apex classes for fetching and updating expenses (`fetchExpensesForApproverContact`, `approveExpense`, `rejectExpense`) are correctly set up. This component is designed for approvers to manage expense records effectively, offering functionalities such as approval of individual or all expenses, rejection of expenses with a reason, and viewing attached files.

### Important Notes

- The component relies on Apex controllers for backend operations. Make sure the Apex classes and methods are properly defined and have the necessary access rights.
- Custom styles are imported from `c/nuCSS`. Ensure this static resource or similar is available in your Salesforce org for styling purposes.
- The component uses SLDS classes extensively for its layout and styling. Familiarity with SLDS is recommended for customization.
- Ensure that the API names used in the component (e.g., field names in the `lightning-input` and `lightning-datatable`) match those in your Salesforce org's schema.


### Conclusion

`NuExpenseApproval` offers a comprehensive solution for managing expense approvals within Salesforce. It leverages LWC capabilities, Apex backend operations, and SLDS for styling, ensuring a smooth experience for users dealing with expense records.