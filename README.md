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
 http://127.0.0.1:8000/posts/
 
 ## Introducción al template system
Template system de Django es una manera de presentar los datos usando HTML, está inspirado en Jinja2 y su sintaxis, por lo cual comparte muchas similitudes. Permite incluir alguna lógica de programación.

Se crea una carpeta Templates

https://docs.djangoproject.com/en/2.2/ref/templates/builtins/


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

https://docs.djangoproject.com/en/2.2/ref/contrib/admin/

http://127.0.0.1:8000/admin/


## Creación del modelo de posts
Para reflejar los cambios en la base de datos, siempre que se crea o se edita un modelo debemos cancelar el server, ejecutar makemigrations, migrate y luego de nuevo vovler a correr el servidor con runserver.
Con respecto a las imágenes, Django por defecto no está hecho para servir la media, pero editando las urls logramos que se puedan mostrar. Para servir archivos de media, usamos MEDIA_ROOT y MEDIA_URLS.

Reto de la clase:
Crea el modelo de posts y registralo en el admin.

https://docs.djangoproject.com/en/2.2/ref/models/fields/#foreignkey

https://docs.djangoproject.com/en/2.2/ref/settings/#media-root
(.env) ➜  platzigram git:(Creación-del-modelo-de-posts) ✗ python3 manage.py makemigrations

(.env) ➜  platzigram git:(Creación-del-modelo-de-posts) ✗ python3 manage.py migrate
http://127.0.0.1:8000/admin/


# Templates, auth y middlewares
## Templates y archivos estáticos
Los templates quedarán definidos en un nuevo folder que llamaremos /templates/.

El concepto de archivos estáticos en Django, son archivos que se usan a través de la aplicación para pintar los datos. Pueden ser archivos de imagen, audio y video, o archivos css y scripts js.

Para servir archivos estáticos, nos apoyamos en STATIC_ROOT y STATIC_URLS.
https://docs.djangoproject.com/en/2.2/ref/templates/builtins/#extends

http://127.0.0.1:8000/posts/


https://docs.djangoproject.com/en/2.2/topics/auth/default/#authentication-in-web-requests

## Login
Vamos a asegurarnos que para acceder a la aplicación tengamos una cuenta de usuario. Para esto vamos a ver el proceso de autenticación que django nos ofrece para crear la página de login de Platzigram.

https://docs.djangoproject.com/en/2.2/topics/auth/default/#authentication-in-web-requests
http://127.0.0.1:8000/users/login/


## Logout
Completaremos el flujo de autenticación del usuario que iniciamos en la clase anterior agregando la funcionalidad de Logout. Ademas incorporamos algo de estilos al formulario de Login.

https://docs.djangoproject.com/en/2.2/topics/auth/default/#how-to-log-a-user-out

## Signup
Crearemos el Registro de usuario a partir de la clase perfil, por lo que usaremos un formulario personalizado. Definiremos un nuevo Template para el formulario. Dejaremos que el browser se encargue de las validaciones generales. Sólo validaremos en python la coincidencia entre password y confirmación del password. Incluiremos una validación con try/catch para evitar que se dupliquen usuarios con mismo nombre.

https://docs.djangoproject.com/en/2.2/topics/auth/default/#creating-users

http://127.0.0.1:8000/users/signup/
(.env) ➜  platzigram  python3 manage.py runserver

## Middlewares
Un middleware en Django es una serie de hooks y una API de bajo nivel que nos permiten modificar el objeto request antes de que llegue a la vista y response antes de que salga de la vista.

Django dispone de los siguientes middlewares por defecto:

SecurityMiddleware
SessionMiddleware
CommonMiddleware
CsrfViewMiddleware
AuthenticationMiddleware
MessageMiddleware
XFrameOptionsMiddleware
Crearemos un middleware para redireccionar al usuario al perfil para que actualice su información cuando no haya definido aún biografía o avatar.


https://docs.djangoproject.com/en/2.2/topics/http/middleware/


# Forms
## Formularios en Django
La clase utilitaria para formularios de Django nos ayuda a resolver mucho del trabajo que se realiza de forma repetitiva. La forma de implementarla es muy similar a la implementación de la clase models.model.

