### **Course Title: Python GUI Development with Tkinter**
**Subtitle:** From First Window to Finished Application

---

### **Module 1: Introduction to GUI Programming**

*   **Slide 1: Title Slide**
    *   Python GUI Development with Tkinter
    *   Your Name / Institution
    *   [A nice graphic of a desktop application]

*   **Slide 2: Course Overview**
    *   **What you will learn:**
        *   Fundamentals of GUI programming.
        *   How to build desktop applications with Python's built-in library, Tkinter.
        *   Create interactive forms, buttons, and menus.
        *   Structure your GUI code for maintainability.
        *   Package your application for others to use.
    *   **Prerequisites:** Basic Python knowledge (variables, functions, loops).

*   **Slide 3: What is a GUI?**
    *   Graphical User Interface.
    *   Contrast with CLI (Command-Line Interface).
    *   Why use a GUI? (User-friendliness, visual feedback, accessibility).
    *   Examples: Web browsers, text editors, games.

*   **Slide 4: What is Tkinter?**
    *   Python's standard, built-in GUI library.
    *   A wrapper around the **Tk** GUI toolkit.
    *   **Pros:**
        *   Included with Python (no installation needed!).
        *   Cross-platform (Windows, macOS, Linux).
        *   Simple to learn, great for beginners.
        *   Lightweight and fast.
    *   **Cons:**
        *   Default widgets can look a bit dated (we'll fix this with `ttk`!).

*   **Slide 5: Setup & "Hello, GUI!"**
    *   Checking your installation (usually not needed).
    *   **Code:** The simplest Tkinter window.
        ```python
        import tkinter as tk

        # 1. Create the root window
        window = tk.Tk()
        window.title("Hello, World!")
        window.geometry("300x200")

        # 2. Start the event loop
        window.mainloop()
        ```
    *   **Explanation:** `tk.Tk()`, `title()`, `geometry()`, and the crucial `mainloop()`.

---

### **Module 2: Core Concepts - Widgets & Layouts**

*   **Slide 6: Anatomy of a Tkinter App**
    *   **The Root Window:** The main container.
    *   **Widgets:** The building blocks (buttons, labels, text boxes).
    *   **Layout Managers:** How you arrange widgets in the window.
    *   **Events & Callbacks:** Making your app interactive.

*   **Slide 7: Fundamental Widgets: The "Must-Knows"**
    *   `Label`: For displaying text or images.
    *   `Button`: For triggering actions.
    *   `Entry`: For single-line text input.
    *   `Text`: For multi-line text input.
    *   `Frame`: A container to group other widgets.
    *   (Show a screenshot with each widget labeled).

*   **Slide 8: Introduction to Layout Management**
    *   You can't just place widgets anywhere (well, you *can*, but you shouldn't!).
    *   Layout managers control the size and position of widgets automatically.
    *   **The Three Managers:**
        *   `pack()`: Stacks widgets on top of or next to each other.
        *   `grid()`: Arranges widgets in a table-like grid.
        *   `place()`: Puts widgets at a specific X/Y coordinate.

*   **Slide 9: The `pack()` Manager**
    *   Simplest to use.
    *   **Key options:** `side` (`tk.TOP`, `tk.BOTTOM`, `tk.LEFT`, `tk.RIGHT`), `fill` (`tk.X`, `tk.Y`, `tk.BOTH`), `expand` (`True`/`False`).
    *   **Live Demo/Code:** Show a simple packing example.
    *   **Best for:** Simple, linear layouts.

*   **Slide 10: The `grid()` Manager**
    *   Most versatile and commonly used.
    *   **Key options:** `row`, `column`, `rowspan`, `columnspan`, `sticky` (`N`, `S`, `E`, `W`).
    *   **Live Demo/Code:** Create a simple login form (Labels and Entries in a grid).
    *   **Best for:** Complex forms, table-like structures.

*   **Slide 11: CRITICAL RULE: Don't Mix Managers!**
    *   **BIG BOLD TEXT:** Never use `pack()` and `grid()` in the same master window/frame.
    *   Explain why: They have conflicting algorithms for controlling space, and your application will freeze.
    *   Show how to use `Frame` widgets to nest layouts if needed.

---

### **Module 3: Events and Interactivity**

*   **Slide 12: Making a Button Do Something (`command`)**
    *   The `command` option is the easiest way to handle events.
    *   It links a button click to a Python function (a "callback").
    *   **Code Example:**
        ```python
        def say_hello():
            print("Hello, Tkinter!")

        button = tk.Button(window, text="Click Me!", command=say_hello)
        ```
    *   **Important:** Pass the function name, don't *call* it (`say_hello`, not `say_hello()`).

