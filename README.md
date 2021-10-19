import sys;
import sqlite3; 
import re   

conn=sqlite3.connect("test2.db")

cur=conn.cursor()



class Patient:

    def __init__(self,name,pid,gender,age,doctor):
        self.patient_name = name
        self.pid = pid 
        self.gender = gender 
        self.age = age 
        self.doctor = doctor 
    
    def getpname(self):
        return self.patient_name 

    def getpid(self):
        return self.pid 

    def getgender(self):
        return self.gender 
    
    def getage(self):
        return self.age 
    
    def getdoctor(self):
        return self.doctor 

    def setpname(self):
        self.patient_name = value

    def setpid(self):
        self.pid = value 

    def setgender(self):
        self.gender = value 
    
    def setage(self):
        self.age = value

    def setdoctor(self):
        self.doctor = value 
    
class Doctor:

    def __init__(self,name,doc_id,gender,specialization,age,phone_no):
        self.docname = name 
        self.doc_id = doc_id
        self.specialization = specialization 
        self.gender = gender 
        self.age = age 
        self.phone_no = phone_no 
    
    def getdocname(self):
        return self.docname 

    def getdoc_id(self):
        return self.doc_id

    def getspecialization(self):
        return self.specialization 

    def getgender(self):
        return self.gender 

    def getage(self):
        return self.age 
    
    def getphone(self):
        return self.phone_no

    def setdocname(self):
         self.docname = value  
    
    def setdoc_id(self):
        self.doc_id = value 

    def setspecialization(self):
         self.specialization  = value

    def setgender(self):
         self.gender = value 

    def setage(self):
        self.age = value 
    
    def setphone(self):
        self.phone_no = value 

class main:

    def userChoice(self):
        
        print("******************************")
        print(" Hospital Management System")
        print("******************************")
        print("1. Add New Patient Details")
        print("2. Add New Doctor Details")
     
        print("3. View All Patient Details")
        print("4. View All Doctor Details")
        print("5.Check Bed Availability")

        print("6. Exit")

        n = int(input("Enter your Choice:"))
        if n == 1:
            self.insertPatient() 
        
        elif n == 2:
            self.insertDoctor() 
        
        elif n == 3:
            self. viewPatient()

        elif n == 4:
            self.viewDoctor() 
        
        elif n == 5:
            self.check()

        elif n == 6:
            print("Thank you")
            sys.exit
    
    def insertPatient(self):
    


        name = input("Enter Patient Name:")
        pid = int(input("Enter Patient id:"))
        gender = input("Enter the gender of the patient:")
        if(gender!= "Male" and gender !="Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the patient:"))
        if(age <=0):
            sys.exit("Enter the age of the patient correctly") 
        doctor = input("Enter the name of the doctor who diagnose:")
        pobj = Patient(name, pid, gender, age, doctor)
        conn.execute("insert into Patient values(?,?,?,?,?)", (pobj.getpname(),pobj.getpid(),pobj.getgender(),pobj.getage(),pobj.getdoctor()))
        print("Details are entered")
        


    def insertDoctor(self):


        name1 = input("Enter Doctor's Name:")
        doc_id = int(input("Enter the Doctor's id :"))
        spec = input("Specialization of the doctor:")
        gender = input("Enter the gender of the Doctor:")
        if(gender!="Male" and gender != "Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the doctor:"))
        if(age<=0):
            sys.exit("Enter the age correctly")
        phno = int(input("Enter the phone number:"))
        if(len(str(phno))!=10):
            sys.exit("Invalid Phno")
        dobj = Doctor(name1,doc_id,gender,spec,age,phno)
        conn.execute("insert into Doctor values(?,?,?,?,?,?)",(dobj.getdocname(),dobj.getdoc_id(),dobj.getgender(),dobj.getspecialization(),dobj.getage(),phno))
        print("Details are entered")
    
    def viewPatient(self):

        cur.execute("select * from Patient")
        for n in cur.fetchall():
            print(n)
    
    def viewDoctor(self):
        cur.execute("select * from Doctor")
        for n in cur.fetchall():
            print(n) 

    def check(self):
        no_of_bed = 150 
        count = cur.execute("select count(*) from Patient")
        for i in count:
            if int(i[0])<no_of_bed:
                print(no_of_bed -int(i[0]),"beds are available")
            else:
                print("beds are filled")
            
     
obj = main()
a = True
while(a):
    obj.userChoice()
    b = input("Do you want to continue(y/n):")
    if b == 'n' or b == 'N':
        a = False
