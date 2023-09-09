from tkinter import *

def click(event):
    global scvalue
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(scvalue.get())
            scvalue.set(result)
        except Exception as e:
            scvalue.set("Error")
    elif text == "c":
        scvalue.set("")
    else:
        scvalue.set(scvalue.get() + text)

root = Tk()
root.geometry("644x900")

scvalue = StringVar()
scvalue.set("")
screen = Entry(root, textvar=scvalue, font="lucida 40 bold")
screen.pack(fill=X, ipadx=8, pady=10, padx=10)

# Create a 2D list to represent the button layout
button_grid = [
    ["9", "8", "7", "+"],
    ["6", "5", "4", "-"],
    ["3", "2", "1", "*"],
    ["0", "c", "=", "/"]
]

# Create buttons in a loop
for row in button_grid:
    f = Frame(root, bg="grey")
    for button_text in row:
        b = Button(f, text=button_text, padx=28, pady=22, font="lucida 35 bold")
        b.pack(side='left', padx=18, pady=12)
        b.bind("<Button-1>", click)
    f.pack()

root.mainloop()
