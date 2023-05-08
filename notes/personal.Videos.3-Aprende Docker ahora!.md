---
id: m27nuvkj2rfiek3k3wbjiyj
title: 3-Aprende Docker ahora!
desc: ''
updated: 1683505748828
created: 1682892977504
video_title: Aprende Docker ahora! curso completo gratis desde cero!
date: 2023-04-30T00:00:00.000Z
source: https://www.youtube.com/watch?v=4Dko5W96WHg&t
---

# Permite

- Desarrolla en equipo con un ambiente controlado (lo que genera menos bugs).
- Instalar dependencias rápidamente.
- Hacer despliegues de una forma simple.

# ¿Qué es un contenedor?

Es una manera de empaquetar nuestras aplicaciones, dicha operación nos permite incluir todas las dependencias y archivos de configuración que tengan, lo que los hace **portables**, y en consecuencia fáciles de compartir.

# ¿Dónde se almacenan?

En un repositorio de contenedores, pueden ser **privados** o **públicos** (Docker Hub).

# Antes de los contenedores

Las personas que trabajaban en un proyecto usaban sus propios computadores, lo que ocasionaba diferencias en la instalación de dependencias (podría considerarse factor humano) y finalmente propiciaba la aparición de errores. Docker entra a solucionar este problema (automatizar dependencias).

# ¿Qué es una imagen?

Es un empaquetado que contiene:

- Dependencias
- Código

Finalmente, esto es lo que se comparte

# ¿Qué es un contenedor?

Son capas de imágenes.

> Son livianas en comparación con las máquinas virtuales (mientras que las primeras van en orden de lo MB, las segundas van en orden de GB).

# Virtualización

Docker usa el kernel del sistema operativo en el que se está ejecutando, lo que hace que las imágenes de Docker pesen menos.

## Bonus

Existen tres tipos de virtualización:

- Para virtualización (alto)
- Virtualización parcial (medio)
- Virtualización completa (ninguno)

Haciendo referencia a como el hardware del **anfitrión** se conecta con el del **cliente**.

# ¿Qué es Docker Desktop?

- Una máquina virtual (corre Linux y ejecuta **contenedores**).

- Permite acceder al sistema de archivos y a la red (tanto interna como externa).

- Docker Compose, CLI (commend line interface) ... otras herramientas.

- Corre de forma nativa en Windows WSL 2.

# Instalación

