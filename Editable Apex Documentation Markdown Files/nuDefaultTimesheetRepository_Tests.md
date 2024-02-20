### Description
This class provides unit tests for the `nuDefaultTimesheetRepository` class methods focusing on the computation of overtime across different scenarios such as Weekly, Daily, and Double overtime calculations. It involves creating mock data for testing, which includes contacts, timesheets, and timesheet entry slots, then performing overtime calculations using the `computeOvertime` method of the `nuDefaultTimesheetRepository` class with predefined parameters for each test case.

### Methods
1. **computeOvertime_Weekly_Test()**
   - Tests the computation of weekly overtime. Sets up data to cover 5 days and calls `computeOvertime` with parameters representing a weekly threshold of 40 hours and no daily overtime threshold.
   
2. **computeOvertime_Daily_Test()**
   - Checks the daily overtime calculation. It populates test data for 5 days and invokes `computeOvertime` using parameters for daily overtime with an 8-hour threshold and no double overtime threshold.
   
3. **computeOvertime_Double_Test()**
   - Assesses the computation of double overtime. Similar data setup for 5 days, but `computeOvertime` is called with parameters setting a 7-hour daily threshold and an 8-hour threshold for double overtime.

### Properties
- There are no direct properties used, but mock objects and maps, such as `mockT` for the `nuTimesheet__c` test object and `slotMap` for holding `nuTimesheet_Entry_Slot__c` records, are crucial for test setup.

### Use Case
These tests are designed to validate the `nuDefaultTimesheetRepository` class's ability to accurately compute overtime based on different configurations:
- Verifying weekly overtime calculations ensure correct overtime pay for employees working beyond standard workweek hours.
- Daily overtime tests check for correct overtime computations for those exceeding a day's standard hours.
- Double overtime tests validate the higher pay rate calculations for hours worked past daily and weekly overtime thresholds.

### Important Notes
- It is critical that the `nuMockFactory` referenced in the setup is properly implemented to generate reliable mock data for contacts, timesheets, and timesheet entry slots.
- Custom settings (`NUCSH__c`) are stubbed with placeholder values, indicating potential customization or configuration needs within the real application context.
- The commented-out code related to `ts2__Placement__c mockP` suggests there might have been an intention to include placement data in the test setup, which could be relevant for more comprehensive testing scenarios.
- The use of `Date.today().toStartofWeek()` assumes tests are run in contexts where this calculation is reliable and not affected by locale-specific week start days.
- It's essential to ensure that the `computeOvertime` method handles various overtime scenarios as expected, making these tests critical for ensuring the accuracy and reliability of payroll-related functionalities in the system.