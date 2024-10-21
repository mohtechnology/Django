
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
