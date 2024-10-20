# Django
# Create Django App
```bash
django-admin startproject PROJECT_NAME
```
# Run Server
```bash
python manage.py runserver
```
#### Port Changing
* Default Port 8000
```bash
python manage.py runserver 8001
```
---------------------------------------------------
---------------------------------------------------
# Rendering HTML Text Only
## View.py 
```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello World")

def about(request):
    return HttpResponse("Hello About")
```

## Urls.py
```python
from django.contrib import admin
from django.urls import path
from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home),
    path('about/', views.about),
]
```
------------------------------------------------
------------------------------------------------
# Rendering Templates
## Setting.py
```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ['templates'], # Adding Templates Folder Here
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```
## Views.py
```bash
from django.shortcuts import render

def home(request):
    return render(request, 'index.html')

def about(request):
    return render(request, 'about.html')
```
----------------------------------------
----------------------------------------
# Linking Static Files
## Setting.py
```python
import os

STATIC_URL = 'static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR,'static')]
```
## index.html
```html
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="{% static "style.css" %}">
</head>
<body>
    <h1>Hello World</h1>
</body>
</html>
```
----------------------------------------
----------------------------------------
# File Organization in Django
```bash
my_project/
├── manage.py
├── my_project/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
├── file_manager/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── migrations/
│   ├── models.py
│   ├── templates/
│   │   └── file_manager/
│   │       ├── upload.html
│   │       └── file_list.html
│   ├── urls.py
│   ├── views.py
├── media/
│   └── files/
└── static/
```
------------------------------------------
------------------------------------------

