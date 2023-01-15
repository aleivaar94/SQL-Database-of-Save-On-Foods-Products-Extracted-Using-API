![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)	![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)

# SQL Database of Save-On-Foods products extracted using API

![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/save-on-foods-logo.png)

In today’s society data is the new gold, and the web is the doorway to get it. However, not all this data can be easily downloaded for analysis. This is where web scrapping comes in.

Web scrapping aka web data extraction is used for extracting data from websites. Various Python libraries such as [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), [Selenium](https://www.selenium.dev/documentation/) and [Scrapy](https://scrapy.org/) are used to extract data from a website. One of the most efficient and simple methods to extract data from a website is by accessing and requesting it’s API.

API or Application Programming Interface is a set of definitions and protocols that allows applications to communicate between each other. Each time you interact with The Weather Network you are communicating with their servers to get the forecast for the next 7 days, for examples. Or in this case, to search for specific grocery items in the Save-On-Foods website.

In this project, I extract products from Save-On-Foods website and store it in SQL database.

## Demo
![demo](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/code-scrapping-API-gif.gif)



## Methodology

I used the chrome developer tool to see the network requests. The API usually appears after clicking the next page result at the bottom of the webpage. 

![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/identify-API.png)

<sub><sup>Identifying the Save-On-Foods API by clicking the next page resulst and seeing the ouput in the Network tab of Chrome developer tools.</sup></sub>

The API can be identified by clicking the `Response` tab in chrome developer tools - a json format output containing the products displayed in the webpage appears.

![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/response-API.gif)

<sub><sup>Identifying the Save-On-Foods API using the output in the Response tab in the Chrome developer tools.</sup></sub>

Once the API is identified, the response is copied as cURL (bash) and pasted in Postman API platform to generate the Python Request. The Python Request can be copy and pasted in the coding environment.

![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/copy-API-response.png)

<sub><sup>Copying the API response.</sup></sub>


![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/postman-API.png)

<sub><sup>Generating the Python request code to make request to the the API and extract its data.</sup></sub>


The API output is in JSON, therefore, it’s useful to use a JSON formatter to understand the hierarchy or nesting to extract the data of interest.

![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/json-formatter.png)

It’s important to consider pagination, or how the API request will “scroll” through the data. A pattern is identified in the requests, in which the skip  parameter has to increment by the amount set in the take parameter. This is accounted in the scrapping code.

![image](https://github.com/aleivaar94/SQL-Database-of-Save-On-Foods-Products-Extracted-Using-API/blob/master/images/API-pagination.png)

## Results

A total of 1519 meat products were extracted from the Save-On-Foods website by communicating with it's API.

A function to extract the products with a search term parameter (e.g. meat, plant-based, yogurt) was defined which allows to scrap various items using the same function.

The products are saved in a csv file and a relational database (`save-on-foods-meat-products.csv` and `plant-based-save-on-foods.db`) respectively.