### Description

This Salesforce Lightning Web Component (LWC) named `NuWorkRecordList` is designed to manage and display work records for contacts associated with the user. It dynamically showcases records in two modes based on the selected `statusFilter`: *Unsubmitted* and *Rejected*. The component allows users to submit unsubmitted timesheets and view detailed reasons for any rejections. It employs Salesforce Apex to fetch timesheet data and leverages the Lightning Design System (LDS) for styling. The dynamic theming based on account data provides a customized user experience.

### Methods

**populateContactId**

Fetches the contact ID associated with the current user.
```javascript
@wire(fetchContactId)
populateContactId({error,data}){...};
```

**populateAccountData**

Fetches account data by the contact ID and dynamically sets the component's styling based on the account's theme.
```javascript
@wire(fetchAccountByContactId,{contactId : "$contactId"})
populateAccountData({error, data}){...};
```

**fetchTimesheets**

Fetches timesheets for the contact based on the `statusFilter`. It filters timesheets for either 'Unsubmitted' or 'Rejected' statuses and prepares them for display.
```javascript
fetchTimeSheets() {...};
```

**doViewTs**

Handles navigation to the view page of the selected timesheet.
```javascript
doViewTs(event) {...};
```

**doSubmitTimesheet**

Submits the selected timesheet for processing and updates its status to 'Submitted'.
```javascript
doSubmitTimesheet(event) {...};
```

### Properties

- `@api statusFilter`: External filter status that determines which timesheets to display (either 'Unsubmitted' or 'Rejected').
- `@track timesheets`: The list of timesheets fetched based on the contact and status filter.
- `@track recordCount`: The count of timesheets currently available to display.
- `contactId`: Stores the contact ID associated with the current user.
- `accountId`: Stores the account ID associated with the contact.
- `@track containerStyle`: Dynamic styling applied to the component container based on account data.
- `@track sectionHeadingStyle`: Dynamic styling applied to section headings within the component based on account data.
- `showSpinner`: Controls the visibility of the loading spinner.

### Use Case

- **For a Recruiting Agency:** This component can be used by recruitment or staffing agencies on their Salesforce platform to manage work records for their contractors or employees. It provides an efficient way to monitor the submission and rejection of timesheets, facilitating timely payroll processing and dispute resolution.

### HTML Structure

The HTML template dynamically displays a loading spinner, a header with the total number of items, and a table containing timesheet data. It conditions rendering elements based on `isSubmitMode` and `statusFilter`.

### Important Notes

- The component uses the `NavigationMixin` for navigating to record view pages, making it compatible with Salesforce's Single Page Application (SPA) architecture.
- The dynamic styling (`containerStyle` and `sectionHeadingStyle`) relies on custom fields `Use_Portal_Theme__c`, `Tertiary_Color__c`, `Secondary_Color__c`, and `Primary_Text_Color__c` from the account object, which must exist and be populated for the styling to apply.
- Error handling and logging are implemented for Apex calls and update operations, ensuring easier debugging and user feedback.
- The component employs Salesforce's Lightning Data Service (LDS) functionalities (`updateRecord`) for performing CRUD operations directly from the client-side without custom Apex controllers for updating records, enhancing performance and leveraging Salesforce's built-in security features.
- The CSS file imports styles from a custom static resource which allows for additional customization and theming beyond what is dynamically set from the account settings.