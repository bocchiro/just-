# just-
from tkinter import *
from functools import partial

primer = ''  # '**2'

def click(nameB):
  global primer
  if nameB == "DEL" :
    primer = primer[:len(primer) -1]
    nameB = ""
    if primer == '':
      label.config(text = '0')
    else:
      label.config(text = primer)
  else:
    if nameB == 'C' :
      primer = ''
      label.config(text = "0")
    else:
      if nameB == '=':
        primer = str(eval(primer))
        label.config(text = primer)
      else:
        if nameB == 'X^2':
          if primer != '' :
            primer = primer + '**2'
            primer = str(eval(primer))
            label.config(text = primer)      
        else:
          primer += nameB
          label.config(text = primer)
        
root = Tk()
root.config(bg = "black")
root.geometry("485x550")
root.title("Калькулятор")
root.resizable(False, False)

label = Label(text='0', font=("Consolas", 21, "bold"), bg="black", foreground="white")
label.place(x = 10, y = 50)

buttonNames = [
"C", "DEL", "*", "=",
"1", "2", "3", "/",
"4", "5", "6", "+", 
"7", "8", "9", "-",
"(", "0", ")", "X^2"
]

# '3 + (2 * 2) ** 2'

x = 10
y = 140

for i in buttonNames:
  Button(
    text = i,
    bg="white",
    font=("Consolas", 15),
    command = partial(click, i)
    ).place(
      x = x, 
      y = y,
      width = 115,
      height = 79)
  x += 117
  if x > 400:
      x = 10
      y += 81

root.mainloop()
