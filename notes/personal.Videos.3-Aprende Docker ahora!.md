---
id: m27nuvkj2rfiek3k3wbjiyj
title: 3-Aprende Docker ahora!
desc: ''
updated: 1682893185106
created: 1682892977504
video_title: Aprende Docker ahora! curso completo gratis desde cero!
date: 2023-04-30T00:00:00.000Z
source: 'https://www.youtube.com/watch?v=4Dko5W96WHg&t'
---

# Permite

- Desarrolla en equipo con un ambiente controlado (lo que genera menos bugs).
- Instalar dependencias rápidamente.
- Hacer despliegues de una forma simple.

# ¿Que es un contenedor?

Es una manera de empaquetar nuestras aplicaciones, dicha operación nos permite incluir todas las dependencias y archivos de configuración que tengan, lo que los hace **portables**, y en consecuencia fáciles de compartir.

# ¿Donde se almacenan?

En un repositorio de contenedores, pueden ser **privados** o **públicos** (Docker Hub).

# Antes de los contenedores

Las personas que trabajaban en un proyecto usaban sus propios computadores, lo que ocasionaba diferencias en la instalación de dependencias (podría considerarse factor humano) y finalmente propiciaba la aparición de errores. Docker entra a solucionar este problema (automatizar dependencias).

# ¿Que es una imagen?

Es un empaquetado que contiene:

- Dependencias
- Código

Finalmente esto es lo que se comparte

# ¿Que es un container?

Son capas de imágenes.

# Virtualization

Docker (nos podemos referir a el como una forma de virtualizer) usa el kernel del sistema operativo en el que se esta ejecutando, lo que hace que las imágenes de docker pesen menos (orden de los MB).

## Bonus

Existen tres tipos de virtualization:

- Para virtualization
- Virtualization parcial
- Virtualization completa

Haciendo referencia a como el hardware del **anfitrión** se conecta con el del **cliente**

# ¿Que es Docker Desktop?

- Una virtual machine (corre Linux y ejecuta **containers**).
- Permite acceder al sistema de archivos y a la red.
- Docker Compose, C.L.I(commend line interface) ... otras herramientas.
- Corre de forma nativa en Windows WSL 2

# Instalación

Entramos a la [pagina](https://www.docker.com/) y seleccionamos la version correspondiente a nuestro S.O.

# Comandos de imágenes

Debemos asegurarnos de que Docker este ejecutándose.

- `docker images` nos muestra las imágenes que hemos descargados.
- `docker pull <image>:<version>` para descargar una imagen.
- `docker image rm <image>:<version>` para eliminar una imagen.

# Comandos de contadores

- `docker create <image>` para crear un contenedor, para asignarle un nombre se le agrega el modificador `--name <container name>`
- `docker start <container ID or name>` para ejecutar un contenedor.
- `docker ps` para ver la lista de contenedores ejecutándose, para verlos todos agregamos el modificador `-a`.
- `docker stop <container ID or name>` para detener la ejecución de un contenedor.
- `docker rm <container ID or name>` para eliminar un contenedor.
- `docker logs <container ID or name>` para ver los **logs** de un contenedor (después de hacerlo nos devuelve el prompt), con el modificador `--follow` nos quedamos a la escucha.
- `docker run <container ID or name>` si el contenedor existe, ejecutara el existente, en el caso contrario, descargara la imagen y ejecutara el descargado. Con el modificador `-d` hacemos que nos devuelva el prompt, y no se quede a la escucha de logs.
    > Este ademas acepta todos los modificadores de `--name` y port mapping.

# Port mapping

Consiste en asignar puertos de nuestra maquina (**anfitrión**) a los puertos de los contenedores (**huéspedes**). Esto se hace con el siguiente modificador en la creación del contenedor `-p<host port>:<guest port>` o `-p<guest port>` (para dejar que docker decida), los "enlaces" que hagamos se verán cuando listemos los contenedores.

# Configuración de contenedores

La documentación de los contenedores se encuentra en su respectiva pagina del [Docker Hub](https://hub.docker.com/).

## Dockerfile

Con el propósito de personalizar el despliegue de nuestros contenedores esta este archivo `Dockerfile`, su estructura es la siguiente

```Dockerfile
FROM <image>:<image version or label>

RUN mkdir -p /home/app  # Esta ruta se creara dentro del contenedor

COPY <host directory> # Estamos copiando el código fuente (del host) al contenedor

CMD [<interpreter>, <index file directory>]
```

# Redes

Llamamos red a un conjunto de contenedores que están comunicados entre si.

## Comandos

- `docker network ls` listar las redes.
- `docker network create <network name>` crear una red con el nombre especificado.
- `docker network rm <network name>` eliminar una red con el nombre especificado.
- `docker build -t <image name>:<image version or label> <Dockerfile directory>` crear una red con base a un archivo `Dockerfile`.
- Para crear un contenedor en una red, hacemos uso del comando normal con el modificador `--network <network name>`

# Docker compose

Es un herramienta que nos facilita la tarea de crear un contenedor, es un archivo llamado `docker-compose` y tiene la siguiente estructura:

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

Para ejecutar la configuración descrita usamos el comando `docker compose up` estando en el directorio del archivo. El comando creara los contenedores y redes necesarios, para eliminar todo lo que haga el comando, podemos usar el comando `docker compose down`.