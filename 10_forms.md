# Searching College
### forms.py
```python
from django import forms
from .models import students

class StudentForm(forms.Form):
    student = forms.ModelChoiceField(queryset=students.objects.all(),label="Select Branch Here")
```
### Urls.py
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.tech),
    path('<int:student_id>/', views.student_details, name='student_detail'),
    path('colleges/', views.student_college_view, name='student_college_view')
]
```
### Views.py
```python
from django.shortcuts import render
from .models import students, College
from django.shortcuts import get_object_or_404
from .forms import StudentForm

def tech(request):
    all_students = students.objects.all()
    return render(request, 'students.html', {'all_students' : all_students})

def student_details(request, student_id):
    student = get_object_or_404(students, pk = student_id)
    return render(request, "student_details.html", {'student' : student})

def student_college_view(request):
    colleges = None
    if request.method == "POST":
        form = StudentForm(request.POST)
        if form.is_valid():
            student = form.cleaned_data['student']
            colleges = College.objects.filter(branches=student)
    else:
        form = StudentForm()
    return render(request, 'colleges.html', {'colleges': colleges, 'form' : form})
```
### Colleges.html
```html
{% extends "layout.html" %}

{% block content %}
<form method="POST">
    {% csrf_token %}
    {{form.as_p}}
    <button type='submit'>Search College</button>
</form>
{% if colleges %}
<h2>Colleges</h2>
{% for college in colleges %}
<li>{{college.name}} - {{college.location}}</li>
{% endfor %}

{% endif %}
{% endblock %}
```