*   **Slide 13: Getting and Setting Widget Data**
    *   How to get text from an `Entry` widget: `.get()`
    *   How to insert text into an `Entry` or `Text` widget: `.insert()`
    *   How to delete text: `.delete()`
    *   **Live Demo:** An app that takes a name from an `Entry` and displays "Hello, [Name]" in a `Label`.

*   **Slide 14: The `bind()` Method for Advanced Events**
    *   What if you want to respond to a key press, mouse movement, or right-click?
    *   Use the `.bind()` method.
    *   **Syntax:** `widget.bind("<EventName>", callback_function)`
    *   **Examples:** `<KeyPress>`, `<Button-1>` (left-click), `<Enter>` (mouse enters widget).
    *   Explain the `event` object that gets passed to the callback.

---

### **Module 4: Structuring Your Application with Classes**

*   **Slide 15: Why Use Classes?**
    *   Simple scripts are fine, but complex apps get messy.
    *   **Benefits of Classes:**
        *   **Organization:** Groups UI code and logic together.
        *   **State Management:** `self` holds widget references and data.
        *   **Reusability:** Create custom, reusable widgets.
        *   **Scalability:** Easier to add features and maintain.

*   **Slide 16: Refactoring to a Class-Based App**
    *   Show a simple script-based app.
    *   Then, show the same app refactored into a class.
    *   **Common Pattern:**
        ```python
        class App(tk.Tk):
            def __init__(self):
                super().__init__()
                self.title("My App")
                # ... create widgets ...
                self.create_widgets()

            def create_widgets(self):
                # ... setup all labels, buttons, etc. ...

            def my_callback(self):
                # ... logic for button clicks ...
        ```

---

### **Module 5: Advanced Widgets and Features**

*   **Slide 17: More Widgets!**
    *   `Checkbutton`: On/off toggle.
    *   `Radiobutton`: Select one from a group.
    *   `Scale`: A slider for selecting a value.
    *   `Listbox`: A list of selectable items.
    *   `Spinbox`: An entry with up/down arrows.

*   **Slide 18: Menus and Dialogs**
    *   Making your app feel "native."
    *   **Menus:** Creating a top-level menubar (`File`, `Edit`, `Help`).
    *   **Dialogs (`tkinter.messagebox`):**
        *   `showinfo()`, `showwarning()`, `showerror()`
        *   `askyesno()`, `askokcancel()`
    *   **File Dialogs (`tkinter.filedialog`):** `askopenfilename()`, `asksaveasfilename()`

*   **Slide 19: Looking Better with `ttk` (Themed Tkinter)**
    *   Introduce `tkinter.ttk`.
    *   `ttk` widgets automatically use the native look and feel of the OS.
    *   Show a side-by-side comparison of `tk.Button` vs. `ttk.Button`.
    *   **Recommendation:** Use `ttk` widgets whenever possible!
        ```python
        from tkinter import ttk
        button = ttk.Button(...)
        ```

---

### **Module 6: Project Time!**

*   **Slide 20: Let's Build: A Simple Calculator** (or To-Do List, Temperature Converter, etc.)
    *   **Project Goal:** Build a functional calculator.
    *   **Features:**
        *   Number buttons (0-9).
        *   Operator buttons (+, -, *, /).
        *   A display screen.
        *   Clear and Equals buttons.

*   **Slide 21: Project Planning**
    *   **UI Sketch:** Draw a simple layout of the calculator on the slide.
    *   **Widget Choice:**
        *   Display: A `ttk.Entry` (set to `readonly`).
        *   Buttons: Many `ttk.Button` widgets.
        *   Layout: `grid()` is perfect for this!

*   **Slide 22 - 24: Step-by-Step Implementation**
    *   (These slides would be mostly live coding).
    *   **Step 1:** Create the window and the main layout (the grid).
    *   **Step 2:** Create and place all the buttons.
    *   **Step 3:** Write the callback logic for number and operator clicks.
    *   **Step 4:** Implement the calculation logic for the "=" button.

*   **Slide 25: The Final Product!**
    *   Show a screenshot of the completed calculator.
    *   Show the final, clean, class-based code.
    *   Celebrate the achievement!

---

### **Module 7: What's Next?**

*   **Slide 26: Packaging Your Application**
    *   How to share your app with people who don't have Python.
    *   Introduce **PyInstaller**.
    *   Simple command: `pyinstaller --onefile --windowed your_script.py`
    *   Explain what this does (creates an `.exe` on Windows, `.app` on macOS).

*   **Slide 27: Beyond Tkinter**
    *   Tkinter is fantastic, but there are other options.
    *   **PyQt / PySide:** More powerful, feature-rich, steeper learning curve.
    *   **Kivy:** For multi-touch applications (mobile).
    *   **Flet / Dear PyGui:** Newer, modern libraries.

*   **Slide 28: Summary & Thank You**
    *   Recap what was learned.
    *   You can now build real, working desktop applications!
    *   Further resources (links to documentation, tutorials).
    *   **Q&A**
