---
layout: blog-post
title:  "Using Django As A Microframework, Like Flask."
date:   2016-02-10
categories: blog post
tags: python
author : Ashish T.
author: Ashish Tiwari
author_pic: https://media.licdn.com/mpr/mpr/shrinknp_400_400/AAEAAQAAAAAAAArKAAAAJDI4ODViNjRjLTE4Y2EtNGMwOC04ZjBlLTM1NmY4YzQ4Y2E2Mg.jpg
author_web: www.ashishtiwari.me
author_info: Web, Android, ETL and Python Developer
img: https://lh3.googleusercontent.com/ooj7qZwl58-kAhdyjAR5fjyw9BrFKffVcWOEpRVFuG73pLO8WOWaNvXu43fgRWWSK4Qa0Oc19EaO9gOfHteJHErRE1epH42hP4sGsWQb4J8UCNgDEz_KK89WJ-hZJSib08nXz0cmHfvpCKYykRTQW8Q90EfDGg8G1dD4u9BA-ayT6CvjP9CTC6xbdV_1Kv1NNP548DVdme3YlJJolfrVE7TSkcYenRAxMkeO7EPcuitesHNmIUG9BV481JvkPTZD54T-nEpMfQJPeNiBYNMRKCoA0it6unA1Ua3H8Rx8W3I4jl498HEziiHxxDmvlwCBlPvpbDySjgJFEG-5ctPxX2YYS4V_hQ0ysF9ETg_BTQyP0U-7jWGuIGlJFm-VqyFBsTP3tsVmBs2C0vhY-oqv0cqJMRzZqw1_h8zsKTqARxKYdAPLEMbWGH8LC3Fdk4B4RCRAlkVHnYIsiTKtRL7D_7dPd5X8NRWOkCsjrDpmMUtqBlncOeL-Pcr_NIMRfWgoq-vmPGYZNYkImX1xj06bs9AY-n7J5hGjorQhJqFN6-JbsNi6Mq33UyUyTyeQ_PqtL5FiaNYu1RnRYKpVO5loT7G_trwgW1o=w1024-h644-no
---
Today me and my friend were discussing about **flask** and **django**. We were arguing over flask is microframework and django is not and all other topics related to pros and cons.

I'm not going to start comparing these two great frameworks, but I've created a django-microsite project for a test.

I break down the settings.py, urls.py, views.py in one file. I googled about all these and finally achieved it.

### requirements
* [django](https://www.djangoproject.com/) can be installed by using ```pip install django```

create **django-microsite.py** file.

```
#########################################
# A Pythonic Django Microsite example
# Inspired by Flask and Bottle framework
#########################################

import sys
from django.conf import settings

settings.configure(
 DEBUG=True,
 ROOT_URLCONF = __name__,
 MIDDLEWARE_CLASSES = (
     'django.middleware.common.CommonMiddleware',
     'django.middleware.clickjacking.XFrameOptionsMiddleware',
 ),
)

from django.conf.urls import url
from django.http import HttpResponse
from django.shortcuts import render_to_response

def index(request):
 return HttpResponse("Hey see this! It's working.")

urlpatterns = (
 url(r'^$', index,name="index_page"),
)

if __name__ == "__main__":
 from django.core.management import execute_from_command_line
 execute_from_command_line(sys.argv)
```

You might be thinking, how to run this?

It's a django project :) simply use ```runserver``` command.

```python django-microsite.py runserver```

working code can be found [here](https://github.com/ashish2py/django-microsite).
