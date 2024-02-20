### Description

The `NuClassificationOfBookings` component is designed for the Salesforce Lightning platform. It allows users to classify bookings based on employee types (1099, W2), order the booking records by a selected timeframe (weekly, monthly), and select specific days within that timeframe to view relevant booking data. Additionally, users can download this data as a CSV file. The component utilizes the `lightning-quick-action-panel` to present the UI, `lightning-combobox` for dropdown selections, `lightning-input` for date inputs, and `lightning-datatable` to display the fetched booking data as a table.

### Properties

- `@api recordId`: Refers to the current record ID context of the component.
- `@track tableData`: Tracks the data to be displayed in the datatable.
- `columns`: Defines the structure of columns shown in the datatable.
- `defaultEmployeeType`, `selectedEmployeeType`: Manages the state of the selected employee type through combobox.
- `orberBy`: Determines the ordering of the booking records (weekly or monthly).
- `dateStart`, `dateEnd`: Stores the start and end dates for the selected timeframe.
- `isCsvDisabled`: Controls the disabled state of the CSV download button based on if there is data available.

### Methods

- `handleAccResult(result)`: A wire method to fetch account name using the `getRecord` wire adapter.
- `handleEmployeeTypeSelect(event)`: Handles changes in the employee type selection.
- `handleDaySelect(event)`: Manages the day selection and calculates the start and end dates based on the order by selection (weekly/monthly).
- `handleOrderBySelect(event)`: Handles changes in the order by selection (weekly/monthly).
- `fetchRelatedData()`: Fetches related booking data based on selections of employee type, date start, and date end.
- `buildTableData(timesheets, expenses)`: Processes timesheets and expenses to prepare data for the datatable.
- `downloadCSV(event)`: Initiates the download of a CSV file containing the data displayed in the datatable.

### Use Case

The component is ideally used to classify and analyze bookings within the context of a specific Salesforce record. This could be particularly useful for human resources or project management to review resource allocations or financial expenditures related to employees or contractors (1099, W2) over specified timeframes.

### Important Notes

- Ensure that Apex controllers (`fetchTimesheetsForEmployees` and `fetchExpensesForEmployees`) are properly set up and accessible.
- The component makes use of `lightning/uiRelatedListApi` and `lightning/uiRecordApi` wire adapters which require `@salesforce/schema` imports specific to the Salesforce Org's schema.
- Custom styling is applied through CSS for layout adjustments.
- Important to check user permissions and field level access for fields used in the Apex controllers and component.