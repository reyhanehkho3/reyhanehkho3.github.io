---
title: Migration
publish: true
date created: 2026-02-10
tags:
  - python
  - django
---
### What are Migrations?

In Django, your **Models** define the structure of your data (e.g., `User` has a `first_name` and an `email`). Your **Database** (PostgreSQL, MySQL, SQLite) needs to physically match that structure.

Migrations are the **bridge** between your Python code and your SQL database. Instead of you writing `ALTER TABLE...` SQL commands by hand, Django looks at your models, figures out what changed, and creates a migration to do it for you.

**Key features of migrations:**

- They are **incremental** (each migration builds on the last one).
- They are **reversible** (you can apply a migration to change the DB, or roll it back to a previous state).
- They are **database-agnostic** (the same migration works on PostgreSQL, MySQL, SQLite, etc., because Django translates the Python into the correct SQL for your specific database).

### What are Migration Files?

Migration files are actual **Python files** stored in your app's `migrations/` folder (e.g., `myapp/migrations/0001_initial.py`). 

These files are **auto-generated** by Django using the `makemigrations` command. They are not meant to be edited by hand (unless you are doing advanced database operations).

**What does a migration file look like?**

It contains a Python class called `Migration` that lists the operations to perform. For example:

```python
# myapp/migrations/0002_add_user_age.py

from django.db import migrations, models

class Migration(migrations.Migration):
    dependencies = [
        ('myapp', '0001_initial'),
    ]

    operations = [
        migrations.AddField(
            model_name='user',
            name='age',
            field=models.IntegerField(null=True),
        ),
    ]
```

**The anatomy of a migration file:**

- **`dependencies`** – This tells Django the order to run the files. It lists the previous migration file that must be applied before this one.
- **`operations`** – This is the actual change. It could be `AddField`, `CreateModel`, `RemoveField`, `RenameColumn`, etc.

### The 3-Step Workflow

Every time you change your `models.py`, you follow this exact workflow:

| Step | Command | What it does |
| :--- | :--- | :--- |
| **1** | `python manage.py makemigrations` | Django compares your models to the current database state and **creates** a new migration file in your `migrations/` folder. |
| **2** | `python manage.py migrate` | Django takes the migration files and **executes** the SQL commands against your actual database. |
| **3** | (Optional) `python manage.py showmigrations` | Shows you which migrations have been applied and which are pending. |

### Why do we keep Migration Files in Git?

Because they are Python files, you **must** commit them to your version control system (like Git). 

Here is why:

- If your teammate adds a new field, they commit the migration file.
- When you pull their code, your database is out of sync with the new models. 
- By running `migrate`, Django reads the migration file they committed and updates your local database to match. 

*Never* delete a migration file unless you know exactly what you are doing, or your teammates' databases will break.

### The "Fake" Migrations (Advanced)

Sometimes, your database schema already matches the migrations (e.g., you manually added a column). In this case, you can "fake" a migration:

```bash
python manage.py migrate --fake
```

This tells Django, *"Don't run the SQL, just mark this migration as already applied in the database's `django_migrations` table."*

**Pro Tip:** Always run `makemigrations` immediately after changing `models.py`, but remember that `makemigrations` doesn't touch your database—it only writes the file. The database only changes when you run `migrate`.


---
[[Python]]