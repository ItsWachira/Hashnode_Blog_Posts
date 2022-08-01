## Local File System And Directories With Python

# INTRODUCTION
Python programming language comes with rich libraries which have different methods that serve different functions. One of the most common functions is the manipulation of the local machine file system.

The standard python library which comes embedded in the python interpreter has a number of inbuilt functions that will allow you to manipulate your local file system with ease. Today, we are going to look at a number of methods associated with local file system manipulation.

## Files
Files are named locations on a disk to store related information. They are used to permanently store data in non-volatile memory (e.g. hard disk).

When we want to read from or write to a file, we need to open it first. When we are done, it needs to be closed so that the resources that are tied with the file are freed.

Hence, in Python, a file operation takes place in the following order:


-Open a file 
- Read or write (perform the operation)
-Close the file

## OPENING A FILE IN PYTHON
To open a file in python, use the method below:
open("file_name.txt") 

The open method takes in the file name as an input.
```
open("my_file.txt")
```
Note: The open command will run in the background. It will not necessarily show you any output on the terminal.

## Reading from a file
Once you have opened a file, the next step would be reading its contents. Python provides a read method that easily allows you to read the contents of an open file.

```
my_file.read()
``` 
## Closing a file
Closing an open file in python after use is mandatory so that the resources(memory, CPU power) are freed from the file.

```
my_file.close()
``` 
## The with keyword
Opening and ultimately closing a file in python can be a tedious procedure because of how repetitive it is. In order to improve the procedure, python allows us to use the keyword to open a file and perform all the actions required without worrying about closing the file at the very end. The with method covers the closing operation.
The syntax.

```
with open("my_file.txt") as new_file:
     file_content = new_file.read()
``` 
> The code above opens my_file,  reads its contents, and saves them in a variable called file_content.

The with method takes up the file name as an input and assigns a variable name "as variable_name" that allows us to easily reference the file.

In addition, the with keyword takes up another input called mode which specifies the kind of operation that will occur on the file. The most common operations are reading and writing.


```
with open("new_file.txt", mode="w") as file:
    file.write("doctor")
    print(content)

``` 
> The code above opens a new_file.txt and writes the name doctor.

# FILE PATHS AND DIRECTORIES 
Manipulating file paths and directories in python utilizes two file path directions:

- The absolute file path.

- The relative file path.

The two file paths are almost similar however they have very distinctive differences.
The absolute file path opens files/folders relative to the root directory which in most machines is the C drive. 
An example :
> C:\Users\user_name\python_Project\files_project\my_file.txt

The relative file path on the other hand opens files/folders relative to the current working directory. Meaning the file specified should be conscious of the current directory we are in.
An example :

> ..\Input\Letters\starting_letter.txt

















