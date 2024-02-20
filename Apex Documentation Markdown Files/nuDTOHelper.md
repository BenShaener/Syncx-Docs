### Description

This helper class provides static methods to manage custom properties within a provided list of `nuCustomProperty` objects. These methods include retrieving and setting the value of a property based on its name.

### Methods

- **getCustomPropertyValue(List<nuCustomProperty> customProperties, string propertyName)**
  
  Retrieves the value of a specific custom property by its name.
  
  ```java
  public static object getCustomPropertyValue(List<nuCustomProperty> customProperties, string propertyName)
  ```

- **getCustomPropertyValue(List<nuCustomProperty> customProperties, string propertyName, object defaultValue)**
  
  Overloaded method that retrieves the value of a specific custom property by its name, allowing for a default value if the property does not exist.
  
  ```java
  public static object getCustomPropertyValue(List<nuCustomProperty> customProperties, string propertyName, object defaultValue)
  ```

- **setCustomProperty(List<nuCustomProperty> customProperties, string propertyName, object propertyValue)**
  
  Sets the value of a specified custom property. If the property exists, its value is updated; otherwise, no action is taken.
  
  ```java
  public static void setCustomProperty(List<nuCustomProperty> customProperties, string propertyName, object propertyValue)
  ```

### Properties

This class does not expose any direct properties, as it is designed to operate on `List<nuCustomProperty>` objects passed into its methods.

### Use Case

A common use case for these methods would be during the processing of records in custom Salesforce applications where dynamic properties need to be managed without modifying the underlying data schema. For example, during the import of external data, where additional attributes might be captured and handled in a generic manner without creating specific fields for each attribute.

### Important Notes

- It's crucial to ensure that the `customProperties` list and `propertyName` parameters are not null to avoid null pointer exceptions.
- When using `setCustomProperty`, if the property does not exist in the list, the method will complete without creating a new property. If the functionality for adding new properties is needed, it would require additional implementation.
- These methods operate on generic `Object` types for property values, so typecasting may be necessary when retrieving or setting specific types of values.