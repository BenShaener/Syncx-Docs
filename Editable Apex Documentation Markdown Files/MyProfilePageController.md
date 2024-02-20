### Description
This Apex class is designed to manage portal user profiles within Salesforce, not accessible by guest users. It primarily facilitates the viewing and editing of the logged-in user's profile information.

### Methods

- **getUser()**: Returns the user object with the current user's details.
  ```java
  public User getUser()
  ```

- **MyProfilePageController()**: Constructor method that initializes the user object with details of the logged-in user. Throws `NoAccessException` for guest users.
  ```java
  public MyProfilePageController()
  ```

- **getIsEdit()**: Returns a boolean indicating if the edit mode is active.
  ```java
  public Boolean getIsEdit()
  ```

- **edit()**: Activates the edit mode by setting `isEdit` to true.
  ```java
  public void edit()
  ```

- **save()**: Saves the edits to the user object and exits edit mode. Catches and displays any DML exceptions.
  ```java
  public void save()
  ```

- **changePassword()**: Navigates to the ChangePassword visualforce page.
  ```java
  PageReference changePassword()
  ```

- **cancel()**: Cancels edit mode and refreshes the user's data from the database.
  ```java
  public void cancel()
  ```

### Properties

- **user**: A private instance of the User object containing the logged-in user's information.
- **isEdit**: A private boolean flag indicating whether the user's profile is in edit mode.

### Use Case
This class can be used in a Salesforce community or portal where users require the capability to view and update their own profile information. This includes changes to their email, phone number, address, and other personal details. It ensures that guest users cannot access or modify any user information.

### Important Notes

- Direct access by guest users is prohibited, ensuring an added layer of security by preventing unauthorized access to the profile information.
- The class uses `with sharing` keyword ensuring that the code respects Salesforce's sharing and security model.
- Transaction control is managed within the `save` method, where DML operations are wrapped in a try-catch block to gracefully handle exceptions.
- The profile information is refreshed upon cancellation of edits to ensure the user view reflects the most current data from the Salesforce database.