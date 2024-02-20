### Description

The `CustomLookup` component is a Salesforce Lightning Web Component (LWC) designed to provide a customizable lookup field. It enables users to search for and select a record from a specified Salesforce object. This component includes features like search as you type, displaying search results, selecting a record, and showing the selected record with an option to clear the selection.

### Methods

- **connectedCallback:** Initializes the component by fetching a default record if a `defaultRecordId` is provided.
- **searchResult:** A wire adapter that fetches search results based on user input (`searchKey`).
- **handleKeyChange:** Handles input field changes, implementing a debounce mechanism to limit server calls.
- **toggleResult:** Toggles the visibility of the lookup result section based on user actions (e.g., clicking outside the component).
- **handleRemove:** Clears the currently selected record and updates the UI to show the search input again.
- **handelSelectedRecord:** Handles a user's selection of a record from the search results, updating the UI and selected record state.
- **handelSelectRecordHelper:** A helper method used by `handleRemove` and `handelSelectedRecord` to update the UI when a record is selected or removed.
- **lookupUpdatehandler:** Dispatches a custom event to notify parent components of the selection change.

### Properties

- **label (api):** The label for the lookup field.
- **placeholder (api):** The placeholder text for the search input.
- **iconName (api):** The name of the icon to display in the lookup field and search results.
- **sObjectApiName (api):** API Name of the Salesforce object to search.
- **defaultRecordId (api):** The Id of a default record to display upon initialization.
- **recordType (api):** Specifies the record type for filtering search results.
- **contactFieldName (api):** Field name to identify selections in custom events.
- **hideClearButton (api):** Boolean to control the visibility of the clear button.
- **lstResult:** Private property to store the list of search results.
- **hasRecords:** Flag to indicate if there are search results.
- **searchKey:** Stores the current value of the search input.
- **isSearchLoading:** Controls the visibility of the loading spinner.
- **selectedRecord:** Stores the currently selected record.

### Use Case

This component is useful in situations where a user needs to associate a record from one Salesforce object with another record. For example, linking a `Contact` to an `Account`. It can be customized to search within any Salesforce object by setting the `sObjectApiName` and can be further configured with a default value, custom icons, and placeholder text.

### Important Notes

1. **Debounce Mechanism:** The `handleKeyChange` method implements debouncing to reduce the number of server calls while the user is typing in the search input.
   
2. **Custom Events:** The component uses custom events (`lookupupdate`) to communicate the selection changes to parent components.
   
3. **CSS Classes:** The component makes extensive use of SLDS classes to conform to Salesforce's design system, ensuring that its look and feel are consistent with the Salesforce experience.

4. **Accessibility:** The component is developed with accessibility in mind, using ARIA attributes and roles to make it accessible to people using screen readers and other assistive technologies.