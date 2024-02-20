### Description

This Salesforce Lightning Web Component (LWC) named `NuContactRelatedList` is designed to manage and display candidate records from a Salesforce Org. It utilizes a mixture of standard Salesforce UI elements such as `lightning-datatable`, `lightning-input-field`, `lightning-button`, etc., along with custom components to create a rich user interface for interacting with candidate data. The component's functionality includes searching, sorting, filtering candidates, and creating new candidate records through a modal form.

### Properties

- `sortBy` (String, @track): Key by which the list of candidates is currently sorted.
- `sortDirection` (String, @track): The current direction of sorting (ascending or descending).
- `searchString` (String, @track): The current search query.
- `initialRecords` (Array, @track): The initial list of candidate records before any search or filter is applied.
- `enableContactPollsCreation` (Boolean, @track): Controls the visibility of a modal form for creating new candidate records.
- `contactId` (String): The contact Id related to the current user or context.
- `candidateRt` (String): Candidate record type Id.
- `accountId` (String): Account Id associated with the current user or context.
- `containerStyle` (String): Dynamic styling for the component container, based on account settings or theme.
- `sectionHeadingStyle` (String): Dynamic styling for the page header, based on account settings or theme.
- `columns` (Array): Defines the columns to display in the `lightning-datatable`.

### Methods

- `handleProviderClassChange(event)`: Handles changes to the provider class selection.
- `handleEnableContactCreation()`: Toggles the visibility of the modal for candidate creation.
- `handleEnableContactCreationSuccess(event)`: Handles success after a new candidate is created, and updates the list.
- `createContact()`: Initiates the creation of a new contact based on input from the modal form.
- `validateFields()`: Validates the fields in the form before submission.
- `doSorting(event)`: Sorts the list of candidates based on selected column and direction.
- `sortData(fieldname, direction)`: Helper method for sorting data.
- `handleSearch(event)`: Filters the list of candidates based on a search query.
- `handleClassFilterChange(event)`: Filters the list of candidates based on selected classifications.
- `doFilter()`: Applies the selected filters to the list of candidates.

### Use Case

This component is used for managing candidate records within a Salesforce Org. It allows users to view candidate details, search and filter candidates based on various criteria, and add new candidates through a modal form. It can be particularly useful in recruitment or HR applications where managing a pool of candidates is required.

### Important Notes

1. **Security**: Ensure that Apex controllers and methods have the proper security annotations and access controls to protect sensitive data.
2. **Custom Styles**: The component dynamically applies styles based on account settings or themes. Ensure these settings are properly configured to reflect the desired UI.
3. **Component Communication**: The component demonstrates efficient use of LWC lifecycle hooks and wire service to fetch, display, and refresh data.
4. **Validation**: The component includes client-side validation before attempting to create a new record. Ensure server-side validations are also in place for robustness.
5. **Performance**: The component makes use of `@wire` to automatically cache records and reduce server calls, which helps in improving the performance.

