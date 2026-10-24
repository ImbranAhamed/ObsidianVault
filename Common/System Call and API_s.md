### **1. System Call**

A **system call** is a low-level function that allows a program to request services directly from the operating system's kernel. These services include tasks like accessing hardware, managing processes, reading or writing files, and allocating memory.

#### **How System Calls Work:**

1. A user-level application makes a request for an operating system service.    
2. The request transitions from user mode to kernel mode via a specific instruction (e.g., an interrupt or trap).    
3. The kernel processes the request and performs the operation.    
4. The result is returned to the application, and control is switched back to user mode.    

#### **Examples of System Calls:**

- **Linux**:
    
    - `read()` – Read data from a file.        
    - `write()` – Write data to a file.        
    - `fork()` – Create a new process.        
    - `execve()` – Execute a program.        
    - `open()` – Open a file.

- **Windows**:
    
    - `CreateFile()` – Open or create a file.        
    - `ReadFile()` – Read from a file.        
    - `WriteFile()` – Write to a file.        
    - `CreateProcess()` – Create a new process.        

#### **Key Features of System Calls:**

- Directly interact with the kernel.    
- Provide controlled access to system resources.    
- Often have a higher overhead than regular function calls due to the user-to-kernel mode switch.    

---

### **2. API (Application Programming Interface)**

An **API** is a higher-level abstraction that provides a set of functions or protocols for building software applications. APIs can be used to interact with libraries, frameworks, or even the operating system itself.

#### **How APIs Work:**

1. An application calls a function from an API.    
2. The API translates the function into a system call (if necessary) or performs the operation directly using existing resources.    
3. The API returns the result to the application.    

#### **Examples of APIs:**

- **Standard C Library APIs**:
    
    - `fopen()` – Opens a file (calls the underlying `open()` system call).        
    - `fwrite()` – Writes to a file (wraps the `write()` system call).

- **Windows API**:
    
    - `MessageBox()` – Displays a message box.        
    - `CreateWindow()` – Creates a window.

- **Web APIs**:
    
    - `fetch()` – Fetch resources from the web.        
    - `XMLHttpRequest` – Communicates with a server.

- **Database APIs**:
    
    - `JDBC` – Java API for interacting with databases.        
    - `SQLAlchemy` – Python library for database interaction.        

#### **Key Features of APIs:**

- Provide a convenient interface for developers.    
- Hide the complexity of system calls or hardware interactions.    
- Often portable across platforms, unlike system calls.    

---

### **Key Differences Between System Calls and APIs**

|**Feature**|**System Call**|**API**|
|---|---|---|
|**Level**|Low-level, kernel mode|High-level, user mode|
|**Purpose**|Access kernel or hardware services|Simplify and abstract functionality|
|**Performance**|Slower due to user-to-kernel transition|Faster (if it doesn’t invoke system calls)|
|**Portability**|OS-specific|Often cross-platform|
|**Complexity**|Requires detailed knowledge of the OS|Easier to use for developers|

---

### **Analogy**

Think of system calls as the raw machinery of a car engine, while APIs are like the steering wheel, accelerator, and brake pedals. APIs make it easier to "drive" your program without dealing directly with the "engine" (system calls).