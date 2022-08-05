## web scraping: Guide to Web scraping using BeautifulSoup  Python Module.

# Introduction
Data is growing - from 45 zettabytes in 2019 to an estimated 175 zettabytes by 2025 [according to the world in data.](https://ourworldindata.org/internet)
In today's digital landscape, data is termed the most valuable asset in any organization. Most organizations and businesses today,  are data-driven. They heavily rely on data to spearhead crucial business operations.


There are various tools/ methods people/organizations use to acquire data, analyze and proceed to make crucial business decisions. This article will cover one common data acquisition methodology - web scraping.  

## Prerequisites

- Good understanding of Python.

- Good understanding of HTML.

## What we will learn and Do.

- Web scraping. Its definition and Use cases.

- Web scraping implementation using python beautiful soup module. 😊👨‍💻 Its going to be fun, trust me.

- Legal aspects of web scraping.

- Build a simple web scrapper that extracts data from an HTML file.

**Let's get started.**

## What is web scraping?
Web scraping is the process of using programs/scripts written in various programming languages such as python, javascript, Go, Ruby on Rails e.t.c to extract data and content from a website.

A web scrapper extracts the underlying HTML code from a website and with it data stored in a database. With the data and content obtained, the scrapper can replicate the live site.

## Application/ uses-cases of web scraping.
**Note:** There are legal and illegal applications of web scraping. 


**Below are some of the legal applications of web scraping.
**
-  **Website crawling.** Search engine bots crawl a site, analyze its content, and then rank it.

- **Market research. ** Companies use scrapers to pull data from forums and social media (e.g., for sentiment analysis).

- **Acquire product/business info.** Individual businesses deploy bots(web scrapers) to auto-fetch prices and product descriptions for competitors' seller websites.


** Examples of illegal applications of web scraping.**

- Theft of copyrighted content.
- Undercutting of prices.

## Building your own web scraper.

**We are going to build a simple scrapper that extracts data from an HTML file.**

Note - **Spoiler Alert**: When I was learning about web scraping, at first I thought it was going to be hard and a little complicated. However, when I learned it I realized how easy it is to implement it.

 > Trust me, its going to be fun.😊👨‍💻

For our web scraper, we are going to implement it using **python** however, its worth noting that you can implement the concept using other programming languages such as javascript or Java. 

> I found this interesting [article](https://geekflare.com/web-scraping-in-javascript/#:~:text=You%20are%20going%20to%20learn,we%20want%20from%20the%20data.) that implements it using javascript. You can look it up

## Project setup.
### Step 1
- Create a new folder on your pc and name it: Web scraping project.

- Open your IDE and open the project folder and create two files: an HTML file, save it as **scrapper.html**, and a **main.py file**.

### Step 2
Open your scrapper.html file and write the following code. 

```
<!DOCTYPE html>
<html>

<head>
	<meta charset="utf-8">
	<title> Personal Site</title>
</head>

<body>
	<h1 id="name">Code Bytes</h1>
	<p><em>Founder of <strong><a href="https://www.app.co/">The AppCo.</a></strong>.</em></p>
	<p>I am Web Developer. I ❤️ coffee and motorcycles.</p>
	<hr>
	<h3 class="heading">Books I am reading</h3>
	<ul>
		<li>Cracking the coding interview👨‍💻</li>
		<li>Growth and career advancement📖</li>
		<li>Obama and Kenya.</li>
	</ul>
	<hr>
	<h3 class="heading">Other Pages</h3>
	<a href="https://unsplash.com/s/photos/cars">My car pics</a>
</body>

</html>
``` 
### Step 3.
**The scraper**

Python has an inbuilt module/library called Beautiful soup. The Library contains methods/functions that will help you pull data out of HTML and XML files. It works with a parser to provide idiomatic ways of navigating, searching, and modifying the parse tree. 

For more info on beautiful soup, you can read the [official documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/).

There are a number of functions associated with the beautiful soup library. However, for this tutorial, we are going to cover a few common ones that allow you to scrap any website for data. 

**Steps
**
- Open your main.py file and write the following code.

- Import the beautiful soup library into your project.

```
from bs4 import BeautifulSoup
``` 
> The code above allows you to import the latest version of the beautiful soup library - version 4. 
Bs4 - the library itself houses BeautifulSoup class that has all the methods associated with web scraping. 

```
with open("website.html", encoding="utf8") as file:
    html_content = file.read()

``` 
>  The code above allows you to open the scrapper.html file and read its contents in your main.py file.

Once the import is done, we can proceed to create the scrapper object from the beautiful soup class.

Write the following code.

```
soup = BeautifulSoup(html_content, "html.parser")
``` 
> Remember at the very top we read the scrapper.html file and saved it as html_content. 
We are going to call the Beautifulsoup class, create an object and name it soup. We will parse the html_content we read and an HTML parser as shown above. 

> The HTML parser works by acquiring HTML data and then calling the handler methods when start tags, end tags, text, comments, and other markup elements are encountered. 

**And finally, we can now manipulate the HTML content to obtain various data.**
For instance, we can print out the object soup to view its contents in our python code.

```
print(soup)
``` 
> We get.


![scrapper.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1659689333394/acIJThyF0.jpg align="left")


**And that's it we officially have our scrapper up and running**💯😊🎂

There are a number of functions associated with the beautiful soup library such as:

- Prettify method idents the HTML code for clarity
```
print(soup.prettify())
```

- find_all() method returns a list of all the elements that match the tag

```
print(soup.find_all("p"))
```

- tag.get_text() method returns the text inside the tag.

```
tag.get_text() 
``` 

- tag.get("class/id/href/src/alt") returns the value of the attribute.

```
tag.get("class")
``` 

- soup.select_one("tag") returns the first element that matches the tag

```
soup.select_one("p")
``` 

- soup.select("tag") returns a list of all the elements that match the tag.

```
soup.select("p")
``` 

The above are among the common methods you can mess around with to obtain whichever data from a website you want.

**Take a quick look at the beautiful soup docs to learn more.
**

## The Legal Aspects of Web scraping.

Web scraping can be fun however there are limitations. 

**Not all live sites can be scrapped.** 

Remember data is a crucial aspect of any organization. It's the basis of any operations. Organizations, therefore, take measures to protect their intellectual property - basically their data.

Any practice to obtain their data in an unauthorized manner is termed a criminal offense.

** Which sites can be scraped?**

Any website that presents its data without necessitating a sign-up /  a log-in. For instance  [hackernews.](https://news.ycombinator.com/). You can scrape this site to obtain info on the latest tech news.

## Conclusion. 
We have covered quite interesting topics with this article, including: 

- What is a web scraping and its applications.

- Building a simple web scrapper with python's beautiful soup library.

- Methods associated with beautiful soup library. 

- And the legal and illegal aspects of web scraping.


Feel free to explore further on various use cases of web scraping by building your own bot to scrape data on e. g. the latest crypto data on price movements.

And it's a wrap, thank you so much for making it this far.😊

Happy coding.👨‍💻💡





















 
















