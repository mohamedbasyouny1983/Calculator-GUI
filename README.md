# Calculator-GUI
# calculator code by python tkinter
from tkinter import *
import math
import numpy as np  # Import NumPy for matrix operations

calc = Tk()
calc.title("Simple Calculator")
calc.geometry("550x400")
calc.resizable(width=0, height=0)
calc.configure(bg="black")





e = Entry(calc, bd=10, width=30, font="Arial 21", bg="lightgrey")
e.pack()

matrix_input_frame = Frame(calc, bg="black")
matrix_input_frame.pack(pady=10)

# Matrix input fields
matrix_a_entry = Entry(matrix_input_frame, bd=5, width=15, font="Arial 15", bg="lightgrey")
matrix_a_entry.grid(row=0, column=0, padx=5)
matrix_b_entry = Entry(matrix_input_frame, bd=5, width=15, font="Arial 15", bg="lightgrey")
matrix_b_entry.grid(row=0, column=1, padx=5)



def click(number):
    current_text = e.get()  # Get current text in entry
    e.delete(0, END)        # Clear entry field
    e.insert(0, current_text + str(number))  # Insert the new number

def clear():
    e.delete(0, END)

def add():
    current = e.get()
    e.insert(32, string= "+")

def sub():
    e.insert(32, string="-")
    current = e.get()
  

def mul():
    e.insert(32,string="x")
    current = e.get()
   


def div():
    e.insert(32, string="/")
    current = e.get()
   
def factorial():
    current = e.get()
    e.insert(32, string="n!")

def root():
    current =  e.get()
    e.insert(32, string="root")

def power():
    current =  e.get()
    e.insert(32, string="PR")

def sin():
    current =  e.get()
    e.insert(32, string="sin")

def cos():
    current =  e.get()
    e.insert(32, string="cos")

def tan():
    current =  e.get()
    e.insert(32, string="tan")

def asin():
    current =  e.get()
    e.insert(32, string="asin")  

def acos():
    current =  e.get()
    e.insert(32, string="acos")  

def atan():
    current =  e.get()
    e.insert(32, string="atan")  

def equal():
    current = e.get()




    try:
        if "+" in current:
            numbers = current.split("+")
            result = int(numbers[0].strip()) + int(numbers[1].strip())
        elif "-" in current:
            numbers = current.split("-")
            result = int(numbers[0].strip()) - int(numbers[1].strip())
        elif "/" in current:
            numbers = current.split("/")
            result = int(numbers[0].strip()) / int(numbers[1].strip())
        elif "x" in current:
            numbers = current.split("x")
            result = int(numbers[0].strip()) * int(numbers[1].strip())
        
        elif "n!" in current:
            fact = 1
            numbers = current.split("n!")
            for i in range(1, int(numbers[0])+1):
                fact = fact*i
            result = fact
        
        elif "root" in current:
            numbers = current.split("root")
            result = int(numbers[0]) ** (1/int(numbers[1]))
        
        elif "PR" in current:
            numbers = current.split("PR")
            result = int(numbers[0]) ** (int(numbers[1]))
        
        elif "sin" in current:
            numbers = current.replace("sin", "")
            if numbers.strip() == '':  # Check if the input is empty or just spaces
                raise ValueError("Invalid input")
            result = math.sin(math.radians(int(numbers)))
            
        elif "cos" in current:
            numbers = current.replace("cos", "")
            if numbers.strip() == '':  # Check if the input is empty or just spaces
                raise ValueError("Invalid input")
            result = math.cos(math.radians(int(numbers)))

        elif "tan" in current:
            numbers = current.replace("tan", "")
            if numbers.strip() == '':  # Check if the input is empty or just spaces
                raise ValueError("Invalid input")
            result = math.tan(math.radians(int(numbers)))
                    
        
        elif "asin" in current:
            numbers = current.replace("asin", "")
            if numbers.strip() == '':  # Check if the input is empty or just spaces
                raise ValueError("Invalid input")
            result = math.asin(math.radians(int(numbers)))
            
        elif "acos" in current:
            numbers = current.replace("acos", "")
            if numbers.strip() == '':  # Check if the input is empty or just spaces
                raise ValueError("Invalid input")
            result = math.acos(math.radians(int(numbers)))   
        
        elif "atan" in current:
            numbers = current.replace("atan", "")
            if numbers.strip() == '':  # Check if the input is empty or just spaces
                raise ValueError("Invalid input")
            result = math.atan(math.radians(int(numbers)))
        
        elif "matrix_add" in current:
            matrix_a = np.array(eval(matrix_a_entry.get()))
            matrix_b = np.array(eval(matrix_b_entry.get()))
            result = matrix_a + matrix_b
        elif "matrix_sub" in current:
            matrix_a = np.array(eval(matrix_a_entry.get()))
            matrix_b = np.array(eval(matrix_b_entry.get()))
            result = matrix_a - matrix_b
        elif "matrix_mul" in current:
            matrix_a = np.array(eval(matrix_a_entry.get()))
            matrix_b = np.array(eval(matrix_b_entry.get()))
            result = np.dot(matrix_a, matrix_b)
        else:
            result = "Error"

        clear()
        e.insert(0, result)

    except ZeroDivisionError:
        clear()
        e.insert(0, "Error")
        
        


