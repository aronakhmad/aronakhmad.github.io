---
title:  "Collecting Twitter Data using Python"
subtitle: "Twitter data is widely used for analysis. There are lots of insight we could get from it, but how could you actually collect all those Twitter data tho? Click me to find out!"
author: "Aron Akhmad"
avatar: "img/authors/cat.jpeg"
image: "img/Collecting Data using Python.png"
date:   2020-11-10
---

**Twitter** is a microblogging service or also called social media where you can tweet out your thoughts within 280 characters. It is used by 330 million people across the world and there are 500 million tweets sent per day. That means, there are a lot of data we could get too as a data geek, *teehee* 😁. Luckily, Twitter allows us to collect data from it for certain purposes. So, for us who want to do research and need Twitter data for it, we can actually ask Twitter for consent and ultimately get those data through Twitter API. But how could we literally do all that, tho?

To collect Twitter data through Twitter API, we need to apply for permission first. You can look it up on the internet about how to do it, and don’t you worry about it, because trust me it is REALLY simple 😗. You just have to register your regular Twitter account into a Twitter developer account, answer several questions, and *poof!!* you’ll get the credentials in a snap. 

## Import Modules
After you got your own Twitter developer account, the next step you need to do is coding. We’re going to be using Python programming language for this. To scrape the Twitter data, we need tweepy and pandas (optional) libraries. Tweepy library is used to connect to the API and to collect the data we needed, while pandas library is used to store the Twitter data into a file just in case for further use.

```python
import tweepy as tw
import pandas as pd
```

## Define Your Twitter Developer Credentials
In order to connect to Twitter API, we need to define our credentials first. There are 4 credentials you need to define, they are API key, API secret key, access token, and access token key. You can get all those 4 keys from your Twitter developer account page. Once you got the keys, you can put them into the code, like this one below.

```python
api_key = 'YOUR_API_KEY'
api_secret_key = 'YOUR_API_SECRET_KEY'
access_token = 'YOUR_ACCESS_TOKEN'
access_token_secret = 'YOUR_ACCESS_TOKEN_SECRET'

auth = tw.OAuthHandler(api_key, api_secret_key)
auth.set_access_token(access_token, access_token_secret)
api = tw.API(auth, wait_on_rate_limit=True, wait_on_rate_limit_notify=True)
```

## Collect the Data
You are already connected to the Twitter API and now you can scrape data through it. First things first, you need to decide the keyword of the tweet that you want to collect and define other parameters if required. There are a bunch of information parameters that you will get from the JSON data Twitter give you, but in this code, we’re going to extract these parameters:

1. User screen name
2. Tweet
3. Retweets count
4. Likes count
5. Tweet's location
6. Source of Tweet
7. Account's verified status
8. Account's date of creation
9. Profile image attachment
10. Bio attachment
11. Statuses count
12. Followings count
13. Followers count
14. Account's location

And here is the code we need to do that. Note that you can adjust the code depending on your needs.

```python
key_words = "insert your keyword here"

search_result = tw.Cursor(api.search,
              q=key_words,
              lang="id",
              truncated=True).items(10)

crawling_result = [api.get_status(data.id, tweet_mode="extended") for data in search_result]

tweet_list = [[status.user.screen_name, status.full_text, status.retweet_count, status.favorite_count, status.geo, status.source, status.user.verified, status.author.created_at, status.author.default_profile_image, status.author.default_profile, status.user.statuses_count, status.user.friends_count, status.user.followers_count, status.user.location] for status in crawling_result]
```

## Convert the Data into a Pandas Dataframe
Next step, we will convert the data into a pandas data frame. This step is intended to convert the data into a neater and easier to read one. And also, since we’re going to store the data into a file, so we better convert it into a data frame cause the data storing process will be easier by doing so and we’ll get more organized data too.

```python
tweet_df = pd.DataFrame(data = tweet_list, 
                    columns=["username", "tweet", "retweet_count", "like_count", "location", "device", "verified_status", "acc_creation_date","no_profile_pic", "no_bio", "tweets_count", "followings_count", "followers_count", "user_location"])
tweet_df
```

## Store the Dataframe into a File
Last but not least, we’ll be storing the data in a file. In this code, we’re going to store it into a CSV file. You can store it into whatever extension type file by adjusting the code. The storing process is done just in case for further use of the data.

```python
tweet_df.to_csv(r'twitter_data_collection.csv', index=False)
```
\
\
And that was pretty much all about how you collect Twitter data through Twitter API. How was it? It was really simple, right? I hope so, *teehee*. I thank you guys for reading this article and I hope it helped you (hopefully lol). Bye for now and take care of your health, guys. 🖤