Entramos a la [página](https://www.docker.com/) y seleccionamos la version correspondiente a nuestro SO.

# Comandos

## Imágenes

Debemos asegurarnos de que Docker esté ejecutándose.

- `docker images`: muestra las imágenes que hemos descargado.
- `docker pull <image>:<version>`: descargar una imagen.
- `docker image rm <image>:<version>`: eliminar una imagen.

## Contadores

- `docker create <image>`: crear un contenedor.

    > `--name <container name>`: asignarle un nombre al contenedor.

- `docker start <container ID or name>`: ejecutar un contenedor.

- `docker ps`: ver la lista de contenedores ejecutándose.

    > Para verlos todos (los que están y no están corriendo) agregamos el modificador `-a`.

- `docker stop <container ID or name>`: detener la ejecución de un contenedor.

- `docker rm <container ID or name>`: eliminar un contenedor.

- `docker logs <container ID or name>`: ver los **logs** de un contenedor (después de hacerlo nos devuelve el prompt).

    > Con el modificador `--follow` nos quedamos a la escucha.

- `docker run <container ID or name>`: si el contenedor existe, ejecutará el existente, en el caso contrario, descargará la imagen, creará un contenedor con la imagen descargada y lo ejecutará.

    > Con el modificador `-d` (detached) hacemos que nos devuelva el prompt (no se quede a la escucha de logs).

    > Acepta todos los modificadores de `--name` y port mapping.

    > Podríamos verlo como un `pull`, `create` y `run`.

> Para referirnos a un contenedor, basta con poner algunos dígitos del ID.

# Port mapping

Consiste en asignar puertos de nuestra máquina (**anfitrión**) a los puertos de los contenedores (**huéspedes**). Esto se hace con el siguiente modificador en la creación del contenedor `-p <host port>:<guest port>` o `-p <guest port>` (para dejar que Docker decida), los "enlaces" que hagamos se verán cuando listemos los contenedores.

# Configuración de contenedores

La documentación de los contenedores se encuentra en su respectiva página dentro del [Docker Hub](https://hub.docker.com/).

## Ejemplo (conexión a una base de datos de Mongo)

1. `docker create -p 27017:27017 --name monguito -e MONGO_INITDB_ROOT_USERNAME=nico -e MONGO_INITDB_ROOT_PASSWORD=password mongo`.

    > `-e` es para pasar variables de entorno.

2. `docker ps -a`.
3. `docker start monguito`.

## Dockerfile

Con el propósito de personalizar el despliegue de nuestros contenedores está el archivo `Dockerfile`, su estructura es la siguiente:

```Dockerfile
FROM <image>:<image version or label>

RUN mkdir -p /home/app  # Esta ruta se creara dentro del contenedor

COPY <host directory> # Estamos copiando el código fuente (del host) al contenedor

CMD [<command>, <argument>]
```

### Ejemplo

```Dockerfile
FROM node:18

RUN mkdir -p /home/app

COPY . /home/app

EXPOSE 3000

CMD ["node", "/home/app/index.js"]
```

# Redes

Llamamos red a un conjunto de contenedores que están comunicados entre sí.

## Comandos

- `docker network ls`: listar las redes.

- `docker network create <network name>`: crear una red con el nombre especificado.

- `docker network rm <network name>`: eliminar una red con el nombre especificado.

- `docker build -t <image name>:<image version or label> <Dockerfile path>` crear una red con base a un archivo `Dockerfile`.

- Para crear un contenedor vinculado a una red en específico, hacemos uso del comando normal con el modificador `--network <network name>`

## Ejemplo

Con el fin de tener una [aplicación](https://github.com/nschurmann/mongoapp-curso-docker/blob/main/index.js) en un contenedor y la base de datos en otra, vamos a seguir los siguientes pasos:

1. Crear la red por la cual los contenedores se van a comunicar: `docker network create mired`.

2. Cambiar la ruta donde hacemos la conexión a la base de datos.

    ```js
    mongoose.connect('mongodb://nico:password@localhost:27017/miapp?authSource=admin')

    mongoose.connect('mongodb://nico:password@monguito:27017/miapp?authSource=admin')
    ```

3. Construimos la imagen para nuestra aplicación: `docker built -t miapp:1 .`

    > El `.` hace referencia a la ruta donde esta el **Dockerfile**.

4. Crear los contenedores: `docker create docker create -p 27017:27017 --network mired --name monguito -e MONGO_INITDB_ROOT_USERNAME=nico -e MONGO_INITDB_ROOT_PASSWORD=password mongo` y `docker create -p 3000:3000 --name chanchito --network mired myapp:1`

> Después de hacer estos pasos deberíamos tener conexión a la aplicación a traves de nuestro puerto 3000.

# Docker compose

Es una herramienta que nos facilita la tarea de crear un contenedor, es un archivo llamado `docker-compose.yml` y tiene la siguiente estructura:

```docker-compose
version: "<version>"
services:
    <container name>:
        build: <dockerfile directory>
        ports:
            - "<host port>:<guest port>"
            ..
        links:
            - <container name>
            ...
        environment:
            - <environment configuration>
            ...
```

## Ejemplo

```docker-compose
version: "3.9"
services:
    chanchito:
        build: .
        ports:
            - "3000:3000"
        links:
            - monguito
    monguito:
        image: mongo
        ports:
            - "27017:27017"
        environment:
            - MONGO_INITDB_ROOT_USERNAME=nico
            - MONGO_INITDB_ROOT_PASSWORD=password
```

Para ejecutar la configuración descrita usamos el comando `docker compose up` estando en el directorio del archivo. El comando creará los contenedores y redes necesarios, para eliminar todo lo que haga el comando, podemos usar el comando `docker compose down`.

# Volúmenes

Responde a la necesidad de conservar información y manifestar cambios de nuestra aplicación.

## Tipos

- Anónimos: solo indicamos la ruta del contenedor.

    > No los podemos referenciar.

- De anfitrión u host: especificamos la ruta del contenedor que va a ser montada en la ruta del host (también especificada).

- Nombrado: solo indicamos la ruta del contenedor.

    > Si lo podemos referenciar.

## Ejemplo

```docker-compose
version: "3.9"
services:
    chanchito:
        build: .
        ports:
            - "3000:3000"
        links:
            - monguito
    monguito:
        image: mongo
        ports:
            - "27017:27017"
        environment:
            - MONGO_INITDB_ROOT_USERNAME=nico
            - MONGO_INITDB_ROOT_PASSWORD=password
        volumes:
        - mongo-data:/data/db
volumes:
    mongo-data:
```

# Ambientes y hot reload

Consiste en tener varios **Dockerfile** según nuestro propósito.

## Ejemplo (desarrollo)

```Dockerfile
FROM node:18

RUN npm -i -g nodemon
RUN mkdir -p /home/app

WORKDIR /home/app

EXPOSE 3000

CMD ["nodemon", "index.js"]
```

```docker-compose
version: "3.9"
services:
    chanchito:
        build:
            context: .
            dockerfile: Dockerfile.dev
        ports:
            - "3000:3000"
        links:
            - monguito
        volumes:
            - .:/home/app
    monguito:
        image: mongo
        ports:
            - "27017:27017"
        environment:
            - MONGO_INITDB_ROOT_USERNAME=nico
            - MONGO_INITDB_ROOT_PASSWORD=password
        volumes:
        - mongo-data:/data/db
volumes:
    mongo-data:
```

Ahora ejecutamos `docker compose -f docker-compose-dev.yml`.

 > `-f` es para especificar el archivo.
