
# Creating Another App in It
```bash
python manage.py startapp APP_NAME
```
## Setuping New App
### Settings.py (FIRST_APP)
```python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'APP_NAME',
]
```
### Urls.py (FIRST_APP)
```python
from django.contrib import admin
from django.urls import path, include
from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home),
    path('about/', views.about),
    path('APP_URL/', include('APP_NAME.urls')), # Transfering Control
]
```
### Urls.py (NEW_APP)
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.FUNCTION_NAME)
]
```
### Views.py (NEW_APP)
```python
from django.shortcuts import render

def FUNCTION_NAME(request):
    return render(request, 'index.html')
```
