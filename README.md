Django beyond the tutorial
==========================

This repository complements a series of blog posts on <https://consideratecode.com>:

* [Getting to know your Users - User Authentication with Django's built-in views](https://consideratecode.com/2018/03/05/django-authentication-views-login-logout/)

This repository is based on ithe Django project you build in the official
Django tutorial: the `mysite` project with the `polls` app.

Installation
------------
This project requires Python 3.4 or higher and Django 2.0.

The recommended way to install this project is to use [Pipenv](https://consideratecode.com/pipenv/). The included `Pipfile` will set up a virtual environment with Python 3.6.x and Django 2.0.x, the latest versions as of this writing.

    $ pipenv install
    $ pipenv shell

Alternatively you can use the provided `requirements.txt` file to install Django with pip.

    $ pip install -r requirements.txt

Then we have to create a database by running the migrations. By default, the project uses a file-based SQLite database. Change into the directory `mysite` and use the `migrate` management command.

    $ cd mysite
    $ python manage.py migrate

Next, create a superuser to access the built-in admin.

    $ python manage.py createsuperuser --username daniel
    Email address: daniel@consideratecode.com
    Password:
    Password (again):
    Superuser created successfully.

You can, of course, use whatever username, email and password you want.

Now you are ready to start the application:

    $ python manage.py runserver

Visit <http://localhost:8000/admin/> and check if you can log in.

Note: the application does not have a "home page". If you visit
<http://localhost:8000/>, you will get an 404 Page Not Found error message and
a list of URL patterns Django tried. This is expected at this stage.

Troubleshooting
---------------
Here are some error messages you might encounter.

      File "manage.py", line 14
        ) from exc
             ^
    SyntaxError: invalid syntax

You are trying to run `manage.py` with an incompatible version of Python. Use at least Python 3.4.

    Traceback (most recent call last):
    File "manage.py", line 8, in <module>
        from django.core.management import execute_from_command_line
    ModuleNotFoundError: No module named 'django'

    The above exception was the direct cause of the following exception:

    Traceback (most recent call last):
    File "manage.py", line 14, in <module>
        ) from exc
    ImportError: Couldn't import Django. Are you sure it's installed and available on your PYTHONPATH environment variable? Did you forget to activate a virtual environment?

The error message says it all: you either haven't installed Django yet or you have installed it in a virtual environment.
If you used `pipenv install` to install it, you must run `pipenv shell` everytime you open a new console.

Author
------
Daniel Hepper <daniel@consideratecode.com>

License and Copyright
---------------------
Modified BSD License. For the full terms, see LICENSE.

The code in this repository is based on the Django tutorial, also released
under the Modified BSD License as part of Django by the Django Software
Foundation and individual contributors.

The name "Django" is a registered trademark of the Django Software Foundation.
Please note that any references to the official Django tutorial
are nominative and should not imply affiliation with or endorsement by the
Django Software Foundation.
