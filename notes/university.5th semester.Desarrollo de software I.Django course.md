---
id: 6l3kcjj0n3chaf4npuxbpvi
title: Django course
desc: ''
updated: 1682895183045
created: 1682208376319
---

- [Fuente](https://www.youtube.com/watch?v=T1intZyhXDU)

# Pasos previos

- Instalar [python](https://www.python.org/downloads/)
- Verificar que tenemos python y pip

    ```
    python --version -> Ver la version de python instalada
    pip --version    -> Ver la version de pip instalada
    ```

# Entornos virtuales

Nos permiten tener por proyecto

- Una version de python
- Una version de pip
- Paquetes

> Con el fin de aislar nuestros proyectos para que no hayan interferencias.

---

1. Instalamos un gestor de entornos virtuales: `pip install virtualenv`

    > En caso de estar en Arch `pacman -S python-virtualenv`

2. Inicializamos el entorno virtual en la carpeta donde vayamos a tener un proyecto: `virtualenv env`

3. Abrimos el proyecto con VSC y seleccionamos el interprete del entorno virtual (con la paleta de comandos)

    > Si queremos entrar manualmente podemos escribir `. \venv\Scripts\activate`.

4. Instalamos Django:  `pip install django`

    Para comprobar que se ha instalado correctamente escribimos `django-admin --version` o `python -m django --version` debería mostrarnos la version.

    Otra forma de comprobar si esta instalado es escribiendo

    ```python
    import django
    django.get_version()
    ```

    en el interprete de python.

# Crear proyecto

- Crear un proyecto: `django-admin startproject <name> .`

    > Es recomendable no usar nombres reservados.

- Correr proyecto: `python manage.py runserver <port>`

    > Por defecto corre en el puerto 8000.

# Estructura de un proyecto

- `manage.py`: contiene comandos administrativos.
- `db.sqlite3`: base de datos para testing.
- `<project folder>`: donde se almacena nuestro proyecto.

# Creación de apps

- Django maneja algo llamado apps, que se definen como ciertas funcionalidades juntas.

- Podemos crear una con el comando `python manage.py startapp <app name>`.

    > Cada vez que creemos una app, junto con ella se creara una carpeta.

- Desde la carpeta de nuestro proyecto podremos llamar a las apps que hayamos creado

# Estructura de una app

- Django ya viene con un modulo para interactuar con la base de datos.

# Modelos y bases de datos con Sqlite3

-  Escribimos los comandos `python manage.py makemigrations <app name>?` y `python manage.py migrate <app name>?` para que el proyecto detecte los nuevos modelos que hayamos creado.

    > Para ver el contenido del archivo `db.sqlite3` podemos usar el programa [DB Browser for SQLite](https://sqlitebrowser.org/dl/)

# Django shell

- `python manage.py shell`

```python
from myapp.models import Project, Task

project = Project(name = "My first project")

project.save() # Add a register in the database

Project.objects.all() # Get all register in the table

Project.objects.get(id = 1) # Get a specific register in the table

project.task_set.all() # Get Task related to a project

project.task_set.create() # Add a task to a project (through its foreign key)

project.task_set.get(id = 1) # Get a specific task from a project

Projects.objects.filter(name__startwith = "application") # An get without an error
```

# Params