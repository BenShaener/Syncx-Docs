## Description

The `RelatedFilesTable` component, designed for Salesforce Lightning Experience, beautifully presents a table of related document files for a given record. It fetches related files based on specific criteria and allows users to review these documents by navigating to their URLs. This component elegantly encapsulates the functionality using Salesforce Lightning Web Component (LWC) standards, Apex controller calls for data retrieval, and utilizes Lightning Design System (LDS) for styling to ensure a consistent user experience that aligns with Salesforce's design aesthetics.

## Methods

### renderedCallback()
This lifecycle hook is invoked when the component has been inserted into the DOM and after every render of the component. It calls the `getRelatedFiles()` method to fetch the related files every time the component renders.

```javascript
renderedCallback() {
    this.getRelatedFiles();
}
```

### getRelatedFiles()
An `@api` decorated method, making it publicly available for invocation from other components or for compositional purposes. It calls the `getRelatedFiles` Apex method with parameters `recordId` and `withoutCv`. It updates the component's `data` property with the fetched results or logs an error in case of failure.

```javascript
@api
getRelatedFiles() {
    getRelatedFiles({ recordId: this.recordId, withoutCv: this.withoutCv })
    .then(result => {
        this.data = result;
    })
    .catch(error => {
        console.error('nuQuickActionPresentCandidate get files error', JSON.stringify(error));
    })
}
```

### previewHandler(event)
Handles clicks on the "Review" button within the data table. It uses the `NavigationMixin.Navigate` method to navigate the user to the document's URL specified in the button's `data-url` attribute.

```javascript
previewHandler(event) {
    this[NavigationMixin.Navigate]({ 
        type:'standard__webPage',
        attributes:{ 
            url: event.target.dataset.url
        }
    })
}
```

## Properties

- `recordId`: Decorated with `@api`, it allows the parent component to pass the record ID for which the related files are to be fetched.

- `withoutCv`: Another `@api` decorated property indicating whether to exclude certain files based on criteria (e.g., CV files).

- `data`: An array that holds the fetched related files data after it is retrieved from the Apex controller.

## Use Case

This component is ideal for use cases where a Salesforce record is associated with various document files, and there's a need to display these files in a structured manner within the Lightning Experience. Specifically, it can serve as a component on a record page, showing all related documents that a user can review directly by clicking a button.

## Important Notes

- Ensure the Apex class `nuController_RelatedLists` and its method `getRelatedFilesWithCriteria` are properly defined and set up with the required permissions. The Apex method should be capable of accepting `recordId` and `withoutCv` parameters and return the related files.

- Customize the component by adjusting CSS classes as per the Salesforce Lightning Design System (SLDS) to maintain design consistency across your Salesforce org.

- The component employs Lightning Data Service (LDS) and Navigation service. Make sure to test the navigation functionality thoroughly as URL redirection behavior might vary based on Salesforce's setup and version.

- As with any component that fetches data from the server, consider handling large data volumes and implement pagination or lazy loading if necessary to enhance performance.

- Review and adhere to Salesforce's security best practices, especially concerning Apex controller methods used in Lightning Web Components.