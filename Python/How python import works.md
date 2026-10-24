In Python, the `import` statement is used to include the functionality of other Python modules or libraries into your program. This allows you to reuse code and take advantage of existing libraries and functions instead of writing everything from scratch.

Here’s what the `import` statement does:

### 1. **Load and Execute Code**

- When you import a module, Python executes all the code in the module at the time of the import. This means any function definitions, class definitions, and even code outside these structures (like print statements or initializations) in the module are executed.    

### 2. **Expose Attributes and Functions**

- Once imported, you can access the functions, classes, and variables defined in the module as attributes. These are accessible using dot notation (`module_name.function_name`).    

### 3. **Doesn't Contain Only Declarations**

- Modules often include both **declarations** (e.g., function and class definitions) and **executable code**. For example:

   ```python
    # module.py
    print("Module is being executed!")
    def greet():
        print("Hello, World!")  ```
    
    If you import this module:
    
   ```python
    import module
    ```
    
    The statement `print("Module is being executed!")` runs immediately during the import, in addition to making the `greet()` function available.


### 4. **Optional Initialization**

- Some modules include initialization code that runs only once when the module is first imported. This is useful for setting up configurations or connecting to resources.    

### Example of Import Variants:

1. **Basic Import**
    
   ```python
    import math
    print(math.sqrt(16))  # Access math.sqrt
   ```
    
2. **Import Specific Attributes**
    
   ```python
    from math import sqrt
    print(sqrt(16))  # Direct access
    ```
    
3. **Custom Name**
    
   ```python
    import math as m
    print(m.sqrt(16))  # Aliased name
   ```
    
4. **Import All** (not recommended due to namespace pollution):
    
   ```python
    from math import *
    print(sqrt(16))  # Direct access without module prefix
    ```
   

### Summary

The `import` statement is not just about declarations. It also executes the module code (except when wrapped in `if __name__ == "__main__":`) and makes the defined attributes, functions, and classes available to your program.


---

When the Python interpreter encounters an import statement like `import math`, it follows a systematic process to locate, load, and execute the specified module. Here's a detailed breakdown of what happens:

---

### 1. **Checking the Module's Existence in `sys.modules`**

- **What happens:**  
    Python first checks the `sys.modules` dictionary, which caches all modules that have already been loaded in the current session.
    
    - If the module (`math`) is found in `sys.modules`, Python uses the already-loaded module and skips the loading process.

    - If the module is not found, Python proceeds to locate and load it.        
- **Why:**  
    This ensures that the module is loaded only once per session, even if imported multiple times, improving efficiency.    

---

### 2. **Locating the Module**

- **Search Path:**  
    Python searches for the module in the directories listed in the `sys.path` variable. This variable contains:
    
    - The directory of the script being executed.        
    - The standard library directories.        
    - Any directories specified in the `PYTHONPATH` environment variable.        
    - The `site-packages` directory (for third-party modules).        
    
    Example of `sys.path`:
    
   ```python
    import sys
    print(sys.path)
    ```
    
- **Search Order:**  
    Python looks for:
    
    1. **Built-in Modules:**  
        These are compiled into the Python interpreter (e.g., `math`, `sys`). If found, it stops searching further.
        
    2. **Compiled Files:**  
        It looks for `.pyc` (compiled Python) files in a `__pycache__` directory.
        
    3. **Source Files:**  
        It searches for a `.py` source file.
        
    4. **Package Directories:**  
        If the module is part of a package, Python checks for an `__init__.py` file in the directory.
               
- **Error Handling:**  
    If the module is not found, Python raises an `ImportError` or `ModuleNotFoundError`.
    

---

### 3. **Loading the Module**

- Once the module is located, Python loads it into memory:
    
    - For **built-in modules** (like `math`), the module is already compiled and ready to use.        
    - For **pure Python modules**, Python compiles the `.py` file into bytecode (if not already compiled) and stores it in a `.pyc` file inside a `__pycache__` directory.        

---

### 4. **Executing the Module**

- Python executes the module's code in a new namespace to define its functions, classes, and variables.
    
    - If the module has top-level executable code (e.g., `print` statements), it will run during this phase.        
    - Python skips code wrapped in `if __name__ == "__main__":` because that part is executed only when the module is run as a standalone program.

- The module’s namespace is stored as a `module object`, and its name is registered in `sys.modules`.    

---

### 5. **Binding the Module Name**

- Finally, Python binds the name of the module (e.g., `math`) to the `module object` in the importing script's namespace. You can now use the module's attributes or functions, such as `math.sqrt`.    

---

### Example Walkthrough

Consider the import statement:

```python
import math
```

1. **Check `sys.modules`:**
    
    - Python checks if `math` is already in `sys.modules`.        
    - If found, it reuses the existing `module object`.      

2. **Locate the Module:**
    
    - Python recognizes `math` as a built-in module.        

3. **Load the Module:**
    
    - Since `math` is built-in, Python skips searching the filesystem and directly loads the precompiled module.

4. **Execute the Module:**
    
    - Any initializations or constants defined in the `math` module are executed.

5. **Bind the Module:**
    
    - The name `math` is bound to the module object, and you can now use `math.sqrt`, `math.pi`, etc.        

---

### Notes on Specific Import Variants

#### **`from math import sqrt`:**

- Python follows the same steps but only binds `sqrt` to the current namespace, not the entire `math` module.    

#### **Circular Imports:**

- If two modules import each other, Python might encounter issues if one module is still being loaded while the other tries to import it. Python uses `sys.modules` to break this cycle by referencing partially loaded modules.    

---

### Summary of Steps

1. Check if the module is already in `sys.modules`.    
2. Locate the module using the paths in `sys.path`.    
3. Load the module (from source, precompiled bytecode, or built-in library).    
4. Execute the module's code.    
5. Bind the module name to its namespace.    

This systematic process ensures efficient and modular handling of imports in Python.