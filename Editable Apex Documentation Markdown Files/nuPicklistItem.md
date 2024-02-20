### Description
This class is designed to represent a picklist item in Salesforce Lightning components. It is structured to hold the label and value of the item, as well as additional information such as whether the item pertains to a multi-day event or is related to hours only. The class is marked with `without sharing`, indicating it does not enforce the sharing rules of the running user.

### Methods
This class does not explicitly define any methods. All interactions are facilitated through the properties defined within the class.

### Properties
- **label (`String`)**: Represents the label of the picklist item. This is what users will see in the UI.
  
- **value (`Object`)**: Holds the value of the picklist item. This could be of any data type, hence it is defined as an `Object`.
  
- **multiDay (`Object`)**: An additional property that can be used to signify if the picklist item is related to events that span multiple days. The data type is `Object`, allowing for flexibility in what this property might represent (e.g., boolean, string, etc.).
  
- **hoursOnly (`Object`)**: Similar to `multiDay`, this property is intended to indicate if the picklist item pertains to hour-specific events or configurations. Its open `Object` type allows for various data types to be used.

### Use Case
A common use case for this class is in the creation and handling of dynamic picklists in Salesforce Lightning components or Aura/LWC. Developers can instantiate this class to generate picklist items that carry more information than just labels and values, enabling more complex selection scenarios (e.g., filtering events based on their duration type).

### Important Notes
- **Flexibility and Type Safety**: Given that `value`, `multiDay`, and `hoursOnly` are defined as `Object`, it provides flexibility in what these properties can hold. However, it is essential to handle these with care in the consuming code to prevent runtime errors due to type mismatches.
  
- **without sharing**: The class does not enforce row-level security, field-level security, or sharing rules. Be mindful of this in contexts where enforcing these controls is crucial.

This class serves as a template for enhancing the functionality and information carrying capability of picklist items in a Salesforce environment, acknowledging the need for custom attributes beyond the standard label-value pairings.