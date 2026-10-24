The `using` statement in C# serves two primary purposes, and its behavior depends on the context in which it's used. Here's a detailed explanation:

---

## 1. **Namespace Import (`using <namespace>;`)**

### **Purpose:**

The `using` statement is used to import namespaces, allowing you to access classes, interfaces, and other types defined within those namespaces without having to use fully qualified names.

### **How It Works:**

- When you write `using System;`, it makes all the types in the `System` namespace available in the current file.    
- This allows you to use types like `Console` directly instead of `System.Console`.    

### **Example:**

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello, World!"); // No need to write System.Console
    }
}
```

### **Key Points:**

- **Compile-Time Directive:**  
    The `using` statement for namespaces is a compile-time feature. It simply tells the compiler where to look for types.    
- **Doesn't Import Code:**  
    It doesn't load or "import" the namespace into memory. It just provides a shortcut to access types.    

---

## 2. **Resource Management (`using (<resource>) { ... }`)**

### **Purpose:**

The `using` statement is used to ensure proper disposal of resources that implement the `IDisposable` interface. It provides a way to manage unmanaged resources like file handles, database connections, or network streams.

### **How It Works:**

- The `using` block automatically calls the `Dispose()` method on the object at the end of the block, even if an exception occurs.
    
- This ensures that resources are released promptly and correctly.    

### **Example:**

```csharp
using (var file = new System.IO.StreamWriter("example.txt"))
{
    file.WriteLine("Hello, World!");
} // Dispose() is called automatically here.
```

### **Key Points:**

- **Automatic Disposal:**  
    At the end of the `using` block, the compiler generates code to call the `Dispose` method of the object.
    
- **Requires `IDisposable`:**  
    The object used in the `using` statement must implement the `IDisposable` interface.
    
- **Exception Safety:**  
    Even if an exception occurs within the block, `Dispose` will still be called.    

### **Equivalent Code Without `using`:**

```csharp
var file = new System.IO.StreamWriter("example.txt");
try
{
    file.WriteLine("Hello, World!");
}
finally
{
    if (file != null)
    {
        file.Dispose();
    }
}
```

---

## 3. **`using` Declaration (C# 8.0 and Later)**

### **Purpose:**

Introduced in C# 8.0, the `using` declaration is a more concise way to declare and manage disposable resources without requiring a nested block.

### **Example:**

```csharp
using var file = new System.IO.StreamWriter("example.txt");
file.WriteLine("Hello, World!");
// Dispose() is called automatically at the end of the enclosing scope.
```

---

## Summary of `using` Statement in C#

|Context|Purpose|Behavior|
|---|---|---|
|**Namespace Import**|Simplifies access to types in namespaces|Compile-time directive, no runtime effect.|
|**Resource Management**|Ensures proper disposal of unmanaged resources|Calls `Dispose` automatically at the end of the block or scope.|
|**Using Declaration**|Simplifies resource management in the same scope|Disposes resources at the end of the enclosing scope.|

---

### How the `using` Statement Works

1. **Reference Only:**  
    When you write `using System;`, you are telling the compiler where to find types such as `Console`, `Math`, or `String`. The `using` statement is essentially a shortcut to avoid writing the fully qualified name (e.g., `System.Console`).
    
2. **Compile-Time Resolution:**  
    The `using` directive does not physically include or copy code from the `System` namespace into your file. Instead, it allows the compiler to resolve references to types in the specified namespace during compilation.
    
3. **Efficient Compilation:**  
    The compiler does not load or duplicate the entire namespace. It simply uses the directive to understand which namespaces to check for types that are referenced in your code.


- **The `using System;` statement:**
    
    - Tells the **C# compiler** to **look in the `System` namespace** for any unqualified types (like `Console`).
        
- **When the compiler sees `Console`:**
    
    - It **searches the metadata** in the referenced assemblies (like `System.Console` from `System.Console.dll` or `System.Runtime.dll`).
        
    - It checks:
        
        - ✅ Is there a `Console` type in `System`?            
        - ✅ Does it have a static method named `WriteLine` that accepts a string?            
- **If everything is valid:**
    
    - The compiler proceeds to emit IL (Intermediate Language) code that calls `System.Console.WriteLine`.        
- **If not found or mismatched:**
    
    - You get a **compile-time error**, such as:
	     error CS0103: The name 'Console' does not exist in the current context