Algunas de las clases disponibles en Django al implementar form, son:

BooleanField
CharField
ChoiceField
TypedChoiceField
DateField
DateTimeField
DecimalField
EmailField
FileField
ImageField"

https://docs.djangoproject.com/en/2.2/ref/forms/fields/

https://docs.djangoproject.com/en/2.2/topics/forms/

## Mostrando el form en el template
Existen diferentes formas en las que se pueden mostrar los valores del form, estas son: as_table, as_p y as_ul. También se pueden mostrar campos de manera individual, incluso customizar las clases que se van a usar para mostrar los errores, etc. Refinaremos la apariencia del form a través de algunas refactorizaciones en el template.


https://docs.djangoproject.com/en/2.2/topics/forms/#working-with-form-templates

http://127.0.0.1:8000/users/me/profile/

## Model forms
ModelForm es una manera más sencilla de crear formularios en Django y en el caso de nuestro proyecto, se adapta mucho mejor al modelo que ya tenemos.
Lo usaremos para crear el formulario de posts.

Aprovecharemos para refinar la funcionalidad en el navbar y conectar el feed con los posts.

https://docs.djangoproject.com/en/2.2/topics/forms/modelforms/

## Validación de formularios
Para aprender a validar los campos de un formulario vamos a actualizar el registro de usuarios.
Hasta este momento el script de validación del formulario Signup está escrito directamente en la vista, y a pesar de que no genera ningún error, puede convertirse en un problema, así que lo recomendable es separarlo. Crearemos un nuevo form con la clase forms.Form, también vamos a introducir un nuevo concepto relacionado con formularios: los widgets.

Los widgets en Django, son una representación de elementos de HTML que pueden incluir ciertas validaciones. Por default todos los campos son requeridos. Los datos depurados se pueden consultar con self.cleaned_data['_nombre_del_field_']
https://docs.djangoproject.com/en/2.2/ref/forms/validation/

https://docs.djangoproject.com/en/2.2/ref/forms/fields/

https://docs.djangoproject.com/en/2.2/ref/forms/widgets/

# Class-based views
## Class-based views
Veamos de qué forma optimizamos el proceso de creación de nuestras apps de forma que no repitamos código. Para veamos cuál es el concepto de class based views.

Las vistas también pueden ser clases, que tienen el objetivo de evitar la repetición de tareas como mostrar los templates, son vistas genéricas que resuelven problemas comunes.


https://docs.djangoproject.com/en/2.2/ref/class-based-views/

https://docs.djangoproject.com/en/2.2/topics/class-based-views/

http://ccbv.co.uk/

http://127.0.0.1:8000/users/hola/

## Protegiendo la vista de perfil, Detail View y List View
En esta clase vamos a usar Detail View para continuar con el perfil de usuario y usaremos List View para definir la lista de views.



http://127.0.0.1:8000/users/me/profile/
http://127.0.0.1:8000/users/sandra/

## CreateView, FormView y UpdateView
En esta clase incorporamos la paginación de posts utilizando page_obj, bootstrap y variables del contexto. Adicionalmente resolvemos el reto de la clase anterior usando DetailView. Remplazamos render y redirect por CreateView para los posts. Implementaremos FormView en sustitución del formulario de registro Signup que teníamos hasta ahora con el fin de optimizar el código y finalmente optimizamos la vista de actualización del perfil con UpdateView.

http://ccbv.co.uk/projects/Django/2.0/django.views.generic.edit/UpdateView/

http://ccbv.co.uk/projects/Django/2.0/django.views.generic.edit/FormView/

http://ccbv.co.uk/projects/Django/2.0/django.views.generic.edit/CreateView/

## Generic auth views
Django cuenta con varias vistas genéricas basadas en clases para resolver muchas de las funcionalidades relacionadas con la autenticación, como es el caso de:

login
logout
password_change
password_change_done
password_reset
password_reset_done
password_reset_confirm
password_reset_complete
Estas vistas genéricas nos permiten ahorrarnos varias líneas de código, además de que incluyen características adicionales de mucha utilidad.

