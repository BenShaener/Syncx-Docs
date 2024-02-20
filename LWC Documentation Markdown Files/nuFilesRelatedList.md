### Description

This Lightning Web Component (LWC) named `NuFilesRelatedList` is designed to display a list of related files for a specific Salesforce record. It utilizes a `lightning-card` to encapsulate a file upload component and a list of files. Each file in the list has options to download or preview it. This component leverages Salesforce's Lightning Design System (SLDS) for styling and is built to be used within the Salesforce Lightning Experience or Salesforce App.

### Methods

1. **connectedCallback**: This lifecycle hook is executed when the component is inserted into the DOM. It calls the Apex method `getRelatedFilesByRecordId` to fetch related files based on the `recordId`. It transforms the fetched data into a format suitable for rendering in the component.

    ```javascript
    connectedCallback() {
        getRelatedFilesByRecordId({recordId : this.recordId})
        .then(data => {
            // Handling data
        })
        .catch(error => {
            // Error handling
        })
    }
    ```

2. **previewHandler**: This method is triggered when the "Preview" button next to a file is clicked. It uses Salesforce's `NavigationMixin` to navigate to the file's preview URL in a new tab or window.

    ```javascript
    previewHandler(event){
        this[NavigationMixin.Navigate]({
            type:'standard__webPage',
            attributes:{
                url: event.target.dataset.url
            }
        })
    }
    ```

### Properties

1. **recordId** *(api)*: The ID of the Salesforce record for which related files are to be displayed. It is decorated with `@api`, making it publicly accessible for the component to be configured with a specific record ID.

    ```javascript
    @api recordId;
    ```

2. **filesList** *(track)*: An array that stores the list of files related to the `recordId`. This property is reactive, meaning any change to its value re-renders the component UI where `filesList` is used.

    ```javascript
    @track filesList = [];
    ```

3. **acceptedFormats**: A getter method that returns an array of accepted file formats for upload, currently configured to only accept PDF files.

    ```javascript
    get acceptedFormats() {
        return ['.pdf'];
    }
    ```

### Use Case

This component can be utilized in Salesforce record pages where there's a requirement to show related files for that record. It's particularly useful for cases like Job Application records where CVs or resumes (in PDF format) are associated with records and need facilities for upload, download, and preview.

### Important Notes:

- **Apex Class Dependency**: This component depends on an Apex class named `nuController_RelatedLists` and specifically a method `getRelatedFilesByRecordId`. You must ensure that this Apex class is properly implemented and accessible by the component to fetch related files.

- **NavigationMixin and File Preview**: For the file preview feature, the `NavigationMixin` is utilized which requires the Salesforce `lightning/navigation` module. This allows files to be previewed in a new browser tab, depending on how the URLs are handled by the browser.

- **RecordId Requirement**: The component requires a valid `recordId` to fetch and display related files. Ensure that the component is placed in contexts where the `recordId` is available, such as a record page.

- **Accepted Formats for Upload**: Currently, the component is restricted to accept only PDF files for upload. This can be adjusted by modifying the `acceptedFormats` getter method to include other file types as needed.

Incorporating this component into your Salesforce org provides an elegant solution for handling file uploads, and displaying related files with options to download or preview directly from a record's page, enhancing the overall user experience.