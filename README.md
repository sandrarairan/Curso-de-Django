# Curso-de-Django
Curso de Django - Platzi
# TABLA DE CONTENIDO
- [Introducción](#Introducción)
- [Vistas](#Vistas)
- [Models](#Models)
- [Templates auth y middlewares](#Templates-auth-y-middlewares)
- [Forms](#Forms)
- [Class-based views](#Class-based-views)
- [Deployment](#)
- [Bonus](#Bonus)
<!-- toc -->

# Introducción
##  Preparación del entorno de trabajo en Mac
Vamos a python.org, en la sección de descargas, descargamos la última versión y hacemos el proceso de instalación.

Los entornos virtuales nos permiten isolar multiples dependencias para el desarrollo de proyecto, puede pasar por ejemplo cuando trabajas con diferentes versiones de python o de django.

Python 3 trae la creación y manejo de entornos virtuales como parte del modulo central.

‘python3 -m venv .env’
```
➜  Curso-Django mkdir platzigram
➜  Curso-Django cd platzigram
➜  platzigram cd ..
➜  Curso-Django python3 -m venv .env
➜  Curso-Django ls -al
total 0
drwxr-xr-x   4 sandrarairan  staff   128 Oct 28 14:58 .
drwxr-xr-x  63 sandrarairan  staff  2016 Oct 27 14:44 ..
drwxr-xr-x   6 sandrarairan  staff   192 Oct 28 14:58 .env
drwxr-xr-x   2 sandrarairan  staff    64 Oct 28 14:32 platzigram
➜  Curso-Django source .env/bin/activate
(.env) ➜  Curso-Django deactivate
➜  Curso-Django cd platzigram
➜  platzigram source ../.env/bin/activate
(.env) ➜  platzigram
```

(.env) ➜  platzigram pip install django -U

(.env) ➜  platzigram pip freeze
Django==2.2.6
pytz==2019.3
sqlparse==0.3.0

# Creación del proyecto Platzigram / Tu primer Hola, mundo! en Django
pip freeze --> para validar las extensiones instaladas.
Django-admin startproject Platzigram . --> para la creación del proyecto.

(.env) ➜  platzigram git:(master) ✗ django-admin startproject platzigram .

https://docs.djangoproject.com/en/2.0/ref/settings/

```
(.env) ➜  platzigram git:(master) ✗ python3 manage.py

Type 'manage.py help <subcommand>' for help on a specific subcommand.

Available subcommands:

[auth]
    changepassword
    createsuperuser

[contenttypes]
    remove_stale_contenttypes

[django]
    check
    compilemessages
    createcachetable
    dbshell
    diffsettings
    dumpdata
    flush
    inspectdb
    loaddata
    makemessages
    makemigrations
    migrate
    sendtestemail
    shell
    showmigrations
    sqlflush
    sqlmigrate
    sqlsequencereset
    squashmigrations
    startapp
    startproject
    test
    testserver

[sessions]
    clearsessions

[staticfiles]
    collectstatic
    findstatic
    runserver
```
(.env) ➜  platzigram git:(master) ✗ python3 manage.py runserver

http://127.0.0.1:8000/hello-world/

# Vistas
## El objeto Request
En esta clase crearemos mas vistas, jugaremos con los diferentes patrones de urls que django nos permite tener, revisaremos cómo django procesa las peticiones.

Reto de la clase: Crea una vista y su respectiva URL en la que recibas números y hagas operaciones con ellos. En la siguiente clase te voy a enseñar a resolverlo.

Regresa la lista ordenada de números en formato json.
```
"""debuger"""
    import pdb; pdb.set_trace()
```

## Creación de la primera app
Vamos a explorar el concepto de Apps en Django y crearemos nuestra primera app.

Una app dentro de Django es un modulo de python que provee un conjunto de funcionalidades relacionadas entre sí.
Las apps son una combinación de models, vistas, urls, archivos estaticos.

Muchas apps en django estan hechas para ser reutilizadas.

El . es la ruta en forlder.

Manage.py

(.env) ➜  platzigram git:(Creación-de-la-primera-app) python3 manage.py startapp post
 "SE CREA UN NUEVO FOLDER POST"
 
 (.env) ➜  platzigram git:(Creación-de-la-primera-app) ✗ python3 manage.py runserver
 
 ## Introducción al template system
Template system de Django es una manera de presentar los datos usando HTML, está inspirado en Jinja2 y su sintaxis, por lo cual comparte muchas similitudes. Permite incluir alguna lógica de programación.

## Patrones de diseño y Django
Un patrón de diseño, en términos generales, es una solución reutilizable a un problema común.
El patrón más común para el desarrollo web es MVC (Model, View, Controller). Django implementa un patrón similar llamado MTV (Model, Template, View).



  
