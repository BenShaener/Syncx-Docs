### Description

The `NuSearchableMultiPicklist` component enables users to search, select, and view multiple options from a dropdown list. Users can add options by clicking on them in the dropdown, which then appear as tags or pills above the search box. Users can also remove previously selected options by clicking an 'x' button on each tag.

### Methods

- **fetchNewValue()**: Simulates fetching new search results asynchronously.
- **search(event)**: Handles the search input event, dynamically filtering dropdown options based on the user's input.
- **handleRemoveOption(event)**: Removes a selected option from the `selectedOptions` array when the user clicks the close icon on a tag.
- **selectSearchResult(event)**: Adds the clicked option from the dropdown to the `selectedOptions` array.
- **onblurClear()**: Clears the search results under certain conditions which are determined by the `dontClose` flag.
- **clearSearchResults(event)**: Clears the current search results, returning the state to no results shown.
- **showPicklistOptions()**: Displays all initial options when the search input is focused, before any search is performed.
- **handleDropdownClick(event)**: Prevents the dropdown from closing when clicking inside of it.
- **handleInputClick(event)**: Manages focus state to control dropdown visibility.

### Properties

- **options**: An array of objects representing all available options. Each object in the array should have `label` and `value` properties.
- **optionsSearch**: An array of objects representing filtered options based on search input.
- **selectedSearchResult**: The currently selected search result.
- **defaultvalue**: A value to preselect an option on the component initialization.
- **selectedOptions**: An array of objects that hold the options selected by the user.

### Use Case

This component could be used in scenarios where a user needs to select multiple options from a large list, such as assigning tags to a blog post or selecting skills on a job search platform. By allowing search and selection in a compact UI, it enhances user experience, especially when dealing with extensive options.

### Important Notes

- **Accessibility**: Ensure that interactions with the component are fully accessible, including keyboard navigation and screen reader support.
- **Singleton Selection Prevention**: The component currently does not prevent the same option from being selected more than once, which could be implemented based on the specific use case requirements.
- **@track Decorator**: The use of the `@track` decorator can be optimized further based on the property's usage. For properties expected to change frequently, `@track` ensures the UI re-renders to reflect those changes.
- **Asynchronous Handling**: The simulated `fetchNewValue` method showcases the capability to handle asynchronous operations, which in real scenarios would likely involve fetching data from a server.

### Example Implementation

The component requires the `options` property to be populated with available selections. Here is an example of how it could be used in a Salesforce Lightning Web Component:

```html
<c-nu-searchable-multi-picklist options={picklistOptions}></c-nu-searchable-multi-picklist>
```

`picklistOptions` should be an array of objects structured as follows:

```javascript
[
  { label: 'Option 1', value: 'opt1' },
  { label: 'Option 2', value: 'opt2' },
  // more options...
]
```

The component also emits custom events `valueselect` and `optionsselect` that can be listened to in order to perform additional actions based on the user's selection.