### Description

The `NuManageDashboardPreferences` component is designed to manage dashboard preferences within a Salesforce Lightning environment. It features a form for editing records related to dashboard preferences, offering fields for basic information, contact association, and template selection. This component utilizes a combination of Lightning Web Components (LWC) and Salesforce Apex to interact with Salesforce records and metadata dynamically. Functionality includes creating new dashboard preference records, updating existing ones, and applying templates to dashboard preferences.

### Methods

**handleContactResult**

Triggered by a wire service to fetch and process the contact's related information like account record type, user type, and account id based on the `recordId` provided.

**connectedCallback**

Lifecycle hook that runs when the component is inserted into the DOM. It initializes the component by fetching object names and setting up the fieldsBySection based on the result.

**getTemplatesAndContactPrefs**

Fetches dashboard preference templates and contact-specific dashboard preferences, preparing the UI for interaction.

**handleFormSubmit**

Handles form submission, either creating a new dashboard preference template or updating an existing record based on the user's input.

**handleFormSuccess**

Executes actions upon successful form submission, including stopping the spinner and displaying a success toast message.

**handleChange**

Handles changes to the combobox for template selection, updating UI state based on the selected template.

**handleCancel**

Resets the form to its initial state or the last saved state.

**handleClearForm**

Clears the form to enable creating a new record by resetting relevant component properties.

### Properties

- **recordId**: The Id of the currently selected record.
- **contactId, accountId, userType**: Trackable properties related to the contact's information.
- **fieldsBySection**: Structure to hold field information organized by sections for rendering.
- **templatesPickvalues**: Array holding picklist options for the templates combobox.
- **dpId, contactDpId, dpName, contactDpName**: Properties for holding dashboard preference record details.
- **selectedTemplateValue, defaultPicklistvalue**: Manage selected values in templates combobox.
- **showSpinner**: Boolean to control the display of the loading spinner.
- **displayContactValue, displayTemplatePicklist**: Booleans to manage UI elements display based on conditions.
- **isNewTemplate**: Indicates when a new template is being created.
- **dpObject**: References the `Dashboard_Preferences__c` object.

### Use Case

This component can be used in Salesforce orgs where dashboard preferences need to be personalized per contact or user. It allows for the creation and application of templates to quickly apply predefined dashboard configurations. Its core functionalities enable users to:

- Create new dashboard preference records.
- Update existing dashboard preference records.
- Select and apply dashboard preference templates to specific contacts.

Ideal for organizations looking to provide a customized dashboard view for their users or for admins needing to manage dashboard preferences efficiently.

### Important Notes

- The component is dependent on the `recordId` to perform operations. Without a valid `recordId`, the component cannot function as expected.
- The component expects specific Salesforce object and field schemas, namely `Dashboard_Preferences__c` and its fields. Customization or changes in these schemas may require corresponding adjustments in the component.
- Commented code (e.g., the button for creating new templates directly from the UI) suggests potential features or adjustments that are currently inactive but can be enabled with slight modifications.
- The error handling is primarily logged to the console. In production, consider implementing user-friendly error messages.