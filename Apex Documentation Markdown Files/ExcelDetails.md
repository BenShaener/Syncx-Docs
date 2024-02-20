**Description**

This class is designed to hold comprehensive details related to Excel data entries, specifically focused on financial and personnel information in a healthcare or similar facility environment. It covers a broad range of data points from basic identifying information like type and facility name to more detailed financial metrics including unit cost and total cost. This class implements the `Comparable` interface, allowing instances of `ExcelDetails` to be compared and sorted, primarily based on the provider's last name.

**Methods**

1. `compareTo(Object other)`

```java
public Integer compareTo(Object other)
```

- Description: Implements the `Comparable` interface's `compareTo` method to provide a way to compare `ExcelDetails` objects, specifically using the `Provider_Last_Name` as the primary field for comparison.
- Parameters: `Object other`: The other `ExcelDetails` object to compare this object to.
- Returns: `Integer`: A negative integer, zero, or a positive integer as this object is less than, equal to, or greater than the specified object.

**Properties**

- `String Type`: The type of entry.
- `String Facility_Name`: Name of the facility.
- `String Cost_Centre`: Cost center identification.
- `String Business_Unit`: Business unit identification.
- `String Specialty`: Specialty information.
- `String Provider_Last_Name`: Last name of the provider.
- `String Provider_First_Name`: First name of the provider.
- `String Agency`: Agency information.
- `String Classification`: Classification type.
- `Date rowDate`: The date of the row entry.
- `String Pay_Code_Category`: Category of the pay code.
- `String Shift_Type`: Type of shift.
- `String Pay_Code`: The pay code.
- `String Pay_Code_Text`: Text description of the pay code.
- `Decimal Hours`: Number of hours.
- `Decimal Unit_Cost`: Cost per unit.
- `Decimal Total_Cost`: Total cost.
- `String Notes`: Any additional notes.
- `Date Invoice_Pay_Period`: The pay period for the invoice.

**Use Case**

- This class can be utilized whenever there's a need to import, store, manipulate, or compare detailed financial and personnel-related data from Excel files into a Salesforce application, particularly in healthcare or similar sectors.
- It is especially useful for applications requiring sorting or comparing records based on provider names or another specified field supported within the class.

**Important Notes**

- The `compareTo` method specifically compares instances based on `Provider_Last_Name` only. If there's a need to compare based on multiple fields or a different field, modifications to the `compareTo` method will be required.
- This class assumes that each record correlates to a single row of data in an Excel spreadsheet, with each property corresponding to a specific column within that row.
- Implementations relying on the `Comparable` interface should ensure that all comparisons and sorts are done in contexts where only `ExcelDetails` objects are involved to prevent `ClassCastException`.