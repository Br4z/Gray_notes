---
id: xsejsb6z7acb7zoxptblpyo
title: CURSO de HTML5 desde CERO 2021
desc: ''
author: Dorian Desings
source: https://www.youtube.com/playlist?list=PLROIqh_5RZeB92ME1GFyeqDVOa-gL0Ybd
updated: 1704685591845
created: 1703983410606
---

## 3 - Vocabulario web

- IP: identificador numérico de una página web, es único y representa la dirección donde está el ordenador que contiene esa página web.

- Dominio web / URL (Uniform Resources Locator): nombre asociado a la IP que utilizamos para solicitar recursos, en nuestro caso un sitio web.

- DNS (Domain Name System): servidor cuya principal función es traducir el nombre de dominio a su identificador único.

- Sitio web: conjunto de uno o varios recursos web alojados en el mismo dominio.

- Servidor web: ordenador cuyo objetivo es servir recursos web.

- Hosting: almacenamiento del servidor web. El disco duro donde el servidor guarda los recursos.

- Petición: acción de pedir recursos a un servidor.

## 4 - ¿Qué es HTML?

- Es un lenguaje de marcado de hipertexto (Hyper Text Markup Languaje). **No** es un lenguaje de programación, es un lenguaje de
estructura.

- Es la base con la que están creadas **todas** las páginas web del mundo.

- Las etiquetas que usamos en el lenguaje le dicen al navegador y a los motores de búsqueda cuál es la estructura de los documentos, elementos, organización, etc.

## 5 - Historia de HTML

- 1989: inicio de su desarrollo.

- 1991: lanzamiento de la web. Se basa en 3 conceptos: HTTP (Hyper Text Transfer Protocol), HTML (Hyper Text Markup Languaje) y URL (Uniform Resources Locator).

- 1992: lanzamiento de HTML (nació de SMGL. Creado por Tim Bernes Lee).

- 1994: creación de la W3C (consorcio que define los estándares de la web).

- 1998: HTML 4 (versión que más duró de HTML).

- 1999: HTML 4.1 — XHTML (actualización del estándar HTML4).

- 2004: creación de la WHATWG.

- 2008: HTML5 (lanzado por WHATWG de forma independiente).

- 2014: estándar HTML5 (lanzado por W3C de forma oficial).

## 11 - Etiqueta section vs article

- `<section>...</section>`: representa una sección genérica de un documento. Sirve para determinar qué contenido corresponde a qué parte de un esquema.

- `<article>...</article>`: representa una composición autocontenida en un documento, una página, una aplicación o en un sitio, que se quiere que sea distribuíble y/o reutilizable de manera independiente.

	> Lo que permite un `<header>` y `<footer>` propios.

## 14 - Etiqueta aside

- `<aside>...</aside>`: representa una sección de una página que consiste en contenido que está indirectamente relacionado con el contenido principal del documento.

## 15 - Elementos de bloque y elementos de línea

- Elementos de bloque: ocupa todo el espacio de su elemento padre (contenedor), creando así un "bloque".

- Elementos de línea: ocupa solo el espacio delimitado por las etiquetas que definen el elemento en línea.

## 17 - Elementos de línea

- Etiquetas de jerarquización.

	1. `<em>...</em>`.

	2. `<strong>...</strong>`.

	3. `<normal text>`.

	4. `<small>...</small>`.

- `<br>` (line break): produce un salto de línea en el texto (retorno de carro).

- `<wbr>` (word break opportunity): representa una posición dentro del texto donde el explorador puede opcionalmente saltar una línea , aunque sus reglas de salto de línea de otra manera no crearían un salto en esa posición.

	> Por defecto, los `-` representan posiciones con este comportamiento.

- `<time>...</time>`: representa un periodo específico en el tiempo.

- `<i>...</i>` (italic): italica.

- `<b>...</b>` (bold): negrita.

- `<u>...</u>` (underline): subrayado.

- `<sup>...</sup>`: define un fragmento de texto que se debe mostrar, por razones tipográficas, más alto, y generalmente más pequeño, que el tramo principal del texto, es decir, en superíndice.

