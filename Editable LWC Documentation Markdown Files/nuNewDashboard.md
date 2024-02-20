### Description

The `NuNewDashboard` component is a Salesforce Lightning Web Component (LWC) designed to display various sections like "Hot Jobs", "Activity & Alerts", "Insights", "Pending Actions", and "Quick Tasks". It dynamically loads content based on the availability of the data and user permissions. The data is retrieved via Apex controllers and static resources. It also supports navigation to different pages or records within the Salesforce environment based on user interactions.

### Properties

- `contactId` & `accountId`: Track the ID of the contact and account, respectively.
- `pendingActionsTiles` & `quickTasksTiles`: Arrays of objects representing the tiles to be displayed in the "Pending Actions" and "Quick Tasks" sections.
- `hotjobs`: An array to contain information about "Hot Jobs".
- `notifications`: An array to contain notification details for the "Activity & Alerts" section.
- `notificationDropdownStyle`: Style information for the display of notifications.
- `keyInsightsId`: A unique identifier for key insights data.
- `isDataComplete`: A boolean indicating if the data loading is complete.
- These flags control the visibility of the respective sections:
  - `enableHotJobs`
  - `enableInsights`
  - `enableActivityAlerts`
  - `enableInsightsUtility`
- `showSpinner`: Controls the visibility of a spinner during data loading.
- Static resources for the "Insights" section:
  - `spendWorkedYTD`
  - `clinicianScheduled`
  - `spendScheduled`

### Methods

- `connectedCallback()`: Initializes the component by fetching data required for rendering.
- `navigateToPage(event)`: Handles navigation to a specific page as per user interaction.
- `navigateToHotjob(event)`: Navigates the user to a detailed view of a selected hot job.
- `navigateToReferenceUrl(event)`: Handles navigation based on the provided record ID or reference URL.

### Use Case

This component is intended to serve as a dashboard within a Salesforce Community or within the Salesforce Lightning Experience. It provides quick access to various sections of interest such as "Hot Jobs", "Activity & Alerts", "Insights", "Pending Actions", and "Quick Tasks". The component is designed to enhance user engagement by dynamically displaying information relevant to the user and providing quick navigation routes to pertinent areas within Salesforce.

### Important Notes

1. **Dynamic Data Loading**: Data for this component is dynamically loaded using Apex controllers (`fetchContactAndRelatedData`, `fetchHotJobOrders`) and static resources. The presence of data dictates the visibility and content of various sections.
2. **Navigation**: This component makes extensive use of the Salesforce NavigationMixin to handle navigation, demonstrating how components can facilitate user navigation within Salesforce.
3. **Styling**: It leverages SLDS (Salesforce Lightning Design System) for its styling needs, ensuring a consistent look and feel with the Salesforce ecosystem.
4. **Responsive Design**: Media queries are included to ensure the component is responsive and adapts to different screen sizes.
5. **Visibility Logic**: The visibility of various sections is controlled through boolean flags that are set based on the data received from the server.
6. **Event Handling**: Event handlers (`navigateToPage`, `navigateToHotjob`, `navigateToReferenceUrl`) are used to manage user interactions, such as clicked links for navigation.

Example of a method for navigating to a specific page:

```javascript
navigateToPage(event) {
    const clickedPageName = event.target.dataset.pagename;
    if (clickedPageName) {
        let destination = {
            type: 'comm__namedPage',
            attributes: {
                pageName: clickedPageName
            }
        };
        this[NavigationMixin.Navigate](destination, false);
        event.stopPropagation();
    }
}
```