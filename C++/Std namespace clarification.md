	related: [[Tags/C++]] #cpp
this is a very common question when learning C++! Let’s break it down carefully.

---

### 1. **What happens when you include a header?**

When you write:

```cpp
#include <iostream>
```

- The **preprocessor** literally copies the contents of `iostream` into your source file.    
- `iostream` contains **declarations** of classes, functions, and objects such as `std::cout`, `std::cin`, `std::endl`, etc.    
- **But it does not put them directly into the global namespace.**    

In fact, all of these declarations are inside the namespace `std`. For example, inside `iostream` (simplified):

```cpp
namespace std {
    class ostream { /* ... */ };
    extern ostream cout;
    extern ostream cerr;
    // ... other stuff
}
```

Notice: `cout` is inside `std`. It’s not directly accessible in the global scope.

---

### 2. **Why can't we use `cout` directly?**

Since `cout` is inside the `std` namespace, if you just write:

```cpp
cout << "Hello";
```

The compiler will give an error like:

```
error: 'cout' was not declared in this scope
```

Because the compiler is looking for `cout` in the **global namespace**, but it only exists in `std`.

---

### 3. **How to access names in a namespace?**

There are three main ways:

**A. Fully qualify the name:**

```cpp
std::cout << "Hello";
std::endl;
```

This explicitly tells the compiler: "I mean the `cout` in the `std` namespace."

**B. Bring individual names into the global namespace:**

```cpp
using std::cout;
using std::endl;

cout << "Hello" << endl;
```

**C. Bring all names from a namespace:**

```cpp
using namespace std;

cout << "Hello" << endl;
```

- This imports **all names** from `std` into the current scope.    
- Convenient but can cause name clashes in larger programs.    

---

### 4. **Key point**

Even though `#include <iostream>` copies the code into your file:

- Those definitions are **inside the `std` namespace**, not in the global scope.    
- The `using` statements or `std::` qualifier are needed to tell the compiler which namespace you are referring to.    

---

✅ **In short:** `#include <iostream>` gives you the declarations, but `std::cout` exists **inside a namespace**. Without either `using namespace std;` or `std::cout`, the compiler doesn’t know where to find it.

---
