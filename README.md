# Making a Calculator using Tkinter from Python
import tkinter

# Tkinter is the inbuilt python module that is used to create GUI applications. 
# It is one of the most commonly used modules for creating GUI applications in Python as it is simple and easy to work with. 
# You don’t need to worry about the installation of the Tkinter module separately as it comes with Python already. 
# It gives an object-oriented interface to the Tk GUI toolkit.  

from tkinter import Tk
from tkinter import Entry, Button, StringVar
import math

class Calculator:
    
    def __init__(self, master):
        master.title("Calculator")
        master.geometry('450x500')
        master.config(bg='Black')
        master.resizable(False,False)
        
        self.equation=StringVar()
        self.entry_value=' '
        Entry(width=30, bg='#FFFFE0', font=('Times New Roman', 28), textvariable=self.equation).place(x=0,y=0)
        
        Button(width=11,height=4,text='x^y',relief='flat',bg='white',command=lambda:self.show('^')).place(x=0 ,y=50)
        Button(width=11,height=4,text='log',relief='flat',bg='white',command=lambda:self.show('log')).place(x=90 ,y=50)
        Button(width=11,height=4,text='ln',relief='flat',bg='white',command=lambda:self.show('ln')).place(x=180 ,y=50)
        Button(width=11,height=4,text='(',relief='flat',bg='white',command=lambda:self.show('(')).place(x=270 ,y=50)
        Button(width=11,height=4,text=')',relief='flat',bg='white',command=lambda:self.show(')')).place(x=360 ,y=50)
        Button(width=11,height=4,text='√x',relief='flat',bg='white',command=lambda:self.show('√')).place(x=0 ,y=125)
        Button(width=11,height=4,text='BACK',relief='flat',bg='white',command=self.backspace).place(x=90 ,y=125)
        Button(width=11,height=4,text='%',relief='flat',bg='white',command=lambda:self.show('prcnt')).place(x=180 ,y=125)
        Button(width=11,height=4,text='mod',relief='flat',bg='white',command=lambda:self.show('%')).place(x=270 ,y=125)
        Button(width=11,height=4,text='/',relief='flat',bg='white',command=lambda:self.show('/')).place(x=360 ,y=125)
        Button(width=11,height=4,text='x!',relief='flat',bg='white',command=lambda:self.show('!')).place(x=0 ,y=200)
        Button(width=11,height=4,text='7',relief='flat',bg='white',command=lambda:self.show(7)).place(x=90 ,y=200)
        Button(width=11,height=4,text='8',relief='flat',bg='white',command=lambda:self.show(8)).place(x=180 ,y=200)
        Button(width=11,height=4,text='9',relief='flat',bg='white',command=lambda:self.show(9)).place(x=270 ,y=200)
        Button(width=11,height=4,text='x',relief='flat',bg='white',command=lambda:self.show('*')).place(x=360 ,y=200)
        Button(width=11,height=4,text='1/x',relief='flat',bg='white',command=lambda:self.show('1/')).place(x=0 ,y=275)
        Button(width=11,height=4,text='4',relief='flat',bg='white',command=lambda:self.show(4)).place(x=90 ,y=275)
        Button(width=11,height=4,text='5',relief='flat',bg='white',command=lambda:self.show(5)).place(x=180 ,y=275)
        Button(width=11,height=4,text='6',relief='flat',bg='white',command=lambda:self.show(6)).place(x=270 ,y=275)
        Button(width=11,height=4,text='-',relief='flat',bg='white',command=lambda:self.show('-')).place(x=360 ,y=275)
        Button(width=11,height=4,text='π',relief='flat',bg='white',command=lambda:self.show('π')).place(x=0 ,y=350)
        Button(width=11,height=4,text='1',relief='flat',bg='white',command=lambda:self.show(1)).place(x=90 ,y=350)
        Button(width=11,height=4,text='2',relief='flat',bg='white',command=lambda:self.show(2)).place(x=180 ,y=350)
        Button(width=11,height=4,text='3',relief='flat',bg='white',command=lambda:self.show(3)).place(x=270 ,y=350)
        Button(width=11,height=4,text='+',relief='flat',bg='white',command=lambda:self.show('+')).place(x=360 ,y=350)
        Button(width=11,height=4,text='e',relief='flat',bg='white',command=lambda:self.show('e')).place(x=0 ,y=425)
        Button(width=11,height=4,text='clear_all',relief='flat',command=self.clear).place(x=90 ,y=425)
        Button(width=11,height=4,text='0',relief='flat',bg='white',command=lambda:self.show(0)).place(x=180 ,y=425)
        Button(width=11,height=4,text='.',relief='flat',bg='white',command=lambda:self.show('.')).place(x=270 ,y=425)
        Button(width=11,height=4,text='=',relief='flat',bg='white',command=self.solve).place(x=360 ,y=425)
        
    def show(self, value):
        self.entry_value += str(value)
        self.equation.set(self.entry_value)
    
    def clear(self):
        self.entry_value = ''
        self.equation.set(self.entry_value)
               
    def backspace(self):
        self.entry_value = self.entry_value[:-1]
        self.equation.set(self.entry_value)
        
    def solve(self):
        if '^' in self.entry_value:
            self.entry_value = self.entry_value.replace('^', '**'),
            self.equation.set(self.entry_value)
            
        if 'log' in self.entry_value:
            self.entry_value = self.entry_value.replace('log', 'math.log(')
            self.entry_value += ')'
            self.equation.set(self.entry_value)
            
        if 'ln' in self.entry_value:
            x=math.log(math.e)
            self.entry_value = self.entry_value.replace('ln', 'math.log(')
            self.entry_value += ')'
            self.equation.set(self.entry_value)
            
        if '√' in self.entry_value:
            self.entry_value = self.entry_value.replace('√', 'math.sqrt(')
            self.entry_value += ')'
            self.equation.set(self.entry_value)
            
        if 'prcnt' in self.entry_value:
            self.entry_value = self.entry_value.replace('prcnt', ' ')
            self.entry_value += '/100'
            self.equation.set(self.entry_value)
            
        if '!' in self.entry_value:
            num = int(self.entry_value[:-1])
            
            self.entry_value = 1
            if num < 0:
                self.equation.set('Math Error')
                
            elif num == 0 and 1:
                self.equation.set(1)
                
            else:
                for i in range (1, num+1):
                    self.entry_value *= i
                    self.equation.set(self.entry_value)
                    
        if 'π' in self.entry_value:
            self.entry_value = self.entry_value.replace('π', 'math.pi')
            self.equation.set(self.entry_value)
            
        if 'e' in self.entry_value:
            self.entry_value = self.entry_value.replace('e', 'math.e')
            self.equation.set(self.entry_value)
            
            
        else:
            result = eval(self.entry_value)
            self.equation.set(result)
root = Tk()
caculator = Calculator(root)
root.mainloop()
