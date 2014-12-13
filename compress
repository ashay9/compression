#!/usr/bin/python
 
 
####################  Files to be imported   #####################################
import os
import tarfile
import time
import fnmatch
import shutil
from tkinter import *
from tkinter import ttk
 
####################  Global Variables   #########################################
 
addfile={}
bigfile={}
addfiles={}
bigfiles={}
 
 
 
class Compress:
 
####################  date tab function to get path   #############################
   
    def getfile(self,abc):
        bigfile[abc]=addfile[abc].get()
        abc=abc+1
        self.callback(abc)
       
 
 
####################  date tab function to create entry   #########################
       
    def callback(self,abc):
        addfile[abc]=ttk.Entry(self.frameadd,width=50)
        addfile[abc].grid(row=abc,column=0,stick='w')
        ttk.Button(self.frameadd,text="add",command= lambda :self.getfile(abc)).grid(row=abc,column=1,stick='e')
 
 
 
####################  month tab function to get path   ############################
       
    def getfile1(self,abcd):
        bigfiles[abcd]=addfiles[abcd].get()
        abcd=abcd+1
        self.callback1(abcd)
 
 
 
####################  month tab function to create entry  ##########################
       
    def callback1(self,abcd):
        addfiles[abcd]=ttk.Entry(self.frameadd1,width=50)
        addfiles[abcd].grid(row=abcd,column=0,stick='w')
        ttk.Button(self.frameadd1,text="add",command= lambda :self.getfile1(abcd)).grid(row=abcd,column=1,stick='e')
 
 
####################  compression algo for date   #################################
       
    def date_hello(self,day,month,year,choice):
        for i in range(len(bigfile)):
            bigfile[i+1]=bigfile[i+1].replace('\\','/')
            for root, dirs, files in os.walk(bigfile[i+1]):
                root=root.replace('\\','/')
                for items in fnmatch.filter(files, "*"):
                    filess = root+"/"+items+"\n"
                    with open("test1.txt", "a") as myfile:
                        myfile.write(filess)
 
        tar = tarfile.open("hello.tar.gz", "w:gz")
 
        if choice=="Yes":
            with open("test1.txt", "r") as f:
                for line in f:
                   line=line.replace('\n','')
                   timea=time.ctime(os.path.getmtime(line))
                   mon=timea[4:7]
                   dat=timea[8:10]
                   yr=timea[20:24]
                   if mon == month and int(dat) == int(day) and yr == year:
                       tar.add(line)
                       os.remove(line)
            tar.close()
            #os.remove("test1.txt")
        else:
            with open("test1.txt", "r") as f:
                for line in f:
                   line=line.replace('\n','')
                   timea=time.ctime(os.path.getmtime(line))
                   mon=timea[4:7]
                   dat=timea[8:10]
                   yr=timea[20:24]
                   if mon == month and int(dat) == int(day) and yr == year:
                       tar.add(line)
            tar.close()
            os.remove("test1.txt")
 
 
####################  compression algo for month    ###################################
           
    def month_hello(self,monthsa,yearsa,choices):
        for i in range(len(bigfiles)):
            bigfiles[i+1]=bigfiles[i+1].replace('\\','/')
            for root, dirs, files in os.walk(bigfiles[i+1]):
                root=root.replace('\\','/')
                for items in fnmatch.filter(files, "*"):
                    filess = root+"/"+items+"\n"
                    with open("test1.txt", "a") as myfile:
                        myfile.write(filess)
 
        tar = tarfile.open("hello.tar.gz", "w:gz")
 
 
        if choices=="Yes":
            with open("test1.txt", "r") as f:
                for line in f:
                   line=line.replace('\n','')
                   timea=time.ctime(os.path.getmtime(line))
                   mon=timea[4:7]
                   dat=timea[8:10]
                   yr=timea[20:24]
                   if mon == monthsa and yr == yearsa:
                       tar.add(line)
                       os.remove(line)
            tar.close()
            os.remove("test1.txt")
        else:
            with open("test1.txt", "r") as f:
                for line in f:
                   line=line.replace('\n','')
                   timea=time.ctime(os.path.getmtime(line))
                   mon=timea[4:7]
                   dat=timea[8:10]
                   yr=timea[20:24]
                   if mon == monthsa and yr == yearsa:
                       tar.add(line)
            tar.close()
            os.remove("test1.txt")
 
 
    def __init__(self,master):
        master.title('Compress Files By Date Or By Month')
        master.resizable(False,False)
        #master.configure(background='#33CCFF')
 
        #self.style=ttk.Style()
        #self.style.configure('TFrame',background='#33CCFF')
        #self.style.configure('TButton',background='#33CCFF')
        #self.style.configure('TLabel',background='#33CCFF')
