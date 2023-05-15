---
id: uywe3wcmbv2xpjqlcdp39cp
title: 6-Tiempo y costos de una app
desc: ''
updated: 1683587628245
created: 1682471901646
---

- Costo

    Es lo que cuesta elaborar o realizar un producto o servicio.

- Precio

    Es la cantidad de dinero que una empresa espera que se le pague por su producto. Todo lo que se cobra por encima del costo será la utilidad (ganancia).

    > Precio = costos + utilidad estimada, comúnmente se usan porcentajes sobre los costos para la utilidad estimada

- Valor

    Es el monto que se le da a un producto o servicio dentro del mercado según las necesidades de los clientes.

    > Mientras el precio es el monto fijado para un producto o servicio, el valor es en esencia el monto que un cliente está dispuesto a pagar.

# Estimación de costos

## Precio por HU

- Se cobra por cada HU.
- Fácil de entender y de aplicar.
- Se cobra por el esfuerzo requerido para cada HU.
- El cliente puede predecir el impacto de agregar o quitar HU.

> Hay que estimar bien o podría tener impactos en los costos del proyecto.

---

- Para la  estimación de costos, los equipos requieren experiencia en la estimación de los puntos de las HU.

- Estimar cuanto cuesta un punto de HU es el factor clave para la mayoría de cálculos.

- El tamaño del producto (Product Backlog) suele ser el factor determinante más importante del costo del desarrollo de software, independientemente de la metodología específica que se utilice.

- Transformar puntos a horas suele ser una actividad compleja y depende de muchos factores.

---

En la metodología Scrum se recomienda tener equipos de 5 a 10 personas máximo. ¿Qué pasa si es un proyecto es muy grande y se tienen muchos desarrolladores?

La respuesta es **Scrum de Scrums** (una reunión diaria de representantes de cada equipo), el fin de esa reunión puede consistir en contestar las siguientes preguntas:

- ¿Qué ha hecho mi equipo hasta ahora desde la última vez que nos reunimos que podría afectar a otros equipos?

- ¿Qué hará mi equipo antes de que nos volvamos a encontrar que pueda afectar a otros equipos?

- ¿A qué problema se enfrenta mi equipo que podría obtener la ayuda de otro equipo para resolverlo?

---

En las empresas es común que los desarrolladores trabajen en más de un proyecto. ¿Cómo se maneja esto en Scrum?

A la hora de hacer la planeación (sprint cero), se planea si el desarrollador tendrá el tiempo disponible, teniendo es cuenta las siguientes horas gastadas en las siguientes actividades:

- Ceremonias Scrum
- Perdidas por productividad (ocio)
- Otros proyectos

> Lo anterior se compara con el tiempo designado para que el desarrollador cumpla con sus tareas (conversion de sus puntos de hitorias de usuario a tiempo).

# App

Es un programa de software diseñado para realizar tareas específicas.

## Tipos

- Movil
- WEB
- Desktop
- Embedded
- Wearable

## Historia

El World Wide Web (WWW) (web) fue creado por Tim Bernes-Lee y asociados del CERN en 1989, con el propósito de crear un nuevo sistema de información estandarizado.

> Su idea central es el **hipertexto**

# WWW

Es un sistema de distribución de documentos de hipertexto o hipermedia interconectados y accesibles a través de internet.

## Características

- Disponible para múltiples plataformas.
- Es distribuido (puede acceder a información geográficamente dispersa).
- Es dinámico (la información se puede actualizar).
- Es de carácter multimedial (gráficos, texto, sonido, video, etc), puede acceder a muchas tipos de información en internet.
- Es interactivo, es decir, permite la interactividad con los usuarios o entre usuarios.
- Es usado hacer páginas web y aplicaciones web

## Arquitecturas

### Cliente-Servidor

Es un modelo de diseño de software, basado en la prestación y uso de servicios; para lo cual requiere de un servidor (provee los servicios) y un cliente (utiliza los servicios).

- Poseen conexiones son **con-estado**.
- Los servidores de aplicaciones mantienen dos tipos de conexiones con estado:

    - intercliente: estado cuyas actualizaciones deben sincronizarse con las transacciones realizadas por otros clientes.
    - intracliente: estado que debe mantenerse para un cliente dado durante una sesión (que puede abarcar varias conexiones).

### Cliente Web - Servidor Web

Es una extensión de la arquitectura cliente/servidor tradicional, donde las conexiones son **sin-estado**. Consiste en:

- Abrir una conexión
- Obtener un recurso (ejecutar un archivo y obtener la respuesta)
- Cerrar la conexión

---

HTTP es un protocolo sin estado.

- No guarda ninguna información sobre conexiones anteriores.
- Al finalizar la transacción todos los datos se pierden.

    > Por esto se popularizaron las cookies.

# Web server

- Permite compartir recursos soportando procesos simultáneos y controlando el acceso a los servicios.
- Atiende muchos clientes con un solo servidor.
- Ubicación distribuida, es decir, puede controlar procesos en equipos geográficamente dispersos.
- Aplicaciones de plataforma independiente.
- Garantiza la integridad de los servicios que están centralizados en el servidor.

# URL (Universal Resource Identifier)

Es una forma precisa de nombrar y localizar los recursos web de manera unívoca. Está compuesta por:

- URL (Universal Resorce Locator)
- URN (Universal Resorce Name)

## Tipos

- Completa: cuando tiene todas las partes de una URL.

    > http://www.osi.org/cgi-bin/datos.py

- Parcial o relativa: Cuando el protocolo y las partes del servidor(subdominio) no son colocadas, el browser interpreta la URL como relativa a la página actual.

    > cgi-bin/datos.py

- Especiales

    - Cuando no existe un archivo predefinido de inicio (index.html), se muestra el contenido del directorio.
    - Página de error.

# Peticiones HTTP o HTTPS

Una petición de envío o solicitud de información entre el navegador y el servidor web se hace usando **GET** o **POST**.

# Tarea

- Variables de sección de una app web

    Son una forma de mantener la información del usuario a lo largo de múltiples solicitudes web. En una aplicación web, se pueden almacenar variables de sesión para guardar datos del usuario, como su nombre de usuario, preferencias, carrito de compras, etc. Las variables de sesión se pueden guardar en la memoria del servidor o en una base de datos.

- Diferencia entre apache y ngix

    Ambos son servidores web populares utilizados para alojar sitios web. Apache es un servidor web gratuito y de código abierto que es compatible con muchos sistemas operativos y lenguajes de programación, y es más adecuado para sitios web pequeños y medianos. Nginx también es un servidor web gratuito y de código abierto, que se utiliza principalmente como servidor proxy y balanceador de carga, y es más adecuado para sitios web de alto tráfico y aplicaciones web que requieren una alta concurrencia.

- Diferencias entre el método GET y POST

    GET y POST son dos de los métodos HTTP utilizados para enviar y recibir datos en una solicitud web. GET se utiliza para solicitar recursos de un servidor web y pasar parámetros a través de la URL. Es útil para solicitudes de solo lectura, como buscar información o cargar una página web. POST, por otro lado, se utiliza para enviar datos a un servidor web, como enviar un formulario de registro o enviar un correo electrónico. La información se envía en el cuerpo de la solicitud y no en la URL. POST es útil para enviar información que debe ser procesada, actualizada o almacenada en el servidor.