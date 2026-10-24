related:  [[Servers Info ]] #server_info [[Request Forwarding]]
### **Overview**

A web server, application server, and database server are components used in a multi-tier architecture to build, deploy, and maintain web applications. Each server type has distinct responsibilities, allowing the system to scale and function efficiently.

---

### **1. Web Server**

A **web server** handles HTTP requests from clients (usually web browsers). Its primary role is to deliver static content like HTML, CSS, JavaScript, and images. It can also forward requests to an application server for dynamic content generation.

- **Examples**: Apache HTTP Server, Nginx, Microsoft IIS.    
- **Tasks**:
    
    - Serving static files.        
    - Handling basic URL routing.        
    - Forwarding API requests to the application server.


---

### **2. Application Server**

An **application server** processes business logic and generates dynamic content. It acts as an intermediary between the web server and the database server.

- **Examples**: Microsoft ASP.NET Core, Spring Boot (Java), Node.js.    
- **Tasks**:
    
    - Executing server-side scripts.        
    - Processing client input.        
    - Communicating with the database server to retrieve or modify data.


---

### **3. Database Server**

A **database server** manages the storage, retrieval, and updating of structured data. It responds to queries from the application server.

- **Examples**: Oracle Database, MySQL, PostgreSQL, Microsoft SQL Server.
- **Tasks**:
    
    - Storing data.        
    - Executing SQL queries.        
    - Ensuring data consistency and security.

A machine hosting a MySQL server or any database server is typically referred to as a "database server" or simply a "server."

In a broader context, it might be called a "database host" or a "database server host." This terminology emphasizes that the primary purpose of the machine is to host the database server software and manage access to the associated databases and data.

However, "server" is the most common and concise way to refer to a machine dedicated to hosting a database server.

---

### **How They Differ**

|Feature|Web Server|Application Server|Database Server|
|---|---|---|---|
|**Purpose**|Serves static files|Processes business logic|Manages data storage|
|**Communication**|Directly with clients|With web server & database|With application server|
|**Technology**|HTTP-based|Middleware, APIs|SQL queries|
|**Example Output**|HTML, images, scripts|Dynamic HTML, JSON|Data rows, records|

---

### **Example Scenario: E-Commerce Application**

Imagine an online store where users browse products, add them to the cart, and place orders.

1. **Web Server**:
    
    - A user accesses `www.example.com`.        
    - The web server delivers the static homepage (HTML, CSS, JavaScript).        
    - For dynamic content (e.g., product catalog), it forwards the request to the application server.
        
2. **Application Server**:
    
    - The application server retrieves the user's cart data by querying the database.
        
    - It processes the logic for adding an item to the cart and returns an updated cart view in JSON.
        
3. **Database Server**:
    
    - The database server stores product details, user profiles, and order history.
        
    - The application server sends an SQL query to fetch the product list or save the new cart state.
        

---

### **Illustration**:

#### User Request Flow:

1. **Client (Browser)**: Requests `www.example.com/products`.
    
2. **Web Server**: Serves basic layout and routes the request for product data to the application server.
    
3. **Application Server**: Executes business logic, queries product data from the database server.
    
4. **Database Server**: Returns product data to the application server.
    
5. **Application Server**: Formats the data (e.g., as JSON) and sends it back to the web server.
    
6. **Web Server**: Delivers the final page with dynamic product content to the client.
    

---

This separation of roles ensures modularity, scalability, and easier maintenance of complex applications.