The **memory layout of a program** in a system running a modern OS (like Windows, Linux, or macOS) is divided into several sections. These sections are used for different purposes such as storing code, data, stack, and heap.

---

## **Memory Layout of a Program in RAM**

When a program is loaded into memory, it is organized into the following sections (from lower to higher memory addresses):

```
+-----------------------+  High Memory Addresses
|       Stack          |  (Grows downward ⬇)
|-----------------------|
|       Heap           |  (Grows upward ⬆)
|-----------------------|
|   BSS Segment        |  (Uninitialized global & static variables)
|-----------------------|
|   Data Segment       |  (Initialized global & static variables)
|-----------------------|
|   Text Segment       |  (Executable machine code)
+-----------------------+  Low Memory Addresses
```

---

### **1. Text Segment (Code Segment)**

- Stores the **compiled machine code** (binary instructions).    
- Read-only to prevent accidental modifications.    
- Example: The binary code of `main()` and other functions.    

---

### **2. Data Segment (Initialized Global & Static Variables)**

- Stores **global and static variables** that are **explicitly initialized**.    
- Example:
    
    ```cpp
    int globalVar = 10;  // Stored in the data segment
    static int count = 0; // Stored in the data segment
    ```
    
- Remains in memory throughout the program's execution.
    

---

### **3. BSS Segment (Uninitialized Data)**

- Stores **global and static variables that are uninitialized**.    
- Initialized to **zero** by the OS before execution.    
- Example:

  ```cpp
    int globalVar;   // Stored in BSS segment
    static int x;    // Stored in BSS segment
    ```
   
- Saves memory by not storing explicit zeros in the binary.    

---

### **4. Heap Segment**

- Stores **dynamically allocated memory** (`new` in C++, `malloc()` in C).    
- Grows **upward** as memory is allocated.    
- The OS manages it using **heap memory managers**.    
- Example:

   ```cpp
    int* ptr = new int[10]; // Allocated on the heap
    ```
   
- **Must be freed manually** (`delete` in C++, `free()` in C).

---

### **5. Stack Segment**

- Stores **function calls, local variables, and return addresses**.    
- Grows **downward** (from higher to lower memory addresses).    
- Uses a **LIFO (Last In, First Out) structure**.    
- Example:
```cpp
    void func() {
        int localVar = 5; // Stored in stack
    }
    ```

- Automatically managed: **pushed when a function is called, popped when it returns**.    
- **Stack Overflow:** If too many nested function calls or large local arrays are used.    

---

## **Memory Layout in Action**

### **Example C++ Program**

```cpp
#include <iostream>
using namespace std;

int globalVar = 10;  // Data Segment
static int staticVar; // BSS Segment

void func() {
    int localVar = 5; // Stack
    int* heapVar = new int(20); // Heap
}

int main() {
    func();
    return 0;
}
```

### **Where Do These Variables Go?**

|Variable|Segment|
|---|---|
|`globalVar = 10`|Data Segment|
|`staticVar`|BSS Segment|
|`localVar` (inside `func()`)|Stack|
|`heapVar` (dynamically allocated)|Heap|
|Function Code (`main()`, `func()`)|Text Segment|

---

## **Key Takeaways**

1. **Text Segment:** Stores machine code (read-only).    
2. **Data Segment:** Stores initialized global/static variables.    
3. **BSS Segment:** Stores uninitialized global/static variables.    
4. **Heap:** Stores dynamically allocated memory (grows upward).    
5. **Stack:** Stores function calls & local variables (grows downward).    

This structured memory layout ensures **efficient program execution** and **proper memory management**. 🚀