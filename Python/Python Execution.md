related: [[Python]] #Python
Python code execution involves several stages, which occur in sequence to run the program. Here’s a breakdown of the process:

---

### **1. Writing the Code**

You write Python code in a text editor or an Integrated Development Environment (IDE). This code is written in human-readable text and saved with a `.py` extension.

---

### **2. Running the Code**

When you run the Python script, the Python interpreter takes over. The process starts with **parsing** the code and converting it into a format that the computer can understand.

---

### **3. Steps in Code Execution**

#### **a. Lexical Analysis**

The interpreter scans the code and breaks it into tokens. Tokens are the smallest meaningful units like keywords, operators, variables, and literals.
#### **b. Parsing**

The tokens are arranged into a structure called an **Abstract Syntax Tree (AST)**. The AST represents the logical structure of your code.
#### **c. Compilation**

The AST is converted into **bytecode**, which is an intermediate, low-level representation of your program. Bytecode is a set of instructions that the Python Virtual Machine (PVM) can understand. The bytecode is usually stored in `.pyc` files in the `__pycache__` directory for reuse.
#### **d. Execution by the Python Virtual Machine (PVM)**

The PVM interprets the bytecode and executes it line by line. During execution:

- Variables are assigned.    
- Functions are called.    
- Control structures (like loops and conditionals) are executed.    
- Any errors (if present) are raised.    

---

### **4. Role of the Python Standard Library**

The standard library provides pre-written modules and functions that your program can use during execution. For example, if your program uses `math.sqrt()`, the library is called during runtime.

---

### **5. Garbage Collection**

Python has an automatic garbage collector to manage memory. It clears unused objects from memory to optimize performance.

---

### **Key Points to Remember**

- Python is an **interpreted language**, meaning code is executed line by line after compilation to bytecode.  
- The Python interpreter combines compilation and execution, making the process fast and dynamic.    
- Errors can occur at runtime since Python does not perform strict compile-time checks like some other languages (e.g., C++ or Java).    


---
The **Python Virtual Machine (PVM)** executes Python bytecode **without converting it into native machine code** by directly interpreting the instructions. It acts like a software-based CPU that **reads and executes** Python bytecode one instruction at a time.

---

## **How Does PVM Execute Python Code?**

### **Step 1: Source Code to Bytecode**

- When you write a Python program:
    
    ```python
    x = 10 + 5
    print(x)
    ```
    
- The **CPython compiler** converts this into **bytecode** (`.pyc` files in `__pycache__`).    
- The bytecode is **not machine code**; it’s a **set of instructions for the PVM**.    
- Example of **Python bytecode** (using `dis` module):    
    ```python
    import dis
    dis.dis("x = 10 + 5")
    ```
    
    Output:
    
    ```
    1           0 LOAD_CONST               0 (10)
                2 LOAD_CONST               1 (5)
                4 BINARY_ADD
                6 STORE_NAME               0 (x)
                8 LOAD_CONST               2 (None)
               10 RETURN_VALUE
    ```
    

---

### **Step 2: PVM Reads and Executes Bytecode**

- The **Python Virtual Machine (PVM)** takes the bytecode and **executes it directly** without converting it to machine code.    
- The PVM is an **interpreter that simulates a CPU in software**.    

### **How does it execute instructions?**

- The PVM has an **evaluation loop** called the **Bytecode Execution Loop**.    
- It reads each **bytecode instruction**, interprets it, and performs the required operation.

- Example:
    
    - `LOAD_CONST 0 (10)`: PVM loads `10` onto the stack.        
    - `LOAD_CONST 1 (5)`: PVM loads `5` onto the stack.        
    - `BINARY_ADD`: PVM pops `10` and `5`, adds them, and pushes `15` back.        
    - `STORE_NAME 0 (x)`: PVM stores `15` in variable `x`.        

---

### **Why Doesn't PVM Convert Bytecode into Machine Code?**

✅ The **PVM directly interprets bytecode** without JIT compiling it into machine code.  
✅ This makes **execution slower** but allows dynamic typing, easy debugging, and cross-platform execution.  
✅ **CPython (default Python implementation) does not use JIT compilation.**

> 🔹 **Alternative:** PyPy (a JIT-enabled Python) compiles hot bytecode sections into native machine code for speed.

---

## **Final Answer**

🔹 The **Python Virtual Machine (PVM) directly interprets bytecode** instead of converting it into machine code.  
🔹 It **reads, decodes, and executes** each bytecode instruction one at a time.  
🔹 This makes Python **slower than compiled languages** but more flexible and platform-independent.

Would you like to explore **how PyPy speeds up Python with JIT?** 🚀

---
---

When you call the Python interpreter to execute a program, a series of steps occur to process and execute your Python code. Here's a breakdown of what happens:

---

### 1. **Loading the Interpreter**

- When you run a Python script (e.g., `python hello.py`), the operating system locates the Python interpreter (e.g., `python3` executable).    
- The interpreter is loaded into memory and initialized.    

---

### 2. **Reading the Script**

- The Python interpreter reads the script file (`hello.py`) line by line.    

---

### 3. **Lexical Analysis (Tokenization)**

- The interpreter breaks down the source code into **tokens**, which are the smallest meaningful units (e.g., keywords, identifiers, operators, etc.).    

**Example**:

```python
print("hello world")
```

Tokenized as:

- `print`: A built-in function name    
- `"hello world"`: A string literal    

---

### 4. **Parsing**

- The tokens are analyzed syntactically to ensure they follow Python's grammar rules.    
- The result is an **Abstract Syntax Tree (AST)**, a structured representation of the code's logic.    

**Example**:

```python
print("hello world")
```

AST:

```
Call(
    func=Name(id='print', ctx=Load()),
    args=[Constant(value='hello world')],
    keywords=[]
)
```

---

### 5. **Bytecode Compilation**

- The AST is compiled into **Python bytecode**, an intermediate representation.    
- Bytecode is a low-level, platform-independent set of instructions executed by the Python Virtual Machine (PVM).    

**Example**:  
Bytecode for `print("hello world")`:

```
LOAD_NAME 0 (print)
LOAD_CONST 1 ('hello world')
CALL_FUNCTION 1
RETURN_VALUE
```

- The bytecode may be cached (e.g., in `.pyc` files) to speed up future executions.    

---

### 6. **Execution by the Python Virtual Machine (PVM)**

- The PVM reads and executes the bytecode instructions one at a time.    
- For `print("hello world")`:
    
    1. **LOAD_NAME**: Locate the `print` function.        
    2. **LOAD_CONST**: Push the constant string `"hello world"` onto the stack.        
    3. **CALL_FUNCTION**: Call the `print` function with the string argument.        
    4. **RETURN_VALUE**: Complete the function call and clean up.        

---

### 7. **Output**

- The `print` function interacts with the standard output stream and sends the string `"hello world"` to the console.    

---

### Summary Flow

1. **Interpreter Initialization** → 2. **Lexical Analysis** → 3. **Parsing** → 4. **Bytecode Compilation** → 5. **Execution by PVM** → 6. **Output**    

This process ensures Python programs are executed in a consistent and portable way across different environments.