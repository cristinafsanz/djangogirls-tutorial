# djangogirls-tutorial

Learning Python & Django from the Django Girls event

17 Noviembre 2018: [DjangoGirls: Taller de programación de Python y Django](https://www.eventbrite.es/e/entradas-djangogirls-taller-de-programacion-de-python-y-django-orientado-a-mujeres-48504011805)

Se va a seguir el [tutorial de Django Girls](https://tutorial.djangogirls.org/es).

## Previo al taller

### [Instalación](https://tutorial.djangogirls.org/es/installation/)

#### Instalar Python

- Aplicaciones - Preferencias del sistema- Seguridad y privacidad - pestaña "General". "Permitir aplicaciones descargadas desde:" "Mac App Store y desarrolladores identificados."

- Instalar [Python](https://www.python.org/downloads/release/python-361/): Descargar el archivo Mac OS X 64-bit/32-bit installer.

- Haz doble clic en python-3.7.1-macosx10.9.pkg para ejecutar al instalador.

- Verifica que la instalación fue exitosa:

```
$ python3 --version
Python 3.7.1
```

#### Editor de código

Por ahora lo haré con VSCode (ya lo tengo instalado) usando la extensión de [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python).

#### Crear un entorno virtual (virtualenv)

Virtualenv aísla tu configuración de Python/Django por cada proyecto.

- Encontrar un directorio en el que quieras crear el virtualenv:

```
cd /Users/cristinafernandez/Others
mkdir djangogirls-tutorial
cd djangogirls-tutorial
```

- Haremos un virtualenv llamado myvenv:

```
python3 -m venv myvenv
```

Nota: Puedes usar cualquier otro nombre, pero sólo utiliza minúsculas y no incluyas espacios. También es una buena idea mantener el nombre corto.

#### Trabajar con virtualenv

- Inicia el entorno virtual ejecutando:

```
source myvenv/bin/activate
```

- Sabrás que tienes virtualenv iniciado cuando veas que la línea de comando en tu consola tiene el prefijo (myvenv).

- Cuando trabajes en un entorno virtual, python automáticamente se referirá a la versión correcta, de modo que puedes utilizar python en vez de python3.

#### Instalar Django

- Debemos asegurarnos que tenemos la última versión de pip, el software que utilizamos para instalar Django:

```
python3 -m pip install --upgrade pip
```

- Instalar paquetes con un fichero de requisitos (requirements):

  - Crear un fichero `requirements.txt`en la raíz y añadir:

  ```
  Django~=2.0.6
  ```

  - Ejecutar: 

  ```
  pip install -r requirements.txt
  ```

#### Instalaciones adicionales (Git y GitHub)

- Habría que instalar [Git](https://tutorial.djangogirls.org/es/installation/#instalar-git) y crear una cuenta de [GitHub](https://tutorial.djangogirls.org/es/installation/#crear-una-cuenta-de-github) si no se tuviera.

#### Crear una cuenta de PythonAnywhere

PythonAnywhere es un servicio para ejecutar código Python en servidores "en la nube". Lo vamos a usar para alojar nuestro sitio para que esté disponible en Internet.

- Crea una cuenta de Principiante ("Beginner") en [PythonAnywhere](https://www.pythonanywhere.com/pricing/): https://www.pythonanywhere.com/user/cristinafsanz/.

- La URL del blog será cristinafsanz.pythonanywhere.com, como el nombre de usuario elegido. Lo mejor es usar tu apodo o elegir un nombre que indique de qué trata tu blog.

#### Crear un token para la API de PythonAnywhere

- Sólo 1 vez.

- [Account - API Token](https://www.pythonanywhere.com/user/cristinafsanz/account/#api_token): Create new API token

#### Nota: myvenv en .gitignore para no subirlo al repo

```
cat .gitignore
myvenv
```

## Taller

### [¡Tu primer proyecto en Django!](https://tutorial.djangogirls.org/es/django_start_project/)

```
django-admin startproject mysite .
```

- Cambios del settings.py del tutorial

- Configurar una base de datos:

```
python manage.py migrate
```

- Iniciar el servidor:

```
python manage.py runserver
```

Ya se tiene la aplicación en http://127.0.0.1:8000/.

### [Modelos en Django](https://tutorial.djangogirls.org/es/django_models/)

- Crear una aplicación separada dentro de nuestro proyect

```
python manage.py startapp blog
```

- Después de crear una aplicación, también necesitamos decirle a Django que debe utilizarla: en mysite/settings.py.

- Crear el modelo del Post en blog/models.py.

  - models.Model significa que Post es un modelo de Django, así Django sabe que debe guardarlo en la base de datos.

- Crear tablas para los modelos en tu base de datos

  - Tenemos que hacer saber a Django que hemos hecho cambios en nuestro modelo:

  ```
  python manage.py makemigrations blog
  ```

  - Django preparó un archivo de migración que ahora tenemos que aplicar a nuestra base de datos:

  ```
  python manage.py migrate blog
  ```

### [Administrador de Django](https://tutorial.djangogirls.org/es/django_admin/)

- Para agregar, editar y borrar los posts que hemos modelado, usaremos el administrador (admin) de Django: blog/admin.py.

- En http://127.0.0.1:8000/admin/.

- Deberás crear un superusuario (superuser), que es un usuario que tiene control sobre todo el sitio:

```
python manage.py createsuperuser
```

```
Username (leave blank to use 'cristinafernandez'):
Email address: cristinafsanz@gmail.com
Password:
Password (again):
Superuser created successfully.
```

- Entra con las credenciales de super usuario que tu escogiste; verás el panel de administrador de Django.

- Añade cinco o seis publicaciones en tu blog (al menos dos o tres posts (pero no todos) tengan la fecha de publicación definida).

### [Despliega](https://tutorial.djangogirls.org/es/deploy/)

- Vamos a usar PythonAnywhere. PythonAnywhere es gratuito para aplicaciones pequeñas que no tienen muchos visitantes, y con eso tendrás más que suficiente por ahora.

- Crear nuestro repositorio Git

```
git init
git config --global user.name "Cristina Fernández"
git config --global user.email cristinafsanz@gmail.com
```

- .gitignore

```
*.pyc
*~
__pycache__
myvenv
db.sqlite3
/static
.DS_Store
```

- Subir todos los ficheros a GitHub (git add ., git commit -m...., git push origin master)

- Configurar nuestro blog en PythonAnywhere.

  - [Dashboard](https://www.pythonanywhere.com/user/cristinafsanz/): 
  
    - Iniciar consola "Bash".

    - Para desplegar una aplicación web en PythonAnywhere necesitas descargar tu código de GitHub y configurar PythonAnywhere para que lo reconozca y lo sirva como una aplicación web. PythonAnywhere tiene una herramienta automática que lo hará todo por nosotros:

    - En la consola de [PythonAnywhere](https://www.pythonanywhere.com/user/cristinafsanz/consoles/11064741/): 

    ```
    pip3.6 install --user pythonanywhere
    ```

    - Ahora ejecutaremos el asistente para configurar automáticamente nuestra aplicación desde GitHub.

    - En la consola de [PythonAnywhere](https://www.pythonanywhere.com/user/cristinafsanz/consoles/11064741/): 

    ```
    pa_autoconfigure_django.py https://github.com/cristinafsanz/djangogirls-tutorial.git
    ```

    - Crear superuser en la consola de PythonAnywhere (ahí creo con username cristinafsanz, en vez de cristinafernandez como en local):

    ```
    python manage.py createsuperuser
    ```

    - Sección [Web](https://www.pythonanywhere.com/user/cristinafsanz/webapps/#tab_id_cristinafsanz_pythonanywhere_com): Viene la página web: http://cristinafsanz.pythonanywhere.com/.

    - Admin: http://cristinafsanz.pythonanywhere.com/admin/.

### [URLs en Django](https://tutorial.djangogirls.org/es/django_urls/)

- En el archivo mysite/urls.py:

```
from django.urls import path, include
from django.contrib import admin

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')),
]
```

- blog/urls.py:

```
from django.urls import path
from . import views
```

### [Vistas en Django](https://tutorial.djangogirls.org/es/django_views/)

- Una View es un lugar donde ponemos la "lógica" de nuestra aplicación. Pedirá información del modelo que has creado antes y se la pasará a la plantilla.

- blog/views.py

### [Primera plantilla](https://tutorial.djangogirls.org/es/html/)

Las plantillas se guardan en el directorio de blog/templates/blog. 

- Crear un directorio llamado templates dentro de blog. Luego crear otro directorio llamado blog dentro de tu directorio de templates.

- Crear fichero post_list.html dentro de blog/templates/blog

- Despliegue de nuevo

  - Subir a GitHub los cambios

  - En la consola de PythonAnywhere:

  ```
  cd ~/cristinafsanz.pythonanywhere.com
  $ git pull
  ```

  - Comprobar que están los cambios: puedes ir a la página "Files" y ver tu código en PythonAnywhere.

  - Finalmente, ve a la página "Web" y pulsa Reload en tu aplicación web.

### [ORM de Django y QuerySets](https://tutorial.djangogirls.org/es/django_orm/)

- Un QuerySet es, en esencia, una lista de objetos de un modelo determinado. Un QuerySet te permite leer los datos de la base de datos, filtrarlos y ordenarlos.

- En consola local:

```
python manage.py shell
```

```
>>> from blog.models import Post
>>> Post.objects.all()
<QuerySet [<Post: Post de prueba>, <Post: Otro post>, <Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>]>
```

- Crear objetos

```
>>> from django.contrib.auth.models import User
>>> User.objects.all()
<QuerySet [<User: cristinafernandez>]>
>>> me = User.objects.get(username='cristinafernandez')
>>> Post.objects.create(author=me, title='Sample title', text='Test')
<Post: Sample title>
```

- Comprobación

```
>>> Post.objects.all()
<QuerySet [<Post: Post de prueba>, <Post: Otro post>, <Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>, <Post: Sample title>]>
```

- Filtrar objetos

```
>>> Post.objects.filter(author=me)
<QuerySet [<Post: Post de prueba>, <Post: Otro post>, <Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>, <Post: Sample title>, <Post: Desde QuerySet>]>
```

```
>>> Post.objects.filter(title__contains='title')
<QuerySet [<Post: Sample title>]>
```

```
>>> from django.utils import timezone
>>> Post.objects.filter(published_date__lte=timezone.now())
<QuerySet [<Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>]>
```

```
post = Post.objects.get(title="Sample title")
post.publish()
```

```
>>> Post.objects.filter(published_date__lte=timezone.now())
<QuerySet [<Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>, <Post: Sample title>]>
```

- Ordenar posts

```
>>> Post.objects.order_by('created_date')
<QuerySet [<Post: Post de prueba>, <Post: Otro post>, <Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>, <Post: Sample title>, <Post: Desde QuerySet>]>
```

- Encadenar QuerySets

```
>>> Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')
<QuerySet [<Post: Ryan>, <Post: Ryan 2>, <Post: Ryan 3>, <Post: Sample title>]>
```

- Cerrar la consola

```
>>> exit()
```

### [Datos dinámicos en plantillas](https://tutorial.djangogirls.org/es/dynamic_data_in_templates/)

-  En nuestra view post_list necesitaremos tomar los modelos que deseamos mostrar y pasarlos a una plantilla. 

- blog/views.py

  ```
  from .models import Post
  ```

  - El punto antes de models indica el directorio actual o la aplicación actual. Ambos, views.py y models.py están en el mismo directorio.

  - En la función render tenemos el parámetro request (todo lo que recibimos del usuario via Internet) y otro parámetro dándole el archivo de la plantilla ('blog/post_list.html')

### [Plantillas de Django](https://tutorial.djangogirls.org/es/django_templates/)

- Las etiquetas de plantilla de Django nos permiten insertar elementos de Python dentro del HTML, para que puedas construir sitios web dinámicos más rápida y fácilmente.

### [CSS](https://tutorial.djangogirls.org/es/css/)

- Carpeta static dentro de blog. Y carpeta css dentro de static. Dentro blog.css

- Referenciarlo en post_list.html:

```
{% load static %}
```

```
<link rel="stylesheet" href="{% static 'css/blog.css' %}">
```

- Parar y arrancar si no se cargan los estilos

### [Extendiendo plantillas](https://tutorial.djangogirls.org/es/template_extending/)

- base.html.

- post_list.html:

  ```
  {% extends 'blog/base.html' %}
  ```

### [Extiende tu aplicación](https://tutorial.djangogirls.org/es/extend_your_application/)

- Crea un enlace a la página de detalle de una publicación.

- Añadir un enlace al fichero blog/templates/blog/post_list.html con Django template tags.

```
<a href="{% url 'post_detail' pk=post.pk %}">{{ post.title }}</a>
```

- Crea una URL al detalle de una publicación: blog/urls.py

- Añade la vista de detalle de la publicación: blog/views.py

- Crear una plantilla para post detail: post_detail.html

- Despliegue

  - Actualizar los ficheros estáticos (static files) en el servidor

  ```
  workon cristinafsanz.pythonanywhere.com
  python manage.py collectstatic
  ```

  - El comando manage.py collectstatic es un poco como el comando manage.py migrate. Hacemos cambios en nuestro código y luego le decimos a Django que los aplique, bien a la colección de ficheros estáticos o bien a la base de datos.

  - Reload en el servidor

### [Formularios de Django](https://tutorial.djangogirls.org/es/django_forms/)

- Podemos definir los formularios de Django desde cero o crear un ModelForm, el cual guardará el resultado del formulario en el modelo.

- Crear forms.py dentro de blog.

- Enlace a una página con el formulario: blog/templates/blog/base.html

- Vista post_new en blog/views.py.

- Plantilla post_edit.html

- Guardar el formulario: vista blog/views.py

- Validación de formularios: En nuestro modelo Post no dijimos (a diferencia de published_date) que estos campos no son requeridos, así que Django, por defecto, espera que estén definidos. Django se encarga de validar que todos los campos en el formulario estén correctos. 

- Editar formulario