In programming, the distinction between normal (or primitive) variables and object reference variables is crucial, especially in languages like Java, C#, and others that support both primitive types and objects.

### Normal (Primitive) Variables:

- **Definition**: Primitive variables directly store the values of primitive data types.    
- **Data Types**: Common primitive data types include integers, floats, characters, and booleans. In Java, for example, these are `int`, `float`, `char`, and `boolean`.    
- **Storage**: The actual value is stored in the memory location associated with the variable.    
- **Example**:
    
   ```java
    int x = 10;  // 'x' directly holds the value 10
    ```


### Object Reference Variables:

- **Definition**: Object reference variables store references (or addresses) to objects in memory, rather than the actual objects themselves.    
- **Data Types**: These variables refer to objects created from classes. In Java, for example, any variable that refers to an instance of a class is an object reference variable.    
- **Storage**: The reference variable holds the address of the memory location where the actual object is stored.    
- **Example**:
    
   ```java
    String str = "Hello";  // 'str' holds a reference to the object "Hello" in memory
    MyClass obj = new MyClass();  // 'obj' holds a reference to an instance of MyClass
  ```


### Key Differences:

1. **Memory Management**:
    
    - **Primitive**: Directly stores the value in the memory location.        
    - **Object Reference**: Stores the memory address of the actual object.

2. **Value Handling**:
    
    - **Primitive**: Contains the actual value.        
    - **Object Reference**: Contains a reference to the object.

3. **Operations**:
    
    - **Primitive**: Operations on primitive variables work directly on the value.        
    - **Object Reference**: Operations on reference variables affect the referenced object.

4. **Memory Allocation**:
    
    - **Primitive**: Typically allocated on the stack.        
    - **Object Reference**: Reference is stored on the stack, but the object itself is allocated on the heap.        
5. **Default Values**:
    
    - **Primitive**: Have default values (e.g., `0` for `int`, `false` for `boolean`).        
    - **Object Reference**: Default value is `null`.        

### Examples in Java:

```java
// Primitive variable example
int a = 5;  // 'a' holds the value 5 directly

// Object reference variable example
String s = "Hello";  // 's' holds a reference to the string object "Hello"

// Example with custom class
class Person {
    String name;
}

Person p = new Person();  // 'p' holds a reference to a new Person object
p.name = "John";  // The actual Person object has its name field set to "John"
```

In summary, primitive variables hold the actual data value, while object reference variables hold a reference to the data stored in objects. This distinction affects how the variables are manipulated and how memory is managed in the programming language.