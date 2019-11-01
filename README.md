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

# Models
## La M en el MTV
El Modelo en Django usa diferentes opciones para conectarse a múltiples bases de datos relacionales, entre las que se encuentran: SQLite, PostgreSQL, Oracle y MySQL.
Para la creación de tablas, Django usa la técnica del ORM (Object Relational Mapper), una abstracción del manejo de datos usando OOP.

➜  Curso-Django source .env/bin/activate
(.env) ➜  Curso-Django cd platzigram
(.env) ➜  platzigram git:(master)


https://docs.djangoproject.com/en/2.2/ref/settings/#databases

https://docs.djangoproject.com/en/2.2/ref/models/fields/

```
python3 manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 17 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.

October 31, 2019 - 16:17:09
Django version 2.2.6, using settings 'platzigram.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

```
(.env) ➜  platzigram git:(master) ✗ python3 manage.py migrate
```
se abre DB  browser  for sql https://sqlitebrowser.org/dl/

- SE CREA LA TABLA USER EN MODEL.PY

```
(.env) ➜  platzigram git:(master) ✗ python3 manage.py makemigrations
Migrations for 'post':
  post/migrations/0001_initial.py
    - Create model User
(.env) ➜  platzigram git:(master) ✗
```
```
(.env) ➜  platzigram git:(master) ✗ python3 manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 1 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): post.
Run 'python manage.py migrate' to apply them.
```
```
(.env) ➜  platzigram git:(master) ✗ python3 manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, post, sessions
Running migrations:
  Applying post.0001_initial... OK
  ```
  
  ## El ORM de Django
https://docs.djangoproject.com/en/2.2/topics/db/queries/

- Como nuestra BD cambio porque se agrego is_admin = models.BooleanField(default=False)
```
(.env) ➜  platzigram git:(El-ORM-de-Django) python3 manage.py makemigrations
Migrations for 'post':
  post/migrations/0002_user_is_admin.py
    - Add field is_admin to user
 ```
 
 ```
 (.env) ➜  platzigram git:(El-ORM-de-Django) ✗ python3 manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, post, sessions
Running migrations:
  Applying post.0002_user_is_admin... OK
```
    
- Consola interactiva pero con django.
```
(.env) ➜  platzigram git:(El-ORM-de-Django) ✗ python3 manage.py shell
Python 3.8.0 (v3.8.0:fa919fdf25, Oct 14 2019, 10:23:27)
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
```
```
(.env) ➜  platzigram git:(El-ORM-de-Django) ✗ python3 manage.py shell
Python 3.8.0 (v3.8.0:fa919fdf25, Oct 14 2019, 10:23:27)
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
from post.models import User
>>> sandra = User.objects.create(
... email='hola@gmail.com',
... password='1234567',
... first_name='sandra',
... last_name='rairan'
... )
>>> sandra.email
'hola@gmail.com'
```
- Otra forma de guardar los datos es instanciando:
``` 
>>> tata= User()
>>> tata.pk
>>> tata.email = 'tata@gmail.com'
>>> tata.first_name= 'Tata'
>>> tata.last_name = 'Rairan'
>>> tata.password = 'MSIComputer'
>>> tata.save()
>>> tata.delete()
(1, {'post.User': 1})
```

- Scripts para crear datos:
```
from datetime import date

users = [
    {
        'email': 'ejemplo1@platzi.com',
        'first_name': 'Ejemplo1',
        'last_name': 'Apellido1',
        'password': '1234567',
        'is_admin': True
    },
    {
        'email': 'ejemplo2@platzi.com',
        'first_name': 'Ejemplo2y',
        'last_name': 'Apellido2',
        'password': '987654321'
    },
    {
        'email': 'ejemplo3a@platzi.com',
        'first_name': 'Ejemplo3',
        'last_name': 'Apellido3',
        'password': 'qwerty',
        'birthdate': date(1990, 12,19)
    },
    {
        'email': 'ejemplo4@platzi.com',
        'first_name': 'Ejemplo4',
        'last_name': 'Apellido4',
        'password': 'msicomputer',
        'is_admin': True,
        'birthdate': date(1981, 11, 6),
        'bio': "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
    }
]

from post.models import User

for user in users:
    obj = User(**user)
    obj.save()
    print(obj.pk, ':', obj.email)
```


## Glosario
ORM: Object-relational mapping. Es el encargado de permitir
el acceso y control de una base de datos relacional a través de
una abstracción a clases y objetos.

Templates: Archivos HTML que permiten la inclusión y ejecución
de lógica especial para la presentación de datos.

Modelo: Parte de un proyecto de Django que se encarga de estructurar
las tablas y propiedades de la base de datos a través de clases de Python.

Vista: Parte de un proyecto de Django que se encarga de la
lógica de negocio y es la conexión entre el template y el modelo.

App: Conjunto de código que se encarga de resolver una parte
muy específica del proyecto, contiene sus modelos, vistas, urls, etc.

Patrón de diseño: Solución común a un problema particular.

## Extendiendo el modelo de usuario
El modelo de usuarios que acabamos de construir funciona bien y es válido, sin embargo tiene algunas cosas que podrían representar fallas de seguridad en la aplicación. Por esto vamos a explorar el modelo de usuarios que nos provee Django.

```
(.env) ➜  platzigram git:(El-ORM-de-Django) python3 manage.py shell
Python 3.8.0 (v3.8.0:fa919fdf25, Oct 14 2019, 10:23:27)
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from django.contrib.auth.models import User
>>> u = User.ojects.create_user(username='tata', password='admin123')
Traceback (most recent call last):
  File "<console>", line 1, in <module>
