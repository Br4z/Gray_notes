---
id: l0sk48zvo2y1ymlzbx0cr0r
title: Git and GitHub
desc: ''
updated: 1691022897909
created: 1688233264399
---

## Course

- Video title: Aprende Git y GitHub - Curso desde Cero.

- [Source](https://www.youtube.com/watch?v=mBYSUUnMt9M).

### ¿Qué es Git?

Es un sistema de control de versiones que nos permite rastrear los cambios que hemos hecho en un conjunto de archivos.

### ¿Qué es GitHub?

Es un servicio de hosting que nos permite almacenar proyectos de desarrollo de software y control de versiones usando Git.

### Conceptos básicos

- Control de versiones: sistema encargado de administrar los cambios realizados en programas de computadora o conjunto de archivos.

- Repositorio: colección de archivos de distintas versiones de un proyecto.

- Commit.

	Componentes básicos de la línea del tiempo de un proyecto de Git. Son como un registro o "foto" del estado de un proyecto en un momento específico.

	> El nombre de un commit debe ser bastante informativo, sin ser muy largo, es decir, conciso.

- Rama (branch): es una línea independiente de desarrollo en el repositorio.

### Configurar usuario y correo electrónico

- Usuario: `git config --goblal user.name "<user name>"`.

- Correo: `git config --goblal user.email "<user email>"`.

	> Es recomendable no poner un correo personal, sino uno que te proporciona GitHub.

> Si queremos hacer la configuración para un repositorio en específico, quitamos la flag `--global`.

Para ver los campos configurados, podemos escribir `git user.<attibute>`

- Rama creada por defecto: `git config --global init.defaultBranch "<branch name>"`.

### Crear repositorio

Escribimos el comando `git init` en la carpeta donde queremos crear el repositorio.

> init de initialize.

Se creará una carpeta llamada `.git`.

### Las tres áreas de Git

Dependiendo del área en la que está un archivo, nos referiremos a su estado de una forma diferente.

1. Directorio de trabajo.

	La carpeta del proyecto que contiene los archivos y el directorio `.git` del repositorio.

	Cuando un archivo se encuentra en esta área, decimos que el archivo (su versión) está modificada (modified).

2. Área de preparación.

	Conjunto de archivos y cambios que serán incluidos en el próximo **commit**.

	> En inglés **staging area**.

	Cuando un archivo se encuentra en esta área, decimos que el archivo (su versión) está preparada (staged).

3. Repositorio (directorio `.git`).

	Directorio que contiene los metadatos y las versiones de tu proyecto.

	Cuando un archivo se encuentra en esta área, decimos que el archivo (su versión) está confirmada (committed).

#### Estados de un archivo

- Modificado.

	Si la versión del archivo contiene cambios que **no** son parte del repositorio y **no** se han añadido al área de preparación.

- Preparado.

	Si la versión del archivo contiene cambios que **no** son parte del repositorio, pero fue añadido al área de preparación.

- Confirmada.

	Si la versión ya se encuentra en el directorio de Git.

### Git status

- `git status`: verificar el estado del repositorio.

En VSC el estado de un archivo tiene una representación visual:

- Modificado: su símbolo es una `U` (untracked) y es de color verde.

- Preparado: su símbolo es una `A` (added) y es de color verde.

- Confirmado: no tiene símbolo.

### Commits

El identificador de un commit se denomina **sha** (Secure Hash Algorithm) que identifica:

- Los cambios realizados.

- Donde se realizaron los cambios.

- Quien realizo los cambios.

En cada commit veremos fecha, hora, usuario y correo.

### Crear un commit

- `git commit -m "<message>`: crear un commit con el mensaje `<message>`.

- `git log`: ver historial de commits.

- `git commit`: crear un commit con el mensaje que pongas en el editor seleccionado como predeterminado.

### Asociar editor de texto

- `git config --global core.editor "<editor>"`: configurar un editor predeterminado para Git.

	> Para VSC se pone `code --wait`.
	>
	> El `--wait` es para que Git espere a que el archivo se guarde y se cierre antes de realizar cualquier acción.

### Modificar un commit

- `git commit --amend`: cambiar el mensaje del último commit hecho.

	> Este proceso puede ser arriesgado si lo hacemos sobre repositorios remotos (ya que puedan estar siendo usados por otras personas).

### Deshacer el último commit

- `git reset --soft HEAD~1`: deshacer el último commit hecho, dejando los cambios de ese commit (entre el último y el penúltimo) en el área de preparación.

	> `--soft` hace solo se deshaga el registro del commit y no cambie (modificar o eliminar) archivos.

	> `HEAD~1` hace referencia al último commit.

### Crear una rama en Git

- `git branch "<name>"`: crear una rama llamada `<name>` basada en la rama actual.

- `git branch`: ver ramas del repositorio local.

### Cómo cambiar de rama

- `git checkout "<name>"`: cambiar a la rama llamada `<name>`.

	> Con el flag `-b` se creará y cambiará a la rama llamada `<name>`.

### Cambiar el nombre de una rama

- `git branch -m "<name>"`: cambiar el nombre de la rama actual a `<branch name>`.

- `git branch -m "<branch name>" "<name>"`: cambiar el nombre de la rama `<branch name>` a `<name>`.

> `-m` de modify.

### Eliminar una rama

- `git branch -d "<branch name>"`: eliminar la rama llamada `<branch name>`.

	> `-d` de delete.

### git log para ramas

- `git log --oneline`: mostrar los registros de los commits en una línea.

- `git log -p`: mostrar los registros de los commits con las líneas modificadas (agregadas y eliminadas).

### Fusionar ramas en Git

Proceso que permite combinar varias líneas independientes de desarrollo en una sola rama.

- `git merge "<branch name>"`: recibir los cambios de la rama `<branch name>` en la rama actual.

Esta operación puede ocasionar **conflictos** cuando se editan las mismas líneas de los mismos archivos de las dos ramas al mismo tiempo.

- `git merge --continue`: continuar con el proceso de fusión, una vez solucionados los conflictos.

### Introducción a GitHub

GitHub es un servicio de **hosting** que nos permite almacenar proyectos de desarrollo de software con control de versiones usando Git.

### Clonar un repositorio

Crear una copia local de un repositorio remoto, incluyendo sus versiones e historial de commits.

"origin" es el nombre por defecto se le asigna al repositorio remoto del que estamos clonamos.

- `git clone <source>`: clonar el repositorio que este asociado con el origen `<source>`.

### Crear un commit en un repositorio clonado

- `git remote`: ver el nombre asociado al repositorio remoto.

	> `-v` para ver las direcciones asociadas a las operaciones **fetch** (traer cambios) y **push** (enviar cambios).

### Enviar cambios a GitHub (push)

- `git push`: enviar los cambios realizados en un repositorio local a un repositorio remoto para que ambos tengan la misma información.

### Ocultar tu correo en GitHub

En `Settings > Emails` encontrarás un correo **anónimo** (con dominio `@users.noreply.github.com`) asociado a tu correo primario.

> Lo recomendado es configurar tu Git con este correo **anónimo**.

### Configurar HTTPS con un token

En `Settings > Developer settings > Personal access tokes > Tokens` podemos crear un token con la fecha de expiración y permisos especificados.

### Incorporar cambios con git pull

- `git pull <source> <branch name>`: descargar el contenido de un repositorio remoto e **inmediatamente actualizar** un repositorio local para que ambos tengan la misma información.

> Normalmente, usamos origin como `<source>`.

### git pull vs. git fetch

- `git fect <source>`.

	**Verificar** los cambios realizados en el repositorio remoto sin combinar esos cambio con el repositorio local.

	Te permite saber **si se han realizado cambios** en el repositorio remoto desde la última vez que actualizaste tu repositorio local con **git pull**.

	Podremos ver los cambios (si lo hay) accediendo a la rama remota.

### Enviar repositorio local a GitHub

1. `git remote -v`: verificar que no tiene direcciones remotas asociadas.

2. `git remote add origin <source>`: agregar la dirección del repositorio remoto.

3. `git branch -m main`: cambiar el nombre de la rama actual a "main".

4. `git push origin main`: enviar los cambios de nuestra rama "main" a la rama "main" del repositorio remoto.

### Bifurcar un repositorio

Bifurcar un repositorio es crear una copia de un repositorio remoto en tu cuenta de GitHub (terminando con otro repositorio remoto).

> Normalmente, se hacen con el fin de contribuir al proyecto original mediante **pull requests**.

### Pull requests

Son una solicitud de combinar tus cambios con el repositorio original del proyecto.

Lo normal es hacer un **fork** del proyecto y crear una nueva rama que contendrá nuestro aporte al proyecto original.

### Issues en GitHub

Se pueden ver como una lista de pendientes (errores y mejoras) para un repositorio. Lo ideal es que si vamos a contribuir a un proyecto (repositorio), primero abramos un issue de lo que pensamos hacer antes de invertir tiempo en hacerlo.

> Es decir, lo estemos usando para ponernos de acuerdo con los **administradores** del repositorio original.

### Crear ramas en GitHub

Queremos traer una rama remota a nuestro repositorio local, podemos usar los siguientes enfoques:

1. Crear una rama local (con el mismo nombre que la rama creada remotamente) y hacer un `git pull origin <branch name>`.

2. Hacer un `git fetch origin` y cambiar a la rama `git checkout <branch name>`.

### Eliminar ramas

1. `git branch -d <branch name>`: eliminar la rama del repositorio local.

2. `git push origin -d <branch name>`: eliminar la rama del repositorio remoto.

## Situations

- Pull a remote branch.

	1. First.

		- `git fetch origin`.

	2. Second.

		- `git checkout <remote branch name>`.

		- `git pull origin <remote branch name>`.

- Stash changes.

	- `git stash`.

		> Optional, you can add a message adding `save <message>`.

- Unstash changes.

	1. The stashed will be removed after you apply them to the code you're working on.

		- `git stash pop`.

	2. The stashed won't be removed after you apply them to the code you're working on.

		- `git stash apply`.

- Discard changes.

	- `git rm --cached <file>`.

		> To discard all, use the wildcard `*`.

- Delete commits history.

	1. `git checkout --orphan new_branch`.

	2. Commit all files.

	3. `git branch -d main`.

	4. `git branch -m main`.

	5. `git push -f origin main`.
