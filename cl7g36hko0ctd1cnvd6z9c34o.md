## RESTful API: Build a Nodejs RESTful API with Express and SQLite3

# Introduction
## What is REST
**REST **stands for **Re**presentation **S**tate **T**ransfer. An architectural design pattern that simplifies the communication between computer systems. Software systems that are REST compliant are also called REStful systems. They are **stateless **and **separate the concern **of the client and the server in an HTTP communication protocol.

### Separation of Client & Server

The development of the client and server can take place independently. We don’t have to bother while changing how each side work. Until and unless both sides know which format of the message to send, which is understood by the other side, they can be developed independently.

### Statelessness

The client and Server don’t have to know the state of the other side while communicating. They can understand each other messages without knowing anything about each other.

 For more info on this, you can look up [restfulapi. net](https://restfulapi.net/statelessness/).

## What is CRUD?
When we build API, we define four basic functionalities namely:

- Create. 

- Read

-  Update.

- Delete.


The CRUD paradigm is common in constructing web applications because it provides a common framework and design pattern that can easily be replicated by developers in constructing performant and usable  API models.

**REST & CRUD Together**
In the REST API, each verb in CRUD relates to a specific HTTP method.

> Create— **POST**

> Read— **GET**

> Update— **PUT**

> Delete—** Delete**

The above four are the basic building blocks for a performant backend service.

## Setting Up Database and Initial NodeJs File
Create a project folder on your machine.
On your terminal, type > npm init to set up the project with basic details. 

Run the below command inside the folder.


```
npm install sqlite3 --save
npm install express --save 

```

Create a new file in the project folder and name it **restwithnodejs.js** and write the code below:


```
const sqlite3 = require('sqlite3');
const express = require("express");
var app = express();

const HTTP_PORT = 8000
app.listen(HTTP_PORT, () => {
    console.log("Server is listening on port " + HTTP_PORT);
});

const db = new sqlite3.Database('./emp_database.db', (err) => {
    if (err) {
        console.error("Erro opening database " + err.message);
    } else {

        db.run('CREATE TABLE employees( \
            employee_id INTEGER PRIMARY KEY AUTOINCREMENT NOT NULL,\
            last_name NVARCHAR(20)  NOT NULL,\
            first_name NVARCHAR(20)  NOT NULL,\
            title NVARCHAR(20),\
            address NVARCHAR(100),\
            country_code INTEGER\
        )', (err) => {
            if (err) {
                console.log("Table already exists.");
            }
            let insert = 'INSERT INTO employees (last_name, first_name, title, address, country_code) VALUES (?,?,?,?,?)';
            db.run(insert, ["John", "James", "JJ", "Kenya", 100]);
            db.run(insert, ["Simon", "King", "SK", "South Africa", 155]);
            db.run(insert, ["Bernard", "Blinder", "BB", "UK", 005]);
        });
    }
});
``` 

> Run the file.
> It will start the server on port 8000. It will also create the employee table and insert some sample records into the database.

 ## HTTP methods
### GET request

```
app.get("/employees/:id", (req, res, next) => {
    var params = [req.params.id]
    db.get(`SELECT * FROM employees where employee_id = ?`, [req.params.id], (err, row) => {
        if (err) {
          res.status(400).json({"error":err.message});
          return;
        }
        res.status(200).json(row);
      });
});
``` 
### POST request
After getting an employee by id, we need something by which we can insert an employee


```
app.post("/employees/", (req, res, next) => {
    var reqBody = re.body;
    db.run(`INSERT INTO employees (last_name, first_name, title, address, country_code) VALUES (?,?,?,?,?)`,
        [reqBody.last_name, reqBody.first_name, reqBody.title, reqBody.address, reqBody.country_code],
        function (err, result) {
            if (err) {
                res.status(400).json({ "error": err.message })
                return;
            }
            res.status(201).json({
                "employee_id": this.lastID
            })
        });
});
``` 

### PUT request
Now suppose we want to update the existing employee.

```
app.patch("/employees/", (req, res, next) => {
    var reqBody = re.body;
    db.run(`UPDATE employees set last_name = ?, first_name = ?, title = ?, address = ?, country_code = ? WHERE employee_id = ?`,
        [reqBody.last_name, reqBody.first_name, reqBody.title, reqBody.address, reqBody.country_code, reqBody.employee_id],
        function (err, result) {
            if (err) {
                res.status(400).json({ "error": res.message })
                return;
            }
            res.status(200).json({ updatedID: this.changes });
        });
});
``` 

And this basically it.  You can run the code on [postman](https://www.postman.com/)
to test the functionality of the API.


**---**
## Conclusion
In this post, we learned about building a basic RestFul API with express and SQLite3. I hope this post, will help you to design a great RESTful API.

Where do I go from here? Well, you can build a client-side using a frontend framework that implements the CRUD functionality which consumes the API. I will leave this to you as a challenge, have fun.

Happy coding.👨‍💻😊











