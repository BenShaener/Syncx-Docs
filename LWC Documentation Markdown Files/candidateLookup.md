### Description

The provided Salesforce Lightning Web Component (LWC), named `CandidateLookup`, is a custom lookup component designed to search and select records from any given Salesforce object. It allows users to type in search queries, view matching results, and then select a record from those results. Once a record is selected, it is displayed as a "pill" within the component, with an option to remove the selection. This component is a versatile tool for scenarios where a custom record search and selection functionality is needed beyond the standard Salesforce lookup fields.

### Methods

1. **toggleResult(event):** Toggles the display of the search result section based on user interaction (such as clicking on the search input or clicking outside the component).

2. **handleKeyChange(event):** Handles input changes in the search field. It features debouncing to limit the frequency of search operations triggered by user input.

3. **handleRemove():** Clears the currently selected record, making the search input available for a new search.

4. **handelSelectedRecord(event):** Handles the selection of a record from the search results. It updates the component's state to reflect the selected record and adjusts the UI to display the selection as a "pill".

5. **handelSelectRecordHelper():** A helper function that updates the UI based on the current selection state of the component.

6. **lookupUpdatehandler(value):** Dispatches a custom event named `lookupupdate` to notify parent components of a selection change. The selected record (or null if a selection is cleared) is passed as the event's detail.

### Properties

1. **label (String):** (API) The label for the lookup component.

2. **placeholder (String):** (API) The placeholder text for the search input field.

3. **iconName (String):** (API) The name of the icon to be used in the lookup component.

4. **sObjectApiName (String):** (API) API name of the Salesforce object this lookup component is searching against.

5. **recordType (String):** (API) Specified record type for the search query.

6. **jobOrderId (String):** (API) The Job Order Id used to fetch specialty and credentials for the job order.

7. **agency (String):** (API) Specifies the agency ID to be used in the search query.

8. **isSelected (Boolean):** Tracks whether a record is currently selected.

9. **isSearchLoading (Boolean):** Indicates whether a search is currently in progress.

10. **searchKey (String):** The current value of the search input field.

11. **lstResult (Array):** Stores the list of records fetched by the search.

12. **selectedRecord (Object):** Stores the currently selected record.

### Use Case

This component is ideal for implementing custom lookup functionality in Salesforce Lightning applications where users need to search and select records from specific objects with custom filtering logic. It's particularly useful in scenarios requiring searches across different objects or customized search criteria beyond the capabilities of standard lookup fields.

### Important Notes

- The component uses `@wire` adapters to fetch search results based on user input and to extract specific fields (`Specialty__c`, `Credential_Accepted__c`) from a given Job Order record.
- Debouncing is implemented to improve performance and reduce the number of executed queries when searching.
- The component illustrates a practical application of handling both input and selection events while providing visual feedback using SLDS styling.
- Ensure that the Apex controller (`CustomLookupController.fetchCandidate`) used for fetching records is properly implemented with necessary access controls and optimized query logic.
- This component assumes the use of Salesforce Lightning Design System (SLDS) styles for consistent UI rendering within the Salesforce ecosystem.