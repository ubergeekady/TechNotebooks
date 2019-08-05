## Django Cheatsheet

```
pip3 install virtualenv
virtualenv venv -p python3

sudo python3.6 get-pip.py
sudo pip3.6 install virtualenv

source venv/bin/activate
pip install django
django-admin startproject Shortify
cd Shortify
python manage.py runserver
python manage.py startapp ShortifyApp
python manage.py migrate
```

**urls.py - main**

```python
from django.contrib import admin
from django.urls import path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('ShortifyApp.urls')),
]
```

ShortifyApp/urls.py (make new)

```python
from django.urls import path, include
from django.views.generic import TemplateView

app_name = 'shortifyapp'

urlpatterns = [
    path('', TemplateView.as_view(template_name='homepage.html')),
]
```

mkdir - ShortifyApp/templates/homepage.html

```python
INSTALLED_APPS = [
    'ShortifyApp.apps.ShortifyappConfig',
  ]
```