button_1 = Button(calc,text="7",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(7))
button_1.place(x= 0, y = 60)

button_2 = Button(calc,text="8",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(8))
button_2.place(x= 70, y = 60)

button_3 = Button(calc,text="9",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(9))
button_3.place(x= 140, y = 60)

button_4 = Button(calc,text="4",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(4))
button_4.place(x= 0, y = 135)

button_5 = Button(calc,text="5",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(5))
button_5.place(x= 70, y = 135)

button_6 = Button(calc,text="6",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(6))
button_6.place(x= 140, y = 135)

button_7 = Button(calc,text="1",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(1))
button_7.place(x= 0, y = 210)

button_8 = Button(calc,text="2",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(2))
button_8.place(x= 70, y = 210)

button_9 = Button(calc,text="3",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(3))
button_9.place(x= 140, y = 210)


button_10 = Button(calc,text="0",font=("Arial bold",19), bg="Grey", bd="10", padx=10, pady=5, command = lambda: click(0))
button_10.place(x= 0, y = 285)

button_11 = Button(calc,text="C",font=("Arial bold",19), bg="green", bd="10", padx=10, pady=5, command = clear)
button_11.place(x= 70, y = 285)

button_12 = Button(calc,text="=",font=("Arial bold",19), bg="blue", bd="10", padx=10, pady=5, command = equal)
button_12.place(x= 140, y = 285)

button_13 = Button(calc,text="+",font=("Arial bold",19), bg="crimson", bd="10", padx=12, pady=5, command = add)
button_13.place(x= 210, y = 60)

button_14 = Button(calc,text="-",font=("Arial bold",22), bg="crimson", bd="10", padx=12, pady=5, command = sub)
button_14.place(x= 210, y = 135)

button_15 = Button(calc,text="/",font=("Arial bold",22), bg="crimson", bd="10", padx=12, pady=5, command = div)
button_15.place(x= 210, y = 210)

button_16 = Button(calc,text="x",font=("Arial bold",19), bg="crimson", bd="10", padx=12, pady=5, command = mul)
button_16.place(x= 210, y = 285)

button_17 = Button(calc,text="n!",font=("Arial bold",19), bg="crimson", bd="10", padx=12, pady=5, command = factorial)
button_17.place(x= 280, y = 60)

button_18 = Button(calc,text="rt",font=("Arial bold",19), bg="crimson", bd="10", padx=12, pady=5, command = root)
button_18.place(x= 280, y = 135)

button_19 = Button(calc,text="PR",font=("Arial bold",15), bg="crimson", bd="10", padx=12, pady=5, command = power)
button_19.place(x= 280, y = 210)

button_20 = Button(calc,text="sin",font=("Arial bold",16), bg="crimson", bd="10", padx=12, pady=5, command = sin)
button_20.place(x= 360, y = 60)

button_21 = Button(calc,text="cos",font=("Arial bold",16), bg="crimson", bd="10", padx=12, pady=5, command = cos)
button_21.place(x= 360, y = 135)

button_21 = Button(calc,text="tan",font=("Arial bold",16), bg="crimson", bd="10", padx=12, pady=5, command = tan)
button_21.place(x= 360, y = 210)

button_22 = Button(calc,text="asin",font=("Arial bold",15), bg="crimson", bd="10", padx=12, pady=5, command = asin)
button_22.place(x= 450, y = 60)

button_23 = Button(calc,text="acos",font=("Arial bold",15), bg="crimson", bd="10", padx=12, pady=5, command = acos)
button_23.place(x= 450, y = 135)

button_24 = Button(calc,text="atan",font=("Arial bold",15), bg="crimson", bd="10", padx=12, pady=5, command = atan)
button_24.place(x= 450, y = 210)


# Matrix operation buttons
button_25 = Button(calc, text="Add Matrices", font=("Arial bold", 12), bg="crimson", command=lambda: click("matrix_add"))
button_25.place(x= 280 , y= 280)

button_26 = Button(calc, text="Subtract Matrices", font=("Arial bold", 12), bg="crimson", command=lambda: click("matrix_sub"))
button_26.place(x= 280 , y= 320)

button_27 = Button(calc, text="Multiply Matrices", font=("Arial bold", 12), bg="crimson", command=lambda: click("matrix_mul"))
button_27.place(x= 280 , y= 360)


calc.mainloop()