- `<sub>...</sub>`: define un fragmento de texto que se debe mostrar, por razones tipográficas, más bajo, y generalmente más pequeño, que el tramo principal del texto, es decir, en subíndice.

## 19 - Introducción a los atributos

Son valores adicionales que configuran los elementos y/o ajustan su comportamiento. En términos generales hay dos tipos de atributos:

1. Comunes: `<attribute>=<value>`.

2. Booleanos: `<attribute>`.

## 21 - Atributos globales

- `class=<value>`: es una lista de las clases del elemento separada por espacios. Las clases permiten a CSS y Javascript seleccionar y acceder a elementos específicos a través de los selectores de clase o funciones como el método `document.getElementsByClassName` del DOM.

- `id=<id>`: define un identificador único (ID) el cual no debe repetirse en todo el documento. Su propósito es identificar el elemento al vincularlo (usando un identificador de fragmento), en scripts u hojas de estilo (con CSS).

- `title=<title>`: contiene un texto representando información relacionada con el elemento al cual pertenece.

	> Tal información puede típicamente, pero no necesariamente, ser presentada al usuario como un tip.

- `data-<data name>`: forman una clase de atributos, llamados atributos de datos modificables, permite a la información propietaria ser intercambiada entre el HTML y su representación en el DOM que puede ser usada por scripts.

	> La propiedad `HTMLElement.dataset` otorga acceso a ellos.

## 22 - Introducción a enlaces

- Enlaces / hipervínculos: nos permiten vincular documentos a otros documentos o recursos, vincular a partes específicas de documentos o hacer que las aplicaciones estén disponibles en una dirección web.

	`<a href=<source>...</a>`.

## 23 - Rutas absolutas y relativas

### Rutas absolutas

El navegador buscará ese recurso desde la raíz superior del servidor, sin referencia al contexto dado por el documento actual.

#### Ejemplo (rutas absolutas)

- URL completa: `https://developer.mozilla.org/es/docs/Learn`.

- Protocolo implícito: `//developer.mozilla.org/es/docs/Learn`.

	El navegador llamará a esa URL con el mismo protocolo que el utilizado para cargar el documento que aloja esa URL.

- Nombre de dominio implícito: `/es/docs/Learn`.

	El navegador utilizará el mismo protocolo y el mismo nombre de dominio que el utilizado para cargar el documento que aloja esa URL.

	> Este es el caso de uso más común para una URL absoluta dentro de un documento HTML.

### Rutas relativas

El navegador buscará ese recurso desde la ruta del documento actual.

#### Ejemplo (rutas relativas)

Supongamos que las URL se invocan desde el documento ubicado en la siguiente URL: `https://developer.mozilla.org/es/docs/Learn`.

- Subrecursos: `Skills/Infrastructure/Understanding_URLs`.

	El navegador intentará encontrar el documento en un subdirectorio del que contiene el recurso actual.

	> `https://developer.mozilla.org/es/docs/Learn/Skills/Infrastructure/Understanding_URLs`.

- Volviendo en el árbol de directorios: `../CSS/display`.

	El navegador subirá al directorio padre (el directorio que contiene el recurso actual).

	> Se usa el `../` convención de escritura, heredada del mundo del sistema de archivos UNIX.

	> `https://developer.mozilla.org/es/docs/Learn/../CSS/display` o `https://developer.mozilla.org/es/docs/CSS/display`.

## 24 - Atributos de los enlaces

- `target=<value>`: especifica en donde desplegar la URL enlazada.

	- `_self`: carga la URL en el mismo contexto de navegación que el actual. Este es el comportamiento por defecto.

	- `_blank`: carga la URL en un nuevo contexto de navegación. Usualmente, es una pestaña, sin embargo, los usuarios pueden configurar los navegadores para utilizar una ventana nueva en lugar de la pestaña.

- `download=<value?>`: indica descargar a los navegadores una URL en lugar de navegar hacia ella, por lo que el usuario será dirigido para guardarla como un archivo local. Si el atributo tiene un valor, este se utilizará como nombre de archivo por defecto en el mensaje Guardar que se abre cuando el usuario hace clic en el enlace.