AttributeError: type object 'User' has no attribute 'ojects'
>>> u = User.objects.create_user(username='tata', password='admin123')
>>> u
<User: tata>
>>> u.pk
1
>>> u.user:name
Traceback (most recent call last):
  File "<console>", line 1, in <module>
NameError: name 'name' is not defined
>>> u.username
'tata'
>>> u.password
'pbkdf2_sha256$150000$OZVofYb5DIGh$SqixreQk0GKI/RLf+ZbxnC0X2aAJTkZvNVaFikjaiyc='
>>>
```

(.env) ➜  platzigram git:(El-ORM-de-Django) ✗ python3 manage.py createsuperuser

(.env) ➜  platzigram git:(El-ORM-de-Django) ✗ python3 manage.py runserver

## Implementación del modelo de usuarios de Platzigram
Las opciones que Django propone para implementar Usuarios personalizados son:

Usando el Modelo proxy
Extendiendo la clase abstracta de Usuario existente
La opción OneToOneField restringe la posibilidad de tener perfiles duplicados.
Django no guarda archivos de imagen en la base de datos sino la referencia de su ubicación.


https://docs.djangoproject.com/en/dev/topics/auth/customizing/#extending-the-existing-user-model

https://docs.djangoproject.com/en/2.2/ref/models/fields/

https://github.com/django/django/blob/master/django/contrib/auth/models.py

(.env) ➜  platzigram git:(Implementación-del-modelo-de-usuarios-de-Platzigram) python3 manage.py startapp users

(Crea un folder users)


Las opciones que Django propone para implementar Usuarios personalizados son:
- Usando el Modelo proxy
- Extendiendo la clase abstracta de Usuario existente

Para el presente proyecto debemos crear los campos de usuario:

website
biography
phone_number
profile picture
created
modified
Luego debemos crear la app que se llamará users

sudo python3 manage.py startapp
Crear el modelo
Se debe importar lo que necesitamos

from django.contrib.auth.models import User
- Luego se crea los campos adicionales que se necesitan según el proyecto

class Profle(models.Model):
    """Profile Model."""
    """Proxy model that extends the base data with other information"""
    user =models.OneToOneField(User,on_delete=models.CASCADE)
    website=models.URLField(max_length=200,blank=True)
    biography=models.TextField(blank=True)
    phone_number=models.CharField(max_length=20,blank=True)
    picture=models.ImageField(
        upload_to='users/pictures',
        blank=True,
        null=True
    )
    create=models.DateTimeField(auto_now_add=True)
    modified=models.DateTimeField(auto_now=True)


    def__str__(self):
        """Return username."""
        return self.user.username
 - Posterior a eso dirigirse al archivo de settings.py y así como se instaló post se va a instalar users

- Para que funcione el campo ImageField se debe instalar la librería Pillow y se lo hace de la siguiente manera

(.env) ➜  platzigram git:(Implementación-del-modelo-de-usuarios-de-Platzigram) ✗ pip install Pillow 
- Después ejecutar para que se hagan efecto las migraciones: 

python3 manage.py makemigrations
```
(.env) ➜  platzigram git:(Implementación-del-modelo-de-usuarios-de-Platzigram) ✗ python3 manage.py makemigrations
Migrations for 'users':
  users/migrations/0001_initial.py
    - Create model Profile
 ```
 
- (.env) ➜  platzigram git:(Implementación-del-modelo-de-usuarios-de-Platzigram) ✗ python3 manage.py migrate
Y para ingresar al administrador de django crear el super usuario

python3 manage.py createsuperuser

- (.env) ➜  platzigram git:(Implementación-del-modelo-de-usuarios-de-Platzigram) ✗ python3 manage.py runserver
http://127.0.0.1:8000/admin/


## Explorando el dashboard de administración
Registraremos el perfil que acabmos de customizar, junto con el modelo extendido de Usuario, en el admin de Django para poder manejarlo desde la aplicación.
Esto puede hacerse de dos formas: con admin.site.register(Profile) o creando una nueva clase que herede de Admin.ModelAdmin

## Dashboard de Administración
Editaremos el detalle para que sea igual de complejo que el detalle de Usuario y le agregaremos los datos del perfil para no tener que estar cambiando de urls. Usaremos fieldsets y admin.StackedInline.

En la documentción de Django, https://docs.djangoproject.com/en/2.0/ref/contrib/admin/ podemos ver cómo funcionan los fieldsets.