https://docs.djangoproject.com/en/2.2/topics/auth/default/#module-django.contrib.auth.views


http://127.0.0.1:8000/users/login/




# Deployment
## Arquirectura / Conceptos / Componentes
Liberar un proyecto de Django a producción es una tarea bastante sencilla pero que puede confundir a muchos la primera vez que se intente (a mi me sucedió). El objetivo de esta lectura es tener una breve a introducción a la arquitectura de un proyecto de Django corriendo en un servidor de producción (un servidor de verdad) y que consecuentemente los siguientes tutoriales de configuración tengan más sentido al momento de que los leas.

Al principio del curso hablamos de un archivo llamado wsgi.py ubicado dentro del folder de las configuraciones del proyecto, conviviendo junto con el archivo urls.py y settings.py. WSGI significa Web Server Gateway Interface y es un protocolo sencillo de llamadas para que un web server (como NGINX o Apache) se comuniquen con una aplicación web o framework escritos en Python.

WSGI nos permite delegar el trabajo de aplicar reglas complejas de enrutamiento a un web server como NGINX y al mismo tiempo lograr que exista una comunicación del usuario final de nuestro proyecto de Python. Dicho esto, esta sería la ilustración de un servidor que expone múltiples servicios como e-mail a través de pop3, un app server usando SSL, otro app server redirigiendo las peticiones HTTP a HTTPS y una base de datos de PostgreSQL:


Para el caso particular del proyecto del curso, nosotros usaremos un servidor Linux corriendo Ubuntu 16.04 en el cual configuraremos una base de datos de PostgreSQL, un web server NGINX y correremos nuestro proyecto de Django usando Gunicorn. Los archivos estáticos y subidos por los usuarios serán también servidos usando NGINX ya que no es trabajo de Django realizar estas tareas. La base de datos no tiene que estar disponible para el público por lo que no hay necesidad de que NGINX la exponga.

## Cómo conectar Django a una base de datos?
Django obtiene la estructura, acceso y control de los datos de una aplicación a través de su ORM (Object Relational Mapper), esto significa que no importa qué motor de base de datos esté usando, el mismo código seguirá funcionando, configurar esto en un proyecto de Django es cuestión de segundos.

Todo se define dentro del archivo settings.py de nuestro proyecto dentro de la variable DATABASES:

DATABASE

Será el nodo padre que nos servirá para indicar que definiremos una base de datos.
Dentro, tendremos el nodo default este tendrá toda la configuración clave de la base de datos.

datos para conexión de base de datos django.png
Además, Django puede trabajar con múltiples bases de datos usando una estrategia llamada routers por lo que el diccionario DATABASES puede contener múltiples llaves con diferentes bases de datos. Pero eso sí, necesita siempre existir una llave “default”.

Es un diccionario de python el cual requiere definir una base de datos por default, más de eso al final, usando la llave default que a su vez será otro diccionario con los datos de configuración:

La configuración recibirá el engine el cual puede ser:

PostgreSQL: 'django.db.backends.postgresql’
MySQL: 'django.db.backends.mysql’
SQLite: 'django.db.backends.sqlite3’
Oracle: 'Django.db.backends.oracle’
El nombre de la base de datos “NAME”.
El usuario “USER”.
La contraseña “PASSWORD”.
La ubicación o host del servidor de la base de datos “HOST”.
Y el puerto de conexión “PORT”.

Adicionalmente, se pueden configurar más detalles por base de datos, por ejemplo, configurar que todos los queries de una vista sean empaquetados en una sola transacción a la base de datos usando ATOMIC_REQUESTS=True


## Configurar el servidor
Es una buena práctica al conectarnos por primera vez a nuestro servidor actualizar los paquetes del Sistema Operativo con los siguientes comandos:

sudo apt-get update && sudo apt-get upgrade

Configuración inicial del servidor
Creamos un nuevo usuario sin directorio home que tenga la capacidad de correr algunos comandos de súper usuario:
sudo useradd -g sudo -M <username>

Le asignamos una contraseña segura al nuevo usuario:
sudo passwd <username>

