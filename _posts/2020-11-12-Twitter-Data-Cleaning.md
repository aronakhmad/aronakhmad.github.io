---
layout: post
title: Twitter Data Cleaning
subheading: Twitter data contains a bunch of attributes, such as tweets, accounts, dates, and etc. Most likely, Twitter data contains unnecessary things that need to be cleaned. But how could you clean Twitter data? Well, scroll down to find the answer! 😚
author: Aron Akhmad
categories: Data Cleaning
banner: https://www.bbva.com/wp-content/uploads/en/2017/07/A-2807-Twitter-BBVA-1024x416.jpg
---

**Twitter** is one of the most used data sources for data analysis. The reason is that it’s open and free to collect unless you subscribe to the paid version one. Besides, it’s pretty simple to collect data from it. If you haven’t known how to collect Twitter data using python, you can check my previous post, *teehee*.

Twitter data contains a bunch of information parameters. Sometimes, the data contain unnecessary things that need to be cleaned, such as unnecessary characters, links, newlines, and other kinds of stuff. In this article, I’m going to show you how to clean Twitter data using the python programming language.

Firstly, you need to import the modules needed. We're going to use 4 modules here:
1. Pandas, to open data files and to apply certain operations to the data. 
2. Html, to decode HTML entities into regular characters.
3. Re, to filter and delete unnecessary links, hash, username, punctuations or whatever you wish.
4. Nltk, to clean stopwords.

```python
import pandas as pd
import html
import re
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
```

Secondly, we need to import the Twitter data. in this case, I use CSV Twitter data, you may adjust the code if you use another extension type of file. We’re taking advantage of the pandas library here to import the data.

```python
pd.set_option('display.max_colwidth', None) 
data = pd.read_csv('your_sample.csv')
data.head()
```

Once we have imported the data, we’re now ready for the data cleaning process. The first things that we’re going to clean are data duplicates. Most of the time, we don’t need the data duplicates, because in further use (i.e. analysis) these data duplicates could mess up the result by messing up the measurement.

```python
new_data = data.drop_duplicates('Tweet Content',keep='first') #delete the duplicates by dropping them and store the result value to a new variable
new_data.head()
```

If your data has indices included on it, once you drop those data duplicates, you need to store the new data in a new file. Don’t forget to store the new data to a new file without including the index on it, so that we could explore the data more freely later on.

We’re here assuming that we’re only going to use the tweets data, so we’re going to extract the tweets data out of the file.

```python
new_data.to_csv(r'your_new_sample.csv', index = False)
new_sample = pd.read_csv('your_new_sample.csv')
new_sample.head()
tweets = new_sample['Tweet Content'] 
tweets.head()
```

Once we extracted tweet data, we’ll notice things that need to be cleaned. Most of the time, the tweets data returned by Twitter JSON data contain HTML entities and they need to be decoded into characters. So, we’re cleaning them using html library. Apart from that, we also need to clean up newlines since they make the data messy.

```python
for i in range (len(tweets)):
    x = tweets[i].replace("\n"," ") #cleaning newline "\n" from the tweets
    tweets[i] = html.unescape(x)
tweets.head()
```

Sometimes when tweeting, Twitter users will attach media like pictures, videos, etc. Those media will be converted into links on the JSON data. Since we’re only going to be using the text data, which is the tweets, so we need to clean up the links. Also, we will clean up hash characters (only the hash characters not the whole hashtags) and username. All those things will be cleaned using the regex Python library.

```python
for i in range (len(tweets)):
    tweets[i] = re.sub(r"(@[A-Za-z0-9_]+)|[^\w\s]|#|http\S+", "", tweets[i])
tweets.head()
```

Up till now, we already got much cleaner data, but there is one more thing that we need to do to make it even cleaner. In text-data, mostly it contains insignificant words that are not used for the analysis process because they could mess up the analysis score. So, we’re about to clean them now using the nltk Python library. There are several steps you need to do to remove the stopwords:

-	Preparing stopwords
```python
tweets_to_token = tweets
sw = stopwords.words('english') #you can adjust the language as you desire
sw.remove('not') #we exclude not from the stopwords corpus since removing not from the text will change the context of the text
```

-	Tokenize the tweets
```python
for i in range(len(tweets_to_token)):
    tweets_to_token[i] = word_tokenize(tweets_to_token[i])
```

-	Remove the Stopwords
```python
for i in range(len(tweets_to_token)):
    tweets_to_token[i] = [word for word in tweets_to_token[i] if not word in sw]
tweets_to_token
```
\
\
So, that’s pretty much all about how to clean your Twitter data. I hope it was helpful for you. Thank you guys for reading. Bye for now don’t forget to always to keep an eye on your health. 👋🏻😉

