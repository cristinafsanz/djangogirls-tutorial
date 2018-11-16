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

#### myvenv en .gitignore para no subirlo al repo

```
cat .gitignore
myvenv
```