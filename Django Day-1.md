# Django Installation and Models Guide

## 1. Introduction to Django
Django is a high-level Python web framework that promotes rapid development and a clean, pragmatic design. It follows the Model-View-Template (MVT) architectural pattern.

## 2. Installation

### Requirements
- **Python**: Version 3.6 or later (recommended)
- **pip**: Python package installer

### Steps to Install Django
1. **Install Python**:
   - Download from the official [Python website](https://www.python.org/downloads/).
   - Ensure Python is added to your system's PATH.

2. **Install pip**:
   - Typically comes with Python. Verify by running:
     ```bash
     pip --version
     ```

3. **Create a Virtual Environment (Optional but Recommended)**:
   ```bash
   cd your_project_directory
   python -m venv venv

## Activate the virtual environment:
**Windows:** venv\Scripts\activate
**macOS/Linux:** source venv/bin/activate

- **Install Django:**
```
pip install django
```

- **Verify Installation:**
```
python -m django --version
```

## 3. Creating a New Django Project
**(i) Start a Project:**
```
django-admin startproject project_name
```
**(ii) Navigate into the Project Directory:**
```
cd project_name
```
**(iii) Run the Development Server:**
```
python manage.py runserver
```
Access the development server at<br>
http://127.0.0.1:8000/.

## 4. Creating Models in Django
**What are Models?**
Models are Python classes that define the structure of your database, representing the data you want to store.

### Steps to Create Models
**(i) Create an App:**
```
python manage.py startapp app_name
```
**(ii) Define Models:** In models.py of your app directory:
```
from django.db import models

class MyModel(models.Model):
    field_name = models.CharField(max_length=100)
    another_field = models.IntegerField()
    created_at = models.DateTimeField(auto_now_add=True)
```
**(iii) Register the App:** Add the app to INSTALLED_APPS in settings.py:
```
INSTALLED_APPS = [
    ...
    'app_name',
]
```
**(iv) Create and Apply Migrations:**

- Create migrations:
```
python manage.py makemigrations
```
- Apply migrations:
```
python manage.py migrate
```
**(v) Using the Django Admin:** Register your model in admin.py:
```
from django.contrib import admin
from .models import MyModel

admin.site.register(MyModel)
```
**(vi) Create a Superuser:**
```
python manage.py createsuperuser
```
- Access the admin interface at http://127.0.0.1:8000/admin/.

## 5. Common Field Types
**CharField:** Short text strings.
**TextField:** Large text strings.
**IntegerField:** Integer values.
**FloatField:** Floating-point numbers.
**BooleanField:** True/False values.
**DateField:** Date values.
**DateTimeField:** Date and time values.
**EmailField:** Email addresses.
**URLField:** URLs.
**ImageField:** Images (requires Pillow).
**ForeignKey:** Many-to-one relationships.
**ManyToManyField:** Many-to-many relationships.
**OneToOneField:** One-to-one relationships.
### Field Options
**null:** Allows NULL values.
**blank:** Allows empty values in forms.
**default:** Sets a default value.
**unique:** Ensures unique values.
**choices:** Limits field values to specific options.
### Custom Methods
Define methods within your model class for custom logic, like __str__ for a human-readable string representation.
```
class MyModel(models.Model):
    name = models.CharField(max_length=100)

    def __str__(self):
        return self.name
```
## 6. Creating and Applying Migrations
**(i) Create Migrations:**
```
python manage.py makemigrations
```
**(ii) Apply Migrations:**
```
python manage.py migrate
```
## 7. Using Models in Views
Interact with your models in views to manage records.

**Example of Creating and Retrieving Records:**
```
from .models import MyModel

# Create a new entry
new_entry = MyModel(name="John Doe")
new_entry.save()

# Query all entries
all_entries = MyModel.objects.all()

# Filter entries
filtered_entries = MyModel.objects.filter(name="John Doe")

# Update an entry
entry = MyModel.objects.get(id=1)
entry.name = "Jane Doe"
entry.save()

# Delete an entry
entry.delete()
```
## 8. Admin Interface
**(i) Register your model in admin.py:**
```
from django.contrib import admin
from .models import MyModel

admin.site.register(MyModel)
```
**(ii) Access the admin panel:**

- Navigate to http://127.0.0.1:8000/admin/.


## Additional Resources
Django Documentation
Django Tutorial
Django Models Documentation
Django QuerySet Documentation