import sys;
import sqlite3; 
import re   

conn=sqlite3.connect("test2.db")

cur=conn.cursor()



class Patient:

    def __init__(self,name,pid,gender,age,doctor):
        self.patient_name = name
        self.pid = pid 
        self.gender = gender 
        self.age = age 
        self.doctor = doctor 
    
    def getpname(self):
        return self.patient_name 

    def getpid(self):
        return self.pid 

    def getgender(self):
        return self.gender 
    
    def getage(self):
        return self.age 
    
    def getdoctor(self):
        return self.doctor 

    def setpname(self):
        self.patient_name = value

    def setpid(self):
        self.pid = value 

    def setgender(self):
        self.gender = value 
    
    def setage(self):
        self.age = value

    def setdoctor(self):
        self.doctor = value 
    
class Doctor:

    def __init__(self,name,doc_id,gender,specialization,age,phone_no):
        self.docname = name 
        self.doc_id = doc_id
        self.specialization = specialization 
        self.gender = gender 
        self.age = age 
        self.phone_no = phone_no 
    
    def getdocname(self):
        return self.docname 

    def getdoc_id(self):
        return self.doc_id

    def getspecialization(self):
        return self.specialization 

    def getgender(self):
        return self.gender 

    def getage(self):
        return self.age 
    
    def getphone(self):
        return self.phone_no

    def setdocname(self):
         self.docname = value  
    
    def setdoc_id(self):
        self.doc_id = value 

    def setspecialization(self):
         self.specialization  = value

    def setgender(self):
         self.gender = value 

    def setage(self):
        self.age = value 
    
    def setphone(self):
        self.phone_no = value 

class main:

    def userChoice(self):
        
        print("******************************")
        print(" Hospital Management System")
        print("******************************")
        print("1. Add New Patient Details")
        print("2. Add New Doctor Details")
     
        print("3. View All Patient Details")
        print("4. View All Doctor Details")
        print("5.Check Bed Availability")

        print("6. Exit")

        n = int(input("Enter your Choice:"))
        if n == 1:
            self.insertPatient() 
        
        elif n == 2:
            self.insertDoctor() 
        
        elif n == 3:
            self. viewPatient()

        elif n == 4:
            self.viewDoctor() 
        
        elif n == 5:
            self.check()

        elif n == 6:
            print("Thank you")
            sys.exit
    
    def insertPatient(self):
    


        name = input("Enter Patient Name:")
        pid = int(input("Enter Patient id:"))
        gender = input("Enter the gender of the patient:")
        if(gender!= "Male" and gender !="Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the patient:"))
        if(age <=0):
            sys.exit("Enter the age of the patient correctly") 
        doctor = input("Enter the name of the doctor who diagnose:")
        pobj = Patient(name, pid, gender, age, doctor)
        conn.execute("insert into Patient values(?,?,?,?,?)", (pobj.getpname(),pobj.getpid(),pobj.getgender(),pobj.getage(),pobj.getdoctor()))
        print("Details are entered")
        


    def insertDoctor(self):


        name1 = input("Enter Doctor's Name:")
        doc_id = int(input("Enter the Doctor's id :"))
        spec = input("Specialization of the doctor:")
        gender = input("Enter the gender of the Doctor:")
        if(gender!="Male" and gender != "Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the doctor:"))
        if(age<=0):
            sys.exit("Enter the age correctly")
        phno = int(input("Enter the phone number:"))
        if(len(str(phno))!=10):
            sys.exit("Invalid Phno")
        dobj = Doctor(name1,doc_id,gender,spec,age,phno)
        conn.execute("insert into Doctor values(?,?,?,?,?,?)",(dobj.getdocname(),dobj.getdoc_id(),dobj.getgender(),dobj.getspecialization(),dobj.getage(),phno))
        print("Details are entered")
    
    def viewPatient(self):

        cur.execute("select * from Patient")
        for n in cur.fetchall():
            print(n)
    
    def viewDoctor(self):
        cur.execute("select * from Doctor")
        for n in cur.fetchall():
            print(n) 

    def check(self):
        no_of_bed = 150 
        count = cur.execute("select count(*) from Patient")
        for i in count:
            if int(i[0])<no_of_bed:
                print(no_of_bed -int(i[0]),"beds are available")
            else:
                print("beds are filled")
            
     
obj = main()
a = True
while(a):
    obj.userChoice()
    b = input("Do you want to continue(y/n):")
    if b == 'n' or b == 'N':
        a = False
import sys;
import sqlite3; 
import re   

