# Django

## Create Django App
```bash
django-admin startproject PROJECT_NAME
```
## Run Server
```bash
python manage.py runserver
```
#### Port Changing
* Default Port 8000
```bash
python manage.py runserver 8001
```
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
