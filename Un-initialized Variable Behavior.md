- When the compiler encounters the declaration `int score;`, it adds an entry for `score` in its symbol table. 

- The symbol table maps the variable name `score` to its type (`int`) and the memory location where it will be stored.

#### a. **Parsing**

- The compiler reads and parses the declaration `int a;`.    
- It identifies that `a` is a variable of type `int`.
    

#### b. **Symbol Table Entry**

- The compiler adds an entry for the variable `a` to the **symbol table**, which keeps track of all variables and their properties (name, type, scope, size, etc.).
    
- It records:    
    - Variable name (`a`)     
    - Type (`int`, which is 4 bytes on most platforms)        
    - Scope (whether `a` is local, global, or static)        
    - Storage location (stack for locals, data or BSS segment for globals and statics)