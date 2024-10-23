# Creating Table
### models.py (APP)
```python
from django.db import models
from django.utils import timezone

# Create your models here.
class students(models.Model):
    BRANCH_CHOICE = [
        ('CS', 'Computer Science'),
        ('AI', 'Artificial Intelligence'),
        ('DS', 'Data Science'),
    ]
    name = models.CharField(max_length=100)
    image = models.ImageField(upload_to='images/')
    data_time = models.DateTimeField(default= timezone.now)
    branch = models.CharField(max_length=2, choices=BRANCH_CHOICE)
```
### Admin.py (APP)
```python
from django.contrib import admin
from .models import students

# Register your models here.
admin.site.register(students)
```
### Settings.py(PROJECT_APP)
```python
import os

STATIC_URL = 'static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR,'static')]

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR,'media')
```
### Urls.py (PROJECT_APP)
```python

from django.contrib import admin
from django.urls import path, include
from django.conf import settings
from django.conf.urls.static import static
from . import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home),
    path('technology/', include('technology.urls')),

    
    path("__reload__/", include("django_browser_reload.urls")),

] + static(settings.MEDIA_URL, document_root = settings.MEDIA_ROOT)
```
## Now Terminals Commands For It
```bash
python manage.py makemigrations APP_NAME
```
```bash
python manage.py migrate
```
```bash
python manage.py runserver
```
