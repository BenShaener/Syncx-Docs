### Description

This Apex class defines a custom property with a name-value pair structure. It is designed to store the property's name as a String and its value as an Object, making it flexible to hold various data types. The class is marked with `without sharing` to explicitly specify that it does not enforce sharing rules, ensuring that access to data is determined by the class' logic rather than the default sharing settings.

### Methods

1. **nuCustomProperty() (Constructor)**

    - **Description:** Initializes a new instance of the class without setting any property name or value.
    - **Parameters:** None
    - **Returns:** An instance of `nuCustomProperty` with default (null) values for `propertyName` and `propertyValue`.

2. **nuCustomProperty(String name, Object value) (Constructor)**

    - **Description:** Initializes a new instance of the class with specified property name and value.
    - **Parameters:**
        - `String name`: The name of the property.
        - `Object value`: The value of the property.
    - **Returns:** An instance of `nuCustomProperty` with the specified `propertyName` and `propertyValue`.

### Properties

1. **propertyName**
    - **Type:** `String`
    - **Access:** Read/Write
    - **Description:** Stores the name of the property. Marked with `@AuraEnabled` to make it accessible from Lightning components.

2. **propertyValue**
    - **Type:** `Object`
    - **Access:** Read/Write
    - **Description:** Stores the value of the property. The use of `Object` allows for storing various data types. Also marked with `@AuraEnabled` to be accessible from Lightning components.

### Use Case

This class can be used in Salesforce Lightning components to dynamically manage custom properties, where each instance of the class represents a specific property with a name-value pairing. It's particularly useful when there is a need to pass custom properties from Lightning components to Apex classes in a dynamically typed manner, or when dealing with settings or configurations that require a flexible structure.

### Important Notes

- Being marked as `@AuraEnabled`, the properties can be utilized in Lightning Web Components or Aura Components, enhancing the interoperability between the Apex class and the component layer.
- The use of `without sharing` keyword implies that the visibility and access permission to the data the class operates on are not subjected to the running user's permissions or sharing rules. This should be carefully considered during development to avoid unintentional data exposure or access control issues.