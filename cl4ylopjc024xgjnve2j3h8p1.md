## Getting started with APIs with python.

# Introduction
Hello,👋


![HelloTherePrivateFromPenguinsOfMadagascarGIF (2).gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1656440654929/3NxEScV4R.gif align="left")

For the last week, I have been diving deep into learning and demystifying APIs, yes with python. There are a couple of lessons I have learned and I will share them below.
 
APIs are important components of any application. They play a crucial role in bridging the gap between a client's front-end and its backend. 

Today, we going to dive deeper into a bit of APIs using python. 

## What is an API?
An API - An Application Programming Interface is a set of commands, 
functions, protocols, and objects that programmers can use to 
create software or interact with an external system.

Think of API as an interface for programs the same way a client UI (User Interface) is an interface for the user. The interface for each case facilitates interactions.

**Examples of API:**
- library API (jQuery, Express, JavaScript).
- Data request API like a Weather condition API and current time API.
 
**To simplify this concept**


Say you were going to a restaurant, 


![TopExcellentGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1656446372035/A2W31KXLj.gif align="left")


we know that there are things that are on the menu like cakes and desert while 
there are raw ingredients in the Kitchen.
The restaurant would not let you go into the Kitchen to eat ingredients since the 
the restaurant has certain things that they sell and lets you buy and there are other things that are off-limits, which is similar to data.

Facebook has data on users while the police API has data on crimes. They all have certain data that they allow you to access and some data that are not your business.

At a restaurant, you are provided with a menu that allows you to choose what you want and what they provide. Assuming you make an order for a particular meal then it's the role of the waiter to deliver the order to the kitchen and once the meal is prepared the waiter has to serve you the meal on your table.


![WinnieThePoohHungryGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1656446324842/FRk0YvBA0.gif align="left")

Similarly, an API for a particular software provides the interface that allows the backend( where the program logic is stored plus the database) to continuously communicate with the client's user interface.

Communication entails allowing the client's UI to make requests to the server for particular data, processing the requests, and serving the responses from the server to the client's UI.

## Getting started with APIs with Python
> Note: For this article, we are going to discuss and interact with external APIs.

Python provides a library called [requests](https://requests.readthedocs.io/en/latest/). that has a tone of functions and modules that will allow you to interact and use external APIs.

### Terms we should know.

**- API Endpoints.**
    An API endpoint, usually a URL, is basically the specific location/ address on the internet where requests made by the client are sent to retrieve the resources that exist at that location.
> An example is: http://api.open-notify.org/iss-now.json
The endpoint above is an endpoint for the International Space Station API.

**- API calls.**
   An API call is a request made to a server to retrieve a set of data. For instance, each time you log in to an application, you make an API call to retrieve your log-in details, authenticate and execute the log-in function. 

There are a number of requests/ calls you can make to a server. The most common are:

- GET request.

- POST request.

- DELETE request.

**- API parameters.**
An API parameter/ parameters are a set of inputs that are parsed while making an API request/call.
The parameters/ inputs allow you to specify the kind of data you want. Basically, the inputs/ parameters you provide allow you to query for specific data.

In python, parameters are wrapped around in a dictionary.


**-  HTTP response Status codes**
HTTP response status codes indicate whether a specific HTTP request has been successfully completed. Responses are grouped into five classes:

- Informational responses (100–199)
- Successful responses (200–299)
- Redirection messages (300–399)
- Client error responses (400–499)
- Server error responses (500–599)


## APIs in python
Now that we know the basics, let's proceed with interacting with external APIs with python code.

> We are going to make a small project as a demonstration.
Getting started with APIs is fun. The simplest external API to test our knowledge in is The International Space Station API. The API is very simple and clear for beginners. Here is the link for the documentation: http://open-notify.org/Open-Notify-API/ISS-Location-Now/

We are going to make a program that gets the real-time location of the ISS. Let's get started.

### Step 1: Setting up
Create a project folder titled API_basics_testing and within it make a python file. Open your code editor and open the project folder created.

### Step 2: Imports
Import the python requests library into your project. Here is the code for that:

```
import requests
``` 
### Step 3: Make requests/ calls.
Remember that we want to get the real-time location of the ISS therefore we need to send requests to the ISS API endpoint where the data is located.

To do that:

```
response = requests.get(url=" http://api.open-notify.org/iss-now.json")
``` 
> What's happening with the code above?

- Initially, we imported the requests library. 
- The library has a get method that allows us to send requests to an API endpoint and get data from the endpoint. The method takes in a URL as an input. The URL is the API endpoint.
- After, making the request, we save the response/results in a variable called response.

```
print(response)
``` 
> Printing the response will print out an HTTP status code of 200 meaning the request made was successful.

![Screenshot 2022-06-28 223119.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1656444720359/jj2_Jj_NJ.jpg align="left")


### Step 4: Getting the data itself.
The requests library has a method called JSON which allows you to retrieve the data obtained. 
JSON - Javascript Object Notation is the format in which data today is passed/ transferred on the internet by different applications. The reason is simply that JSON format bundles up data into small code files that are lightweight which makes them easy to share across the internet. It's the standard format in which each APIs transfer data between different applications.


use the command below.

```
data = response.json()
``` 
You should obtain the following data. 

![Screenshot 2022-06-28 223906.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1656445293980/k2s17_Rtc.jpg align="left")

Notice that the data is in JSON format with key-value pairs similar to how dictionaries hold data. 

The ISS API holds the real-time location of the ISS - The API provides the longitude and latitude of the ISS.

### Obtaining the Latitude and Longitude of the ISS.


```
longitude = data["iss_position"]["longitude"]
latitude = data["iss_position"]["latitude"]
# create a tuple to hold the latitude and longitude
iss_position = (longitude, latitude)
print(iss_position)
``` 

And we are all done,

![JohnWallDanceGIF.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1656445730935/5bWCbuWRK.gif align="left")

now we have the specific location of the International Space Station. You can go to google earth and paste in the latitude and longitude obtained to see the exact location.



## Conclusion.
APIs serve a crucial role in applications wherever data is involved. There is so much to learn about APIs using python. We are not yet done, we are just getting started.
The articles to follow will cover more complex concepts about APIs with Python. 

Happing coding. 
Changing the world one code statement at a time.😊👨‍💻😜

Seeya👋👋


























