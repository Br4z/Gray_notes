---
id: 6l3kcjj0n3chaf4npuxbpvi
title: Django project
desc: ''
updated: 1683918841337
created: 1682208376319
---

1. Configurar un ambiente virtual de desarrollo.

    ```
    python -m venv .venv      -> Initialize the environment
    source .venv/bin/activate -> Activate the environment
    ```

2. Instalar requerimientos: `pip install -r requirements.txt`.

3. Configurar un proyecto Django: `django-admin startproject flowers_project .`.

4. Crear una aplicación Django: `python manage.py startapp flowers_app`.

5. Configurar variables de ambiente.

    1. Crear archivo `.env`.

    2. Escribir lo siguiente en el archivo `.env` (llenando los campos solicitados):

        ```
        POSTGRES_NAME = User & Default database
        POSTGRES_USER = User & Default database
        POSTGRES_PASSWORD = Password
        POSTGRES_HOST = Server
        POSTGRES_PORT = 5432
        SECRET_KEY = Secret key del archivo en nombre-proyecto/settings.py
        ```

6. Agregar lo siguiente al `settings.py`:

    ```Python
    import os
    from dotenv import load_dotenv
    load_dotenv()
    ```

    ```Python
    SECRET_KEY  =  os.getenv('SECRET_KEY') # Load .env vars

    ALLOWED_HOSTS  =  ["*"] # For this project we'll allow any host

    INSTALLED_APPS  =  [
        ...
        'cloudinary_storage', # To storages images
        'cloudinary',
        'rest_framework',
        'corsheaders',  # To configure the domains allowed to do petitions to the app (is required for the React part)
        'flowers_app',
    ]
    ```

7. Establecer la configuración de la base de datos.

    ```Python
    DATABASES  =  {
        "default": {
            "ENGINE": "django.db.backends.postgresql",
            "NAME": os.getenv("POSTGRES_NAME"),
            "USER": os.getenv("POSTGRES_USER"),
            "PASSWORD": os.getenv("POSTGRES_PASSWORD"),
            "HOST": os.getenv("POSTGRES_HOST"),
            "PORT":os.getenv("POSTGRES_PORT"),
        }
    }
    ```

8. Creamos un superusuario: `python manage.py createsuperuser`

8. Revisar el estado de la aplicación.

    1. `python manage.py makemigrations`
    2. `python manage.py migrate`
    3. `python manage.py runserver`

9. Agregar lo siguiente al `settings.py`

    ```Python
    MEDIA_URL  =  "/media/"

    DEFAULT_FILE_STORAGE  =  "cloudinary_storage.storage.MediaCloudinaryStorage"

    CLOUDINARY_STORAGE  =  {
        "CLOUD_NAME": os.getenv("CLOUDINARY_CLOUD_NAME"),
        "API_KEY":  os.getenv("CLOUDINARY_API_KEY"),
        "API_SECRET":os.getenv("CLOUDINARY_API_SECRET"),
        "SECURE": True,
    }
    ```

10. Hacer migraciones y migrar.

11. Clonar el repositorio del front-end: `git clone https://github.com/michelle-gh/template-react-taller.git`.

12. Instalar dependencias: `npm install --f`

13. Probar la aplicación: `npm start`.

14. Configurar la comunicación entre Django y React en el archivo `settings.py`.

    ```Python
    CORS_ALLOWED_ORIGINS = [
        'http://localhost:3000',
    ]

    CORS_ALLOW_ALL_ORIGINS = True

    CORS_ORIGIN_WHITELIST = [
        'http://localhost:3000'
    ]

    MIDDLEWARE = [
        ...
        'corsheaders.middleware.CorsMiddleware',
    ]
    ```