## 27 - Listas desordenadas

- `<ul>...</ul>` (unordered list): crea una lista desordenada.

> Los elementos de las listas (excepto por las de definición) son `<li>...</li>` (list item).

## 28 - Listas ordenadas

- `<ol>...</ol>` (ordered list): crea una lista ordenada.

## 29 - Listas de definición

- `<dl>...</dl>` (definition list): representa una lista descriptiva. El elemento encierra una lista de grupos de términos (especificados con el uso del elemento `<dt>...</dt>`) y de descripciones (especificadas con elementos `<dd>...</dd>`).

## 30 - Listas anidadas y atributos

- `<ul>`.

	- `type=<value>`: estilo de numeración.

		- `circle`.

		- `disc`.

		- `square`.

- `<ol>`.

	- `type=<value>`: estilo de numeración.

		- `a`: letras minúsculas.

		- `A`: letras mayúsculas.

		- `i`: números romanos en minúsculas.

		- `I`: números romanos en mayúsculas.

		- `1`: números (por defecto).

	- `start=<value>`: número inicial de la secuencia.

## 32 - Estructura básica de una tabla

- `<table>...</table>`: delimitador del contenido de la tabla.

- `<tr>...</tr>` (table row): construye una fila en la tabla.

- `<td>...</td>` (table data): construye una celda en la tabla.

## 33 - Estructura completa de una tabla

- `<caption>...</caption>`: es el encargado de darle un título descriptivo a las tablas.

- `<thead>...</thead>`: define un conjunto de filas que serán la cabecera de las columnas de la tabla.

- `<tbody>...</tbody>`: encapsula un conjunto de filas de la tabla (elementos `<tr>`), indicando que componen el cuerpo de la tabla (`<table>`).

	> Es opcional si no se pone un `<thead>`.

## 34 - Atributos de las tablas

- `rowspan=<value>`: indica el número de filas que abarca la celda.

- `colspan=<value>`: indica el número de columnas que abarca la celda.

## 35 - Seleccionar columnas

- `<colgroup> ... </colgroup>`: define un grupo de columnas dentro de una tabla.

	- `span=<value>`: indica el número de columnas consecutivas que abarca el elemento `<colgroup>`.

## 37 - Más etiquetas importantes de bloque

- `<address>...</address>`: aporta información de contacto para su `<article>` más cercano o ancestro `<body>`; en el último caso lo aplica a todo el documento.

- `<blockquote>...</blockquote>`: crea citas en bloque, marca las citas a otros autores o documentos.

	- `cite=<value>`: proporciona un enlace al documento original o fuente.

- `<pre>...</pre>`: representa texto preformateado. El texto en este elemento típicamente se muestra en una fuente fija, no proporcional, exactamente como es mostrado en el archivo.

- `<div>...</div>` (division): sirve para crear secciones o agrupar contenidos.

- `<hr>...</hr>` (horizontal line): representa un cambio de tema entre párrafos.

	> En versiones previas de HTML representaba una línea horizontal. Aún puede ser representada como una línea horizontal en los navegadores visuales, pero ahora es definida en términos semánticos y no tanto en términos representativos, por tanto, para dibujar una línea horizontal se debería usar el CSS apropiado.

## 38 - Más etiquetas de línea

- `<span>...</span>`: sirve para aplicar estilo al texto o agrupar elementos en línea.

- `<q>...</q>`: indica que el texto adjunto es una cita corta en línea.

	> La mayoría de los navegadores modernos implementan esto rodeando el texto entre comillas.

- `<code>...</code>`: sirve para marcar el código de un programa.

---

Una **entidad** es un conjunto de caracteres ("string") que comienza con un ampersand (`&`) y termina con un punto y coma (`;`) .

> Son utilizadas frecuentemente para imprimir en pantalla caracteres reservados (aquellos que serían interpretados como HTML por el navegador) o invisibles (como tabulaciones).

