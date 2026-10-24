
Related: [[Java]] #java
JDK, JRE, and JVM are key components in the Java ecosystem. Here's a detailed explanation of each:

---

### **1. Java Virtual Machine (JVM)**

- The **JVM** is the heart of the Java platform.    
- It is an abstract machine that provides a runtime environment for executing Java bytecode.    
- The JVM ensures Java's "Write Once, Run Anywhere" capability by abstracting the underlying operating system and hardware.
#### Key Responsibilities:

1. **Class Loading**: Loads `.class` files into memory.    
2. **Bytecode Verification**: Ensures that bytecode is valid and secure.    
3. **Execution**: Converts bytecode into machine code using:
    
    - **Interpreter**: Executes bytecode line by line.        
    - **JIT (Just-In-Time) Compiler**: Compiles frequently executed bytecode into native machine code for better performance.        
4. **Garbage Collection**: Automatically manages memory by reclaiming unused objects.
#### Important Note:
- The JVM is platform-specific. For example, there are different JVMs for Windows, Linux, and macOS.   

---

### **2. Java Runtime Environment (JRE)**

- The **JRE** provides the environment necessary to run Java applications.
    
- It includes:    
    - The **JVM**.        
    - Core libraries (e.g., `java.util`, `java.io`).        
    - Other supporting files.
#### Use Case:

- If you only need to **run** Java applications (not develop them), you can install the JRE.

#### Example Structure:

```
JRE = JVM + Libraries + Other Components
```

---

### **3. Java Development Kit (JDK)**

- The **JDK** is a superset of the JRE. It includes all the tools and libraries required for Java development.   
#### What’s Included in the JDK:

1. **JRE**: To run Java applications.    
2. **Development Tools**:    
    - `javac`: The Java compiler for converting `.java` files to `.class` files.        
    - `java`: The launcher for running Java programs.        
    - `javadoc`: For generating documentation from comments.        
    - `jar`: For packaging applications into `.jar` files.        
    - Debugging and profiling tools.        
#### Use Case:

- If you want to **develop** Java applications, you need the JDK.

#### Example Structure:

```
JDK = JRE + Development Tools
```

---

### Summary of Differences:

|Feature|JVM|JRE|JDK|
|---|---|---|---|
|**Purpose**|Runs Java bytecode|Provides runtime for Java programs|Provides tools for developing Java programs|
|**Contains**|Executes `.class` files|JVM + Core Libraries|JRE + Development Tools|
|**Target Audience**|For executing Java code|For running Java programs|For developing Java programs|
|**Example Tools**|None|None|`javac`, `java`, `javadoc`, `jar`|

---

### Analogy:

Think of **JVM**, **JRE**, and **JDK** like a car:

- **JVM**: The engine that runs the car.    
- **JRE**: The car itself (engine + necessary components to run).    
- **JDK**: The car factory (tools to build the car, including the car itself).    
