### Description

The `NuQuickActions` component is a versatile Salesforce Lightning Web Component (LWC) designed to handle a wide array of quick actions related to recruitment processes, like submitting candidates, presenting candidates, setting up interviews, making offers, and much more. This component dynamically renders child components based on the type of action determined by the `quickActionApiName` property. Each child component represents a specific quick action and is capable of emitting a `finishQuickAction` event upon completion.

### Methods

- **`connectedCallback()`**: Lifecycle hook that runs when the component is inserted into the DOM. It evaluates the `quickActionApiName` property and sets flags to conditionally render the appropriate child component.

- **`finishQuickAction(event)`**: Handler for the `finishQuickAction` event emitted by any of the child components. It further dispatches a `finishQuickAction` event, optionally with details from the event it received.

### Properties

- **`recordId`** (`@api`): The Salesforce record ID related to the quick action.
- **`agencyId`** (`@api`): The Salesforce record ID for the agency, relevant for certain actions.
- **`quickActionLabel`** (`@api`): Label for the quick action, used for display purposes in child components.
- **`quickActionApiName`** (`@api`): API name of the quick action, used to determine which child component to display.
- **`showEndDate`**, **`showStartDate`** (`@api`): Boolean flags to control the visibility of start and end date fields in certain actions.
- Various boolean flags like `isSubmitCandidate`, `isMakeOffer`, etc., which are set based on the `quickActionApiName` and control the rendering logic for different actions.

### Use Case

This component can be used in a Salesforce org where recruitment-related Quick Actions need to be performed directly from a Lightning page. For example, a recruiter could use this component on a Job Order record page to perform actions such as submitting candidates to the job order, presenting them to the hiring manager, or making an offer to the candidate, all without leaving the page.

### Important Notes

- The `connectedCallback()` method plays a crucial role in component initialization by deciding which child component needs to be displayed based on the `quickActionApiName` property.
- The child components are expected to emit a `finishQuickAction` event upon completing their tasks. This event is then captured by the parent `NuQuickActions` component and can be handled or propagated further as needed.
- The component employs Salesforce Lightning Web Component (LWC) technology, making it suitable for embedding within Lightning Experience, Salesforce Mobile App, or any web technology that supports LWC.

### Example

To use this component for a specific quick action, ensure it is placed on a page with its `quickActionApiName` property set to match the API name of the desired action. For example:

```html
<c-nu-quick-actions quick-action-api-name="Job_Order__c.Submit_Candidate" record-id="a1S3h0000074hELEAY"></c-nu-quick-actions>
```

This instantiation of the component will render the UI for submitting a candidate because the `quickActionApiName` matches the case in the `connectedCallback()` method that sets `this.isSubmitCandidate = true`.