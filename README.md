# django-heroku
Minimal configuration to host a Django project at Heroku

## Hidding instance configuration
* pip install python-decouple
* create .env file at the root path and insert the following variables
- SECRET_KEY=Your$eCretKeyHere
- DEBUG=True

### Settings.py
* from decouple import config
* SECRET_KEY = config('SECRET_KEY')
* DEBUG = config('DEBUG', default=False, cast=bool)


## Configuring the Daba Base
* pip install dj-database-url
* 

### Settings.py
* from dj_database_url import parse as dburl
'''
default_dburl = 'sqlite:///' + os.path.join(BASE_DIR, 'db.sqlite3')

DATABASES = {
    'default': config('DATABASE_URL', default=default_dburl, cast=dburl),
}
'''

### .env


## Static files 
pip install dj-static

### wsgi
* from dj_static import Cling
* application = Cling(get_wsgi_application())

### Settings.py
* STATIC_ROOL = os.path.join(BASE_DIR, 'staticfiles')

## Create a requirements.txt
pip freeze > requirements.txt
* Include: gunicorn and psycopg2

## Create a file Procfile and add the following code
* web: gunicorn website.wsgi --log-file -

## Create a file runtime.txt and add the following core
* python-3.5.0
