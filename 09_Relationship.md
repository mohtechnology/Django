# Relationship Means Connection Between Tables
### Admin.py (APP)
```python
from django.contrib import admin
from .models import students, student_review, College, Student_Certificate

# Register your models here.
class StudentReviewInline(admin.TabularInline):
    model = student_review
    extra = 2

class studentsAdmin(admin.ModelAdmin):
    list_display = ('name', 'branch, date_time')
    inlines = [StudentReviewInline]

class CollegeAdmin(admin.ModelAdmin):
    list_display = ('name', 'location')
    filter_horizontal = ("branches",)

class StudentCertificateAdmin(admin.ModelAdmin):
    list_display = ('student', 'certificate_number')

admin.site.register(students)
admin.site.register(College, CollegeAdmin)
admin.site.register(Student_Certificate ,StudentCertificateAdmin)
```
### Models.py (APP)
```python
from django.db import models
from django.utils import timezone
from django.contrib.auth.models import User

# Create your models here.
class students(models.Model):
    BRANCH_CHOICE = [
        ('CS', 'Computer Science'),
        ('AI', 'Artificial Intelligence'),
        ('DS', 'Data Science'),
    ]
    name = models.CharField(max_length=100)
    image = models.ImageField(upload_to='images/')
    date_time = models.DateTimeField(default= timezone.now)
    branch = models.CharField(max_length=2, choices=BRANCH_CHOICE)

    def __str__(self):
        return self.name
    
# One to Many
class student_review(models.Model):
    student = models.ForeignKey(students, on_delete=models.CASCADE, related_name='reviews')
    user = models.ForeignKey(User, on_delete=models.CASCADE)
    rating = models.IntegerField()
    comment = models.TextField()
    date_added = models.DateTimeField(default=timezone.now)

    def __str__(self):
        return f"{self.user.username} review for {self.chai.name}"
    
# Many to Many
class College(models.Model):
    name = models.CharField(max_length=100)
    location = models.CharField(max_length=100)
    branches = models.ManyToManyField(students, related_name=("Colleges"))

    def __str__(self):
        return f"{self.name}"

# One To One
class Student_Certificate(models.Model):
    student = models.OneToOneField(students, on_delete=models.CASCADE, related_name='certificate')
    certificate_number = models.CharField(max_length=100)
    issued_date = models.DateTimeField(default=timezone.now)
    valid_untill = models.DateTimeField()

    def __str__(self):
        return f"Certificate To {self.student.name}"
```
