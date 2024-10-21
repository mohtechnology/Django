
# TailWind (Node.js Needed)
### Installing TailWind
```bash
pip install django-tailwind
```
### Installing TailWind Reload
```bash
pip install 'django-tailwind[reload]'
```
## Setup
### Settings.py
```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'registration',
    'tailwind'
]
```
## Starting TailWind
```bash
python .\manage.py tailwind init
```
 [1/1] app_name (theme): 
#### Enter tailwind app name(default ='theme')
### Settings.py
```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'registration',
    'tailwind',
    'theme',
]

TAILWIND_APP_NAME = 'theme'
INTERNAL_IPS = ['127.0.0.1']
NPM_BIN_PATH = 'C:\\Program Files\\nodejs\\npm.cmd'
```
## Installing Tailwind CSS
```bash
python manage.py tailwind install
```
## Starting TailWind
* Open Another Terminal
```bash
python manage.py tailwind start
```
## Using TailWind
### layout.html
```html
{% load static tailwind_tags %}
{% load static %}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}{% endblock %}</title>
    <link rel="stylesheet" href="{% static "style.css" %}">
    {% tailwind_css %}
</head>
<body>
    {% block content %}{% endblock %}
</body>
</html>
```
### TailWind HTML File
#### Base.html
```html
{% load static tailwind_tags %}
<!DOCTYPE html>
<html lang="en">
	<head>
    <title>Django Tailwind</title>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		{% tailwind_css %}
	</head>

	<body class="bg-gray-50 font-serif leading-normal tracking-normal">
		<div class="container mx-auto">
			<section class="flex items-center justify-center h-screen">
				<h1 class="text-5xl">Django + Tailwind = ❤️</h1>
			</section>
		</div>
	</body>
</html>
```
### index.html
```html
{% extends "layout.html" %}
{% block title %}Home Page{% endblock %}
{% block content %}
<h1 class='bg-orange-500 text-3xl'>Hello World</h1>
{% endblock %}
```
----------------------------------------
----------------------------------------
# TailWind Reload
### Settings.py
```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'registration',
    'tailwind',
    'theme',
    'django_browser_relaod',
]
MIDDLEWARE = [
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',

    "django_browser_reload.middleware.BrowserReloadMiddleware",
    ]
```
### Urls.py (PROJECT_APP)
```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home),
    path('about/', views.about),
    path('registration/', include('registration.urls')),

    path("__reload__/", include("django_browser_reload.urls")),
]
```
