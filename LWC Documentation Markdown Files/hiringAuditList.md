### Description

The `HiringAuditList` component is designed to fetch and display a list of Hiring Audit records dynamically from Salesforce. It provides a powerful UI to filter these records based on various criteria such as Status, Candidate Name, Specialty Name, Location, and more. The component uses Lightning Web Components (LWC) and Salesforce Apex to retrieve data and manipulates it within a Lightning Data Table for a seamless user experience. Additionally, it offers conditional rendering of filters and dynamically adjusts its styling based on theme settings from related accounts.

### Properties

- `testAccountId`: API property used to pass the Account ID for testing purposes.
- `stage`: API property to define the current stage of the hiring audit process.
- `title`: API property to set the title of the component/page.

### Methods

#### `connectedCallback()`

Executes when the component is inserted into the DOM. It initiates the `fetchHiringAuditsData` function to retrieve audit data.

#### `fetchHiringAuditsData()`

Fetches hiring audits data from Salesforce using Apex methods based on the Hired Account's ID. This method also sets up various filters' options used for filtering the displayed data.

#### `renderedCallback()`

Executes after every render of the component. It is used for any post-render actions but is currently not used in this component.

#### `loadMoreData(event)`

(Optional) Can be utilized to fetch more data when the end of a datatable is reached. Currently commented out and not implemented in this example.

#### `doSorting(event)`

Handles sorting of the datatable columns. It captures the columnName and direction (asc/desc) and sorts the data accordingly.

#### `sortData(fieldname, direction)`

Utility method for sorting the datatable rows based on the column selected and the direction of sorting (ascending or descending).

#### `handle[FilterName]Change(event)`

Each `handle[FilterName]Change` method is responsible for capturing filter value changes (e.g., `handleStatusFilterChange`, `handleCandidateFilterChange`) and calls `doFilter` to update the displayed data based on the selected filters.

#### `doFilter()`

Applies all the active filters to the hiring audits data and updates the datatable to only show the filtered results.

### Use Case

The `HiringAuditList` component is ideal for Salesforce Community Pages or internal Salesforce org pages where there's a need to display and interact with a list of hiring audit records. This can be particularly useful for HR departments, recruitment agencies, or any organization managing a large number of hiring processes and looking to streamline their audit review process.

### Important Notes

1. The component relies heavily on Apex backend calls, which requires the respective Apex classes and methods (`nuService_nuJobOrder`, `nuService_Contact`, etc.) to be correctly implemented and accessible.
2. It dynamically adjusts some of its styling based on the `RecordType` and `Use_Portal_Theme__c` fields of the account associated with the user viewing the page. This requires the Account object to have these fields populated correctly.
3. The component includes extensive use of conditional rendering in its template to either show or hide certain UI elements based on the state of the component (e.g., showing different filters based on the value of the `assignment` computed property).
4. There's commented-out functionality related to PDF generation and download, as well as loading more data into the datatable. If needed, these features could be implemented by uncommenting and completing the relevant code parts.
5. The component uses a mix of base Lightning components (like `lightning-datatable`, `lightning-combobox`) and custom components (like `c-nu-searchable-multi-picklist`), indicating a sophisticated UI design that might require interactions between multiple custom components.