####################  Create Notebook (Tabs)   #######################################
        self.notebook = ttk.Notebook(master)
        self.notebook.pack()
        self.date = ttk.Frame(self.notebook)
        self.months = ttk.Frame(self.notebook)
        self.notebook.add(self.date, text = 'date')
        self.notebook.add(self.months, text = 'month')
 
 
 
 
####################  Create and Fill date tab GUI   ##################################
        self.frameadd = ttk.Frame(self.date,relief=RIDGE,padding=(50,20))
        self.frameadd.grid(row=0,column=1,rowspan=2,stick='n')
 
 
        self.framedate = ttk.Frame(self.date,relief=RIDGE,padding=(10,15))
        self.framedate.grid(row=0,column=0,stick='n')
 
 
        self.framedelete = ttk.Frame(self.date,relief=RIDGE,padding=(30,15))
        self.framedelete.grid(row=1,column=0,stick='n')
 
       
 
        ttk.Label(self.frameadd, text = 'Enter Path').grid(row=0,column=0,columnspan=2)
        self.callback(1)
 
 
        ttk.Label(self.framedate, text = 'Select Date').grid(row=0,column=0,columnspan=2)
 
 
        ttk.Label(self.framedate, text = 'Enter Date').grid(row=1,column=0)
        day = StringVar()
        Spinbox(self.framedate, from_ = 1, to = 31, textvariable = day).grid(row=1,column=1)
 
 
 
        ttk.Label(self.framedate, text = 'Enter Month').grid(row=2,column=0)
        month = StringVar()
        self.combobox = ttk.Combobox(self.framedate, textvariable = month)
        self.combobox.grid(row=2,column=1)
        self.combobox.config(values = ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                                  'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
 
 
        ttk.Label(self.framedate, text = 'Enter Year').grid(row=3,column=0)
        year = StringVar()
        Spinbox(self.framedate, from_ = 1990, to = 2014, textvariable = year).grid(row=3,column=1)
 
 
 
        choice = StringVar()
        ttk.Label(self.framedelete, text = 'Do you want to delete original Files after compression?').pack()
        ttk.Radiobutton(self.framedelete, text = 'Yes', variable = choice,
                        value = 'Yes').pack()
        ttk.Radiobutton(self.framedelete, text = 'No', variable = choice,
                        value = 'No').pack()
 
 
        ttk.Button(self.date,text="Compress",command=lambda:self.date_hello(day.get(),month.get(),year.get(),choice.get())).grid(row=2,columnspan=2,stick='n')
 
 
 
####################  Create and Fill month tab GUI   ###################################
 
 
        self.frameadd1 = ttk.Frame(self.months,relief=RIDGE,padding=(50,15))
        self.frameadd1.grid(row=0,column=1,rowspan=2,stick='n')
 
        self.framedate1 = ttk.Frame(self.months,relief=RIDGE,padding=(10,15))
        self.framedate1.grid(row=0,column=0,stick='n')
 
        self.framedelete1 = ttk.Frame(self.months,relief=RIDGE,padding=(30,15))
        self.framedelete1.grid(row=1,column=0,stick='n')
 
        ttk.Label(self.frameadd1, text = 'Enter Path').grid(row=0,column=0,columnspan=2)
 
        self.callback1(1)
 
        ttk.Label(self.framedate1, text = 'Select Date').grid(row=0,column=0,columnspan=2)
 
        ttk.Label(self.framedate1, text = 'Enter Month').grid(row=2,column=0)
        monthsa = StringVar()
        self.combobox = ttk.Combobox(self.framedate1, textvariable = monthsa)
        self.combobox.grid(row=2,column=1)
        self.combobox.config(values = ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                                  'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
 
 
 
        ttk.Label(self.framedate1, text = 'Enter Year').grid(row=3,column=0)
        yearsa = StringVar()
        Spinbox(self.framedate1, from_ = 1990, to = 2014, textvariable = yearsa).grid(row=3,column=1)
 
        choices = StringVar()
        ttk.Label(self.framedelete1, text = 'Do you want to delete original Files after compression?').pack()
        ttk.Radiobutton(self.framedelete1, text = 'Yes', variable = choices,
                        value = 'Yes').pack()
        ttk.Radiobutton(self.framedelete1, text = 'No', variable = choices,
                        value = 'No').pack()
 
 
        ttk.Button(self.months,text="Compress",command= lambda: self.month_hello(monthsa.get(),yearsa.get(),choices.get())).grid(row=2,columnspan=2,stick='n')
       
        
 
def main():           
    
    root = Tk()
    compress = Compress(root)
    root.mainloop()
   
if __name__ == "__main__": main()