Iniciamos sesión con el nuevo usuario:
su <username>

Por último vamos a instalar las dependencias de python, postgress, git y nginix con el siguiente comando:
sudo apt-get install python3-pip python3-dev postgresql postgresql-contrib libpq-dev git nginx

Configurar PostgreSQL
Primero iniciamos sesión con el usuario postgres usando el comando sudo su postgres y después escribimos psql para entrar al shell interactivo de PostgreSQL donde configuramos lo siguiente:

Creamos una base de datos: CREATE DATABASE platzi;

Creamos un usuario para la base de datos: CREATE USER freddier WITH PASSWORD ‘cvander<3’;

Le damos permisos al usuario sobre la base de datos: GRANT ALL PRIVILEGES ON DATABASE platzi TO freddier;

Hecho esto, salimos del shell escribiendo \q seguido de exit para salir de la sesión de postgres.

Configurar el proyecto
Clonar el proyecto de Github:
git clone [https://github.com/pablotrinidad/platzigram.git](https://github.com/pablotrinidad/platzigram.git) platzi

Instalar virtualenv:
sudo pip3 install virtualenv

Crear entorno virtual:
virtualenv -p $(which python3) .venv

Activar entorno virtual:
source .venv/bin/activate

Instalar dependencias para Pillow:
sudo apt-get install libjpeg-dev

Ir al folder del proyecto:
cd platzi

Instalar dependencias de python del proyecto:
pip install -r requirements/prod.txt

Agregar algunas variables de entorno al archivo ~/.bashrc para probar localmente que todo esté funcionando:
vim ~/.bashrc

Las variables deben lucir algo similar a lo siguiente:

export PLATZI_SECRET_KEY="random_key:aasdafasf"
export PLATZI_DB_NAME="platzi"
export PLATZI_DB_USER="freddier"
export PLATZI_DB_PASSWORD="cvander<3"
export PLATZI_DB_PORT="5432"
export PLATZI_DB_HOST="localhost"
export DJANGO_SETTINGS_MODULE="platzi.settings.prod"
Leemos las variables:
source ~/.bashrc

Editamos la variable **ALLOWED_HOSTS **del archivo de settings de producción:
vim platzi/settings/prod.py

La variable tendrá algo como lo siguiente, donde gatos.io será tu dominio o IP:

ALLOWED_HOSTS = [’gatos.io’]
Hacer un Sanity Check
Hasta este punto el proyecto debe ser capaz de escribir a la base de datos además de servirse usando el servidor de desarrollo y gunicorn. Probémoslo:

Reflejar el modelo de Django en PostgreSQL: ./manage.py migrate
Crear un súper usuario: ./manage.py createsuperuser
Correr servidor de desarrollo: ./manage.py runserver 0.0.0.0:8000
Correr gunicorn: gunicorn platzi.wsgi -b 0.0.0.0:8000
Si todo funcionó correctamente, los pasos 3 y 4 debieron mostrar tu sitio en la URL o IP en el puerto 8000.

Configurar Nginx
Iniciar sesión como súper usuario: sudo su -
Ir al directorio de Nginx: cd /etc/nginx/
Borrar los antiguos archivos de configuración: rm sites-*/default
Crear un nuevo archivo vim sites-available/app con el siguiente contenido:
upstream django_app {
    server 127.0.0.1:8000;
}

server {

    listen 80;
    server_name demo.gatos.io;

    access_log /var/log/nginx/app.log;
    error_log /var/log/nginx/app.error.log;

    location /static {
        autoindex on;
        alias /home/platzi/platzi/staticfiles/;
    }

    location /media {
        autoindex on;
        alias /home/platzi/platzi/media/;
    }

    location / {
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header Host $http_host;
        proxy_redirect off;

        proxy_pass http://django_app;
    }

}
Enlazar los archivos: ln -s /etc/nginx/sites-available/app /etc/nginx/sites-enabled/
Reiniciar Nginx: service nginx restart
Configurar Gunicorn
Regresamos a la sesión de Platzi: exit
Creamos directorios para los scripts y los logs: mkdir deploy logs
Creamos un script dentro de deploy vim deploy/gunicorn_start con un contenido similar al siguiente:
#!/bin/bash

NAME="platzi"
VIRTUALENV="/home/platzi/venv/"
DJANGODIR="/home/platzi/platzi/"
USER=platzi
GROUP=sudo
NUM_WORKERS=3
DJANGO_WSGI_MODULE=platzi.wsgi

echo "Starting $NAME as `whoami`"

cd $VIRTUALENV
source bin/activate
cd $DJANGODIR

export PLATZI_SECRET_KEY="&wrw__y!3_hlh@&1v)a!%=ext=-7zuqewv+#^qu^63g)a(3f3@"

export PLATZI_DB_NAME="platzi"
export PLATZI_DB_USER="cvander"
export PLATZI_DB_PASSWORD="adminadmin123"
export PLATZI_DB_PORT="5432"
export PLATZI_DB_HOST="localhost"

export DJANGO_SETTINGS_MODULE="platzi.settings.prod"

export PYTHONPATH=$DJANGODIR:$PYTHONPATH

exec gunicorn ${DJANGO_WSGI_MODULE} \
        --workers $NUM_WORKERS \
        --user=$USER --group=$GROUP \
        --log-level=debug \
        --bind=127.0.0.1:8000
Hacer el script ejecutable: chmod +x deploy/gunicorn_start
Probar el script: deploy/gunicorn_start
Mientras el script esté corriendo, el proyecto estará viviendo en la IP en el puerto 80.

Crear un servicio
Iniciar sesión como súper usuario: sudo su -
Ir al directorio de los servicios: cd /etc/init
Crear el servicio vim platzi.conf con el siguiente contenido:
# platzi

# description "Platzi Linux Service"
# authon "Pablo Trinidad"

start on startup

script
    exec /home/platzi/deploy/gunicorn_start
end script
Iniciar servicio: service platzi start
Por último regresamos al directorio que contiene el proyecto y ejecutamos: ./manage.py collectstatic


## Preparación del VPS (en AWS)
El servidor
Para la demostración de la clase se usa una máquina t2.nanoque Amazon Web Services provee con Ubuntu Server. Toda la configuración del proyecto vive en el mismo servidor. Es decir, tanto la base de datos como los archivos estáticos y el código fuente son manejados por una sola máquina. Es importante mencionar que en casos donde nuestro proyecto es más grande y requiere de una mejor arquitectura, es recomendable separar cada uno de estos de manera que la base de datos tenga su propio servidor, que exista un balanceo de carga hacia las instancias que manejan el código y que la media y los estáticos sean servidos desde una CDN. El caso de instalación que veremos en este post es un método que se puede usar en cualquier servidor Linux con Ubuntu Server; por lo que no es una configuración que únicamente se pueda llevar a cabo usando AWS. Cualquier proveedor que te dé acceso a una máquina Linux es útil.

Crear el servidor
Una vez dentro de la consola de administración de Amazon Web Services sigue estos pasos:

Accede a la sección de Amazon EC2
Da clic en el botón Launch Instance
Selecciona Ubuntu 16.04 como el Sistema Operativo deseado
Elige el tipo de instancia que más se adecúe a tus necesidades (t2.micro es parte de la capa gratuita)
En el paso 3, deja todas las configuraciones tal y como están
Selecciona la cantidad de GB de almacenamiento que quieras tener en tu instancia
Asigna un nombre descriptivo a la instancia
Crea un nuevo grupo de seguridad con el puerto 22, 80 y 8000 abiertos desde cualquier IP por el protocolo TCP
Selecciona Launch
Crea nuevas llaves SSH y descargarlas al ordenador
Conectarse al servidor
Para conectarnos al servidor usaremos la llave que acabamos de descargar. Es muy importante nunca perder esta llave ya que si la perdemos no tendremos otra forma de acceder al servidor.

Poner la llave en modo lectura: [shell]chmod 0400 Platzi.pem[/shell]
Conectarse al servidor usando la IP pública que AWS nos asigna: [shell]sudo ssh -i Platzi.pem ubuntu@IP[/shell]
