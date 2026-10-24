related: [[Python]] #Python

The Python Virtual Machine (PVM) is a core part of the Python interpreter, and its job is to execute the bytecode. Here's a detailed breakdown of how it works and what happens when the PVM "sees" the bytecode:

---
### **1. What is Bytecode?**

- Bytecode is a low-level, platform-independent representation of your Python program.
- It is a series of instructions for the PVM, not the CPU. These instructions are in binary format and correspond to Python's internal instruction set (opcodes).

For example:

```python
a = 1 + 2
```

Compiles to bytecode (viewable using the `dis` module):

```plaintext
  1           0 LOAD_CONST               1 (1)
              2 LOAD_CONST               2 (2)
              4 BINARY_ADD
              6 STORE_NAME               0 (a)
              8 LOAD_CONST               0 (None)
             10 RETURN_VALUE
```

---

### **2. The Python Virtual Machine (PVM)**

- The PVM is a stack-based virtual machine.
- It processes bytecode instructions sequentially, one at a time, using a **stack** to store intermediate values and results.    

---

### **3. What Happens When PVM Sees Bytecode?**

#### **Step-by-Step Execution**

1. **Instruction Fetching**:
    
    - The PVM reads the next bytecode instruction from the compiled bytecode file (e.g., `.pyc`).        
2. **Instruction Decoding**:
    
    - The bytecode is decoded to determine which operation (opcode) needs to be performed.       
    - Each opcode has a corresponding implementation in the PVM.

3. **Execution**:
    
    - The PVM executes the operation specified by the opcode.
    - Many operations involve manipulating the stack:
        
        - **LOAD_CONST** pushes a constant (e.g., `1` or `2`) onto the stack.            
        - **BINARY_ADD** pops the top two values, adds them, and pushes the result back onto the stack.
        - **STORE_NAME** assigns the top value of the stack to a variable.      
    
4. **Loop Until Done**:
    
    - The PVM continues fetching, decoding, and executing instructions until it reaches an opcode like `RETURN_VALUE`, which signals the end of execution.        

---

### **4. How Does the PVM Execute Bytecode in Binary?**

- The PVM itself is a compiled binary program (written in C for CPython).
- The PVM's binary code contains a loop (called the **interpreter loop**) that fetches and executes bytecode instructions.    

Here’s a high-level pseudocode of the interpreter loop:

```c
while (instruction = fetch_next_instruction(bytecode)) {
    switch (instruction.opcode) {
        case LOAD_CONST:
            push(stack, instruction.argument);
            break;
        case BINARY_ADD:
            right = pop(stack);
            left = pop(stack);
            push(stack, left + right);
            break;
        case STORE_NAME:
            value = pop(stack);
            store_to_namespace(instruction.argument, value);
            break;
        ...
    }
}
```

---

### **5. Memory and State Management**

- The PVM maintains a **stack** for intermediate calculations and a **namespace** for variables.    
- It also manages memory allocation and garbage collection for Python objects created during execution.

---

### **6. Why Doesn't the PVM Run on the CPU Directly?**

- Bytecode is platform-independent and not in a format the CPU can execute directly.
- The PVM acts as a middle layer, interpreting the bytecode and issuing corresponding system-level operations (via its binary implementation).   

---

### **Conclusion**

When the PVM sees bytecode:

1. It fetches, decodes, and executes each instruction sequentially.    
2. It uses a stack-based execution model.    
3. The PVM's binary code (written in C) translates bytecode instructions into real operations.    

This process makes Python portable and dynamic, but slower than directly compiled languages like C or C++.