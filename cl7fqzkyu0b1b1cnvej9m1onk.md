## Build a basic RESTful API with Flask-RESTful extension library.

# Introduction
[Flask](https://flask.palletsprojects.com/en/2.0.x/quickstart/) is a micro-framework built using python programming language. 
Flask has a lot of features that allow it to build a backend server with ease. However, flask is lightweight and hence it is suitable for smaller projects. For larger projects with a lot of functionality, features, and users, I would recommend building your backend server with [Django.](https://docs.djangoproject.com/en/4.1/)

In this article, I’ll discuss building a basic RESTful API with Flask framework. 

## What is a RESTful API?
APIs are handy programs that enable two software components to communicate with each other using a set of guidelines and protocols. 

The process of designing is significant because the API design impacts how developers consume it, error prevention, its consistency as well as vital performance metrics. Thus, API design and architecture influence users who make use of it.

APIs are built using different architectures depending on the intended use case. The architectures include:

- REST

- SOAP

- GRAPHQL

**A RESTful API **is an API that abides by the guidelines, processes, and methodology of the REST API architecture. Basically, an API designed and built using the REST architecture.

REST architecture has 5 main methods that are implemented. They include:

- GET method.

- PUT method.

- POST method.

- DELETE method.

- PATCH method.


**Note: ** REST stands for **RE**presentational **S**tate **T**ransfer.

## Building a basic RestFul API with Flask.
**Step 1:** Create a folder on your machine and name it REST-API-project.

 **Step 2:** Open your code editor and cd into the project folder created above and create a main.py file.
 
**Step 3**: We'll use virtualenv as our development environment, therefore go ahead and activate it in your project. On your terminal, run this command:

```
virtualenv .

. bin/activate
``` 
**Step4**: let's install flask into our project. On your terminal, run this command:

```
pip install flask-restful
``` 
Flask-restful is an extention of the flask framework that allows us to build REST APIs quickly. Take a look at the official [documentation](https://flask-restful.readthedocs.io/en/latest/) for more information.

**Step5:** Open the main.py file and set up the necessary imports. Write the code below.

```
from flask import Flask
from flask_restful import Resource, Api

app = Flask(__name__)
api = Api(app)

``` 
**Step6:** Set up a basic class that will hold our sample data. However, you can build a database and add sample data to use for this project. 

An example is [SQLite](https://www.sqlite.org/docs.html) Database which comes integrated into the python package.

Write this code:

```
class Quotes(Resource):
    def get(self):
        return {
            'James': {
                'quote': ['Don't talk, write the code.', 
                    ]
            },
            'Linus': {
                'quote': ['Talk is cheap. Show me the code.']
            }

        }
``` 
For POST request: 

```
def post(self):
        parser.add_argument('quote', type=str)
        args = parser.parse_args()

        return {
            'status': True,
            'quote': '{} added. Good'.format(args['quote'])
        }

``` 

In this example, we used static data. As I said you can use your own data from the database you created. 

**Step7: **Now we need to add this class as a resource to the API library wrapper. 


```
api.add_resource(Quotes, '/')

``` 

The complete code: 

```
from flask import Flask
from flask_restful import Resource, Api

app = Flask(__name__)
api = Api(app)

parser = reqparse.RequestParser()

def post(self):
        parser.add_argument('quote', type=str)
        args = parser.parse_args()

        return {
            'status': True,
            'quote': '{} added. Good'.format(args['quote'])
        }

class Quotes(Resource):
    def get(self):
        return {
            'James': {
                'quote': ['Don't talk, write the code.', 
                    ]
            },
            'Linus': {
                'quote': ['Talk is cheap. Show me the code.']
            }

        }
api.add_resource(Quotes, '/')

if __name__ == '__main__':
    app.run(debug=True)
``` 


## What is postman?

![images.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661836078563/U8S6em1wT.png align="center")

[Postman](https://www.postman.com/) is an application that allows us to design, build and test APIs. It has a lot of in-built features that allow developers to build production-ready APIs. Further, postman has an in-built feature that allows us to document our APIs- an essential procedure that makes it easy for other developers to consume the APIs we build with ease.

For this tutorial, we are going to test the API built using postman. I have already signed up, so I am going straight to testing. 

Above code, we created a method named **POST** for HTTP POST requests. 
Let’s try a simple HTTP Post request with the Postman:

![wrhocz6jvjdpwknavbqg.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661836909181/TnDxCjDVK.png align="center")



***
## Conclusion
In this post, we learned about building a basic RestFul API with Flask. I hope this post, will help you to design a great RESTful API.

Where do I go from here? Well, there are a lot more ways we could improve our current API; you could add bonus routes like PUT, UPDATE  and  DELETE. I will leave this to you as a challenge, have fun.

Happy coding.👨‍💻😊


























