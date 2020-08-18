# python-DATABASE-TABLE-using-Tkinter
#Python project
import tkinter as tk
from tkinter import *
from tkinter import ttk
import sqlite3
root=Tk()

label1=Label(root,text="Registration Form",font=('arial',20,'bold'),bg="black",fg="white")
label1.pack(side=TOP,fill=X)


label2=Label(root,text=" ",font=('arial',15,'bold'),bg="black",fg="white")
label2.pack(side=BOTTOM,fill=X)

def create():
    conn=sqlite3.connect('database.db')
    c=conn.cursor()
    c.execute("CREATE TABLE IF NOT EXISTS new1(id integer primary key autoincrement,name TEXT,father TEXT,city TEXT,state TEXT,sqltime TIMEESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL)")
    conn.commit()
    conn.close()
create()    

#Student name
label1=Label(root,text="Enter Student Name",font=('arial',9,'bold'))
label1.place(x=30,y=60)
name_entry=StringVar()
name_entry=ttk.Entry(root,textvariable=name_entry)
name_entry.place(x=190,y=60)

#Father name
label2=Label(root,text="Enter your Father name",font=('arial',9,'bold'))
label2.place(x=30,y=100)
name_entry2=StringVar()
name_entry2=ttk.Entry(root,textvariable=name_entry2)
name_entry2.place(x=190,y=100)

#city option

label3=Label(root,text="City",font=('arial',9,'bold'))
label3.place(x=350,y=60)
name_entry3=StringVar()
name_entry3=ttk.Entry(root,textvariable=name_entry3)
name_entry3.place(x=400,y=60)

#state 
label4=Label(root,text="State",font=('arial',9,'bold'))
label4.place(x=350,y=100)
name_entry4=StringVar()
name_entry4=ttk.Entry(root,textvariable=name_entry4)
name_entry4.place(x=400,y=100)






def savedata():
    conn=sqlite3.connect('database.db')
    c=conn.cursor()
    c.execute('INSERT INTO new1(name,father,city,state) VALUES(?,?,?,?)',(name_entry.get(),name_entry2.get(),name_entry3.get(),name_entry4.get()))
    conn.commit()
    print("data saved")
    name_entry.delete(0,END)
    name_entry2.delete(0,END)
    name_entry3.delete(0,END)
    name_entry4.delete(0,END)

btn=ttk.Button(root,text="Save data ",command=savedata)
btn.place(x=210,y=150,width=100,height=50)
root.geometry('700x700')
root.mainloop()
