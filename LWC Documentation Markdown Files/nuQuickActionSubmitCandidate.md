### Description

This Salesforce Lightning Web Component (LWC), `NuQuickActionSubmitCandidate`, provides a modal interface for submitting a candidate selection related to a job order and agency within Salesforce. The component displays a modal with a candidate lookup field that allows the user to search and select a candidate record. Once a candidate is selected, their ID is captured for submission when the "Save" button is clicked. The component utilizes an Apex controller method `submitCandidate` to submit the selected candidate's information.

### Methods

- **handleLookupRecord(event):** Reacts to the "lookupupdate" event emitted by the `c-candidate-lookup` component. It grabs the selected candidate's ID from the event's detail.

- **doSubmit(event):** Handles submission by invoking the Apex method `submitCandidate` with the selected candidate ID, job order ID, and agency ID. It utilizes promises to handle the response and potentially triggers a toast message if submission is duplicated.

- **closeQuickAction(event):** Dispatches a custom event, `finishquickaction`, signaling that the modal should be closed without performing any action.

- **@wire(getObjectInfo, { objectApiName: CONTACT_OBJECT }):** Wired method to get the record type ID for 'Candidate' from the `Contact` object's metadata.

### Properties

1. **@api jobOrderId:** External ID for a job order passed into the component.
2. **@api agencyId:** External ID for an agency passed into the component.
3. **@api quickActionLabel:** External label for the quick action, displayed as the modal's heading.
4. **candidateRecordTypeId:** Stores the record type ID for "Candidate", derived from the Contact object.
5. **candidateId:** The ID of the selected candidate to be submitted.

### Use Case

This component can be utilized in Salesforce as a quick action or a part of a bigger flow that requires selection and submission of candidate records linked to specific job orders and agencies. It's particularly useful in recruitment processes within Salesforce, allowing for streamlined candidate submissions with minimal user input. 

### Important Notes

- **Lookup Component Dependency:** This component uses a custom component, `c-candidate-lookup`, for looking up candidate records. Ensure this component is available and properly configured in your org.
  
- **Apex Controller Dependency:** The component relies on an Apex controller, `nuController_QuickActions`, specifically the `submitCandidate` method. This method must exist and be accessible by the component.
  
- **Error Handling:** The component uses a utility, `fireToast`, to display error messages. Make sure this utility is implemented and handles custom toast messages properly.

- **Record Type ID Fetching:** The component fetches the Record Type ID for "Candidate" dynamically; ensure the Contact object has a "Candidate" record type set up.

### CSS

Here is the CSS snippet used in the component:

```css
.hidden-submit {
    display: none;
}
```

This class is utilized to initially hide the submit button and programmatically trigger the form submission if needed (though the related JS functionality is commented out in the provided code).

### Example Usage

The component could be placed on a Lightning Page or within another component, and invoked with specific `jobOrderId` and `agencyId` values to tie the candidate submission to those records:

```html
<c-nu-quick-action-submit-candidate job-order-id="a1S4P000000k9UJ" agency-id="a2D4P000000k9UI" quick-action-label="Submit Candidate">
</c-nu-quick-action-submit-candidate>
```

This would render the modal for submitting a candidate for the specified job order and agency.