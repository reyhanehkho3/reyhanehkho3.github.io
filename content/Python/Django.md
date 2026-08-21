---
title: Django
publish: true
date created: 2026-05-28
tags:
  - python
  - framework
---
If you don't have it installed, install it in a venv using pip. 
```bash
pip install django
```
create the project:
```bash
django-admin startproject myfirstproject
```
Navigate into the project. Create an app (this is where your actual code lives). Here is an example:
```bash
python manage.py startapp hello
```

```text
myfirstproject/
├── manage.py              # Command-line utility for Django
├── myfirstproject/        # Project configuration folder
│   ├── __init__.py
│   ├── settings.py        # Project settings
│   ├── urls.py           # URL routing
│   └── wsgi.py           # Deployment settings
└── hello/                 # Your app folder
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py          # Database models (empty for now)
    ├── tests.py
    ├── views.py           # Where we'll write our logic
    └── migrations/
```

Then we can make the urls and stuff.

Note:
```bash
# This creates the database tables Django needs
python manage.py migrate
```

then we run the development server
```bash
# Start the server
python manage.py runserver
```
---
[[Python]]