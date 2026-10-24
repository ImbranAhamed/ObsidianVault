Different programming languages follow various **naming conventions** for identifiers (such as variables, functions, classes, constants, etc.). Below are the commonly followed naming conventions across multiple languages:

### 1. **Camel Case (`camelCase`)**

- The first word starts with a lowercase letter, and subsequent words start with uppercase.    
- **Used in:** JavaScript, Java, C#, Swift, Kotlin    
- **Example:**

   ```csharp
    string userName;
    int totalAmount;
    ```


### 2. **Pascal Case (`PascalCase`)**

- Every word starts with an uppercase letter.    
- **Used in:** C#, .NET, Pascal, TypeScript    
- **Example:**

  ```csharp
    class StudentDetails { }
    void CalculateSalary() { }
    ```


### 3. **Snake Case (`snake_case`)**

- Words are separated by underscores (`_`).    
- **Used in:** Python, Ruby, C, SQL, PHP    
- **Example:**

  ```python
    user_name = "John"
    total_amount = 1000
    ```
  

### 4. **Kebab Case (`kebab-case`)**

- Words are separated by hyphens (`-`).    
- **Used in:** CSS, HTML class names, URLs    
- **Example:**
  ```css
    .nav-bar {
      background-color: blue;
    }
    ```

### 5. **Upper Snake Case (`UPPER_SNAKE_CASE`)**

- Similar to snake_case but in uppercase, usually used for constants.    
- **Used in:** C, C++, Python, Java, JavaScript    
- **Example:**
  ```c
    #define MAX_VALUE 100
    const int PI = 3.14;
    ```

### 6. **Hungarian Notation (`prefixVariableName`)**

- Prefix denotes the type or purpose of the variable.    
- **Used in:** Older C, C++ (not commonly used now)    
- **Example:**
  ```c
    int iCount; // i for integer
    char *pszName; // psz for pointer to string
    ```


### 7. **SCREAMING_SNAKE_CASE**

- Similar to UPPER_SNAKE_CASE, used for global constants.    
- **Used in:** Java, Python, C++    
- **Example:**
  ```java
    public static final int MAX_LIMIT = 5000;
    ```


### 8. **Train Case (`Train-Case`)**

- Similar to PascalCase but uses hyphens instead of spaces.    
- **Used in:** URLs, API endpoint names    
- **Example:**
  ```
    /Get-User-Details
    ```
   

### **Language-Specific Naming Conventions**

|Language|Naming Convention|
|---|---|
|C#|PascalCase (classes, methods), camelCase (variables, parameters), UPPER_SNAKE_CASE (constants)|
|Java|camelCase (variables, methods), PascalCase (classes), UPPER_SNAKE_CASE (constants)|
|Python|snake_case (variables, functions), PascalCase (classes), UPPER_SNAKE_CASE (constants)|
|JavaScript|camelCase (variables, functions), PascalCase (classes), UPPER_SNAKE_CASE (constants)|
|SQL|snake_case (table, column names)|
|PHP|snake_case (functions, variables), PascalCase (classes)|

Would you like a more detailed explanation of any specific convention? 😊