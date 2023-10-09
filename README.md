from tkinter import *
root = Tk()

root.title('CALCULATOR')
root.config(bg= 'pink',cursor='dot',)
root.iconbitmap(r"D:\tkinter\calculator-131994967672059924.png")
e = Entry(root, width=30, borderwidth=5, bg='navyblue', fg='white')
e.grid(row=0, column=1, columnspan=4)

def num(x):
    if x not in ['+', '-']:
        current = e.get()
        e.delete(0, END)
        e.insert(0, str(current)+str(x))
    elif x=='+':
        global ca,v1
        v1 = e.get()
        ca = 'add'
        e.delete(0,END)
    else:
        v1 = e.get()
        ca = 'sub'
        e.delete(0, END)
def div():
    global ca, v1
    v1 = e.get()
    ca = 'div'
    e.delete(0, END)

def mul():
    global ca, v1
    v1 = e.get()
    ca = 'mul'
    e.delete(0, END)
def equal():
    v2 = e.get()
    e.delete(0, END)
    if ca=='add':
        e.insert(0, str(int(v1)+int(v2)))
    elif ca=='sub':
        e.insert(0, str(int(v1) - int(v2)))
    elif ca=='div':
        e.insert(0, str(int(v1)/int(v2)))
    else :
        e.insert(0, str(int(v1)+int(v2)))
r, c=1, 1
for i in ['1', '2', '3', '4', '5', '6', '7', '8', '9', '-', '0', '+']:
    Button(root, text=i, height=4, width=6, command=lambda value=i : num(value),padx=5, activebackground='black', activeforeground='white').grid(row=r, column=c, padx=1, pady=0)
    c += 1
    if c > 3:
        c = 1
        r += 1
Button(root, text='/', height=4, width=6, command=div, activebackground='black', activeforeground='white').grid(row=1, column=4,padx=3, pady=3)
Button(root, text='*', height=4, width=6, command=mul, activebackground='black', activeforeground='white').grid(row=2, column=4,padx=3, pady=3)
Button(root, text='=', height=9, width=6,command=equal, activebackground='black', activeforeground='white').grid(row=3, column=4,padx=3, pady=3,rowspan=2)
root.mainloop()
