## DJANGO BOILERPLATE

![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSeNhAb4isYY-lAJmAqa7eJ21Tz52Wo9Y7QvQ&usqp=CAU)

In this project i created a boilerplate to build the skeleton of a simple web page using `DJANGO` framework in python language.

Let´s follow those simple steps to build it:

`1)` First, we want to install Python on our machine. We can download it from the [official Python website](https://www.python.org/). Choose the package for your machine ie, if you’re on Windows, use the Windows installation package.

Then we install the Django software using the command 

`pip install Django`.

`2)` After making sure our software is installed properly on our machine, we navigate into the directory we want to create our project in. I am creating my project on my desktop so I can see the folder displayed on my desktop. For this tutorial, we will name our project folder `djangoboilerplate`. To create the folder, we type the command:

`django-admin startproject djangoboilerplate`

`3)` We then navigate into our project directory. As we can see, there are 4 main files; `settings.py, wsgi.py, urls.py, and asgi.py`. The most important file in this folder will be our `settings.py` file because this is where we will be installing our app. Type those commands from project´s main folder. 

`cd djangoboilerplate`

`ls`

`4)` In our project directory (djangoboilerplate), we will create our application by running the following command in our CL, the app name is `portfolio`:

`python3 manage.py startapp portfolio`

`5)` We then run a command to start our server:

`python3 manage.py runserver`

Don´t worry for the warning messages, it´s normal because you didn´t aply the migrations yet, we will cover it later.

`6)` Now our app is running!, now le´ts install it  in the `settings.py` file located in our project directory (djangoboilerplate). We should install the app in the INSTALLED_APPS object list:

````
# Application definition

...
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'portfolio',
]
...
````
`7)` It's time to create our views. For this tutorial, we will be create function-based views. Our function will return a `HttpResponse`. For this to happen, we must first import the HTTP module into our `portfolio` folder `views.py` file:

````
from django.shortcuts import render
from django.http import HttpResponse
# Create your views here.
def home(request):
    return HttpResponse("My first Django Website")
````

`8)` Create a `urls.py` file within our `portfolio` folder. After that, we will import the path module and our views. Create a list object called `urlpatterns` and define our path:

````
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name = 'home'),
]
````
`9)` In our `urls.py` file located in our project directory `djangoboilerplate`, let’s import our included module, we will then use the include module to include the `urls.py` file from our app:

````
"""djangoboilerplate URL Configuration

The `urlpatterns` list routes URLs to views. For more information please see:
    https://docs.djangoproject.com/en/dev/topics/http/urls/
Examples:
Function views
    1. Add an import:  from my_app import views
    2. Add a URL to urlpatterns:  path('', views.home, name='home')
Class-based views
    1. Add an import:  from other_app.views import Home
    2. Add a URL to urlpatterns:  path('', Home.as_view(), name='home')
Including another URLconf
    1. Import the include() function: from django.urls import include, path
    2. Add a URL to urlpatterns:  path('blog/', include('blog.urls'))
"""
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('portfolio.urls')),
]

````
`10)` Now let´s run `python3 manage.py runserver` to start the server and open it in your favorite browser, Voalá! you got your first web made with `DJANGO` framework!

![image](https://miro.medium.com/max/1400/1*1SFCtupjZNIVXXztBbm2Gg.png)

