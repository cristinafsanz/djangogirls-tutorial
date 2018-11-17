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


