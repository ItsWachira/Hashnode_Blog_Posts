## How to send emails with python using SMTP

# Introduction
Hello there, 

This tutorial article falls under a series I will be writing on web development using python and javascript. 
Prerequisites:
- Create two new email accounts with whichever email provider- google, yahoo, or Hotmail. I would recommend a google and a yahoo one- there are common obviously.😁😂

- Establish which email will be the sender and which one will be the recipient. For this tutorial article, I will be using a Gmail account as the sending email and a yahoo email as the recipient email.

## How does the email work.
### introduction
Note: There are a number of ways to send emails over the internet using various tools for instance javascript nodemailer,  web APIs services such as formsubmit.co and so much more. However, for this tutorial, we are going to use python and SMTP

Sending and receiving emails on the internet is facilitated by mail servers established by different email providers such as Gmail by google. 

SMTP - Small mail transfer protocol is a set of communication guidelines that allow sending and receiving electronic mails over the internet. The main purpose of SMTP is used to set up communication rules between mail servers. 

![mail.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1655800609216/Syq1iPAaG.jpg align="left")

To put this into context: mail servers are digital post offices, your email account takes up the role of a mailbox and an email protocol takes up the role of a postman.

For this case, we will be using Small Mail Transfer Protocol(SMTP) to send emails and a
Python library called smtplib.

## Setting up
Open your text editor and create a python file - I am using pycharm for this project.
## Step 2
import SMTP library into your project using the command below

```
import smtplib
``` 
## Step 3 - Establish a connection to a mail server.

Assuming you created two new Gmail and yahoo email accounts, create a connection to the Gmail email server by using the code below.

```
connection = smtplib.SMTP("smtp.gmail.com")
``` 
##  Step 4- Create variables to hold your email credentials 

```
my_email = "sampleemail@gmail.com"
my_password = "passwaord"
``` 

## Step 5 - Secure your connection.
It's important that you secure your connection to the Gmail mail servers. Securing your connection to the servers will prevent unauthorized access to your email in the event it's intercepted in transit.

This is done by calling the tls function on your connection. 
```
connection.starttls()
``` 
The tls function is an inbuilt method that encrypts your email data sent via the connection established to email servers. The method is drawn from transport layer security protocol designed to provide communications security over a network.

## Step 6 - log in to your email account 
Run the code below to log in. The log-in method takes two parameters to facilitate a successful log-in: your email and password. Make sure there are no typos on the email and password held on the variables we created earlier. 

```
connection.login(user=my_email, password=my_password)
``` 
## Step 7 - Sending the email. 
We are going to call the sendmail method on our connection. The method takes up 3 parameters : 
                 
- The sending address.

- The recipient's address. ( Avoid typos while typing it out to avoid errors.)

- The message with its subject and its body.
Run the following command.

```
connection.sendmail(from_addr=my_email, to_addrs="receipient_email@yahoo.com", msg=" Subject: My_subject \n\n My message body"
``` 
Note: The subject and the body are separated using back slashes with an n to create new lines between them.

## Step 8 - Close the connction.

Close the connection to the Gmail mail servers.


```
connection.close()
``` 
## Troubleshooting guide.
A few errors might occur after running the code above. It's important that you get to know the type of errors and ways in which you can debug.

- Typo errors. 
Please check on the spellings of which section to make sure no errors don't occur.

- Gmail/yahoo email security. 
Email providers establish critical security measures to prevent any unauthorized access to email accounts. For this reason, there are few security checks that enhance security that are set by default.  
Go to your email settings and check that access by less secure apps option on the security section is turned on. This will allow our program to access your email to send the email.




And we are done.
It's good to note that there are other ways to send emails over the web, this is just one of them, and more precisely using python to accomplish the task. 





























