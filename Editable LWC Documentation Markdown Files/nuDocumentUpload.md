### Description

The Lightning Web Component (LWC) named `NuQuickActionPresentCandidate` is designed to facilitate the process of presenting a candidate in Salesforce. It features a modal dialog with dynamic content based on the candidate's information, particularly focusing on the candidate's CV. The component supports uploading a CV, previewing an existing CV, and submitting the candidate’s information for further processing. It also uses a custom child component `c-nu-provider-presentation-form` for a form presentation and integrates with the Salesforce Lightning Design System (SLDS) for styling.

### Methods

- **handleHAResult**: Triggered when receiving the candidate ID from the `c-nu-provider-presentation-form`. This method fetches related files to check if the CV is available and updates the component's state accordingly.

```javascript
handleHAResult(event) {
    ...
}
```

- **submitProviderPresentation**: Invoked when the “Next” button is clicked. This method submits the provider presentation form.

```javascript
submitProviderPresentation() {
    ...
}
```

- **clearProviderPresentation**: Invoked when the “Clear Form” button is clicked. This method clears the provider presentation form.

```javascript
clearProviderPresentation() {
    ...
}
```

- **handleUploadFinished**: Executed when the file upload is completed. It updates the state to reflect the availability of the CV.

```javascript
handleUploadFinished() {  
    ...
}
```

- **previewHandler**: Handles the event for previewing the candidate's CV by navigating to the CV's URL.

```javascript
previewHandler(event) {
    ...
}
```

- **closeQuickAction**: Closes the quick action modal.

```javascript
closeQuickAction() {
    ...
}
```

- **doPresent**: Handles the presentation process of the candidate by updating certain records and closing the quick action upon completion.

```javascript
doPresent() {
    ...
}
```

### Properties

- **hiringAuditId** (`@api`): The identifier for the hiring audit record.
- **candidateId**: The candidate's identifier, updated after fetching related files.
- **cvPreviewUrl**: The URL to preview the candidate's CV.
- **headerText**: The text displayed in the modal header, default is "Present Candidate".
- **isCvAvailable**: A boolean indicating if the candidate's CV is available.
- **showSpinner**: Controls the visibility of the spinner during asynchronous operations.
- **isPresentButtonDisabled**: A boolean to enable or disable the "Present" button based on certain conditions.
- **showPresentationForm**: Determines whether the presentation form or the CV upload interface should be displayed.

### Use Case

The `NuQuickActionPresentCandidate` component is used within Salesforce to streamline the process of presenting candidates to clients. It provides a user-friendly interface for:
- Viewing if a candidate's CV is available and previewing it.
- Uploading a new CV if it's not available.
- Submitting candidate presentation information through a custom form.
- Dynamically updating the presentation status of a candidate.

### Important Notes

- The component utilizes Salesforce's `lightning/uiRecordApi` for record operations like fetching and updating records.
- It makes use of custom Apex methods like `getRelatedFilesByRecordId` to fetch related documents (e.g., CVs).
- The component is integrated with SLDS for consistent Salesforce UI styling.
- NavigationMixin from `lightning/navigation` is used for navigating to external web pages, such as CV previews.
- This component should be placed in contexts where a `hiringAuditId` can be provided as it's essential for its operations.
- The component assumes that the `c-nu-provider-presentation-form` child component exposes methods for submitting and clearing the form, which is crucial for interaction.
