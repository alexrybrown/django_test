Django_Test Setup
=================

Installation
============

To begin you can clone this repository and setup Django using the following instructions.

Linux Installation (Debian/Ubuntu)
----------------------------------

Note:

    - The following will assume you are cloning the sourcecode to **~/Projects/django_test**.  If you are cloning to a different location, you will need to adjust these instructions accordingly.
    - A dollar sign ($) indicates a terminal prompt, as your user, not root.

1.  Clone the source::

        $ cd ~/Projects
        $ git clone git@github.com:alexrybrown/django_test.git

2. Install some required packages::

        $ sudo apt-get install python3 python3-dev python-pip libpq-dev postgresql postgresql-contrib

3.  Install virtualenv and virtualenvwrapper::

        $ pip install virtualenv
        $ pip install virtualenvwrapper

4.  Add the following to your **~/.bashrc** or **~/.zshrc** file::

        source /usr/local/bin/virtualenvwrapper.sh

5.  Type the following::

        $ source /usr/local/bin/virtualenvwrapper.sh

6.  Create your virtualenv (for Python 3)::

        $ mkvirtualenv django_test -p /usr/bin/python3


7.  Add the following to the end of the file **~/.virtualenvs/django_test/bin/postactivate**::

        export DJANGO_SETTINGS_MODULE=django_test.settings.settings
        export PYTHONPATH=~/Projects/django_test

8.  Activate the virtualenv::

        $ workon django_test

9.  Install the required Python libraries (ensure you're within the new virtual environment).::

        (django_test)$ pip install -r ~/Projects/django_test/requirements.pip
        
10. Create Database.::

        (django_test)$ sudo su - postgres
        (django_test)$ psql
        postgres=# CREATE DATABASE django_test;
        postgres=# CREATE USER django_test_user with PASSWORD 'password'; 
        postgres=# ALTER ROLE django_test_user SET client_encoding TO 'utf8';
        postgres=# ALTER ROLE django_test_user SET default_transaction_isolation TO 'read committed';
        postgres=# ALTER ROLE django_test_user SET timezone TO 'UTC';
        postgres=# GRANT ALL PRIVILEGES ON DATABASE django_test TO django_test_user;
        postgres=# \q
        (django_test)$ exit
        
11.  Start the runserver.::

        (django_test)$ python ~/Projects/django_test/manage.py runserver
        
12.  Open your browser and see your site.::

        http://127.0.0.1:8000/