conn=sqlite3.connect("test2.db")

cur=conn.cursor()



class Patient:

    def __init__(self,name,pid,gender,age,doctor):
        self.patient_name = name
        self.pid = pid 
        self.gender = gender 
        self.age = age 
        self.doctor = doctor 
    
    def getpname(self):
        return self.patient_name 

    def getpid(self):
        return self.pid 

    def getgender(self):
        return self.gender 
    
    def getage(self):
        return self.age 
    
    def getdoctor(self):
        return self.doctor 

    def setpname(self):
        self.patient_name = value

    def setpid(self):
        self.pid = value 

    def setgender(self):
        self.gender = value 
    
    def setage(self):
        self.age = value

    def setdoctor(self):
        self.doctor = value 
    
class Doctor:

    def __init__(self,name,doc_id,gender,specialization,age,phone_no):
        self.docname = name 
        self.doc_id = doc_id
        self.specialization = specialization 
        self.gender = gender 
        self.age = age 
        self.phone_no = phone_no 
    
    def getdocname(self):
        return self.docname 

    def getdoc_id(self):
        return self.doc_id

    def getspecialization(self):
        return self.specialization 

    def getgender(self):
        return self.gender 

    def getage(self):
        return self.age 
    
    def getphone(self):
        return self.phone_no

    def setdocname(self):
         self.docname = value  
    
    def setdoc_id(self):
        self.doc_id = value 

    def setspecialization(self):
         self.specialization  = value

    def setgender(self):
         self.gender = value 

    def setage(self):
        self.age = value 
    
    def setphone(self):
        self.phone_no = value 

class main:

    def userChoice(self):
        
        print("******************************")
        print(" Hospital Management System")
        print("******************************")
        print("1. Add New Patient Details")
        print("2. Add New Doctor Details")
     
        print("3. View All Patient Details")
        print("4. View All Doctor Details")
        print("5.Check Bed Availability")

        print("6. Exit")

        n = int(input("Enter your Choice:"))
        if n == 1:
            self.insertPatient() 
        
        elif n == 2:
            self.insertDoctor() 
        
        elif n == 3:
            self. viewPatient()

        elif n == 4:
            self.viewDoctor() 
        
        elif n == 5:
            self.check()

        elif n == 6:
            print("Thank you")
            sys.exit
    
    def insertPatient(self):
    


        name = input("Enter Patient Name:")
        pid = int(input("Enter Patient id:"))
        gender = input("Enter the gender of the patient:")
        if(gender!= "Male" and gender !="Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the patient:"))
        if(age <=0):
            sys.exit("Enter the age of the patient correctly") 
        doctor = input("Enter the name of the doctor who diagnose:")
        pobj = Patient(name, pid, gender, age, doctor)
        conn.execute("insert into Patient values(?,?,?,?,?)", (pobj.getpname(),pobj.getpid(),pobj.getgender(),pobj.getage(),pobj.getdoctor()))
        print("Details are entered")
        


    def insertDoctor(self):


        name1 = input("Enter Doctor's Name:")
        doc_id = int(input("Enter the Doctor's id :"))
        spec = input("Specialization of the doctor:")
        gender = input("Enter the gender of the Doctor:")
        if(gender!="Male" and gender != "Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the doctor:"))
        if(age<=0):
            sys.exit("Enter the age correctly")
        phno = int(input("Enter the phone number:"))
        if(len(str(phno))!=10):
            sys.exit("Invalid Phno")
        dobj = Doctor(name1,doc_id,gender,spec,age,phno)
        conn.execute("insert into Doctor values(?,?,?,?,?,?)",(dobj.getdocname(),dobj.getdoc_id(),dobj.getgender(),dobj.getspecialization(),dobj.getage(),phno))
        print("Details are entered")
    
    def viewPatient(self):

        cur.execute("select * from Patient")
        for n in cur.fetchall():
            print(n)
    
    def viewDoctor(self):
        cur.execute("select * from Doctor")
        for n in cur.fetchall():
            print(n) 

    def check(self):
        no_of_bed = 150 
        count = cur.execute("select count(*) from Patient")
        for i in count:
            if int(i[0])<no_of_bed:
                print(no_of_bed -int(i[0]),"beds are available")
            else:
                print("beds are filled")
            
     
obj = main()
a = True
while(a):
    obj.userChoice()
    b = input("Do you want to continue(y/n):")
    if b == 'n' or b == 'N':
        a = False
import sys;
import sqlite3; 
import re   

conn=sqlite3.connect("test2.db")

