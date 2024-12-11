### Random Password Generator using Python

Passwords are essential for protecting accounts and sensitive information. A strong password typically includes a combination of lowercase, uppercase letters, symbols, and digits, with a length of at least 10 characters.

### Python Password Generator:
This project uses Python's `random` and `tkinter` modules to create a password generator. It's ideal for beginners looking to practice Python programming.

### Project Prerequisites:
No extra installations are needed for `random` and `string` modules. Tkinter is built-in, but if you encounter errors, you can install it on Linux using:

```bash
sudo apt-get install python3-tkinter
```

### Overview:
- **Random**: Used to generate random passwords.
- **Tkinter**: Used to create a simple GUI for the password generator.

This project helps you build a functional, beginner-level password generator application.

### 1. **Import Required Modules**
```python
import random
from tkinter import messagebox
from tkinter import *
```
Explanation:
- **random** is used to generate a random password.
- **messagebox** is used to display error prompts if the user fails to provide inputs.
- **tkinter** is used to create the graphical user interface (GUI) components.

### 2. **Define the Password Generator Function**
```python
def generate_password():
    try:
        repeat = int(repeat_entry.get())
        length = int(length_entry.get())
    except:
        messagebox.showerror(message="Please key in the required inputs")
        return

    # Check if repetition is allowed
    if repeat == 1:
        password = random.sample(character_string, length)
    else:
        password = random.choices(character_string, k=length)
    
    password = ''.join(password)  # Convert list to string
    password_v = StringVar()
    password = "Created password: " + str(password)
    password_v.set(password)

    password_label = Entry(password_gen, bd=0, bg="gray85", textvariable=password_v, state="readonly")
    password_label.place(x=10, y=140, height=50, width=320)
```
Explanation:
- A **try-except** block is used to handle invalid inputs for length and repetition.
- If repetition is allowed (`repeat == 2`), **random.choices** is used. If no repetition is allowed (`repeat == 1`), **random.sample** is used.
- The generated password is converted from a list to a string using `''.join()`.
- A read-only **Entry** widget is used to display the generated password.

### 3. **Define the Character String**
```python
character_string = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[\]^_`{|}~"
```
Explanation:
- A string containing uppercase letters, lowercase letters, digits, and special characters is defined. This is used to generate the password.

### 4. **Create the User Interface**
```python
password_gen = Tk()
password_gen.geometry("350x200")
password_gen.title("PythonGeeks Password Generator")
```
Explanation:
- The **Tk()** class is used to create the main window.
- The window size is set to `350x200` and the title is set to "PythonGeeks Password Generator".

### 5. **Add Input Widgets**
```python
title_label = Label(password_gen, text="PythonGeeks Password Generator", font=('Ubuntu Mono', 12))
title_label.pack()

length_label = Label(password_gen, text="Enter length of password: ")
length_label.place(x=20, y=30)
length_entry = Entry(password_gen, width=3)
length_entry.place(x=190, y=30)

repeat_label = Label(password_gen, text="Repetition? 1: no repetition, 2: otherwise: ")
repeat_label.place(x=20, y=60)
repeat_entry = Entry(password_gen, width=3)
repeat_entry.place(x=300, y=60)
```
Explanation:
- **Label** widgets are used to display text such as "Enter length of password" and "Repetition?".
- **Entry** widgets are used to capture user input for the length and repetition settings.

### 6. **Add a Button to Call the `generate_password` Function**
```python
password_button = Button(password_gen, text="Generate Password", command=generate_password)
password_button.place(x=100, y=100)
```
Explanation:
- A **Button** widget is created. When clicked, it will call the `generate_password` function to generate and display a password.

### 7. **Run the Application**
```python
password_gen.mainloop()
```
Explanation:
- The **mainloop()** method is called to start the Tkinter event loop, which listens for user interactions such as button clicks.

### Complete Code:
```python
import random
from tkinter import messagebox
from tkinter import *

# Define the character string
character_string = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!#$%&'()*+,-./:;<=>?@[\]^_`{|}~"

# Password generator function
def generate_password():
    try:
        repeat = int(repeat_entry.get())
        length = int(length_entry.get())
    except:
        messagebox.showerror(message="Please key in the required inputs")
        return

    # Check if repetition is allowed
    if repeat == 1:
        password = random.sample(character_string, length)
    else:
        password = random.choices(character_string, k=length)
    
    password = ''.join(password)  # Convert list to string
    password_v = StringVar()
    password = "Created password: " + str(password)
    password_v.set(password)

    password_label = Entry(password_gen, bd=0, bg="gray85", textvariable=password_v, state="readonly")
    password_label.place(x=10, y=140, height=50, width=320)

# Create the user interface
password_gen = Tk()
password_gen.geometry("350x200")
password_gen.title("PythonGeeks Password Generator")

# Add input widgets
title_label = Label(password_gen, text="PythonGeeks Password Generator", font=('Ubuntu Mono', 12))
title_label.pack()

length_label = Label(password_gen, text="Enter length of password: ")
length_label.place(x=20, y=30)
length_entry = Entry(password_gen, width=3)
length_entry.place(x=190, y=30)

repeat_label = Label(password_gen, text="Repetition? 1: no repetition, 2: otherwise: ")
repeat_label.place(x=20, y=60)
repeat_entry = Entry(password_gen, width=3)
repeat_entry.place(x=300, y=60)

# Generate password button
password_button = Button(password_gen, text="Generate Password", command=generate_password)
password_button.place(x=100, y=100)

# Start the Tkinter event loop
password_gen.mainloop()
```

### How It Works:
1. The user enters the password length and chooses whether they want repetition of characters.
2. When the **"Generate Password"** button is clicked, the password is generated using the specified parameters.
3. The generated password is displayed in a read-only input field.
