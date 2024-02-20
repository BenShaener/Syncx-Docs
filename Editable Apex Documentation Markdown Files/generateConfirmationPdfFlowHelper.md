### Description
This Apex class provides functionality for generating PDF documents based on the details of placements. It is designed to work within Salesforce's Lightning Flow, allowing automation processes to invoke the PDF generation functionality. The class includes a method that is specifically designed to be called from Lightning Flows, taking in custom inputs and querying necessary data before calling another utility for the actual PDF generation.

### Methods

- `generatePDF(List<FlowInputs> placements)`
  
  This is an invocable method that can be called from Salesforce Lightning Flows. It takes a list of `FlowInputs` objects, queries for related `nuPlacement__c` records based on the `placementId` provided within the first `FlowInputs` item, and then triggers the PDF generation process for the specified placement. The start and end dates from the flow inputs are adjusted (start date is decremented by one day) before being passed to the PDF generation utility.

  **Parameters:**
  
  - `placements`: A list of `FlowInputs` objects, each containing a `placementId`, `startInput`, and `endInput`. 
  
  **Returns:**
  
  - Void (The method does not return a value).

### Properties

- `FlowInputs`
  
  This is a nested class that serves as a container for input variables that are passed into the invocable method from a Lightning Flow. It includes the following properties:
  
  - `placementId`: An `Id` representing the unique identifier of a placement.
  - `startInput`: A `Date` indicating the start date input for the PDF generation process.
  - `endInput`: A `Date` indicating the end date input for the PDF generation process.

### Use Case

This class is specifically designed for use in Salesforce Lightning Flows where there's a need to automate the generation of PDF documents that summarize placement details. A typical use case might involve creating a Flow that triggers when a placement record is updated or reaches a certain status, and then uses this class to generate a PDF document containing relevant details of the placement for sharing with stakeholders or for record-keeping purposes.

### Important Notes

- The `generatePDF` method directly queries for a `nuPlacement__c` record using the `placementId` provided from the first item in the `placements` list, indicating that it currently supports processing for a single placement at a time. For bulk processing of placements, the method would need to be adapted or called iteratively.
- The actual PDF generation is delegated to `nuGateway_Calendar.generatePDF()`, a method not defined within this class. It's essential to ensure that this external method supports the expected functionality and that its API contract remains compatible with how it's being called here.
- Since the class uses SOQL queries and DML operations (indirectly through `nuGateway_Calendar.generatePDF()`), it's important to be mindful of Salesforce's governor limits when designing Flows that invoke this method.
- Error handling is not explicitly implemented in this class; it relies on the consuming Flow or external utility (`nuGateway_Calendar.generatePDF()`) to handle exceptions or errors that may arise during the process.