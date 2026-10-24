### **What is an Environment Variable?**

An **environment variable** is a key-value pair that stores configuration settings for the operating system and applications. It helps define how system processes and programs behave.

---

### **Purpose of Environment Variables**

1. **Configuration Settings** – Stores system-wide or user-specific settings.
2. **Path Management** – Specifies where to find executables, libraries, and scripts.    
3. **Security** – Stores sensitive data like API keys without hardcoding them in code.    
4. **Customization** – Allows users to modify system behavior dynamically.    

---

### **Where Are Environment Variables Stored in Linux Mint?**

1. **System-wide Environment Variables**
    
    - Stored in system configuration files:
        
        - `/etc/environment` → System-wide environment variables.            
        - `/etc/profile` → Environment variables for all users.            
        - `/etc/bash.bashrc` → System-wide Bash-specific settings.            
2. **User-specific Environment Variables**
    
    - Stored in user configuration files:
        
        - `~/.bashrc` → Environment variables for the current user.            
        - `~/.bash_profile` or `~/.profile` → Persistent environment variables for login shells.            

---

### **How to Use Environment Variables in Linux Mint?**

#### **1. Viewing Environment Variables**

- Run the following command in the terminal:

   ```bash
    printenv
    ```

- To check a specific variable:

   ```bash
    echo $HOME
    ```


#### **2. Creating an Environment Variable**

- **Temporary Variable (Session Only)**

   ```bash
    export MY_VAR="Hello World"
   ```

    - This variable exists only in the current terminal session.

- **Permanent Variable (Persistent Across Reboots)**
    
    1. Open the `.bashrc` or `.profile` file:
        
     ```bash
        nano ~/.bashrc
      ```
        
    2. Add the following line at the end:
        
       ```bash
        export MY_VAR="Hello World"
        ```
        
    3. Save and exit (`Ctrl + X`, then `Y` and `Enter`).
        
    4. Apply the changes:
        ```bash
        source ~/.bashrc
        ```


#### **3. Removing an Environment Variable**

- **Unset Temporary Variable:**
    
    ```bash
    unset MY_VAR
    ```
    
- **Remove Permanent Variable:**
    
    - Open `~/.bashrc` or `~/.profile`, delete the line, and run `source ~/.bashrc`.
      

Let me know if you need further clarification! 🚀