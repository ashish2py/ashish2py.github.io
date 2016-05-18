---
layout: article
title:  "Twitter bot to win an Amazon #AWSomeday T-Shirt!"
date:   2016-03-10 22:28:32 +0530
categories: blog post
author : Ashish T.
---
# Why?
Today morning around 4am, when I was working on some stuff then I thought about twitting something but I dont wanted to tweet from the twitter Page. Instead, I wanted to tweet from terminal where I was doing other programming stuffs... So I decided to write a python-script to Post a tweet from my Terminal .
So I googled about "tweet from python" and I came across python-twitter and I started following Wiki for implementing that thing .
Steps that need to be followed are as follows

# App registration on Twitter
Set your application's "Access level : Read, write, and direct messages "
Otherwise you will get an error for "Access level : Read Only"(TwitterError: Read-only application cannot POST.)

# Authentication
Copy your authentication credentials and paste on some TextEditor, for e.g.

```
consumer_key = 'consumer_key',
consumer_secret = 'consumer_secret',
access_token_key = 'access_token_key',
access_token_secret = 'access_token_secret'
```

# Dependencies Installation ( Python-Twitter )

Make sure that you have first two libraries installed in your system.

* [SimpleJSON](http://cheeseshop.python.org/pypi/simplejson) - simplejson is a simple, fast, complete, correct and extensible JSON
* [PythonOAUTh2](http://github.com/simplegeo/python-oauth2) - To create OAuth clients and servers.
* [HTTPLib2](http://code.google.com/p/httplib2/) - A comprehensive HTTP client library!
* [PythonTwitter](http://code.google.com/p/python-twitter/) - A Python wrapper around the Twitter API.

Install each library either using *pip install -package_name-* or by the below method.
```
python setup.py build && python setup.py install
```

# Write down program
create a python file and write the below code in it.


```
import twitter
import time
api  = twitter.Api()
def tweet(tweet_status):
	status = api.PostUpdate(tweet_status)

api = twitter.Api(
    consumer_key = '--your-key',
    consumer_secret = '--your-secret-key--',
    access_token_key = '--your-token-key--',
    access_token_secret = '--your-toeken-secret--'
)

tweet_list = ['#AWSomeday','#AmazonDynamoDB','#AmazonS3',
    '#AmazonGlacier','#Amazon #IMBreakingCloud']

for x in range(200):
    for m in tweet_list:
        tweet_status = "With these services "+"#"+str(x)+" "+m+"#AWSomeday"            
        time.sleep(2)
        tweet(tweet_status)
```

That's it!!
Now run this file with python
```
python filename.py
```
