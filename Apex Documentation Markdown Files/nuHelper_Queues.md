### Description

This class is designed to interact with Salesforce Queue objects, specifically those related to Synchronization processes like Credentialing, Accounting (Time is Money), and Accounting (Dollars and Cents). It provides utility functionalities to fetch queue IDs by their developer names and to filter null or empty strings from collections.

### Methods

- **Constructor:** Initializes the `nuHelper_Queues` object by fetching and storing Queue IDs based on predefined group developer names. It populates the `queueIdByDeveloperName` Map with these IDs.
    ```java
    public nuHelper_Queues()
    ```
- **filterSet(Set<String> setToFilter):** Filters the given Set by removing null or empty strings, returning a new Set with the filtered values.
    ```java
    public static Set<String> filterSet(Set<String> setToFilter)
    ```
- **filterList(List<String> listToFilter):** Filters the given List by removing null or empty strings, returning a new List with the filtered values.
    ```java
    public static List<String> filterList(List<String> listToFilter)
    ```

### Properties

- **queueIdByDeveloperName:** A Map to store Queue IDs indexed by their developer names.
    ```java
    public Map<String, Id> queueIdByDeveloperName
    ```
- **SYNC_CREDENTIALING, SYNC_ACCOUNTING_TIM, SYNC_ACCOUNTING_DAC:** Constants representing the developer names of the relevant queues.
    ```java
    public final String SYNC_CREDENTIALING
    public final String SYNC_ACCOUNTING_TIM
    public final String SYNC_ACCOUNTING_DAC
    ```
- **ALL_GROUPS:** A List containing developer names of all queues this class is concerned with.
    ```java
    public final List<String> ALL_GROUPS
    ```

### Use Case

This class can be utilized in any context where there is a need to work with specific Salesforce Queues by their developer names particularly, but not limited to, synchronization processes. It is also useful for cleaning collections of strings (Sets and Lists) by removing any null or empty values, which is a common requirement after fetching and before processing collections.

### Important Notes

- This class is declared without sharing to ensure it runs in system context to fetch queue details without being influenced by the user's permission set. This might be important for orgs where not all users have access to all queues.
- The fetching of Queue IDs based on developer names is performed only once during the initialization of the object. This means that if queues are added or removed after the object's instantiation, it won't reflect these changes.
- The `filterSet` and `filterList` methods are static, allowing them to be utilized without instantiating the class, providing utility functionality that can be used in broader contexts.