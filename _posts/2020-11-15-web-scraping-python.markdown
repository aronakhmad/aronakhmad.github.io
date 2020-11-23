---
title:  "Web Scraping with Python"
subtitle: "Website is one of data resources. you can get informations from there. In this article you'll find out how to create an automated web scraper using Python."
author: "Aron Akhmad"
avatar: "img/authors/cat.jpeg"
image: "img/web_scraping_python.jpg"
date:   2020-11-15
---

The internet is evolving so fast and massively since the past years. The amount of internet users is increasing every day. There are tons of data created each day and it makes data become a thing nowadays. Data analytics is an important role now in many fields. In a company, for example, many companies demanding data analytics to make certain decisions the company makes, like pricing. A company needs to put a reasonable price for the product and sometimes they need to compare the price from its competitors. They could collect the competitors’ pricing data from websites, and that is where web scraping is spot-on at. Web Scraping is one of the scraping methods that you can choose to collect data from websites. However, here you will learn how to build an automated web scraper with Python. This method will absolutely ease your work to gather information from websites as it is automated. Okay, enough chit chat. Get ready for it cause we’re about to start learning now!

## What is web scraping?

Web scraping is a process where you collect or gather information from the internet (websites). There are several methods of web scraping, from the naive copy-paste method to the more advanced one with the automated method. Web scraping is becoming more popular nowadays as the internet is becoming more massive too. There is a lot of information that we could get from the internet. People often gathering information from it for certain purposes, i.e. research or analysis. In this article, we will learn how to scrape and collect data from websites.

## Why scrape the web?

Sometimes we face some situations where we need to surf the web back and forth to get information from it as much as we can -- for example; buying something from an online marketplace. When we're doing it we usually scan every price and other details from the posted products as we're looking for the most suitable product for us. In this case, it’s kind of inefficient to scan the web manually. Now that technology has evolved enormously, why don’t we use it to ease our work? Hold on a sec! You're about to know how to build an automated web scraper with Python. Keep scrolling down!

In order to build an automated web scraper, you need to follow the steps below. There are several steps to do it:

## Step 1: Inspect the Website
Open the website that you desire to scrape from your favorite browser. Take a glimpse and try to analyze the structure of the website, then go to developer tools of your web browser. This one below is a picture of how you get into developer tools using Google Chrome.

<img src="img/developer_tools.png" width="100%" height="100%" align='center'/>

Once you clicked the developer tools, the web inspector will be opened alongside the website you’re opening like this picture below.

<img src="img/web_inspector.png" width="100%" height="100%" align='center'/>
 
Scan through the HTML code to find the elements that represent the data that you want to scrape from the website. You can hover every line of the code to find it as the browser will highlight the website's element that represents the code you’re hovering to. Once you found it, take a sign on it as you will use it for the next step on your code.

## Step 2: Scrape the Website using Selenium
Now, you can start coding to scrape the website. In this article, we will do it using Python, and the library that we will be using to scrape the website is Selenium. If you haven’t installed the library yet, you can install it first using pip command.

```
pip install selenium
```

Once it’s installed, now we can use it to scrape the website you desire. But before doing that, you need to make sure that you have placed a browser driver on your computer. A browser driver is a driver that is exclusively used and controlled by selenium for scrapping purposes using a particular browser. You can look it up on the internet about how to install a browser driver on your computer but if you’re using Chrome, you can download ChromeDriver **[here](https://chromedriver.chromium.org/)**.

Now that you are set, you can start using the selenium library on the code for scraping. Here is how you set your web scraper using selenium and ChromeDriver. Note that you can adjust the code below depending on what kind of browser driver you’re using.

```
from selenium import webdriver as wd

driver = wd.Chrome('path to your webdriver')
link = "the website link"
driver.get(link)
content = driver.page_source
```

## Step 3: Parse the HTML code using BeautifulSoup4
Once you have scraped the web, now you need to highlight the information that you want to collect using the HTML tags you have got earlier in step 1. Note that selenium will return the HTML code and you will never store the HTML code as it’s messy and hard to read. You need to translate the HTML code, and this is where you need the BeautifulSoup4 library on your code. This library will parse the HTML code and return the information you need in text or string. If you haven’t installed this library yet, you can easily get one by executing this command below.

```
pip install beautifulsoup4
```

Now that it’s installed, you can now start using it to parse the HTML code. You can use the `find` function to find a specific HTML code. Specify the HTML code you want to get by providing the HTML tag for the function parameter. The code below is an example of how.

```
from bs4 import BeautifulSoup

soup = BeautifulSoup(content)
example = soup.find(id = 'someHTML-ID')
```

If you want to scrape more data, you can use the `findall` function and it will return an iterable object that you can scrape information from. Keep in mind that the returned value is an object, so you need to do iteration and specify some specific information later on. You can get the text value from any specific tag with `object.text`. The code below is an example of how.

```
x = soup.findall('div', attrs={'class':'someHTML-Class'})
info_data = []
for i in x:
    info1 = x.find('span', attrs={'class':'someClass1'}))
    info2 = x.find('div', attrs={'class':'someClass2'}))
    info3 = x.find('span', attrs={'class':'someClass3'}))
    info_data.apppend([info1, info2, info3])
```

Now that you have reached this part of the article, roughly speaking we can say that you have known how to scrape data from the web. You have learned how to search HTML element that contains the information you want to scrape by scanning the browser web inspector tools, how to scrape and get the website HTML code using selenium, and how to parse the HTML code to get the actual information using beautifulsoup4. You can take advantage of those and scrape the web. The program code might be slightly different depending on the website you desire to scrape, but if you want to know the actual example, you can visit my web scraping code on my GitHub repo **[here](https://github.com/aronakhmad/Web-Scraping-using-Python)**.