cur=conn.cursor()



class Patient:

    def __init__(self,name,pid,gender,age,doctor):
        self.patient_name = name
        self.pid = pid 
        self.gender = gender 
        self.age = age 
        self.doctor = doctor 
    
    def getpname(self):
        return self.patient_name 

    def getpid(self):
        return self.pid 

    def getgender(self):
        return self.gender 
    
    def getage(self):
        return self.age 
    
    def getdoctor(self):
        return self.doctor 

    def setpname(self):
        self.patient_name = value

    def setpid(self):
        self.pid = value 

    def setgender(self):
        self.gender = value 
    
    def setage(self):
        self.age = value

    def setdoctor(self):
        self.doctor = value 
    
class Doctor:

    def __init__(self,name,doc_id,gender,specialization,age,phone_no):
        self.docname = name 
        self.doc_id = doc_id
        self.specialization = specialization 
        self.gender = gender 
        self.age = age 
        self.phone_no = phone_no 
    
    def getdocname(self):
        return self.docname 

    def getdoc_id(self):
        return self.doc_id

    def getspecialization(self):
        return self.specialization 

    def getgender(self):
        return self.gender 

    def getage(self):
        return self.age 
    
    def getphone(self):
        return self.phone_no

    def setdocname(self):
         self.docname = value  
    
    def setdoc_id(self):
        self.doc_id = value 

    def setspecialization(self):
         self.specialization  = value

    def setgender(self):
         self.gender = value 

    def setage(self):
        self.age = value 
    
    def setphone(self):
        self.phone_no = value 

class main:

    def userChoice(self):
        
        print("******************************")
        print(" Hospital Management System")
        print("******************************")
        print("1. Add New Patient Details")
        print("2. Add New Doctor Details")
     
        print("3. View All Patient Details")
        print("4. View All Doctor Details")
        print("5.Check Bed Availability")

        print("6. Exit")

        n = int(input("Enter your Choice:"))
        if n == 1:
            self.insertPatient() 
        
        elif n == 2:
            self.insertDoctor() 
        
        elif n == 3:
            self. viewPatient()

        elif n == 4:
            self.viewDoctor() 
        
        elif n == 5:
            self.check()

        elif n == 6:
            print("Thank you")
            sys.exit
    
    def insertPatient(self):
    


        name = input("Enter Patient Name:")
        pid = int(input("Enter Patient id:"))
        gender = input("Enter the gender of the patient:")
        if(gender!= "Male" and gender !="Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the patient:"))
        if(age <=0):
            sys.exit("Enter the age of the patient correctly") 
        doctor = input("Enter the name of the doctor who diagnose:")
        pobj = Patient(name, pid, gender, age, doctor)
        conn.execute("insert into Patient values(?,?,?,?,?)", (pobj.getpname(),pobj.getpid(),pobj.getgender(),pobj.getage(),pobj.getdoctor()))
        print("Details are entered")
        


    def insertDoctor(self):


        name1 = input("Enter Doctor's Name:")
        doc_id = int(input("Enter the Doctor's id :"))
        spec = input("Specialization of the doctor:")
        gender = input("Enter the gender of the Doctor:")
        if(gender!="Male" and gender != "Female" and gender!="Transgender"):
            sys.exit("Enter the gender correctly")
        age = int(input("Enter the age of the doctor:"))
        if(age<=0):
            sys.exit("Enter the age correctly")
        phno = int(input("Enter the phone number:"))
        if(len(str(phno))!=10):
            sys.exit("Invalid Phno")
        dobj = Doctor(name1,doc_id,gender,spec,age,phno)
        conn.execute("insert into Doctor values(?,?,?,?,?,?)",(dobj.getdocname(),dobj.getdoc_id(),dobj.getgender(),dobj.getspecialization(),dobj.getage(),phno))
        print("Details are entered")
    
    def viewPatient(self):

        cur.execute("select * from Patient")
        for n in cur.fetchall():
            print(n)
    
    def viewDoctor(self):
        cur.execute("select * from Doctor")
        for n in cur.fetchall():
            print(n) 

    def check(self):
        no_of_bed = 150 
        count = cur.execute("select count(*) from Patient")
        for i in count:
            if int(i[0])<no_of_bed:
                print(no_of_bed -int(i[0]),"beds are available")
            else:
                print("beds are filled")
            
     
obj = main()
a = True
while(a):
    obj.userChoice()
    b = input("Do you want to continue(y/n):")
    if b == 'n' or b == 'N':
        a = False
