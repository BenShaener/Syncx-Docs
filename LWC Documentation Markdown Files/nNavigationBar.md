## Description

The Lightning Web Component (LWC) named `NNavigationBar` provides a dynamic, role-based navigation bar for a Salesforce app. It adapts its appearance and available links depending on whether the user is identified as an "Agency", "Client", or "Candidate". This component uses a mix of standard Salesforce Lightning, custom CSS for styling, and JavaScript for behavior. It demonstrates usage of Salesforce's `NavigationMixin` for navigating to different pages within the Salesforce app and the `@wire` service to interact with the Salesforce data layer. The component is designed to be responsive, changing layout for mobile devices.

## Methods

### `navigateToHome()`
Navigates the user to the home page of the application.

```javascript
navigateToHome(){
    this[NavigationMixin.Navigate]({
        type: 'standard__namedPage',
        attributes: {
            name: 'Home'
        },
    });
}
```

### `navigateToPage(e)`
Navigates the user to a specific page based on the `data-navinfo` attribute of the clicked element. The method uses a switch case to determine the navigation target based on the attribute value.

```javascript
navigateToPage(e){ /* Implementation */ }
```

### `handleMobileNav()`
Toggles the mobile navigation view, showing or hiding the mobile navigation menu.

```javascript
handleMobileNav(){
    this.appClicked = !this.appClicked;
}
```

### Lifecycle Hooks
- `connectedCallback()`: Used to perform work in the lifecycle hook but the implementation is empty for this component.

## Properties

### `portal`
An API property (`@api`) that holds the role information such as "Agency", "Client", or "Candidate" to tailor the navigation bar based on the user's role.

### Computed Properties
- `isAgency`, `isCandidate`, `isClient`: Computed properties that return a boolean value based on the `portal` property to conditionally render parts of the template.
- `linkContainerClass`, `closeClass`: Computed properties to determine the CSS class of the link container and close button, toggling mobile view styles based on the `appClicked` state.

## Use Case

This component can be used in any Salesforce application that requires a dynamic and responsive navigation bar, capable of adjusting its content based on user roles. It's suitable for applications with different types of users, each needing access to different areas of the application. By detecting the user's role, the navigation bar ensures users can easily find and access the features and information relevant to them.

## Important Notes

- The component utilizes Salesforce's `NavigationMixin` to handle navigation. Ensure that your Salesforce environment supports this feature.
- The `@wire(CurrentPageReference)` is used to log the current page reference but can be extended for more advanced routing and state management use cases.
- The CSS uses custom properties (e.g., `var(--primary-color)`) which should be defined in the imported `c/nSharedCss` file or another global CSS file.
- Media queries in the CSS ensure the navigation bar is responsive and adapts to different screen sizes, switching to a hamburger menu on smaller screens.
- The JavaScript `switch` statement in `navigateToPage` method outlines how navigation is handled based on the `data-navinfo` attribute. It's customizable based on the specific pages and navigation paths relevant to your application.
- This component assumes the presence of certain Salesforce object pages (e.g., `Job_Order__c`, `Timesheets__c`) that might need to be adjusted based on the actual Salesforce configuration and object schema in use.