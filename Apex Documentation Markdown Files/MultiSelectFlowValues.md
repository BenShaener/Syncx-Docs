### Description
This class provides functionality to process a list of strings, specifically intended for use in Salesforce Flows. The main purpose is to take a single string input, which contains semi-colon separated values, split it into individual strings, and then wrap this list into another list before returning it. This is particularly useful when working with multi-select choices in Salesforce Flow where choices are often represented as a single string of semi-colon-separated values.

### Methods
- **CheckValues(List<string> values)**
  - **Description**: Takes a list of strings as input, processes the first item of the list by splitting it into separate strings based on semi-colons, and then returns these as a new list nested within another list. If the input list is empty, it returns null.
  - **Parameters**: `List<string> values` - A list of strings, where ideally the first string contains semi-colon-separated values to be processed.
  - **Returns**: `List<List<string>>` - A list containing a single list of the separated string values. If the input is empty, returns null.
  - **Example**:
    ```java
    List<string> input = new List<string>{'apple;banana;orange'};
    List<List<string>> result = MultiSelectFlowValues.CheckValues(input);
    ```

### Properties
This class does not define any properties.

### Use Case
A typical use case for this class is within a Salesforce Flow where a multi-select picklist's selected values (which are presented as a single semi-colon-separated string) need to be processed individually. For instance, if there is a need to loop over each selected value for further processing or decision-making within the Flow, this class can be used to split the values and make them more accessible.

### Important Notes
- The method assumes that the list of strings provided as input contains at least one item and that this item is the one that should be split. If the first item is not in the expected format (e.g., does not contain semi-colon-separated values) or if the list is empty, the method's behavior might not be as intended (returning `null` in the case of an empty list).
- This class is marked as `global` and `without sharing`, which means it does not enforce record-level access rules and can be used across different namespaces, making it both highly accessible and powerful, yet something that should be used carefully to avoid unintentional data exposure.