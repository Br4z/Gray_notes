---
id: 6l3kcjj0n3chaf4npuxbpvi
title: Django course
desc: ''
updated: 1682214290785
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