A **browser engine** (sometimes called a **layout engine** or **rendering engine**) is a critical part of a web browser. It is responsible for transforming web content (like HTML, CSS, and JavaScript) into what you see on your screen. Here are the **main components** that a typical browser engine consists of:

---

### 🔧 **1. HTML Parser**

- Parses the HTML code and builds the **DOM tree (Document Object Model)**.    
- Converts textual HTML into a structured, object-oriented representation.    

---

### 🎨 **2. CSS Parser**

- Parses the CSS files and styles defined in HTML.    
- Builds the **CSSOM (CSS Object Model)**, representing all styling information.    

---

### 🌲 **3. Render Tree Construction**

- Combines the DOM and CSSOM into a **render tree**.    
- The render tree contains visual elements in the order they need to appear, along with style information.    

---

### 📐 **4. Layout Engine (Reflow)**

- Calculates the position and size of each element on the screen.    
- This step is called **layout** or **reflow**.    

---

### 🖼️ **5. Painting**

- Converts elements in the render tree into **pixels**.    
- Each node is drawn onto the screen using information from styles, layout, etc.    

---

### 🧠 **6. JavaScript Engine Interface**

- Works with the **JavaScript engine** (like V8, SpiderMonkey) to update DOM/CSSOM dynamically.    
- Handles **event listeners, DOM manipulations**, etc.    

---

### 🚀 **7. Compositing**

- Combines different painted layers and renders them to the screen.    
- Allows features like **smooth scrolling**, **animations**, and **GPU acceleration**.    

---

### 📦 Summary Table

|Component|Responsibility|
|---|---|
|HTML Parser|Build DOM tree|
|CSS Parser|Build CSSOM|
|Render Tree Builder|Combine DOM + CSSOM for visual structure|
|Layout Engine|Calculate element sizes and positions|
|Paint Engine|Paint elements into bitmaps|
|JS Engine Interface|DOM scripting, dynamic updates|
|Compositor|Compositing layers and final screen output|

---

If you want to explore specific browser engines (like **Blink**, **WebKit**, or **Gecko**), I can break those down as well.