> En esta [página](https://www.ascii-code.com) se pueden encontrar el HTML **number** y **name** de todos los caracteres.

## 40 - Estructura básica de un Formulario

- `<form>...</form>`: representa una sección de un documento que contiene controles interactivos que le permiten al usuario enviar información a un servidor web.

- `<label>...</label>`: representa una etiqueta para un elemento en una interfaz de usuario.

- `<input>...</input>`: se usa para crear controles interactivos para formularios basados en la web con el fin de recibir datos del usuario.

- `<button>...</button>`: representa un elemento cliqueable de tipo botón.

## 41 - Asociar input y label

- `<label>`.

	- `for=<ID>`: el ID del elemento de formulario etiquetable (normalmente un `<input>`) relacionado en el mismo documento que el elemento label.

## 42 - button vs type button

- `<input>`.

	- `type=<value>`.

		- `button`: botón sin un comportamiento específico.

> Frente al comportamiento por defecto de `<button>`, un `<input>` del tipo botón no envía información al formulario.

## 43 - Inputs para fechas

- `<input>`.

	- `type=<value>`.

		- `datetime-local`: control para introducir fecha y hora, sin zona horaria específica.

		- `date`: control para introducir una fecha (año, mes y día, sin hora).

		- `datatime`: control para introducir una fecha y hora (horas, minutos, segundos y fracción de segundo).

		- `time`: control para introducir un valor de tiempo sin zona horaria específica.

		- `month`: control para introducir un mes y año, sin zona horaria específica.

		- `week`: control para introducir una fecha que consiste en el número de semana y el año, sin zona horaria específica.

## 44 - Inputs para móviles

- `<input>`.

	- `type=<value>`.

		- `search`: campo para introducir textos de búsqueda.

			> Los saltos de línea son eliminados automáticamente del valor introducido.

		- `tel`: campo para introducir un número telefónico.

			> Los saltos de línea son eliminados automáticamente del valor introducido.

		- `email`: campo para introducir una dirección de correo electrónico.

			> El valor introducido se valida para que contenga una cadena vacía o una dirección de correo válida antes de enviarse.

		- `password`: campo para introducir una contraseña.

			> Su valor se oculta (normalmente con asteriscos).

		- `url`: campo para introducir una URL.

			> El valor introducido se valida para que contenga una cadena vacía o una ruta URL absoluta antes de enviarse. Los saltos de línea y espacios en blanco al principio o al final del valor son eliminados automáticamente.

## 45 - Inputs extra

- `<input>`.

	- `type=<value>`.

		- `color`: control para especificar un color.

		- `number`: campo para introducir un número de punto flotante.

		- `range`: control para introducir un número cuyo valor exacto no es importante. Este control usa los siguientes valores predeterminados si no se especifica cada atributo:

			- `min`: $0$.

			- `max`: $100$.

			- `value`: $\frac{ \text{ min } + ( \text{ max } - \text{ min }) }{ 2 }$, o $\text{ min }$ si $\text{ max }$ es menor que $\text{ min }$.

			- `step`: $1$.

		- `reset`: botón que restaura los contenidos de un formulario a sus valores predeterminados.

		- `text`: campo de texto de línea simple.

			> Los saltos de línea son eliminados automáticamente del valor introducido.

## 46 - Input radio

- `<input>`.

	- `type=<value>`.

		- `radio`: botón radio.

			- Se debe usar el atributo `value` para definir el valor que se enviará por este elemento.

			- Se usa el atributo `checked` para indicar si el elemento está seleccionado de forma predeterminada.

			- Los botones radio que tengan el mismo valor para su atributo `name` están dentro del mismo "grupo de botones radio".

				> Solo un botón radio dentro de un grupo puede ser seleccionado a la vez.

## 47 - Input checkbox

- `<input>`.

	- `type=<value>`.

		- `checkbox`: casilla de selección.

			- Se debe usar el atributo `value` para definir el valor que enviará este elemento.

			- Se usa el atributo `checked` para indicar si el elemento está seleccionado de forma predeterminada.

## 48 - Elemento select básico

- `<select>...</select>`: representa un control que muestra un menú de opciones. Las opciones contenidas en el menú son representadas por elementos `<option>`, los cuales pueden ser agrupados por elementos `<optgroup>`.

## 50 - Datalist

- `<datalist>...</datalist>`: contiene un conjunto de elementos `<option>` que representan los valores disponibles para otros controles.

	> Tiene que precederle un `<input>` con un atributo `name=<value>` o `list=<value>` para que, con un atributo `id=<value>` se vincule a la lista.

## 51 - Más elementos para formularios

- `<fieldset>...</fieldset>`: permite organizar en grupos los campos de un formulario.

- `<leyend>...</leyend>`: crea un título para un grupo de campos (`<fieldset>`) de un formulario.

- `<input>`.

	- `type=<value>`.

		- `file`: control que permite al usuario seleccionar un archivo. Se puede usar el atributo `accept` para definir los tipos de archivo que el control podrá seleccionar.

- `<progress>...</progress>`: se utiliza para visualizar el progreso de una tarea.

	- `max=<value>`: este atributo indica la cantidad numérica que demora la finalización de la tarea.

	- `value=<value>`: este atributo indica la cantidad numérica de la tarea que ya se ha completado.

- `<meter>...</meter>`: representa un valor escalar dentro de un rango conocido o un valor fraccionario.

	- `value=<value>`: el valor numérico actual.

	- `min=<value>`: el límite numérico inferior del intervalo medido.

	- `max=<value>`: el límite numérico superior del intervalo medido.

	- `low=<value>`: el límite numérico superior del extremo inferior del rango medido.

		> Si no se especifica, o si es menor que el valor mínimo, el valor `low` es igual al valor mínimo.

	- `high=<value>`: el límite numérico inferior del extremo superior del rango medido.

		> Si no se especifica, o si es mayor que el valor máximo, el valor `high` es igual al valor máximo.

	- `optimum=<value>`: este atributo indica el valor numérico óptimo.

		> Cuando se utiliza con el atributo `low` y el atributo `high`, da una indicación de en qué punto del intervalo se considera preferible.

- `<textarea>...</textarea>`: representa un control para la edición multilínea de texto sin formato.

	- `cols=<value>`: la anchura visible del control de texto, en caracteres de anchura media.

		> Si está definido debe ser positivo. Si no, por defecto, el valor es 20 (HTML 5).

	- `rows=<value>`: el número de líneas visibles en el control.

## 52 - Atributos para formularios

- `<input>`.

	- `placeholder=<value>`: una pista para el usuario sobre lo que puede introducir en el control.

	- `readonly`: indica que el usuario no puede modificar el valor del control.

		> Es ignorado si el atributo type es `hidden`, `range`, `color`, `checkbox`, `radio`, `file`, o de tipo botón (como `button` o `submit`).

	- `disable`: indica que el control no está disponible para interacción.

		> El valor de un control deshabilitado no es enviado con el formulario.

	- `type=<number, range, date, month, week, time, datetime-local>`.

		- `min=<value>`: el valor mínimo.

		- `max=<value>`: el valor máximo.

	- `type=<text, email, search, password, tel, o url>`.

		- `minlength=<number>`: especifica la longitud mínima de caracteres (en puntos de código Unicode) que el usuario puede introducir.

		- `maxlength=<number>`: especifica el número máximo de caracteres (en puntos de código Unicode) que el usuario puede introducir.

- `<option>`.

	- `selected`: indica si esta opción es la inicialmente seleccionada.

- `autofocus`: indica que elemento debe enfocarse al cargar la página, o cuando se muestra el `<dialog>` del que forma parte.

## 53 - Envío GET vs POST

- `<input>`.

	- `name=<value>`: el nombre del control, el cual es enviado con los datos del formulario.

## 54 - ¿Qué es el contenido embebido?

Es el que se inserta dentro de una página web, como videos, imágenes o audios, y que se puede reproducir directamente desde el sitio web.

## Imagenes

Los formatos de imágenes para web los podemos clasificar en 2 tipos:

	1. Vectoriales.

		- svg (Scalable Vector Graphics).

			> Recomendado siempre que se pueda.

	2. Mapa de bits.

		- jpg o jpeg (Joint Photographic Experts Group).

		- png 8 y 24.

			> Si se necesita transparencia.

		- gif

			> Si necesitáis una imagen animada.

		- webp

			> El formato que menos pesa.
