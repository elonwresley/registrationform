# registrationform
from tkinter import *
import smtplib
import re
linux = Tk()
linux.geometry("400x300")
linux.title("Sign Up Registration Form")
fonti = ("Times", 10,"italic")

##################################################SMTP FORM##########################################
email_dergusi = "spinupdroplet@gmail.com"
passw_dergusi = "undisputed2@"
email_pranusi=""
subjekti = "JCoders Module 1 - SignUp"
mesazhi = "jCoders Module 1 - Basic Python\n\nPas ndjekjes se kursit jCoders,modulit te pare Basic Python erdha ne perfundim te ketij programi te quajtur Sign Up Registration Form.\nTeachers:Fiona Shehu dhe Gzim Mehmeti\nProgram is Created By Andi Gela"
server = smtplib.SMTP('smtp.gmail.com',587)
server.ehlo()
server.starttls()
BODY = '\r\n'.join([
	'To: %s' % email_pranusi,
	'From: %s' % email_dergusi,
	'Subject: %s' % subjekti,'',mesazhi ])



########################################Firstname###########################################################
lblfirstname = Label(linux,fg="red",text="Firstname*",font=fonti).place(x=15,y=5)
entfirstname = Entry(linux)
entfirstname.place(x=15,y=25)
########################################Surname###########################################################
surnamelbl = Label(linux,fg="red",text="Surname*",font=fonti).place(x=200,y=5)
entsurname = Entry(linux)
entsurname.place(x=200,y=25)
########################################Email##########################################################

lblemail = Label(linux,fg="red",text="Your Email*",font=fonti).place(x=15,y=50)
entemail = Entry(linux)
entemail.place(x=15,y=70)
lblemailconfirmation = Label(linux,fg="red",text="Email Confirmation*",font=fonti).place(x=200,y=50)
entemailconfirmation = Entry(linux)
entemailconfirmation.place(x=200,y=70)
########################################Address###########################################################
lbladdress = Label(linux,fg="red",text="Address*",font=fonti).place(x=15,y=93)
entaddress = Entry(linux)
entaddress.place(x=15,y=113)
########################################Zip Code###########################################################


ziplbl = Label(linux,fg="red",text="Zip Code*",font=fonti).place(x=200,y=93)
entzip = Entry(linux)
entzip.place(x=200,y=113)







########################################Password###########################################################
passwordlbl = Label(linux,fg="red",text="Password*",font=fonti).place(x=15,y=134)
entpassword = Entry(linux,show="*")
entpassword.place(x=15,y=155)
lblpasswordconfirmation = Label(linux,fg="red",text="Password Confirmation*",font=fonti).place(x=200,y=131)
entpasswordconfirmation = Entry(linux,show="*")
entpasswordconfirmation.place(x=200,y=155)



def CheckInformation():
	global email_dergusi
	global email_pranusi
	email_pranusi=entemail.get() and entemailconfirmation.get()
	global mesazhi
	print("Firstname :" + entfirstname.get() + "\nSurname :" + entsurname.get() + "\nEmail :"+entemail.get() + "\nEmail Confirmation :"+entemailconfirmation.get()
	+ "\nPassword :"+entpassword.get() + "\nPassword Confirmation :"+entpasswordconfirmation.get() + "\nZip Code :"+entzip.get() + "\nAddress :"+entaddress.get())
	server.login(email_dergusi,passw_dergusi)
	try:
		server.sendmail(email_dergusi,email_pranusi,BODY)
		print('Email Sent Sucessfully')
	except:
		print('Error Sending Email')
	wr = open("simple.txt",'w')
	wr.write("Firstname :" + entfirstname.get() + "\nSurname :" +entsurname.get() + "\nEmail :" +entemail.get() + "\nEmail Confirmation :" +entemailconfirmation.get()
	+ "\nAddress :" +entaddress.get() + "\nZip Code :" +entzip.get() + "\nPassword :" +entpassword.get() + "\nPassword Confirmation :" +entpasswordconfirmation.get())
	wr.close()
	match1 = re.search(r"([\w.-]+@[\w.-]+.\w+)", str(entemail.get()))
	match2 = re.search(r"([\w.-]+@[\w.-]+.\w+)", str(entemailconfirmation.get()))
	#############################perputhja e emailes################################
	if entemail.get() == entemailconfirmation.get():
		print("Email Perputhet")
	else:
		print("Email Nuk Perputhet")

	############################Emaila a eshte Valide?###################################
	if match1:
		print("EMAIL IT'S TRUE")
	else:
		print("Email it's not true")
	if match2:		
		print("EMAIL Confirmation It's True")
	else:
		print("Email Confirmation It's Not True")

	##################################Perputhja e Passwordit##################################
	if entpassword.get() == entpasswordconfirmation.get():
		print("Passwordi Perputhet")
	else:
		print("Passwordi Nuk Perputhet")

	linux.destroy()

btnsubmit = Button(linux,text="Submit",width="5",height="1",command=CheckInformation)
btnsubmit.place(x=171,y=200)







mainloop()

from tkinter import *
linux1=Tk()
linux1.title("Verify Account")
linux1.geometry("400x200")
mesazhiderguar = Label(linux1,text="Hello Dear, We sent you an email to verify your account",fg="red").place(x=50,y=65)

mainloop()
