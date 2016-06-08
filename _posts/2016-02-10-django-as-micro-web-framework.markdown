---
layout: article
title:  "Using Django As A Microframework, Like Flask."
date:   2016-02-10 22:28:32 +0530
categories: blog post
author : Ashish T.
tags: python django microframework flask code snippet github
---
## #django as microframework

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
 SECRET_KEU='secretkeygoeshere',
 ROOT_URLCONF = __name__,
 MIDDLEWARE_CLASSES = (
     'django.middleware.common.CommonMiddleware',
     'django.middleware.clickjacking.XFrameOptionsMiddleware',
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

#### reference
> * **[django project](https://github.com/ashish2py/django-microsite)**
> * **[django configurations](https://github.com/ashish2py/django-microsite)**
