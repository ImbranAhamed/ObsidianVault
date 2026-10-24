### **Definition**
A **cross-platform** application is one that can run on multiple platforms, but it may require some **modifications or separate builds** for each platform.

### **How it Works?**
- The code is **compiled separately** for each OS.
- It might use **conditional compilation** or **platform-specific libraries**.

### **Example: C++**
C++ is **not platform-independent** because it is compiled directly into **machine code**. However, it is **cross-platform** because you can compile the same C++ code for different OS.

#### **Example C++ Code**
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, World!" << endl;
    return 0;
}
```
#### **Compilation for Different Platforms**
```sh
g++ -o hello_linux hello.cpp   # Compile for Linux
cl hello.cpp                   # Compile for Windows
```
🔹 **Why is C++ Cross-Platform and Not Platform-Independent?**
- It must be **compiled separately** for each OS.
- It may require **modifications** for different OS-specific features.

### **Other Examples of Cross-Platform Software**
- **C# (with .NET Core)** → Runs on Windows, Linux, macOS but requires separate builds.
- **Electron Apps (VS Code, Slack)** → Use JavaScript but package separately for Windows/macOS/Linux.
- **Game Engines (Unity, Unreal Engine)** → Can compile for Windows, macOS, Android, iOS, etc.

---
