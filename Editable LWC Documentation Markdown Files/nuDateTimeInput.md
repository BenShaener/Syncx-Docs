### Description

The `NgDateTimeInput` component is a Salesforce Lightning Web Component (LWC) designed to input dates and times. It provides a versatile and configurable input field for dates, times, or both, according to the provided properties. Users have the option to apply or strip out Salesforce Lightning Design System (SLDS) styling, making it adaptable for various UI requirements.

### Methods

- **handleChange(event):** This method triggers when the input field loses focus (`onblur`). It prepares an object `realData` containing the field's name, value, a modified version of the value (`mil`), the type of input (time or the specified type), and the associated root date `dte`. It then updates the component's `value` property with the new value and fires a custom event named `datetimechange`, passing the `realData` object as event detail.

### Properties

- **@api fieldName:** A unique name to identify the field.
- **@api value:** The current value of the input field. Default is an empty string.
- **@api type:** Specifies the type of input, such as "date", "time", etc. No default value.
- **@api label:** The label text associated with the input field. No default value.
- **@api rootDate:** An additional data point that can be passed for contextual use. No default value.
- **@api timeOnly:** A Boolean to indicate if the input is exclusively for times. Default is `false`.
- **@api stripStyling:** A Boolean to determine if SLDS styling should be applied. If `true`, styling is stripped. Default is `false`.

### Use Case

In a Salesforce Lightning experience, where a user needs to input a date, time, or both, depending on the context, the `NgDateTimeInput` component can be utilized to capture this input efficiently. Its flexibility allows for usage in both styled and unstyled contexts, making it suitable for different UI designs. The component also supports additional data like a base date (`rootDate`) for more complex logic.

### Important Notes

- The component distinguishes between time-only and other types of input through the `timeOnly` property. This affects how the `type` of the emitted `datetimechange` event's detail is determined.
- The `handleChange` method updates the component's `value` with every input change, ensuring the component's state is always up-to-date.
- Custom events in Lightning Web Components, such as `datetimechange` fired in this component, can be captured by parent components for further handling or processing of the input data.
- It's important to correctly bind the component's properties (`fieldName`, `value`, `type`, `label`, `rootDate`, `timeOnly`, `stripStyling`) when using it to ensure the component behaves as expected.
- The `stripStyling` property offers flexibility in utilizing the component within various design systems, not limited to Salesforce's Lightning Design System (SLDS).